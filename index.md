---
layout: default
---

# Developer Setup Guide

**v1.1** · Published March 4, 2026 · Author: M. Suter, Switzerland

> **From zero to deployed** — everything you need to start building with Claude Code, GitHub, and Cloud Infrastructure. No prior experience required.

<p align="center" style="margin: 1.5em 0;">
  <a href="claude-setup-assistant.txt" download="claude-setup-assistant.md" style="display: inline-block; background: #f97316; color: white; padding: 14px 28px; border-radius: 10px; font-size: 18px; font-weight: 700; text-decoration: none; cursor: pointer;">Download Setup Assistant for Claude.ai</a>
  <br>
  <em style="font-size: 14px; color: #64748b;">Save the file, then upload it to <a href="https://claude.ai">Claude.ai</a> — it will walk you through the entire setup step by step.</em>
</p>

<!-- ==================== BASIC TAB ==================== -->
<div id="tab-basic" class="tab-panel active" markdown="1">

![Architecture Overview — How Coding, Versioning, and Hosting fit together](architecture.svg)

This guide covers two paths. Both use **Claude Code + GitHub** — they only differ in where your app is hosted:

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left;"></th>
      <th style="padding:10px 14px; text-align:left;">Path A: Railway</th>
      <th style="padding:10px 14px; text-align:left;">Path B: Azure</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>What is it?</strong></td>
      <td style="padding:8px 14px;">Modern, simple cloud platform</td>
      <td style="padding:8px 14px;">Microsoft enterprise cloud</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Best for</strong></td>
      <td style="padding:8px 14px;">Side projects, startups, MVPs</td>
      <td style="padding:8px 14px;">Business apps, compliance, enterprise</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Complexity</strong></td>
      <td style="padding:8px 14px;">Easy — connect GitHub, done</td>
      <td style="padding:8px 14px;">More setup, more control</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Deploy time</strong></td>
      <td style="padding:8px 14px;">~10 minutes</td>
      <td style="padding:8px 14px;">~45 minutes</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Auto-deploy</strong></td>
      <td style="padding:8px 14px;">Yes (on git push)</td>
      <td style="padding:8px 14px;">Yes (via GitHub Actions)</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>EU data residency</strong></td>
      <td style="padding:8px 14px;">Limited (US servers)</td>
      <td style="padding:8px 14px;">Yes (<code>westeurope</code>, <code>switzerlandnorth</code>)</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Compliance (GDPR, SOC2)</strong></td>
      <td style="padding:8px 14px;">Limited</td>
      <td style="padding:8px 14px;">Full</td>
    </tr>
    <tr style="background:#1e293b; color:white;">
      <td style="padding:10px 14px;" colspan="3"><strong>Monthly Cost</strong></td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Claude Pro</strong> (required)</td>
      <td style="padding:8px 14px;">$20/month</td>
      <td style="padding:8px 14px;">$20/month</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>GitHub</strong></td>
      <td style="padding:8px 14px;">Free</td>
      <td style="padding:8px 14px;">Free</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Hosting + Database</strong></td>
      <td style="padding:8px 14px;">~$5/month</td>
      <td style="padding:8px 14px;">~$42/month</td>
    </tr>
    <tr style="background:#e2e8f0; font-weight:bold;">
      <td style="padding:10px 14px;"><strong>Total</strong></td>
      <td style="padding:10px 14px;"><strong>~$25/month</strong></td>
      <td style="padding:10px 14px;"><strong>~$62/month</strong></td>
    </tr>
  </tbody>
</table>

> Claude Pro ($20/month) is required for Claude Code. For heavy usage, Claude Max ($100–200/month) gives higher limits. Free Claude accounts can only use Claude.ai in the browser — not Claude Code.

> **Don't want to read all this?** Download the [Setup Assistant](claude-setup-assistant.md) file, upload it to [Claude.ai](https://claude.ai), and it will walk you through the entire setup step by step — like a personal tutor. No reading required.

---

## Table of Contents

0. [Before You Start — What Are You Building?](#0-before-you-start--what-are-you-building)
1. [The Workflow](#1-the-workflow)
2. [Prerequisites](#2-prerequisites)
3. [Git & GitHub](#3-git--github)
4. [Claude Code](#4-claude-code)
5. [Your First Project](#5-your-first-project)
6. [Path A: Deploy to Railway](#6-path-a-deploy-to-railway)
7. [Path B: Deploy to Azure](#7-path-b-deploy-to-azure)
8. [Security & Privacy](#8-security--privacy)
9. [Comparison & FAQ](#9-comparison--faq)

---

## 0. Before You Start — What Are You Building?

Before you install anything, take 2 minutes to answer these questions. They determine which path is right for you — and what you need to think about from day one.

### What's your project type?

| Question | → Hobby / Side Project | → Startup / MVP | → Business / Enterprise |
|----------|----------------------|-----------------|------------------------|
| Who is it for? | Just me, friends | Early users, public | Paying customers, company |
| Will it handle user data? | No / minimal | Some (emails, profiles) | Yes (personal data, payments) |
| Does it need to comply with laws? | No | Maybe (Terms of Service) | Yes (GDPR, DSGVO, HIPAA) |
| Will it process payments? | No | Maybe later | Yes |
| Does your company have IT policies? | No | No | Probably yes |
| How bad is it if the app goes down? | No big deal | Annoying | Costs money / reputation |

### Your result:

**Mostly left column? → Path A: Railway**
- Get started fast, worry about the rest later
- Perfect for learning, prototyping, and side projects
- You can always migrate to Azure later

**Mostly middle column? → Path A: Railway, but read [Section 8: Security & Privacy](#8-security--privacy)**
- Railway is fine to start, but you need to think about data protection early
- Set up proper authentication, HTTPS (automatic), and privacy policies
- Plan your migration path to Azure if you grow

**Mostly right column? → Path B: Azure**
- Start with the enterprise setup from day one
- You need compliance certifications, audit logs, and data residency
- It's more work upfront, but saves you from painful migrations later

### Common mistakes to avoid

> **"I'll add security later"** — No. If your app collects user data (emails, names, locations), you need HTTPS, secure authentication, and a privacy policy from day one. The good news: both Railway and Azure provide HTTPS automatically.

> **"I'll just use a free database somewhere"** — Free database tiers often have no backups, no encryption, and servers in the US (which may violate EU data protection laws if your users are in Europe). Use Railway's or Azure's managed databases instead.

> **"I'll store API keys in my code"** — Never. One accidental `git push` and your keys are public. Always use environment variables (see [Security & Privacy](#8-security--privacy)).

> **"I don't need version control for a small project"** — You do. Git is your undo button. Without it, one bad change can destroy hours of work.

---

## 1. The Workflow

Building a project involves four phases. Here's what you use at each stage:

### Phase 1: Concept & Design → Claude.ai (Browser)

Before writing any code, you start with an idea. Open [claude.ai](https://claude.ai) in your browser and describe your project. Claude helps you:

- **Brainstorm** features and user flows
- **Create mockups** — describe what your app should look like, and Claude generates text-based wireframes
- **Plan architecture** — what tech stack, what database, how should it work?
- **Write specs** — Claude turns your vague idea into a clear project description

**Example conversation with Claude.ai:**

```
You: I want to build an app where bands can find venues to play at.
     It should show venues on a map, with ratings and contact info.

Claude: Great idea! Here's a suggested architecture:
        - Frontend: Next.js with TypeScript
        - Database: PostgreSQL for venues, ratings, and user data
        - Map: Leaflet.js with OpenStreetMap
        - Here's a mockup of the main screen...
```

The output of this phase is a **clear project description** that you'll use in the next phase.

> **Critical: Document as you go!** Claude.ai chats have a context limit. After long conversations, Claude starts forgetting earlier details. To avoid this:
>
> 1. **Ask Claude to create markdown summaries** at every milestone: *"Summarize everything we've decided so far as a markdown document"*
> 2. **Save these markdowns locally** (copy-paste into a `.md` file on your computer)
> 3. **Start new chats for new topics** — don't cram everything into one endless conversation
> 4. **Upload your summary markdown** at the start of each new chat so Claude has the full context
>
> Think of it like saving your game. If you don't save, you might lose progress. A well-written markdown is your save file.
>
> **Example flow:**
> ```
> Chat 1: Brainstorm idea → save concept.md
> Chat 2: Upload concept.md → design database → save database-schema.md
> Chat 3: Upload concept.md + database-schema.md → plan API → save api-spec.md
> ```

### Phase 2: Build → Claude Code (Terminal)

Now you build it. Open your terminal, navigate to your project folder, and type `claude`. Paste your concept from Phase 1, and Claude Code writes the actual code:

```bash
cd my-project
claude
> Here's my project concept: [paste from Claude.ai]
> Build this step by step.
```

Claude Code reads, writes, and runs code on your machine. You describe what you want in plain English, and it builds it.

> **Critical: Set up Claude Code properly!** Claude Code is only as good as the instructions you give it. Do this from day one:
>
> 1. **Run `/init`** — Claude analyzes your project and creates a `CLAUDE.md` file. This file is loaded at every session start and tells Claude what your project is, which commands to use, and how your code is structured. A good `CLAUDE.md` = fewer mistakes.
>
> 2. **Keep `CLAUDE.md` updated** — When your project evolves (new tech, new commands, new conventions), update the file. Ask Claude: *"update CLAUDE.md with our current setup"*
>
> 3. **Use `/compact` in long sessions** — Claude Code also has a context limit. When a session gets long, type `/compact` to summarize the conversation and free up space. Do this before Claude starts making mistakes or forgetting earlier changes.
>
> 4. **Start new sessions for new tasks** — Don't build your entire app in one session. Finish a feature, commit, exit (`Ctrl+C`), then start fresh with `claude`. Each new session reads your `CLAUDE.md` and starts clean.
>
> 5. **Commit before risky changes** — Before asking Claude to do something big (refactor, delete, restructure), commit your current work: *"commit everything"*. If Claude messes up, you can undo with `git checkout .`

### Phase 3: Version Control → GitHub

Every time you reach a milestone, save your progress:

```
> commit my changes and push to GitHub
```

GitHub stores every version of your code. If something breaks, you can always go back.

### Phase 4: Deploy → Railway or Azure

Once your code is on GitHub, your cloud provider automatically deploys it. Every `git push` triggers a new deployment. Your app is live within minutes.

**That's the loop:** *Concept → Build → Push → Live. Repeat.*

---

## 2. Prerequisites

Before we start, you need a few things installed on your machine.

### 2.1 A Terminal

You'll be typing commands in a terminal. Here's how to open one:

- **Windows**: Press `Win + R`, type `cmd` or use **Windows Terminal** from the Microsoft Store (recommended)
- **macOS**: Press `Cmd + Space`, type `Terminal`
- **Linux**: Press `Ctrl + Alt + T`

### 2.2 Install Node.js

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

### 2.3 Install Git

Git tracks your code changes and syncs with GitHub.

- **Windows**: Download from [https://git-scm.com/download/win](https://git-scm.com/download/win) — install with all defaults
- **macOS**: Run `git --version` in Terminal — it will prompt you to install if needed
- **Linux**: `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora)

Verify:

```bash
git --version
# Should print something like: git version 2.x.x
```

### 2.4 Configure Git (one-time setup)

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## 3. Git & GitHub

### 3.1 What is Git vs. GitHub?

- **Git** = version control on your computer. It tracks every change you make.
- **GitHub** = a website that stores your Git repositories online, so you can collaborate and deploy.

Think of it like this: Git is the save system, GitHub is the cloud storage.

### 3.2 Create a GitHub Account

1. Go to [https://github.com](https://github.com)
2. Click **Sign up**
3. Choose a username, enter your email, create a password
4. Verify your email

### 3.3 Install the GitHub CLI

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

### 3.4 Essential Git Commands

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

## 4. Claude Code

### 4.1 What is Claude Code?

Claude Code is an AI coding assistant that runs in your terminal. It can:

- Read and understand your entire codebase
- Write, edit, and refactor code
- Run commands (build, test, deploy)
- Search the web for documentation
- Work with Git and GitHub
- Debug errors and fix bugs

It's like having a senior developer pair-programming with you, right in your terminal.

### 4.2 Get Access

Claude Code requires a paid subscription. You need **one** of these:

| Option | Cost | Best for |
|--------|------|----------|
| **Claude Pro** | $20/month | Individuals getting started |
| **Claude Max** | $100–200/month | Heavy usage, more capacity |
| **Claude for Teams** | $30/user/month | Team collaboration |
| **API Credits** | Pay-as-you-go | Flexible billing |

Sign up at [https://claude.ai](https://claude.ai) and choose a plan.

### 4.3 Install Claude Code

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

### 4.4 First Launch & Authentication

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

### 4.5 Basic Usage

Once Claude Code is running, just type what you want in plain English:

```
> explain what this project does

> find all files that handle user login

> fix the bug where the page shows a blank screen after login

> write unit tests for the checkout function

> commit my changes with a descriptive message

> create a pull request
```

### 4.6 Key Commands

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

### 4.7 Permission Modes

Claude Code has three permission modes that control how much autonomy it has:

| Mode | Description | When to use |
|------|-------------|-------------|
| **Plan** | Read-only. Claude analyzes but doesn't change anything. | Exploring unfamiliar code |
| **Normal** | Claude asks permission before each change. | Default, recommended for beginners |
| **Auto** | Claude makes changes without asking. | When you trust it and want speed |

Toggle with `Shift+Tab` during a session.

### 4.7.1 YOLO Mode: `--dangerously-skip-permissions`

> **USE WITH CAUTION** — This flag is extremely efficient but skips ALL safety checks. Claude will execute any action (edit files, run commands, delete things) without asking you first. Only use this if you know what you're doing and trust your instructions.

```bash
claude --dangerously-skip-permissions
```

**Why it's powerful**: No more clicking "approve" on every file edit or command. Claude just does everything — fast, autonomous, no interruptions. Great for repetitive tasks, large refactors, or when you have a solid CLAUDE.md guiding it.

**Why it's dangerous**: Claude can and will run destructive commands if it thinks that's the right solution. There's no "are you sure?" — it just does it. One wrong instruction and files are gone, databases are wiped, or code is pushed.

**Rules of thumb:**
- Use it on throwaway branches or projects you can restore
- Use it when your CLAUDE.md is well-defined and tested
- Use it for read-heavy tasks (analysis, code review)
- Never use it on production databases or critical infrastructure
- Never use it if you're unsure what Claude might do
- Never use it without version control (git) as a safety net

### 4.8 CLAUDE.md — Project Instructions

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

### 4.9 Team Setup

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

## 5. Your First Project

Let's put it all together. We'll create a project, push it to GitHub, and prepare it for deployment.

### 7.1 Create a New Project

```bash
# Create project folder
mkdir my-app
cd my-app

# Initialize Node.js project
npm init -y

# Initialize Git
git init
```

### 7.2 Start Claude Code

```bash
claude
```

Ask Claude to scaffold your project:

```
> set up a basic Next.js app with TypeScript
```

Claude will create all the files, install dependencies, and configure everything.

### 7.3 Push to GitHub

```bash
# Create a new repo on GitHub and push
gh repo create my-app --public --source=. --push
```

Your code is now on GitHub. From here, choose your deployment path:

---

## 6. Path A: Deploy to Railway

> **Best for**: Side projects, startups, MVPs. Simple and fast.

### 7.1 What is Railway?

Railway is a modern cloud platform that makes deploying apps effortless. Connect your GitHub repo, and it deploys automatically on every push. No DevOps knowledge needed.

### 7.2 Create an Account

1. Go to [https://railway.com](https://railway.com)
2. Click **Sign up** → **Sign in with GitHub**
3. Authorize Railway
4. You get a **30-day free trial** with $5 credit

> **Note**: After the trial, the Hobby plan is $5/month (includes $5 usage credit — most small apps run for free within this).

### 7.3 Deploy Your App

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

### 7.4 Add a PostgreSQL Database

1. In your Railway project dashboard, click **+ New** → **Database** → **PostgreSQL**
2. Railway creates the database instantly
3. The `DATABASE_URL` environment variable is automatically available to your app

That's it — no connection strings to copy, no configuration files.

### 7.5 Environment Variables

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

### 7.6 Custom Domain

1. Click your service → **Settings** → **Domains**
2. Click **+ Custom Domain**
3. Enter your domain (e.g., `myapp.com`)
4. Add the CNAME record at your DNS provider
5. SSL is automatic and free

### 7.7 That's It!

Every time you `git push`, Railway automatically rebuilds and deploys. Your workflow:

```
Write code → git push → Railway deploys → Live in ~60 seconds
```

---

## 7. Path B: Deploy to Azure

> **Best for**: Business applications, compliance requirements, enterprise teams.

### 7.1 What is Azure?

Microsoft Azure is an enterprise cloud platform with 60+ global data centers. It offers compliance certifications (HIPAA, SOC 2, GDPR), advanced security, and deep integration with the Microsoft ecosystem.

### 7.2 Create an Account

1. Go to [https://azure.microsoft.com/free](https://azure.microsoft.com/free)
2. Click **Start free**
3. Sign in with a Microsoft account (or create one)
4. Verify identity with a credit card (temporary $1 hold, reversed after verification)
5. You get **$200 free credit for 30 days** + many always-free services

### 7.3 Install Azure CLI

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

### 7.4 Create Infrastructure

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

### 7.5 Add PostgreSQL

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

### 7.6 Environment Variables

```bash
az webapp config appsettings set \
  --name my-app-name \
  --resource-group my-app-rg \
  --settings \
    DATABASE_URL="postgresql://myadmin:YourSecurePassword123!@my-app-db.postgres.database.azure.com:5432/myappdb?sslmode=require" \
    ANTHROPIC_API_KEY="sk-ant-..." \
    NODE_ENV="production"
```

### 7.7 Set Up CI/CD with GitHub Actions

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

### 7.8 Custom Domain

1. Azure Portal → your App Service → **Custom domains**
2. Click **+ Add custom domain**
3. Enter your domain
4. Add the DNS records (A record + TXT record) at your DNS provider
5. Azure provides free SSL via managed certificates

### 7.9 Useful Azure CLI Commands

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

## 8. Security & Privacy

This section is essential reading. Skipping it can lead to leaked API keys, legal trouble, or data breaches. It only takes 5 minutes.

### 8.1 The Golden Rules

| Rule | Why | How |
|------|-----|-----|
| **Never put secrets in code** | One `git push` and they're public forever | Use environment variables (Railway dashboard / Azure App Settings) |
| **Always use HTTPS** | Without it, data is sent unencrypted | Both Railway and Azure provide this automatically |
| **Always have backups** | Databases can fail, humans make mistakes | Use managed databases (Railway/Azure) — backups are automatic |
| **Use Git for everything** | Your undo button if something goes wrong | Commit often, push to GitHub |
| **Keep dependencies updated** | Old packages have known vulnerabilities | Run `npm audit` regularly |

### 8.2 API Keys & Secrets

Your app will use API keys (e.g., for Claude AI, payment providers, email services). These are like passwords — if someone gets them, they can use your services and run up your bill.

**Where to store them:**

```
.env                          ← Local development (NEVER commit this)
Railway Dashboard → Variables  ← Production (Path A)
Azure App Settings             ← Production (Path B)
```

**Protect your `.env` file — add to `.gitignore`:**

```
# .gitignore
.env
.env.local
.env.production
```

**What if you accidentally committed a secret?**
1. Immediately rotate (change) the key in the provider's dashboard
2. The old key is in git history forever — changing the file doesn't help
3. Use `git filter-branch` or [BFG Repo Cleaner](https://rtyley.github.io/bfg-repo-cleaner/) to remove it from history
4. Or easier: rotate the key and move on

### 8.3 Data Privacy & GDPR

If your app collects data from users in Europe (EU/EEA/Switzerland), you must comply with **GDPR** (General Data Protection Regulation) / **DSGVO** (German equivalent).

**When does GDPR apply?**
- You collect names, email addresses, or any personal data
- You use analytics or tracking (Google Analytics, etc.)
- You store user-generated content
- Your users are in Europe (regardless of where your server is)

**Minimum requirements:**

| Requirement | What to do |
|------------|-----------|
| **Privacy Policy** | Add a page explaining what data you collect and why |
| **Cookie Banner** | If you use cookies beyond essential ones |
| **Data Processing Agreement** | With your hosting provider (Railway/Azure both offer this) |
| **Right to deletion** | Users must be able to request their data be deleted |
| **Data minimization** | Only collect what you actually need |
| **Server location** | Ideally EU. Azure: choose `westeurope`. Railway: check region |

**Path A (Railway):** Servers are primarily in US. For EU compliance, check if EU regions are available or consider if this matters for your use case.

**Path B (Azure):** Choose `westeurope` (Netherlands) or `germanywestcentral` (Frankfurt) for full EU data residency. Azure has all compliance certifications (GDPR, HIPAA, SOC 2, ISO 27001).

### 8.4 Authentication — Don't Build Your Own

If your app needs user login, **do not build authentication from scratch**. Use a proven solution:

| Solution | Cost | Complexity | Best for |
|----------|------|-----------|----------|
| [NextAuth.js / Auth.js](https://authjs.dev) | Free | Low | Next.js projects |
| [Clerk](https://clerk.com) | Free tier | Very low | Fast setup, beautiful UI |
| [Supabase Auth](https://supabase.com/auth) | Free tier | Low | If using Supabase |
| [Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/) | Pay-as-you-go | Medium | Enterprise / Azure path |

### 8.5 HTTPS & Encryption

- **Railway**: HTTPS is automatic and free on all domains
- **Azure**: HTTPS is automatic and free with managed certificates
- **Custom domains**: Both providers handle SSL certificates automatically

You don't need to do anything — just make sure you never use `http://` links in your code. Always use `https://`.

### 8.6 Security Checklist

Before going live, check these off:

- [ ] No API keys or secrets in your code (check with `git log --all -p | grep -i "api_key\|secret\|password"`)
- [ ] `.env` is in `.gitignore`
- [ ] HTTPS is enabled (automatic on Railway/Azure)
- [ ] Database has a strong password (20+ characters, random)
- [ ] Authentication uses a proven library (not custom-built)
- [ ] Privacy policy exists (if collecting user data)
- [ ] Cookie banner exists (if using non-essential cookies)
- [ ] `npm audit` shows no critical vulnerabilities
- [ ] Error messages don't expose internal details to users
- [ ] Admin routes/pages are protected by authentication

---

## 9. Comparison & FAQ

### Side-by-Side Comparison

| Feature | Railway | Azure |
|---------|---------|-------|
| **Setup time** | ~10 min | ~45 min |
| **Learning curve** | Easy | Steep |
| **Auto-deploy from GitHub** | Built-in | Via GitHub Actions |
| **PostgreSQL** | One click | CLI or Portal |
| **SSL/HTTPS** | Automatic, free | Automatic, free |
| **Custom domains** | Yes | Yes |
| **Claude Pro (required)** | $20/month | $20/month |
| **Hosting + DB** | ~$5/month | ~$42/month |
| **Total (Dev)** | **~$25/month** | **~$62/month** |
| **Total (Production)** | **~$40–70/month** | **~$120–400/month** |
| **Free tier** | 30-day trial ($5) | 30-day trial ($200) |
| **Compliance (HIPAA, SOC2)** | Limited | Full |
| **EU data residency** | Limited (US servers) | Yes (`westeurope`, `switzerlandnorth`) |
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

### Lessons from the Field

These are real lessons learned from deploying 4 production apps across Railway and Azure. They'll save you hours of debugging.

#### Deployment Gotchas

**Railway:**
- `git push` is all you need — Railway auto-detects, builds, and deploys. No config files needed in most cases.
- If your app uses **Prisma** (database ORM), keep `prisma` and `tsx` in `dependencies`, NOT `devDependencies`. Railway installs with `--omit=dev` and your build will fail silently.
- After first deploy: go to **Settings → Networking → Generate Domain** — otherwise your app is deployed but not exposed to the internet ("Unexposed service").
- If builds feel stale, set `NIXPACKS_NO_CACHE=1` temporarily to clear the build cache.

**Azure:**
- **Always use Service Principal for GitHub Actions**, not Publish Profile. Publish Profile is unreliable for new apps and will waste your time.
- The admin username Azure assigns to your database might not be what you typed. Always verify: `az postgres flexible-server show --query administratorLogin`.
- Database passwords with special characters (`!@#$`) can break connection strings. Use only letters and numbers.
- Always append `?sslmode=require` to your PostgreSQL connection string — Azure requires SSL.
- Azure resource names must be globally unique. Use a prefix like `yourname-projectname`.

#### Database Lessons

- **Never skip backups.** Railway and Azure both do automatic backups — use their managed databases, not random free PostgreSQL hosts.
- **Run migrations at startup, not at build time.** On Railway (and Azure), your database isn't reachable during the build phase. Put `prisma migrate deploy` in your start script.
- **Test your database connection locally first** before deploying. If you can't connect from your machine, your app won't be able to either.

#### Code & Architecture

- **Inline styles beat CSS classes for small teams.** Sounds wrong, but eliminates build tools, naming conflicts, and specificity battles. When you grow, you can switch to a design system.
- **Start with `sessionStorage` auth for private/internal apps.** Don't spend days on OAuth before your app even works. Add real auth when you actually need it.
- **Always use a `.gitignore` from day one.** Ask Claude Code: *"create a .gitignore for a Node.js project"* — it knows what to exclude.

#### Working with Claude Code

- **Write a good CLAUDE.md early.** The better your project instructions, the fewer mistakes Claude makes. Include: tech stack, commands to build/test, code style rules.
- **Use Plan Mode (Shift+Tab) before big changes.** Let Claude analyze the codebase first, then switch to Normal mode to implement.
- **Commit often.** Claude sometimes takes a wrong path. If you committed before the change, you can easily undo with `git checkout .` — if you didn't, you might lose work.
- **Don't run complex one-liners on Windows.** Characters like `!` get escaped by bash. Write a `.js` or `.ts` file instead and run it with `node` or `tsx`.

#### Data Privacy (GDPR / DSGVO)

- **If your users are in Europe, you need GDPR compliance from day one** — not "later". This includes a privacy policy, data processing agreements with your hosting provider, and the ability for users to delete their data.
- **Railway's servers are in the US by default.** This may be a problem for EU data residency requirements. Azure lets you choose `westeurope` (Netherlands) or `switzerlandnorth` for full compliance.
- **Don't store more data than you need.** Every field you collect is a field you must protect, explain in your privacy policy, and delete on request.
- **Passwords in your database should be hashed** (use bcrypt or argon2). Never store plain-text passwords. If you're using an auth library (Clerk, NextAuth), this is handled for you.

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

*v1.0 · March 4, 2026 · M. Suter, Switzerland · Built with Claude Code.*

</div>

<!-- ==================== ADVANCED TAB ==================== -->
<div id="tab-advanced" class="tab-panel" markdown="1">

## Multi-Session Team Mode

> **Run multiple Claude Code sessions as a team** — an orchestrator coordinates, multiple developers work in parallel, and a quality control agent checks code quality. Get done in one hour what would normally take a full day.

<div class="sub-tabs">
  <button class="sub-tab active" onclick="switchSubTab('classic', this)">Classic</button>
  <button class="sub-tab" onclick="switchSubTab('autonomous', this)">Autonomous</button>
</div>

<!-- ========== SUB-TAB: CLASSIC ========== -->
<div id="subtab-classic" class="sub-panel active" markdown="1">

### What is Team Mode?

In Basic mode, you work with **one** Claude Code session. That works fine for small tasks. But what about larger projects — e.g., adding multilingual support, fixing responsive bugs, and writing tests all at the same time?

In **Team Mode**, you open multiple terminals, start a separate Claude Code session in each one, and assign each session a **role** and a **name**. The sessions coordinate through files in the project — just like a real development team.

```
Terminal 1: Anton (Orchestrator)        — coordinates, distributes tasks, deploys
Terminal 2: Benno (Planner)             — analyzes requirements, creates plans
Terminal 3: Chasperli (Developer 1)     — works on Feature A
Terminal 4: Donald (Developer 2)        — works on Feature B
Terminal 5: Egon (Developer 3)          — works on Feature C
Terminal 6: Fridolin (Quality Control)  — checks code quality, tests
Terminal 7: Guschti (Planner & Security) — security audits, planning
```

**Prerequisite:** All sessions run in the same project folder and use the same Git repo.

---

### The Team — 7 Agents

| # | Name | Role | Responsibilities |
|---|------|------|-----------------|
| A | **Anton** | Orchestrator | Coordinates the team, distributes tasks, resolves file conflicts, deploys to production. Only he edits `board.md`. |
| B | **Benno** | Planner | Analyzes requirements, reads affected files, designs implementation plans, defines API contracts. Does NOT change code. |
| C | **Chasperli** | Developer 1 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| D | **Donald** | Developer 2 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| E | **Egon** | Developer 3 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| F | **Fridolin** | Quality Control | TypeScript build checks, responsive testing, code review, functional testing. Reports issues — does NOT change code. |
| G | **Guschti** | Planner & Security | Flex role: either planning (like Benno) or security audits (OWASP Top 10, dependency audits, secrets scanning, input validation). Reports findings — does NOT change code. |

**Important:** Roles are strictly separated. A developer only implements what is assigned. The orchestrator reviews and commits.

#### Team Overview

![Team Organigramm — Markus (Product Owner) at the top, Anton (Orchestrator) below, 6 Agents on the same level: Benno, Chasperli, Donald, Egon, Fridolin, Guschti](team-organigramm.svg)

<details><summary>Inline fallback (if SVG doesn't render)</summary>
<div style="max-width:700px; margin:1.5rem auto; font-family:'Open Sans',sans-serif;">
  <div style="text-align:center;">
    <div style="display:inline-block; background:linear-gradient(135deg,#6366f1,#4f46e5); color:#fff; padding:14px 28px; border-radius:12px; font-weight:700; font-size:15px; box-shadow:0 4px 15px rgba(99,102,241,0.3);">
      Markus<br><span style="font-weight:400;font-size:12px;opacity:0.85;">Product Owner</span>
    </div>
  </div>
  <div style="text-align:center;">
    <div style="width:3px;height:28px;background:#94a3b8;margin:0 auto;"></div>
    <div style="width:0;height:0;border-left:7px solid transparent;border-right:7px solid transparent;border-top:9px solid #94a3b8;margin:0 auto;"></div>
  </div>
  <div style="text-align:center;margin-top:4px;">
    <div style="display:inline-block; background:linear-gradient(135deg,#0091DC,#0077b6); color:#fff; padding:14px 28px; border-radius:12px; font-weight:700; font-size:15px; box-shadow:0 4px 15px rgba(0,145,220,0.3);">
      Anton<br><span style="font-weight:400;font-size:12px;opacity:0.85;">Orchestrator</span>
    </div>
  </div>
  <div style="text-align:center;">
    <div style="width:3px;height:28px;background:#94a3b8;margin:0 auto;"></div>
    <div style="width:0;height:0;border-left:7px solid transparent;border-right:7px solid transparent;border-top:9px solid #94a3b8;margin:0 auto;"></div>
  </div>
  <div style="height:3px;background:#94a3b8;margin:0 40px;"></div>
  <div style="display:flex; flex-wrap:wrap; justify-content:center; gap:10px; margin-top:10px;">
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#8b5cf6,#7c3aed);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(139,92,246,0.25);">
      Benno<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Planner</span>
    </div>
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(16,185,129,0.25);">
      Chasperli<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Developer 1</span>
    </div>
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(245,158,11,0.25);">
      Donald<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Developer 2</span>
    </div>
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(239,68,68,0.25);">
      Egon<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Developer 3</span>
    </div>
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#06b6d4,#0891b2);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(6,182,212,0.25);">
      Fridolin<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Quality Control</span>
    </div>
    <div style="flex:1;min-width:90px;max-width:115px;background:linear-gradient(135deg,#f97316,#ea580c);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:13px;font-weight:600;box-shadow:0 3px 10px rgba(249,115,22,0.25);">
      Guschti<br><span style="font-weight:400;font-size:11px;opacity:0.85;">Planner &amp; Security</span>
    </div>
  </div>
  <div style="text-align:center;margin-top:14px;font-size:12px;color:#64748b;font-style:italic;">
    Anton distributes tasks to all agents &middot; Benno plans, Developers implement &middot; Fridolin + Guschti review
  </div>
</div>
</details>

---

### Naming Convention

Team members get fixed names in alphabetical order:

| Order | Name | Default Role |
|-------|------|-------------|
| 1st session | **Anton** | Orchestrator |
| 2nd session | **Benno** | Planner |
| 3rd session | **Chasperli** | Developer 1 |
| 4th session | **Donald** | Developer 2 |
| 5th session | **Egon** | Developer 3 |
| 6th session | **Fridolin** | Quality Control |
| 7th session | **Guschti** | Planner & Security |

When you open a new session, take the next available name. The first session is always the orchestrator.

> **Tip:** When starting a session, just tell Claude: *"You are Benno, Developer on the team. Read status/board.md and check in."* — Claude understands this and behaves accordingly.

---

### Coordination: The `status/` Folder

The heart of team mode is a `status/` folder in the project root. It contains three types of files:

```
project/
├── status/
│   ├── board.md           ← Tasks (only orchestrator edits)
│   ├── nachrichten.md     ← Message board (everyone can append)
│   ├── anton.md           ← Anton's status file
│   ├── benno.md           ← Benno's status file
│   ├── chasperli.md       ← Chasperli's status file
│   └── ...
```

#### `board.md` — The Task List

All tasks live here. **Only the orchestrator edits this file.** Contains:
- Completed tasks (strikethrough)
- Open tasks with description, scope, and affected files
- Team rules

**Example:**

```markdown
## Completed Tasks
- ~~Login screen role display~~ ✅
- ~~Toast system, loading states, CSV export~~ ✅

## Open Tasks

### Feature: Multilingual Support (DE/EN)
**Description:** All UI text should be available in German and English.
**Affected files:** src/i18n.tsx, src/locales/, all pages
**Assigned to:** Chasperli + Benno
```

#### `nachrichten.md` — The Message Board

Team members communicate here. **Everyone can append** (add new lines), but nobody deletes other people's messages.

**Example:**

```markdown
| From | To | Message | Done |
|------|-----|---------|------|
| Benno | Anton | Feature X done! Please commit. | ⬜ |
| Anton | Benno | ✅ Committed + deployed. | ✅ |
| Chasperli | Benno | Can you help with the multilingual setup? | ⬜ |
```

**Important rule:** Each session polls the message board regularly (~15 seconds) and responds to messages addressed to it.

#### Message Flow Between Agents

![Message Flow — All agents communicate through nachrichten.md as the central message board](message-flow.svg)

<details><summary>Inline fallback (if SVG doesn't render)</summary>
<div style="max-width:680px;margin:1.5rem auto;font-family:'Open Sans',sans-serif;">
  <div style="display:flex;align-items:stretch;gap:0;">
    <div style="display:flex;flex-direction:column;gap:8px;justify-content:center;min-width:100px;">
      <div style="background:linear-gradient(135deg,#8b5cf6,#7c3aed);color:#fff;padding:10px 12px;border-radius:10px 0 0 10px;font-size:12px;font-weight:600;text-align:center;">
        Benno<br><span style="font-size:10px;font-weight:400;">Planner</span>
      </div>
      <div style="background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:10px 12px;border-radius:10px 0 0 10px;font-size:12px;font-weight:600;text-align:center;">
        Chasperli<br><span style="font-size:10px;font-weight:400;">Developer 1</span>
      </div>
      <div style="background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff;padding:10px 12px;border-radius:10px 0 0 10px;font-size:12px;font-weight:600;text-align:center;">
        Donald<br><span style="font-size:10px;font-weight:400;">Developer 2</span>
      </div>
      <div style="background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff;padding:10px 12px;border-radius:10px 0 0 10px;font-size:12px;font-weight:600;text-align:center;">
        Egon<br><span style="font-size:10px;font-weight:400;">Developer 3</span>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:8px;justify-content:center;padding:0 6px;">
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
    </div>
    <div style="flex:1;background:linear-gradient(180deg,#1e293b,#334155);color:#fff;padding:18px 14px;border-radius:14px;text-align:center;display:flex;flex-direction:column;justify-content:center;box-shadow:0 4px 18px rgba(30,41,59,0.35);margin:0 6px;">
      <div style="font-weight:700;font-size:15px;margin-bottom:4px;">nachrichten.md</div>
      <div style="font-size:12px;opacity:0.8;">Central Message Board</div>
      <div style="margin-top:10px;font-size:11px;opacity:0.7;border-top:1px solid rgba(255,255,255,0.15);padding-top:10px;">
        All agents read &amp; write<br>Poll every ~15 seconds
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:8px;justify-content:center;padding:0 6px;">
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:20px;line-height:40px;text-align:center;">&#x27A1;&#xFE0E;</div>
    </div>
    <div style="display:flex;flex-direction:column;gap:8px;justify-content:center;min-width:100px;">
      <div style="background:linear-gradient(135deg,#0091DC,#0077b6);color:#fff;padding:10px 12px;border-radius:0 10px 10px 0;font-size:12px;font-weight:600;text-align:center;">
        Anton<br><span style="font-size:10px;font-weight:400;">Orchestrator</span>
      </div>
      <div style="background:linear-gradient(135deg,#06b6d4,#0891b2);color:#fff;padding:10px 12px;border-radius:0 10px 10px 0;font-size:12px;font-weight:600;text-align:center;">
        Fridolin<br><span style="font-size:10px;font-weight:400;">Quality Control</span>
      </div>
      <div style="background:linear-gradient(135deg,#f97316,#ea580c);color:#fff;padding:10px 12px;border-radius:0 10px 10px 0;font-size:12px;font-weight:600;text-align:center;">
        Guschti<br><span style="font-size:10px;font-weight:400;">Planner &amp; Security</span>
      </div>
    </div>
  </div>
  <div style="text-align:center;margin-top:12px;font-size:12px;color:#64748b;font-style:italic;">
    Agents never communicate directly &mdash; all messages go through nachrichten.md
  </div>
</div>
</details>

#### `<name>.md` — Personal Status Files

Each team member has their own status file. **Only the agent itself writes to its file.** Contains:
- Online/offline status
- Current task
- Affected files (for conflict avoidance!)
- List of completed tasks

**Example (`status/benno.md`):**

```markdown
# Benno — Developer

| Field | Value |
|-------|-------|
| Status | online |
| Logged in | 2026-03-04 14:30 |
| Last activity | 2026-03-04 15:12 |
| Current task | Responsive bugfixes |
| Affected files | src/pages/SupplierDetail.tsx, src/index.css |

## Completed
- Login screen role display — committed by Anton
```

---

### Why Separate Files?

Why not just use a single `STATUS.md`?

**Problem with one file:** When two Claude Code sessions edit the same file simultaneously, one overwrites the other's changes. Claude Code has no file locking — last write wins.

**Solution with separate files:**
- Everyone writes only to their own status file → **no write conflicts**
- `board.md` is only edited by the orchestrator → **single writer**
- `nachrichten.md` is append-only → **minimal conflict risk**

> Think of it like a real team: Everyone has their own desk (status file), there's a whiteboard (board.md) that only the lead writes on, and a mailbox (nachrichten.md) where everyone can drop notes.

---

### Timeout Rule

**15 minutes without activity = offline.**

If a team member hasn't updated their status file for 15 minutes (no new timestamp on "Last activity"), they're considered offline. Their files are then free for others.

**Why?** Claude Code sessions can crash, the user can close the terminal, or the session hits a context limit. Without a timeout rule, files would be blocked indefinitely.

**In practice:** The orchestrator regularly checks timestamps in status files and marks inactive sessions as offline.

---

### Commit Rules

There are two models — choose what fits your team:

**Model A — Centralized (recommended for beginners):**
Only the orchestrator commits and pushes. Developers report completion, the orchestrator reviews and commits.

**Model B — Distributed (recommended for experienced teams):**
Every agent commits and pushes themselves. Format: `feat:` or `fix:` + short description. After pushing, send a message to the orchestrator.

**Why Model A?**
- Avoids merge conflicts from simultaneous commits
- Orchestrator can review changes before they enter the repo
- Clean, traceable commit log

**Why Model B?**
- Faster — no bottleneck at the orchestrator
- Agents are more autonomous
- Works well when tasks have clear file separation

---

### MEMORY.md — Cross-Session Knowledge

Claude Code has an **auto-memory** feature: Important findings are stored in `MEMORY.md` (in the `.claude/` folder) and automatically loaded at every new session start.

**What belongs in MEMORY.md:**
- Tech stack and architecture decisions
- Important file paths and patterns
- Known gotchas and their solutions
- User preferences (e.g., language, code style)

**What does NOT belong:**
- Session-specific tasks (use `status/board.md` for that)
- Temporary state
- Duplicates of CLAUDE.md content

> **Tip:** When the team discovers something important (e.g., "Prisma must be in dependencies, not devDependencies"), the orchestrator should save it in MEMORY.md — then all future sessions know it automatically.

---

### Standard Workflow — Visual Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    Standard Team Workflow                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ① Markus + Anton                                              │
│     Define requirements ──────────────────────────────────┐     │
│                                                           │     │
│  ② Anton → Benno                                          │     │
│     "Plan feature X" ─────────┐                           │     │
│                                ▼                           │     │
│  ③ Benno → Anton              │                           │     │
│     Detailed plan ◀───────────┘                           │     │
│                                                           │     │
│  ④ Anton creates tasks in board.md                        │     │
│     ├── Task A → Chasperli                                │     │
│     ├── Task B → Donald                                   │     │
│     └── Task C → Egon                                     │     │
│                    │         │         │                   │     │
│  ⑤ Developers     ▼         ▼         ▼    (parallel!)   │     │
│     implement + commit + push                             │     │
│                    │         │         │                   │     │
│  ⑥ Anton → Fridolin ◀───────┴─────────┘                  │     │
│     "Quality check please"                                     │     │
│                    │                                       │     │
│  ⑦ Fridolin → Anton                                      │     │
│     Quality report (OK or issues)                              │     │
│                    │                                       │     │
│  ⑧ Anton → Guschti (planning or security audit)           │     │
│     Flex: analysis/planning or security review            │     │
│                    │                                       │     │
│  ⑨ Anton deploys to production ◀──────────────────────────┘     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

Shortcut (small tasks): Anton → Developer → Commit → Done (no Planner/Quality Control)
```

### Example Workflow

Here's a typical flow with three sessions:

**1. Orchestrator (Anton) starts and plans**

```
Terminal 1:
> claude --dangerously-skip-permissions
> "You are Anton, the Orchestrator. Read status/board.md and distribute the open tasks."
```

Anton reads the task list, checks which developers are online, and distributes tasks via `nachrichten.md`:

```markdown
| Anton | Benno | Please do the responsive bugfixes. Details in board.md. | ⬜ |
| Anton | Chasperli | Please set up the multilingual framework. Details in board.md. | ⬜ |
```

**2. Developer (Benno) checks in and works**

```
Terminal 2:
> claude --dangerously-skip-permissions
> "You are Benno, Developer. Read status/board.md and nachrichten.md."
```

Benno sees his task, updates `status/benno.md`, and starts working. He polls `nachrichten.md` regularly for new instructions.

**3. Developer (Chasperli) works in parallel**

```
Terminal 3:
> claude --dangerously-skip-permissions
> "You are Chasperli, Developer. Read status/board.md and nachrichten.md."
```

Chasperli works on a different feature at the same time — no conflict because they work on different files (listed in status files).

**4. Benno finishes**

Benno writes in `nachrichten.md`:

```markdown
| Benno | Anton | Responsive bugfixes done! Changed files: src/index.css, SupplierDetail.tsx. Please commit. | ⬜ |
```

**5. Anton commits**

Anton reads the message, reviews the changes, and commits:

```
Terminal 1:
> "Commit Benno's responsive bugfixes and deploy."
```

Anton marks the message as done (✅) and the task in `board.md` as completed.

**6. Next round**

Anton distributes the next task, or Benno asks: *"What's next?"*

---

### Quick Start Checklist

Here's how to set up team mode in your project:

1. **Create the folder:**
   ```bash
   mkdir status
   ```

2. **Create `status/board.md`** with a task template:
   ```markdown
   # Tasks & Rules

   > **Only the Orchestrator edits this file.**

   ## Team
   | Name | Role |
   |------|------|
   | Anton | Orchestrator |
   | Benno | Developer |
   | Chasperli | Developer |

   ## Open Tasks
   (add tasks here)

   ## Rules
   - Status: Everyone writes ONLY to their own file
   - Commits/Push: Only through the orchestrator
   - Messages: Poll the message board every ~15 sec
   - Timeout: 15 min without activity → offline
   ```

3. **Create `status/nachrichten.md`:**
   ```markdown
   # Messages

   > Everyone can append here. Newest message at the bottom.

   | From | To | Message | Done |
   |------|-----|---------|------|
   ```

4. **Start the first session** (Orchestrator):
   ```bash
   claude --dangerously-skip-permissions
   ```
   ```
   > You are Anton, the Orchestrator. Create your status file at status/anton.md
   > and wait for team members.
   ```

5. **Start additional sessions** (Developers):
   ```bash
   claude --dangerously-skip-permissions
   ```
   ```
   > You are Benno, Developer. Read status/board.md and check in.
   ```

6. **Distribute tasks** and get going!

---

### Tips & Best Practices

- **Separate files clearly:** Two developers should never edit the same file at the same time. The orchestrator ensures this when distributing tasks.
- **Always list affected files:** Each developer lists which files they're working on in their status file. This lets others avoid conflicts.
- **Start small:** Begin with 2 sessions (orchestrator + 1 developer) and scale as needed.
- **Maintain CLAUDE.md:** The better the project instructions, the fewer mistakes each session makes.
- **Use `/compact`:** Long sessions consume context. Compress regularly.
- **No overengineering:** Sessions should only do what's in the task — no initiative, no scope creep.

</div>

<!-- ========== SUB-TAB: AUTONOMOUS ========== -->
<div id="subtab-autonomous" class="sub-panel" markdown="1">

### What is Autonomous Mode?

In Classic mode, you manually open terminals and start each Claude Code session yourself. That works, but it means you're the bottleneck — you have to start each session, paste the prompt, and babysit the process.

In **Autonomous Mode**, an orchestrator script watches the message board (`nachrichten.md`) and **automatically spawns Claude Code sessions** when new tasks appear. You write a task for an agent, the script detects it, and a new Claude Code session starts within seconds — without you touching a terminal.

```
You (or Anton) write a task in nachrichten.md
        ↓
Orchestrator script detects the new message
        ↓
Script spawns: claude -p --dangerously-skip-permissions
        ↓
Agent works autonomously (reads task, implements, commits, reports back)
        ↓
Agent writes result to nachrichten.md → goes offline
```

---

### How it Differs from Classic

| Aspect | Classic | Autonomous |
|--------|---------|------------|
| **Starting sessions** | You open terminals manually | Script spawns sessions automatically |
| **Task distribution** | Copy-paste prompts | Write to nachrichten.md, script does the rest |
| **Supervision** | You watch each terminal | Agents work in the background |
| **Scaling** | Limited by your terminal tabs | Up to N concurrent agents (configurable) |
| **Best for** | Learning, small teams, ad-hoc work | Larger projects, recurring tasks, batch processing |

---

### Prerequisites

- **Node.js** installed (v18+)
- **Claude Code** installed and authenticated (`claude --version`)
- The `status/` folder set up as described in the Classic tab
- The orchestrator script in your project (e.g., `scripts/orchestrator.cjs`)

---

### The Team — 7 Agents

The same team structure applies in both Classic and Autonomous modes:

| # | Name | Role | Responsibilities |
|---|------|------|-----------------|
| A | **Anton** | Orchestrator | Coordinates the team, distributes tasks, resolves file conflicts, deploys to production. Only he edits `board.md`. |
| B | **Benno** | Planner | Analyzes requirements, reads affected files, designs implementation plans, defines API contracts. Does NOT change code. |
| C | **Chasperli** | Developer 1 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| D | **Donald** | Developer 2 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| E | **Egon** | Developer 3 | Implements features, fixes bugs, commits + pushes. Only works on assigned tasks. |
| F | **Fridolin** | Quality Control | TypeScript build checks, responsive testing, code review, functional testing. Reports issues — does NOT change code. |
| G | **Guschti** | Planner & Security | Flex role: either planning (like Benno) or security audits (OWASP Top 10, dependency audits, secrets scanning, input validation). Reports findings — does NOT change code. |

---

### Architecture & Flow

![Orchestrator Pipeline — Watch, Parse, Spawn, Execute, Report — fully automated agent lifecycle](orchestrator-flow.svg)

<details><summary>Inline fallback (if SVG doesn't render)</summary>
<div style="max-width:720px;margin:1.5rem auto;font-family:'Open Sans',sans-serif;overflow-x:auto;">
  <div style="display:flex;align-items:center;gap:0;min-width:580px;">
    <div style="flex:1;background:linear-gradient(135deg,#1e293b,#334155);color:#fff;padding:16px 10px;border-radius:12px;text-align:center;box-shadow:0 3px 12px rgba(30,41,59,0.3);">
      <div style="font-weight:700;font-size:14px;">Watch</div>
      <div style="font-size:11px;opacity:0.8;margin-top:4px;">nachrichten.md</div>
    </div>
    <div style="font-size:24px;color:#0091DC;padding:0 6px;font-weight:700;">&#x25B6;&#xFE0E;</div>
    <div style="flex:1;background:linear-gradient(135deg,#0091DC,#0077b6);color:#fff;padding:16px 10px;border-radius:12px;text-align:center;box-shadow:0 3px 12px rgba(0,145,220,0.3);">
      <div style="font-weight:700;font-size:14px;">Parse</div>
      <div style="font-size:11px;opacity:0.8;margin-top:4px;">Match Anton&#x2192;Agent</div>
    </div>
    <div style="font-size:24px;color:#0091DC;padding:0 6px;font-weight:700;">&#x25B6;&#xFE0E;</div>
    <div style="flex:1;background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:16px 10px;border-radius:12px;text-align:center;box-shadow:0 3px 12px rgba(16,185,129,0.25);">
      <div style="font-weight:700;font-size:14px;">Spawn</div>
      <div style="font-size:11px;opacity:0.8;margin-top:4px;">claude -p</div>
    </div>
    <div style="font-size:24px;color:#10b981;padding:0 6px;font-weight:700;">&#x25B6;&#xFE0E;</div>
    <div style="flex:1;background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff;padding:16px 10px;border-radius:12px;text-align:center;box-shadow:0 3px 12px rgba(245,158,11,0.25);">
      <div style="font-weight:700;font-size:14px;">Execute</div>
      <div style="font-size:11px;opacity:0.8;margin-top:4px;">Agent works</div>
    </div>
    <div style="font-size:24px;color:#f59e0b;padding:0 6px;font-weight:700;">&#x25B6;&#xFE0E;</div>
    <div style="flex:1;background:linear-gradient(135deg,#8b5cf6,#7c3aed);color:#fff;padding:16px 10px;border-radius:12px;text-align:center;box-shadow:0 3px 12px rgba(139,92,246,0.25);">
      <div style="font-weight:700;font-size:14px;">Report</div>
      <div style="font-size:11px;opacity:0.8;margin-top:4px;">Result to Anton</div>
    </div>
  </div>
  <div style="text-align:center;margin-top:12px;font-size:12px;color:#64748b;font-style:italic;">
    Orchestrator pipeline: from task detection to completion
  </div>
</div>
</details>

---

### The Orchestrator Script

The orchestrator is a Node.js script that runs in the background. Here's how it works:

#### Parsing Logic

The script reads `nachrichten.md` and looks for lines matching this pattern:

```
| Anton | AgentName | Task description... | ⬜ |
```

It extracts the target agent name and the task description. Messages to "ALLE" (everyone) or already-processed messages are skipped.

#### Agent Spawning

When a new task is detected, the script spawns a Claude Code session:

```javascript
const proc = spawn('claude', ['-p', '--dangerously-skip-permissions', '--verbose'], {
  cwd: PROJECT_ROOT,
  stdio: ['pipe', 'pipe', 'pipe'],
  shell: true,
  env,  // with CLAUDECODE deleted!
});

// Send prompt via stdin (not as argument!)
proc.stdin.write(prompt);
proc.stdin.end();
```

**Key details:**

1. **`--dangerously-skip-permissions`** — Required for headless operation. Without it, Claude would prompt for permission on every file edit and command, which doesn't work in an unattended process.

2. **`-p` flag** — Runs Claude in "print mode" (non-interactive). Takes input, produces output, exits.

3. **`--verbose`** — Shows detailed progress on stderr so you can follow what the agent is doing.

#### Critical Learnings (from Production Use)

These are hard-won lessons from running autonomous agents in a real project:

**1. Delete the `CLAUDECODE` environment variable when spawning**

```javascript
const env = { ...process.env };
delete env.CLAUDECODE;
```

If Claude Code detects it's running inside another Claude Code session (via this env var), it may block or behave unexpectedly. Always delete it before spawning child sessions.

**2. Send the prompt via stdin, not as a CLI argument**

```javascript
// ✅ Correct — via stdin
proc.stdin.write(prompt);
proc.stdin.end();

// ❌ Wrong — as argument
spawn('claude', ['-p', '--dangerously-skip-permissions', prompt]);
```

Long prompts with special characters (`|`, `!`, `"`, newlines) break when passed as shell arguments. Stdin avoids all escaping issues.

**3. Use `.cjs` extension in ES Module projects**

If your project uses `"type": "module"` in `package.json`, Node.js treats all `.js` files as ES modules. The orchestrator uses `require()` (CommonJS), so it must have a `.cjs` extension:

```
scripts/orchestrator.cjs  ← works
scripts/orchestrator.js   ← fails with "require is not defined"
```

**4. Agents must update their status files regularly**

Every agent should update `status/<name>.md` after each major step — not just at the beginning and end. This lets the orchestrator (and monitoring dashboard) track progress in real-time. Include a timestamp on every update.

**5. Monitoring Dashboard on Port 3002**

A companion script (`scripts/dashboard.cjs`) runs an Express server on port 3002 that reads the `status/` folder and displays a live dashboard: who's online, what they're working on, recent messages. Auto-refreshes every 5 seconds.

```bash
node scripts/dashboard.cjs
# Open http://localhost:3002
```

---

#### Role-Specific Prompts

The orchestrator sends different instructions based on the agent's role:

| Role | Instructions |
|------|-------------|
| **Planner** | Read board.md, analyze affected files, create implementation plan, do NOT change code |
| **Developer** | Read board.md, implement the task, commit + push, report to orchestrator |
| **Quality Control** | Run `tsc --noEmit` + `vite build`, review recent commits, check responsive design, report findings |
| **Planner & Security** | Flex role: planning (analyze requirements, design plans) or security (OWASP Top 10, `npm audit`, secrets scan, input validation). Report findings |

Each prompt also includes the standard operating procedure: update status file on start, execute task, update status file after each step, report result, set status to offline.

---

#### Configuration

The orchestrator has a few configurable constants:

```javascript
const MAX_CONCURRENT = 4;        // Max parallel agent sessions
const POLL_INTERVAL = 10_000;    // Check for new messages every 10 seconds
```

In addition to polling, the script uses a **file watcher** on `nachrichten.md` for faster reaction times (~500ms instead of waiting for the next poll cycle).

---

### Running the Orchestrator

```bash
# Start the orchestrator
node scripts/orchestrator.cjs
```

You'll see a startup banner:

```
╔═══════════════════════════════════════════════════════════╗
║   🤖 Multi-Session Orchestrator                          ║
║   Polling: every 10s                                     ║
║   Max parallel: 4                                        ║
║   B: Benno (Planner)    C: Chasperli (Dev)               ║
║   D: Donald (Dev)       E: Egon (Dev)                    ║
║   F: Fridolin (Quality)  G: Guschti (Plan & Security)     ║
╚═══════════════════════════════════════════════════════════╝

Waiting for tasks in status/nachrichten.md...
```

The script runs indefinitely. It marks existing messages as "already processed" on startup (so it doesn't re-run old tasks). New messages trigger agent spawning.

Stop it with `Ctrl+C` — it will gracefully terminate all running agents.

---

### Writing Tasks

To assign a task, add a line to `nachrichten.md`:

```markdown
| Anton | Benno | Analyze the SupplierDetail page and plan the edit feature. Details in board.md. | ⬜ |
```

The orchestrator picks this up within seconds and spawns a Benno session. The `⬜` marker indicates an unprocessed message.

**Format:**

```
| From | To | Task description | ⬜ |
```

- **From** must be `Anton` (the orchestrator only reacts to messages from Anton)
- **To** must be an agent name from the roster (Benno, Chasperli, Donald, Egon, Fridolin, Guschti)
- **Task** should be clear and self-contained — the agent sees only this plus board.md

---

### Agent Lifecycle

Each spawned agent follows this lifecycle:

```
  ┌───────────────────────────────────────────────────────────┐
  │                  Agent Lifecycle                           │
  ├───────────────────────────────────────────────────────────┤
  │                                                           │
  │   ┌─────────┐    Read board.md     ┌──────────┐          │
  │   │  START   │───────────────────▶│ CHECK IN  │          │
  │   └─────────┘    + nachrichten.md  │ (online)  │          │
  │                                    └─────┬─────┘          │
  │                                          │                │
  │                                          ▼                │
  │                                    ┌──────────┐           │
  │                              ┌────▶│ EXECUTE  │──────┐    │
  │                              │     │  task     │     │    │
  │                              │     └─────┬─────┘     │    │
  │                              │           │           │    │
  │                              │     update status     │    │
  │                              │     file (timestamp)  │    │
  │                              │           │           │    │
  │                              │     more steps?       │    │
  │                              └─── yes ◀──┘     no ───┘    │
  │                                                │          │
  │                                                ▼          │
  │                                          ┌──────────┐     │
  │                                          │  COMMIT   │     │
  │                                          │ + PUSH    │     │
  │                                          └─────┬─────┘     │
  │                                                │          │
  │                                                ▼          │
  │   ┌─────────┐    Set status       ┌──────────┐           │
  │   │  EXIT   │◀──  to offline  ◀───│  REPORT  │           │
  │   └─────────┘                     │ to Anton  │           │
  │                                    └──────────┘           │
  └───────────────────────────────────────────────────────────┘
```

The orchestrator shows live stdout/stderr from each agent, prefixed with the agent name:

```
🚀 Benno startet: Analyze the SupplierDetail page...
   [Benno] Reading status/board.md...
   [Benno] Analyzing SupplierDetail.tsx...
   [Benno] Writing implementation plan...
✅ Benno fertig (exit 0)
```

---

### Optional: Monitoring Dashboard

For a visual overview, run the monitoring dashboard alongside the orchestrator:

```bash
# In a separate terminal
node scripts/dashboard.cjs
```

Open `http://localhost:3002` to see:
- **Agent cards** — Name, role, online/offline status, current task, last activity
- **Recent messages** — Latest entries from nachrichten.md
- **Chat interface** — Send messages directly to Anton from the browser

The dashboard auto-refreshes every 5 seconds using fetch + DOM updates (no page reload).

---

### Classic vs. Autonomous — When to Use What

| Scenario | Recommended Mode |
|----------|-----------------|
| First time trying team mode | **Classic** — learn the coordination patterns |
| 2-3 sessions, ad-hoc tasks | **Classic** — manual control is fine |
| 4+ parallel agents | **Autonomous** — manual terminal management gets unwieldy |
| Recurring task patterns | **Autonomous** — standardized prompts work great |
| Batch processing (e.g., 10 bug fixes) | **Autonomous** — write all tasks, let agents process them |
| Exploring / prototyping | **Classic** — you want interactive control |
| Continuous Integration (CI/CD) | **Autonomous** — script can be triggered by CI events |

---

### Quick Start: Autonomous Mode

```
┌────────────────────────────────────────────────────────────────┐
│  Your Setup — 3 Terminals                                      │
├────────────────────┬────────────────────┬──────────────────────┤
│  Terminal 1        │  Terminal 2        │  Terminal 3          │
│                    │                    │  (optional)          │
│  claude            │  node scripts/    │  node scripts/       │
│  (Anton -          │  orchestrator.cjs │  dashboard.cjs       │
│   interactive)     │  (auto-spawns     │  (monitoring on      │
│                    │   agents)         │   port 3002)         │
│  You talk to       │  Watches          │  Shows who's         │
│  Anton, he writes  │  nachrichten.md   │  online, current     │
│  tasks to          │  and spawns new   │  tasks, messages     │
│  nachrichten.md    │  claude sessions  │                      │
└────────────────────┴────────────────────┴──────────────────────┘
```

1. **Set up the `status/` folder** as described in the Classic tab (board.md, nachrichten.md)

2. **Create the orchestrator script** at `scripts/orchestrator.cjs`:
   ```bash
   # Copy from a reference project or write your own
   # Key: parse nachrichten.md, spawn claude -p, pipe prompt via stdin
   ```

3. **Start the orchestrator:**
   ```bash
   node scripts/orchestrator.cjs
   ```

4. **Start the interactive Anton session** (in a separate terminal):
   ```bash
   claude --dangerously-skip-permissions
   ```
   ```
   > You are Anton, the Orchestrator. Write tasks to nachrichten.md
   > for the agents. The orchestrator script will spawn them automatically.
   ```

5. **Write a task** in nachrichten.md (or ask Anton to do it):
   ```markdown
   | Anton | Chasperli | Fix the responsive layout on the login page. Details in board.md. | ⬜ |
   ```

6. **Watch the orchestrator** spawn Chasperli and process the task.

7. **Optionally start the dashboard** for monitoring:
   ```bash
   node scripts/dashboard.cjs
   # Open http://localhost:3002
   ```

</div>

---

*v1.2 · March 5, 2026 · M. Suter, Switzerland · Built with Claude Code + Multi-Session Team Mode.*

</div>
