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

<!-- Tab Navigation -->
<style>
.guide-tabs {
  display: flex;
  gap: 0;
  margin: 2em 0 0 0;
  border-bottom: 3px solid #1e293b;
}
.guide-tab {
  padding: 12px 28px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  border: 2px solid transparent;
  border-bottom: none;
  border-radius: 8px 8px 0 0;
  background: #f1f5f9;
  color: #64748b;
  transition: all 0.2s ease;
  position: relative;
  bottom: -3px;
}
.guide-tab:hover {
  background: #e2e8f0;
  color: #334155;
}
.guide-tab.active {
  background: white;
  color: #1e293b;
  border-color: #1e293b;
  border-bottom: 3px solid white;
}
.guide-tab-badge {
  display: inline-block;
  background: #f97316;
  color: white;
  font-size: 11px;
  font-weight: 700;
  padding: 2px 7px;
  border-radius: 4px;
  margin-left: 6px;
  vertical-align: middle;
}
.tab-panel {
  display: none;
}
.tab-panel.active {
  display: block;
}
</style>

<div class="guide-tabs">
  <button class="guide-tab active" onclick="switchGuideTab('basic', this)">Basic</button>
  <button class="guide-tab" onclick="switchGuideTab('advanced', this)">Advanced <span class="guide-tab-badge">NEU</span></button>
</div>

<script>
function switchGuideTab(tabId, btn) {
  document.querySelectorAll('.tab-panel').forEach(function(p) { p.classList.remove('active'); });
  document.querySelectorAll('.guide-tab').forEach(function(b) { b.classList.remove('active'); });
  document.getElementById('tab-' + tabId).classList.add('active');
  btn.classList.add('active');
}
</script>

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

## Multi-Session Team-Modus

> **Mehrere Claude Code Sessions gleichzeitig als Team nutzen** — ein Orchestrator koordiniert, mehrere Developer arbeiten parallel, ein QC prüft die Qualität. So erledigst du in einer Stunde, wofür du sonst einen ganzen Tag brauchst.

---

### Was ist der Team-Modus?

Im Basic-Modus arbeitest du mit **einer** Claude Code Session. Das funktioniert gut für kleine Aufgaben. Aber was, wenn du ein grösseres Projekt hast — z.B. gleichzeitig i18n einbauen, Responsive Bugs fixen und Tests schreiben?

Im **Team-Modus** öffnest du mehrere Terminals, startest in jedem eine eigene Claude Code Session, und gibst jeder Session eine **Rolle** und einen **Namen**. Die Sessions koordinieren sich über Dateien im Projekt — wie ein echtes Entwickler-Team.

```
Terminal 1: Anton (Orchestrator)  — koordiniert, committed, deployt
Terminal 2: Benno (Developer)     — arbeitet an Feature A
Terminal 3: Chasperli (Developer) — arbeitet an Feature B
Terminal 4: Donald (Developer)    — arbeitet an Feature C
Terminal 5: Egon (Quality Control) — prüft Code-Qualität, testet
```

**Voraussetzung:** Alle Sessions laufen im selben Projekt-Ordner und nutzen dasselbe Git-Repo.

---

### Rollen

| Rolle | Aufgaben | Regeln |
|-------|----------|--------|
| **Orchestrator** | Verteilt Aufträge, koordiniert, committed, pusht, deployt | Nur er editiert die Auftragsliste. Nur er committed/pusht. |
| **Developer** | Entwickelt Features, fixt Bugs, setzt Aufträge um | Arbeitet nur an zugewiesenen Aufgaben. Kein Commit/Push. |
| **Quality Control** | Testet, reviewt Code, prüft Qualität | Meldet Probleme an den Orchestrator. |

**Wichtig:** Die Rollen sind strikt getrennt. Ein Developer committed nie selbst — er meldet dem Orchestrator, dass seine Arbeit fertig ist. Der Orchestrator prüft und committed.

---

### Namensvergabe

Die Team-Mitglieder bekommen feste Namen in alphabetischer Reihenfolge:

| Reihenfolge | Name | Rolle |
|-------------|------|-------|
| 1. Session | **Anton** | Orchestrator |
| 2. Session | **Benno** | Developer |
| 3. Session | **Chasperli** | Developer |
| 4. Session | **Donald** | Developer |
| 5. Session | **Egon** | Quality Control |

Wenn du eine neue Session öffnest, nimmst du den nächsten freien Namen. Die erste Session ist immer der Orchestrator.

> **Tipp:** Beim Starten der Session sagst du Claude einfach: *"Du bist Benno, Developer im Team. Lies status/board.md und melde dich an."* — Claude versteht das und verhält sich entsprechend.

---

### Koordination: Der `status/` Ordner

Das Herzstück des Team-Modus ist ein `status/`-Ordner im Projekt-Root. Er enthält drei Arten von Dateien:

```
project/
├── status/
│   ├── board.md           ← Aufträge (nur Orchestrator editiert)
│   ├── nachrichten.md     ← Briefkasten (alle dürfen appenden)
│   ├── anton.md           ← Antons Status-File
│   ├── benno.md           ← Bennos Status-File
│   ├── chasperli.md       ← Chasperlis Status-File
│   └── ...
```

#### `board.md` — Die Auftragsliste

Hier stehen alle Aufträge. **Nur der Orchestrator editiert dieses File.** Enthält:
- Erledigte Aufträge (durchgestrichen)
- Offene Aufträge mit Beschreibung, Scope und betroffenen Dateien
- Team-Regeln

**Beispiel:**

```markdown
## Erledigte Aufträge
- ~~Login-Screen Rollen-Darstellung~~ ✅
- ~~Toast-System, Loading-States, CSV-Export~~ ✅

## Offene Aufträge

### Feature: Zweisprachigkeit DE/EN
**Beschreibung:** Alle UI-Texte sollen auf Deutsch und Englisch verfügbar sein.
**Betroffene Dateien:** src/i18n.tsx, src/locales/, alle Pages
**Zugewiesen an:** Chasperli + Benno
```

#### `nachrichten.md` — Der Briefkasten

Hier kommunizieren die Team-Mitglieder untereinander. **Jeder darf appenden** (neue Zeilen hinzufügen), aber niemand löscht Nachrichten anderer.

**Beispiel:**

```markdown
| Von | An | Nachricht | Erledigt |
|-----|-----|-----------|----------|
| Benno | Anton | Feature X ist fertig! Bitte committen. | ⬜ |
| Anton | Benno | ✅ Committed + deployed. | ✅ |
| Chasperli | Benno | Kannst du mir bei i18n helfen? | ⬜ |
```

**Wichtige Regel:** Jede Session pollt den Briefkasten regelmässig (alle ~15 Sekunden) und reagiert auf eigene Nachrichten.

#### `<name>.md` — Persönliche Status-Files

Jedes Team-Mitglied hat ein eigenes Status-File. **Nur der Agent selbst schreibt in sein File.** Enthält:
- Online/Offline-Status
- Aktuelle Aufgabe
- Betroffene Dateien (für Konflikt-Vermeidung!)
- Liste erledigter Aufgaben

**Beispiel (`status/benno.md`):**

```markdown
# Benno — Developer

| Feld | Wert |
|------|------|
| Status | online |
| Angemeldet | 2026-03-04 14:30 |
| Letzte Aktivität | 2026-03-04 15:12 |
| Aktuelle Aufgabe | Responsive Bugfixes |
| Betroffene Dateien | src/pages/SupplierDetail.tsx, src/index.css |

## Erledigt
- Login-Screen Rollen-Darstellung — committed by Anton
```

---

### Warum separate Files?

Warum nicht einfach ein einziges `STATUS.md`?

**Problem mit einer Datei:** Wenn zwei Claude Code Sessions gleichzeitig dieselbe Datei editieren, überschreibt eine die Änderungen der anderen. Claude Code hat kein Locking — wer zuletzt schreibt, gewinnt.

**Lösung mit separaten Files:**
- Jeder schreibt nur in sein eigenes Status-File → **keine Write-Konflikte**
- `board.md` wird nur vom Orchestrator editiert → **ein Schreiber**
- `nachrichten.md` wird nur appended (Zeilen hinzugefügt) → **minimales Konfliktrisiko**

> Das ist wie bei einem echten Team: Jeder hat seinen eigenen Schreibtisch (Status-File), es gibt ein Whiteboard (board.md) das nur der Chef beschriftet, und einen Briefkasten (nachrichten.md) wo alle Zettel reinwerfen können.

---

### Timeout-Regel

**15 Minuten ohne Aktivität = offline.**

Wenn ein Team-Mitglied sein Status-File 15 Minuten lang nicht aktualisiert hat (kein neuer Timestamp bei "Letzte Aktivität"), gilt es als offline. Seine Dateien sind dann frei für andere.

**Warum?** Claude Code Sessions können abstürzen, der User kann das Terminal schliessen, oder die Session läuft in ein Context-Limit. Ohne Timeout-Regel wären Dateien endlos blockiert.

**Praxis:** Der Orchestrator prüft regelmässig die Timestamps in den Status-Files und markiert inaktive Sessions als offline.

---

### Commit-Regel

**Nur der Orchestrator committed und pusht.** Ausnahmen nur, wenn der Orchestrator es explizit delegiert.

**Warum?**
- Vermeidet Merge-Konflikte bei gleichzeitigen Commits
- Der Orchestrator kann Änderungen prüfen bevor sie ins Repo gehen
- Ein zentraler Commit-Log bleibt sauber und nachvollziehbar

**Workflow:**
1. Developer meldet: *"Feature X ist fertig"* (via `nachrichten.md`)
2. Orchestrator prüft die Änderungen
3. Orchestrator committed mit beschreibender Message
4. Orchestrator deployt bei Bedarf

---

### MEMORY.md — Session-übergreifendes Wissen

Claude Code hat eine **Auto-Memory**-Funktion: Wichtige Erkenntnisse werden in `MEMORY.md` (im `.claude/`-Ordner) gespeichert und bei jeder neuen Session automatisch geladen.

**Was gehört in MEMORY.md:**
- Tech-Stack und Architektur-Entscheide
- Wichtige Dateipfade und Patterns
- Bekannte Gotchas und deren Lösungen
- User-Präferenzen (z.B. Sprache, Code-Style)

**Was gehört NICHT rein:**
- Session-spezifische Aufgaben (dafür ist `status/board.md`)
- Temporärer State
- Duplikate von CLAUDE.md-Inhalten

> **Tipp:** Wenn das Team etwas Wichtiges herausfindet (z.B. "Prisma muss in dependencies statt devDependencies"), sollte der Orchestrator es in MEMORY.md festhalten — dann wissen es alle zukünftigen Sessions automatisch.

---

### Beispiel-Workflow

So sieht ein typischer Ablauf mit drei Sessions aus:

**1. Orchestrator (Anton) startet und plant**

```
Terminal 1:
> claude --dangerously-skip-permissions
> "Du bist Anton, Orchestrator. Lies status/board.md und verteile die offenen Aufträge."
```

Anton liest die Auftragsliste, prüft welche Developer online sind, und verteilt Aufgaben via `nachrichten.md`:

```markdown
| Anton | Benno | Bitte Responsive Bugfixes machen. Details in board.md. | ⬜ |
| Anton | Chasperli | Bitte i18n Framework einrichten. Details in board.md. | ⬜ |
```

**2. Developer (Benno) meldet sich an und arbeitet**

```
Terminal 2:
> claude --dangerously-skip-permissions
> "Du bist Benno, Developer. Lies status/board.md und nachrichten.md."
```

Benno sieht seinen Auftrag, trägt seine Aufgabe in `status/benno.md` ein, und beginnt zu arbeiten. Er pollt regelmässig `nachrichten.md` für neue Anweisungen.

**3. Developer (Chasperli) arbeitet parallel**

```
Terminal 3:
> claude --dangerously-skip-permissions
> "Du bist Chasperli, Developer. Lies status/board.md und nachrichten.md."
```

Chasperli arbeitet gleichzeitig an einem anderen Feature — kein Konflikt, weil beide an verschiedenen Dateien arbeiten (steht in den Status-Files).

**4. Benno ist fertig**

Benno schreibt in `nachrichten.md`:

```markdown
| Benno | Anton | Responsive Bugfixes fertig! Geänderte Dateien: src/index.css, SupplierDetail.tsx. Bitte committen. | ⬜ |
```

**5. Anton committed**

Anton liest die Nachricht, prüft die Änderungen, und committed:

```
Terminal 1:
> "Bennos Responsive Bugfixes committen und deployen."
```

Anton markiert die Nachricht als erledigt (✅) und den Auftrag in `board.md` als abgeschlossen.

**6. Nächste Runde**

Anton verteilt den nächsten Auftrag, oder Benno fragt: *"Was haben wir noch?"*

---

### Schnellstart-Checkliste

So richtest du den Team-Modus in deinem Projekt ein:

1. **Ordner erstellen:**
   ```bash
   mkdir status
   ```

2. **`status/board.md` anlegen** mit Auftrags-Template:
   ```markdown
   # Aufträge & Regeln

   > **Nur der Orchestrator editiert dieses File.**

   ## Team
   | Name | Rolle |
   |------|-------|
   | Anton | Orchestrator |
   | Benno | Developer |
   | Chasperli | Developer |

   ## Offene Aufträge
   (hier Aufträge einfügen)

   ## Regeln
   - Anwesenheit: Jeder schreibt NUR in sein eigenes File
   - Commits/Push: Nur über den Orchestrator
   - Nachrichten: Briefkasten alle ~15 Sek pollen
   - Timeout: 15 Min ohne Aktivität → offline
   ```

3. **`status/nachrichten.md` anlegen:**
   ```markdown
   # Nachrichten

   > Jeder darf hier appenden. Neueste Nachricht zuunterst.

   | Von | An | Nachricht | Erledigt |
   |-----|-----|-----------|----------|
   ```

4. **Erste Session starten** (Orchestrator):
   ```bash
   claude --dangerously-skip-permissions
   ```
   ```
   > Du bist Anton, Orchestrator. Erstelle dein Status-File unter status/anton.md
   > und warte auf weitere Team-Mitglieder.
   ```

5. **Weitere Sessions starten** (Developer):
   ```bash
   claude --dangerously-skip-permissions
   ```
   ```
   > Du bist Benno, Developer. Lies status/board.md und melde dich an.
   ```

6. **Aufträge verteilen** und loslegen!

---

### Tipps & Best Practices

- **Dateien klar aufteilen:** Zwei Developer sollten nie gleichzeitig dieselbe Datei bearbeiten. Der Orchestrator achtet bei der Auftragsverteilung darauf.
- **Betroffene Dateien immer eintragen:** Jeder Developer listet in seinem Status-File auf, welche Dateien er gerade bearbeitet. So können andere Konflikte vermeiden.
- **Klein anfangen:** Starte mit 2 Sessions (Orchestrator + 1 Developer) und skaliere bei Bedarf.
- **CLAUDE.md pflegen:** Je besser die Projekt-Instruktionen, desto weniger Fehler macht jede Session.
- **`/compact` nutzen:** Lange Sessions verbrauchen Context. Regelmässig komprimieren.
- **Kein Overengineering:** Die Sessions sollen nur tun, was im Auftrag steht — keine Eigeninitiative, keinen Scope erweitern.

---

*v1.1 · March 4, 2026 · M. Suter, Switzerland · Built with Claude Code + Team-Modus.*

</div>
