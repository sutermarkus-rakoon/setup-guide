---
layout: default
---

# Developer Setup Guide

> **From zero to deployed** — everything you need to start building with Claude Code, GitHub, and Cloud Infrastructure. No prior experience required.

This guide covers two paths to get your project live:

| | Path A: Railway | Path B: Azure |
|---|---|---|
| **Complexity** | Simple, fast | More setup, more control |
| **Best for** | Side projects, startups, MVPs | Business apps, compliance, enterprise |
| **Deploy time** | ~10 minutes | ~45 minutes |
| **Cost (Dev)** | ~$5/month | ~$40–50/month |
| **Auto-deploy** | Yes (on git push) | Yes (via GitHub Actions) |

Both paths share the same foundation: **Claude Code + GitHub**. Pick your cloud at the end.

![Architecture Overview — How Coding, Versioning, and Hosting fit together](architecture.svg)

---

## Table of Contents

1. [Prerequisites](#1-prerequisites)
2. [Git & GitHub](#2-git--github)
3. [Claude Code](#3-claude-code)
4. [Your First Project](#4-your-first-project)
5. [Path A: Deploy to Railway](#5-path-a-deploy-to-railway)
6. [Path B: Deploy to Azure](#6-path-b-deploy-to-azure)
7. [Comparison & FAQ](#7-comparison--faq)

---

## 1. Prerequisites

Before we start, you need a few things installed on your machine.

### 1.1 A Terminal

You'll be typing commands in a terminal. Here's how to open one:

- **Windows**: Press `Win + R`, type `cmd` or use **Windows Terminal** from the Microsoft Store (recommended)
- **macOS**: Press `Cmd + Space`, type `Terminal`
- **Linux**: Press `Ctrl + Alt + T`

### 1.2 Install Node.js

Node.js is the runtime that powers most modern web tools.

1. Go to [https://nodejs.org](https://nodejs.org)
2. Download the **LTS** version (green button)
3. Run the installer, accept all defaults
4. Verify it works:

```bash
node --version
# Should print something like: v22.x.x

npm --version
# Should print something like: 10.x.x
```

### 1.3 Install Git

Git tracks your code changes and syncs with GitHub.

- **Windows**: Download from [https://git-scm.com/download/win](https://git-scm.com/download/win) — install with all defaults
- **macOS**: Run `git --version` in Terminal — it will prompt you to install if needed
- **Linux**: `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora)

Verify:

```bash
git --version
# Should print something like: git version 2.x.x
```

### 1.4 Configure Git (one-time setup)

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## 2. Git & GitHub

### 2.1 What is Git vs. GitHub?

- **Git** = version control on your computer. It tracks every change you make.
- **GitHub** = a website that stores your Git repositories online, so you can collaborate and deploy.

Think of it like this: Git is the save system, GitHub is the cloud storage.

### 2.2 Create a GitHub Account

1. Go to [https://github.com](https://github.com)
2. Click **Sign up**
3. Choose a username, enter your email, create a password
4. Verify your email

### 2.3 Install the GitHub CLI

The GitHub CLI (`gh`) lets you interact with GitHub from your terminal.

- **Windows**: `winget install GitHub.cli`
- **macOS**: `brew install gh`
- **Linux**: See [https://github.com/cli/cli/blob/trunk/docs/install_linux.md](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)

Then authenticate:

```bash
gh auth login
```

Choose:
- **GitHub.com**
- **HTTPS**
- **Login with a web browser**

A browser window opens — log in and authorize.

### 2.4 Essential Git Commands

Here's a cheat sheet of the commands you'll use most:

```bash
# Check what files have changed
git status

# Stage files for commit
git add filename.txt          # specific file
git add .                     # all changed files

# Save a snapshot (commit)
git commit -m "describe what you changed"

# Push your commits to GitHub
git push

# Pull latest changes from GitHub
git pull

# Create a new branch
git checkout -b feature/my-new-feature

# Switch between branches
git checkout main
git checkout feature/my-new-feature
```

> **Tip**: You don't need to memorize these. Claude Code can run all git commands for you — just ask it in plain English: *"commit my changes"*, *"create a new branch called feature/login"*.

---

## 3. Claude Code

### 3.1 What is Claude Code?

Claude Code is an AI coding assistant that runs in your terminal. It can:

- Read and understand your entire codebase
- Write, edit, and refactor code
- Run commands (build, test, deploy)
- Search the web for documentation
- Work with Git and GitHub
- Debug errors and fix bugs

It's like having a senior developer pair-programming with you, right in your terminal.

### 3.2 Get Access

Claude Code requires a paid subscription. You need **one** of these:

| Option | Cost | Best for |
|--------|------|----------|
| **Claude Pro** | $20/month | Individuals getting started |
| **Claude Max** | $100–200/month | Heavy usage, more capacity |
| **Claude for Teams** | $30/user/month | Team collaboration |
| **API Credits** | Pay-as-you-go | Flexible billing |

Sign up at [https://claude.ai](https://claude.ai) and choose a plan.

### 3.3 Install Claude Code

**Windows** (PowerShell):

```powershell
irm https://claude.ai/install.ps1 | iex
```

**macOS / Linux**:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Verify:

```bash
claude --version
```

### 3.4 First Launch & Authentication

```bash
# Navigate to your project folder
cd /path/to/your/project

# Start Claude Code
claude
```

On first launch:
1. A browser window opens automatically
2. Log in with your Claude account
3. Authorize Claude Code
4. You're ready!

> If the browser doesn't open, press `c` to copy the login URL manually.

### 3.5 Basic Usage

Once Claude Code is running, just type what you want in plain English:

```
> explain what this project does

> find all files that handle user login

> fix the bug where the page shows a blank screen after login

> write unit tests for the checkout function

> commit my changes with a descriptive message

> create a pull request
```

### 3.6 Key Commands

| Command | What it does |
|---------|-------------|
| `claude` | Start a new session |
| `claude -c` | Continue your last conversation |
| `claude -r` | Resume a previous session |
| `/help` | Show all available commands |
| `/clear` | Reset the conversation context |
| `/compact` | Summarize conversation (saves memory) |
| `Shift+Tab` | Toggle permission mode (Plan → Normal → Auto) |
| `Esc` | Stop Claude mid-action |
| `Ctrl+C` | Exit Claude Code |

### 3.7 Permission Modes

Claude Code has three permission modes that control how much autonomy it has:

| Mode | Description | When to use |
|------|-------------|-------------|
| **Plan** | Read-only. Claude analyzes but doesn't change anything. | Exploring unfamiliar code |
| **Normal** | Claude asks permission before each change. | Default, recommended for beginners |
| **Auto** | Claude makes changes without asking. | When you trust it and want speed |

Toggle with `Shift+Tab` during a session.

### 3.7.1 YOLO Mode: `--dangerously-skip-permissions`

> ⚠️ **USE WITH CAUTION** — This flag is extremely efficient but skips ALL safety checks. Claude will execute any action (edit files, run commands, delete things) without asking you first. Only use this if you know what you're doing and trust your instructions.

```bash
claude --dangerously-skip-permissions
```

**Why it's powerful**: No more clicking "approve" on every file edit or command. Claude just does everything — fast, autonomous, no interruptions. Great for repetitive tasks, large refactors, or when you have a solid CLAUDE.md guiding it.

**Why it's dangerous**: Claude can and will run destructive commands if it thinks that's the right solution. There's no "are you sure?" — it just does it. One wrong instruction and files are gone, databases are wiped, or code is pushed.

**Rules of thumb:**
- ✅ Use it on throwaway branches or projects you can restore
- ✅ Use it when your CLAUDE.md is well-defined and tested
- ✅ Use it for read-heavy tasks (analysis, code review)
- ❌ Never use it on production databases or critical infrastructure
- ❌ Never use it if you're unsure what Claude might do
- ❌ Never use it without version control (git) as a safety net

### 3.8 CLAUDE.md — Project Instructions

`CLAUDE.md` is a special file in your project root that tells Claude about your project. It's loaded automatically every session.

**Auto-generate one:**

```bash
claude /init
```

**Or create manually** — `CLAUDE.md`:

```markdown
# My Project

## Tech Stack
- Frontend: React + TypeScript
- Backend: Node.js, Express
- Database: PostgreSQL
- Deploy: Railway

## Commands
- Dev server: npm run dev
- Build: npm run build
- Test: npm test

## Code Style
- Use TypeScript for all new files
- Use ES modules (import/export)
- Write tests for new features
```

### 3.9 Team Setup

When working with others, commit these files to your repo:

```
your-project/
├── CLAUDE.md                    # Shared project instructions
├── .claude/
│   ├── settings.json            # Shared permission rules
│   └── settings.local.json      # Personal overrides (gitignore this!)
```

**Shared permissions** — `.claude/settings.json`:

```json
{
  "permissions": {
    "allow": [
      "Bash(npm install)",
      "Bash(npm test)",
      "Bash(npm run build)",
      "Bash(npm run dev)"
    ]
  }
}
```

This way, every team member gets the same Claude Code experience.

---

## 4. Your First Project

Let's put it all together. We'll create a project, push it to GitHub, and prepare it for deployment.

### 4.1 Create a New Project

```bash
# Create project folder
mkdir my-app
cd my-app

# Initialize Node.js project
npm init -y

# Initialize Git
git init
```

### 4.2 Start Claude Code

```bash
claude
```

Ask Claude to scaffold your project:

```
> set up a basic Next.js app with TypeScript
```

Claude will create all the files, install dependencies, and configure everything.

### 4.3 Push to GitHub

```bash
# Create a new repo on GitHub and push
gh repo create my-app --public --source=. --push
```

Your code is now on GitHub. From here, choose your deployment path:

---

## 5. Path A: Deploy to Railway

> **Best for**: Side projects, startups, MVPs. Simple and fast.

### 5.1 What is Railway?

Railway is a modern cloud platform that makes deploying apps effortless. Connect your GitHub repo, and it deploys automatically on every push. No DevOps knowledge needed.

### 5.2 Create an Account

1. Go to [https://railway.com](https://railway.com)
2. Click **Sign up** → **Sign in with GitHub**
3. Authorize Railway
4. You get a **30-day free trial** with $5 credit

> **Note**: After the trial, the Hobby plan is $5/month (includes $5 usage credit — most small apps run for free within this).

### 5.3 Deploy Your App

**Via Dashboard (easiest):**

1. Click **New Project** → **Deploy from GitHub Repo**
2. Select your repository
3. Railway auto-detects your app type and builds it
4. Your app is live within minutes!

**Via CLI:**

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login
railway login

# Link to your project
railway link

# Deploy
railway deploy
```

### 5.4 Add a PostgreSQL Database

1. In your Railway project dashboard, click **+ New** → **Database** → **PostgreSQL**
2. Railway creates the database instantly
3. The `DATABASE_URL` environment variable is automatically available to your app

That's it — no connection strings to copy, no configuration files.

### 5.5 Environment Variables

1. Click on your service in the dashboard
2. Go to **Variables** tab
3. Add your variables:

```
ANTHROPIC_API_KEY=sk-ant-...
NODE_ENV=production
```

Or via CLI:

```bash
railway variables set ANTHROPIC_API_KEY=sk-ant-...
```

### 5.6 Custom Domain

1. Click your service → **Settings** → **Domains**
2. Click **+ Custom Domain**
3. Enter your domain (e.g., `myapp.com`)
4. Add the CNAME record at your DNS provider
5. SSL is automatic and free

### 5.7 That's It!

Every time you `git push`, Railway automatically rebuilds and deploys. Your workflow:

```
Write code → git push → Railway deploys → Live in ~60 seconds
```

---

## 6. Path B: Deploy to Azure

> **Best for**: Business applications, compliance requirements, enterprise teams.

### 6.1 What is Azure?

Microsoft Azure is an enterprise cloud platform with 60+ global data centers. It offers compliance certifications (HIPAA, SOC 2, GDPR), advanced security, and deep integration with the Microsoft ecosystem.

### 6.2 Create an Account

1. Go to [https://azure.microsoft.com/free](https://azure.microsoft.com/free)
2. Click **Start free**
3. Sign in with a Microsoft account (or create one)
4. Verify identity with a credit card (temporary $1 hold, reversed after verification)
5. You get **$200 free credit for 30 days** + many always-free services

### 6.3 Install Azure CLI

**Windows:**

```powershell
winget install Microsoft.AzureCLI
```

**macOS:**

```bash
brew install azure-cli
```

**Linux:**

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

Then log in:

```bash
az login
# A browser opens — sign in with your Azure account
```

### 6.4 Create Infrastructure

```bash
# 1. Create a Resource Group (a container for your resources)
az group create --name my-app-rg --location westeurope

# 2. Create an App Service Plan (the server your app runs on)
az appservice plan create \
  --name my-app-plan \
  --resource-group my-app-rg \
  --sku B1 \
  --is-linux

# 3. Create the Web App
az webapp create \
  --name my-app-name \
  --resource-group my-app-rg \
  --plan my-app-plan \
  --runtime "node:20-lts"
```

> **Tip**: `--name` must be globally unique. Try something like `my-app-yourname`.

### 6.5 Add PostgreSQL

```bash
# Create a PostgreSQL Flexible Server
az postgres flexible-server create \
  --name my-app-db \
  --resource-group my-app-rg \
  --location westeurope \
  --sku-name Standard_B1ms \
  --storage-size 32 \
  --admin-user myadmin \
  --admin-password "YourSecurePassword123!"

# Create a database
az postgres flexible-server db create \
  --resource-group my-app-rg \
  --server-name my-app-db \
  --database-name myappdb
```

Your connection string will be:

```
postgresql://myadmin:YourSecurePassword123!@my-app-db.postgres.database.azure.com:5432/myappdb?sslmode=require
```

### 6.6 Environment Variables

```bash
az webapp config appsettings set \
  --name my-app-name \
  --resource-group my-app-rg \
  --settings \
    DATABASE_URL="postgresql://myadmin:YourSecurePassword123!@my-app-db.postgres.database.azure.com:5432/myappdb?sslmode=require" \
    ANTHROPIC_API_KEY="sk-ant-..." \
    NODE_ENV="production"
```

### 6.7 Set Up CI/CD with GitHub Actions

Create the file `.github/workflows/deploy.yml` in your project:

```yaml
name: Deploy to Azure

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: '20'

      - run: npm install
      - run: npm run build

      - uses: azure/webapps-deploy@v3
        with:
          app-name: 'my-app-name'
          publish-profile: ${{ secrets.AZURE_PUBLISH_PROFILE }}
          package: .
```

**Get your publish profile:**

1. Azure Portal → your App Service → **Deployment Center** → **Manage publish profile** → **Download**
2. Copy the entire XML content
3. GitHub → your repo → **Settings** → **Secrets and variables** → **Actions** → **New repository secret**
4. Name: `AZURE_PUBLISH_PROFILE`, Value: paste the XML

Now every push to `main` automatically deploys to Azure.

### 6.8 Custom Domain

1. Azure Portal → your App Service → **Custom domains**
2. Click **+ Add custom domain**
3. Enter your domain
4. Add the DNS records (A record + TXT record) at your DNS provider
5. Azure provides free SSL via managed certificates

### 6.9 Useful Azure CLI Commands

```bash
# View logs in real-time
az webapp log tail --name my-app-name --resource-group my-app-rg

# Restart the app
az webapp restart --name my-app-name --resource-group my-app-rg

# Check app status
az webapp show --name my-app-name --resource-group my-app-rg --query state

# Scale up (more power)
az appservice plan update --name my-app-plan --resource-group my-app-rg --sku B2

# List all your resources
az resource list --resource-group my-app-rg --output table
```

---

## 7. Comparison & FAQ

### Side-by-Side Comparison

| Feature | Railway | Azure |
|---------|---------|-------|
| **Setup time** | ~10 min | ~45 min |
| **Learning curve** | Easy | Steep |
| **Auto-deploy from GitHub** | Built-in | Via GitHub Actions |
| **PostgreSQL** | One click | CLI or Portal |
| **SSL/HTTPS** | Automatic, free | Automatic, free |
| **Custom domains** | Yes | Yes |
| **Pricing (Dev)** | ~$5/month | ~$40–50/month |
| **Pricing (Prod)** | ~$20–50/month | ~$100–400/month |
| **Free tier** | 30-day trial ($5) | 30-day trial ($200) |
| **Compliance (HIPAA, SOC2)** | Limited | Full |
| **Multi-region** | Limited | 60+ regions |
| **Private networking** | No | Yes (VNet) |
| **Monitoring** | Basic | Advanced (App Insights) |
| **Best for** | Indie devs, startups | Enterprise, regulated industries |

### FAQ

**Q: Which path should I choose?**
> If you're building a side project or startup MVP, choose **Railway**. If you're building for a company that needs compliance, security certifications, or Microsoft integration, choose **Azure**.

**Q: Can I switch later?**
> Yes! Your code stays the same. Only the deployment target changes. Moving from Railway to Azure (or vice versa) mainly means updating environment variables and deploy configuration.

**Q: How much will it cost me?**
> Railway: $5/month gets most small apps running. Azure: expect $40–50/month minimum for a web app + database in development.

**Q: Do I need to know DevOps?**
> For Railway: No. For Azure: basic understanding helps, but this guide covers everything you need.

**Q: Can I use Claude Code without Railway or Azure?**
> Absolutely! Claude Code works locally on your machine. Railway/Azure are only needed when you want to deploy your app to the internet.

**Q: Is my API key safe?**
> Yes, as long as you store it in environment variables (Railway dashboard or Azure App Settings) and never commit it to your code. Add `.env` to your `.gitignore` file.

---

## Quick Reference Card

### Daily Workflow

```bash
# Start your day
cd my-project
claude                    # Start Claude Code

# Work with Claude
> fix the login bug
> add a dark mode toggle
> write tests for the new feature

# Save and deploy
> commit my changes
> push to GitHub
# Railway/Azure auto-deploys!
```

### Useful Links

| Resource | URL |
|----------|-----|
| GitHub | [github.com](https://github.com) |
| Claude AI | [claude.ai](https://claude.ai) |
| Claude Code Docs | [docs.anthropic.com/en/docs/claude-code](https://docs.anthropic.com/en/docs/claude-code) |
| Railway | [railway.com](https://railway.com) |
| Railway Docs | [docs.railway.com](https://docs.railway.com) |
| Azure Portal | [portal.azure.com](https://portal.azure.com) |
| Azure Docs | [learn.microsoft.com/azure](https://learn.microsoft.com/azure) |
| Node.js | [nodejs.org](https://nodejs.org) |
| Git | [git-scm.com](https://git-scm.com) |

---

*Last updated: March 2026. Built with Claude Code.*
