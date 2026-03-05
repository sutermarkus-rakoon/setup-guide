---
layout: default
---

# Developer Setup Guide

**v1.1** · Published March 4, 2026 · Author: M. Suter, Switzerland

> **From zero to deployed** — everything you need to start building with Claude Code, GitHub, and Cloud Infrastructure. No prior experience required.

<!-- ==================== OVERVIEW TAB ==================== -->
<div id="tab-overview" class="tab-panel active" markdown="1">

<div class="autonomy-intro">
  Just as <strong>autonomous driving</strong> has defined levels from driver-assisted to fully self-driving,
  <strong>AI-assisted development</strong> follows a similar progression — from simple chatbots to fully autonomous coding teams.
  <br><br>
  This guide helps you climb that ladder. Here's where each level stands:
</div>

<div class="progress-container">
  <div style="position: relative;">
    <div class="progress-bar-track">
      <div class="progress-bar-fill"></div>
      <div class="progress-marker"></div>
    </div>
  </div>
  <div class="progress-labels">
    <span>L1</span>
    <span>L2</span>
    <span>L3</span>
    <span class="active-label">L4 &#x25C0; You are here</span>
    <span>L5</span>
  </div>
</div>

<div class="autonomy-levels">

  <!-- L1 -->
  <div class="autonomy-level">
    <div class="level-indicator">
      <div class="level-dot dot-l1">L1</div>
      <div class="level-line"></div>
    </div>
    <div class="level-card">
      <h3>AI Chatbot</h3>
      <p>You write code in your IDE. When you get stuck, you switch to a browser, describe your problem to an AI chatbot, and <strong>copy-paste</strong> the answer back. The AI has no access to your project — you are the middleman.</p>
      <div class="level-tools">
        <span class="level-tool">ChatGPT</span>
        <span class="level-tool">Claude.ai</span>
        <span class="level-tool">Gemini</span>
      </div>
    </div>
  </div>

  <!-- L2 -->
  <div class="autonomy-level">
    <div class="level-indicator">
      <div class="level-dot dot-l2">L2</div>
      <div class="level-line"></div>
    </div>
    <div class="level-card">
      <h3>Embedded AI</h3>
      <p>AI lives <strong>inside your editor</strong>. It sees your open file and suggests completions as you type. You accept or reject each suggestion — the AI assists, but <strong>you drive</strong>.</p>
      <div class="level-tools">
        <span class="level-tool">GitHub Copilot</span>
        <span class="level-tool">Cursor</span>
        <span class="level-tool">Windsurf</span>
        <span class="level-tool">Cline</span>
      </div>
    </div>
  </div>

  <!-- L3 -->
  <div class="autonomy-level">
    <div class="level-indicator">
      <div class="level-dot dot-l3">L3</div>
      <div class="level-line"></div>
    </div>
    <div class="level-card">
      <h3>
        AI Agent
        <span class="level-badge badge-basic">BASIC TAB</span>
      </h3>
      <p>The AI becomes an <strong>autonomous agent</strong>. It reads your entire project, writes code across multiple files, runs commands, and commits to Git — all from a single instruction. One agent, one project.</p>
      <div class="level-tools">
        <span class="level-tool">Claude Code CLI</span>
        <span class="level-tool">Codex CLI</span>
      </div>
      <a href="#" onclick="switchGuideTab('basic', document.querySelectorAll('.header-tab')[1]); return false;" class="level-link link-basic">Read the Basic Guide &rarr;</a>
    </div>
  </div>

  <!-- L4 -->
  <div class="autonomy-level">
    <div class="level-indicator">
      <div class="level-dot dot-l4">L4</div>
      <div class="level-line"></div>
    </div>
    <div class="level-card card-current">
      <h3>
        Multi-Agent Team
        <span class="level-badge badge-current">WE ARE HERE</span>
        <span class="level-badge badge-advanced">ADVANCED TAB</span>
      </h3>
      <p>Multiple AI agents work <strong>in parallel</strong>, coordinated through a shared filesystem. Each agent has a role — Orchestrator, Planner, Developer, QC, Security — like a real dev team. They assign tasks, communicate via a message board, and commit independently.</p>
      <div class="level-tools">
        <span class="level-tool">Claude Code CLI &times; 7</span>
        <span class="level-tool">Orchestrator Script</span>
        <span class="level-tool">Status Board</span>
        <span class="level-tool">Message System</span>
      </div>
      <a href="#" onclick="switchGuideTab('advanced', document.querySelectorAll('.header-tab')[2]); return false;" class="level-link link-advanced">Read the Advanced Guide &rarr;</a>
    </div>
  </div>

  <!-- L5 -->
  <div class="autonomy-level">
    <div class="level-indicator">
      <div class="level-dot dot-l5">L5</div>
      <div class="level-line"></div>
    </div>
    <div class="level-card" style="border-style: dashed; background: #fafafa;">
      <h3>
        Fully Autonomous
        <span class="level-badge badge-future">FUTURE</span>
      </h3>
      <p>The AI team plans, implements, tests, and <strong>deploys without human intervention</strong>. Token budget management, automatic error recovery, night-mode execution, and cross-project orchestration. We're building toward this.</p>
      <div class="level-tools">
        <span class="level-tool">Night Mode</span>
        <span class="level-tool">Token Budget Mgmt</span>
        <span class="level-tool">Auto-Resume</span>
        <span class="level-tool">Multi-Project Platform</span>
      </div>
    </div>
  </div>

</div>

<div style="text-align: center; margin: 2rem 0; padding: 1.5rem; background: #f8fafc; border-radius: 10px; border: 1px solid #e2e8f0;">
  <p style="margin: 0 0 0.5rem 0; font-size: 16px; color: #1e293b; font-weight: 600;">Ready to get started?</p>
  <p style="margin: 0 0 1rem 0; font-size: 14px; color: #64748b;">Choose your level. The <strong>Basic</strong> tab gets you to L3 (single agent). The <strong>Advanced</strong> tab takes you to L4 (multi-agent team).</p>
  <div style="display: flex; gap: 12px; justify-content: center; flex-wrap: wrap;">
    <a href="#" onclick="switchGuideTab('basic', document.querySelectorAll('.header-tab')[1]); return false;" class="level-link link-basic" style="font-size: 15px; padding: 8px 24px;">Basic Guide (L3)</a>
    <a href="#" onclick="switchGuideTab('advanced', document.querySelectorAll('.header-tab')[2]); return false;" class="level-link link-advanced" style="font-size: 15px; padding: 8px 24px;">Advanced Guide (L4)</a>
  </div>
</div>

</div>

<!-- ==================== BASIC TAB ==================== -->
<div id="tab-basic" class="tab-panel" markdown="1">

<p align="center" style="margin: 1.5em 0;">
  <a href="claude-setup-assistant.txt" download="claude-setup-assistant.md" style="display: inline-block; background: #f97316; color: white; padding: 14px 28px; border-radius: 10px; font-size: 18px; font-weight: 700; text-decoration: none; cursor: pointer;">Download Setup Assistant for Claude.ai</a>
  <br>
  <em style="font-size: 14px; color: #64748b;">Save the file, then upload it to <a href="https://claude.ai">Claude.ai</a> — it will walk you through the entire setup step by step.</em>
</p>

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

### What is Team Mode?

In Basic mode, you work with **one** Claude Code session. That works fine for small tasks. But what about larger projects — e.g., adding multilingual support, fixing responsive bugs, and writing tests all at the same time?

In **Team Mode**, you open multiple terminals, start a separate Claude Code session in each one, and assign each session a **role** and a **name**. The sessions coordinate through files in the project — just like a real development team.

```
Terminal 1: Anton (Orchestrator)          — coordinates, distributes tasks, deploys
Terminal 2: Benno (Planner)               — analyzes requirements, creates plans
Terminal 3: Chasperli (Planner & Security) — security audits, planning
Terminal 4: Donald (Developer 1)          — works on Feature A
Terminal 5: Egon (Developer 2)            — works on Feature B
Terminal 6: Fridolin (Developer 3)        — works on Feature C
Terminal 7: Guschti (Quality Control)     — checks code quality, tests
Terminal 8: Wilma (Expert)                — domain-specific expert consultations
```

**Prerequisite:** All sessions run in the same project folder and use the same Git repo.

---

### The Team — 8 Agents

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left; width:30px;">#</th>
      <th style="padding:10px 14px; text-align:left;">Name</th>
      <th style="padding:10px 14px; text-align:left;">Role</th>
      <th style="padding:10px 14px; text-align:left;">Responsibilities</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">A</td>
      <td style="padding:8px 14px;"><strong>Anton</strong></td>
      <td style="padding:8px 14px;">Orchestrator</td>
      <td style="padding:8px 14px;">Coordinates the team, distributes tasks, resolves file conflicts, deploys to production. Only he edits <code>boards/&lt;project&gt;.md</code>.</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">B</td>
      <td style="padding:8px 14px;"><strong>Benno</strong></td>
      <td style="padding:8px 14px;">Planner</td>
      <td style="padding:8px 14px;">Analyzes requirements, reads affected files, designs implementation plans, defines interface specifications. Does NOT change code.</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">C</td>
      <td style="padding:8px 14px;"><strong>Chasperli</strong></td>
      <td style="padding:8px 14px;">Planner &amp; Security</td>
      <td style="padding:8px 14px;">Flex role: either planning (like Benno) or security audits — checks OWASP Top 10 risks, scans third-party packages for vulnerabilities, searches for exposed secrets, verifies input validation. Reports findings — does NOT change code.</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">D</td>
      <td style="padding:8px 14px;"><strong>Donald</strong></td>
      <td style="padding:8px 14px;">Developer 1</td>
      <td style="padding:8px 14px;">Implements features, fixes bugs, commits + pushes. Only works on assigned tasks.</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">E</td>
      <td style="padding:8px 14px;"><strong>Egon</strong></td>
      <td style="padding:8px 14px;">Developer 2</td>
      <td style="padding:8px 14px;">Implements features, fixes bugs, commits + pushes. Only works on assigned tasks.</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">F</td>
      <td style="padding:8px 14px;"><strong>Fridolin</strong></td>
      <td style="padding:8px 14px;">Developer 3</td>
      <td style="padding:8px 14px;">Implements features, fixes bugs, commits + pushes. Only works on assigned tasks.</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">G</td>
      <td style="padding:8px 14px;"><strong>Guschti</strong></td>
      <td style="padding:8px 14px;">Quality Control</td>
      <td style="padding:8px 14px;">TypeScript type checks, responsive testing, code review, functional testing. Reports issues — does NOT change code.</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">H</td>
      <td style="padding:8px 14px;"><strong>Wilma</strong></td>
      <td style="padding:8px 14px;">Expert</td>
      <td style="padding:8px 14px;">Domain-specific expert consultations (legal, security, architecture, etc.). Activated via <code>Expert:DOMAIN</code> pattern. Produces written assessments in <code>experts/outputs/</code>. Does NOT change code.</td>
    </tr>
  </tbody>
</table>

**Important:** Roles are strictly separated. A developer only implements what is assigned. The orchestrator reviews and commits.

#### Team Overview

![Team Organigramm — Markus (Product Owner) at the top, Anton (Orchestrator) below, 7 Agents on the same level: Benno, Chasperli, Donald, Egon, Fridolin, Guschti, Wilma](team-organigramm.svg)

<details><summary>Inline fallback (if SVG doesn't render)</summary>
<div style="max-width:780px; margin:1.5rem auto; font-family:'Open Sans',sans-serif;">
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
  <div style="height:3px;background:#94a3b8;margin:0 20px;"></div>
  <div style="display:flex; flex-wrap:wrap; justify-content:center; gap:8px; margin-top:10px;">
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#8b5cf6,#7c3aed);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(139,92,246,0.25);">
      Benno<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Planner</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(16,185,129,0.25);">
      Chasperli<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Planner &amp; Sec</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(245,158,11,0.25);">
      Donald<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Developer 1</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(239,68,68,0.25);">
      Egon<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Developer 2</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#06b6d4,#0891b2);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(6,182,212,0.25);">
      Fridolin<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Developer 3</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#f97316,#ea580c);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(249,115,22,0.25);">
      Guschti<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Quality Control</span>
    </div>
    <div style="flex:1;min-width:80px;max-width:100px;background:linear-gradient(135deg,#ec4899,#db2777);color:#fff;padding:10px 6px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;box-shadow:0 3px 10px rgba(236,72,153,0.25);">
      Wilma<br><span style="font-weight:400;font-size:10px;opacity:0.85;">Expert</span>
    </div>
  </div>
  <div style="text-align:center;margin-top:14px;font-size:12px;color:#64748b;font-style:italic;">
    Anton distributes tasks to all agents &middot; Benno + Chasperli plan &middot; Donald/Egon/Fridolin implement &middot; Guschti reviews &middot; Wilma consults
  </div>
</div>
</details>

---

### Naming Convention

Team members get fixed names in alphabetical order:

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left;">Order</th>
      <th style="padding:10px 14px; text-align:left;">Name</th>
      <th style="padding:10px 14px; text-align:left;">Default Role</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">1st session</td>
      <td style="padding:8px 14px;"><strong>Anton</strong></td>
      <td style="padding:8px 14px;">Orchestrator</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">2nd session</td>
      <td style="padding:8px 14px;"><strong>Benno</strong></td>
      <td style="padding:8px 14px;">Planner</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">3rd session</td>
      <td style="padding:8px 14px;"><strong>Chasperli</strong></td>
      <td style="padding:8px 14px;">Planner &amp; Security</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">4th session</td>
      <td style="padding:8px 14px;"><strong>Donald</strong></td>
      <td style="padding:8px 14px;">Developer 1</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">5th session</td>
      <td style="padding:8px 14px;"><strong>Egon</strong></td>
      <td style="padding:8px 14px;">Developer 2</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">6th session</td>
      <td style="padding:8px 14px;"><strong>Fridolin</strong></td>
      <td style="padding:8px 14px;">Developer 3</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">7th session</td>
      <td style="padding:8px 14px;"><strong>Guschti</strong></td>
      <td style="padding:8px 14px;">Quality Control</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">8th session</td>
      <td style="padding:8px 14px;"><strong>Wilma</strong></td>
      <td style="padding:8px 14px;">Expert</td>
    </tr>
  </tbody>
</table>

When you open a new session, take the next available name. The first session is always the orchestrator.

> **Tip:** When starting a session, just tell Claude: *"You are Benno, Planner on the team. Read the board and check in."* — Claude understands this and behaves accordingly.

---

### Coordination: The `status/` and `boards/` Folders

The heart of team mode is centralized in the **agent-hub** repository. Status files and boards live there — not in individual project repos:

```
agent-hub/
├── status/
│   ├── nachrichten.md     ← Message board (everyone can append)
│   ├── anton.md           ← Anton's status file
│   ├── benno.md           ← Benno's status file
│   ├── chasperli.md       ← Chasperli's status file
│   └── ...
├── boards/
│   ├── setup-guide.md     ← Tasks for setup-guide project
│   ├── agent-hub.md       ← Tasks for agent-hub project
│   ├── supplieronboarding.md
│   └── ...                ← One board per project
```

#### `boards/<project>.md` — The Kanban Board

Each project has its own board file in the `boards/` folder. **Only the orchestrator edits board files.** Tasks flow through 5 stages:

```
Idea → Analysis → Implementation → QC → Done
```

Features use **project-prefix IDs** (e.g., `SG-F-001` for setup-guide, `SO-F-001` for supplieronboarding). Tasks within a feature use an arrow prefix (`→`).

**Example (`boards/setup-guide.md`):**

```markdown
# Kanban — Setup Guide (SG)

### Idea
| ID | Feature | Prio | Beschreibung |
|----|---------|------|--------------|
| SG-F-003 | Dark Mode | P3 | Dark mode toggle for the guide |

### Analysis
| ID | Feature | Prio | Zugewiesen | Beschreibung |
|----|---------|------|------------|--------------|

### Implementation
| ID | Feature/Task | Prio | Zugewiesen | Status |
|----|--------------|------|------------|--------|
| SG-F-001 | Advanced Tab Update | P1 | Chasperli | |
| → | Shared Section: Team 8 Agents | | ⬜ | |
| → | Neue Abschnitte: CLAUDE.md, Expert Agents | | ⬜ | |

### Quality Control
| ID | Feature/Task | Zugewiesen | Status |
|----|--------------|------------|--------|

### Done
| ID | Feature/Task | Abgeschlossen | Beschreibung |
|----|--------------|---------------|--------------|
```

#### `nachrichten.md` — The Message Board

Team members communicate here. **Everyone can append** (add new lines), but nobody deletes other people's messages. Uses a **5-column format** to support multi-project communication:

**Example:**

```markdown
| From | To | Project | Message | Done |
|------|-----|---------|---------|------|
| Benno | Anton | setup-guide | Feature X done! Please commit. | ⬜ |
| Anton | Benno | supplieronboarding | ✅ Committed + deployed. | ✅ |
| Chasperli | Anton | setup-guide | Advanced Tab Update done. Committed + pushed. | ⬜ |
```

The **Project** column identifies which project the message relates to. This is essential in a multi-project setup where agents work across different repositories.

**Important rule:** Each session polls the message board regularly (~15 seconds) and responds to messages addressed to it.

#### Message Flow Between Agents

![Message Flow — All agents communicate through nachrichten.md as the central message board](message-flow.svg)

<details><summary>Inline fallback (if SVG doesn't render)</summary>
<div style="max-width:680px;margin:1.5rem auto;font-family:'Open Sans',sans-serif;">
  <div style="display:flex;align-items:stretch;gap:0;">
    <div style="display:flex;flex-direction:column;gap:6px;justify-content:center;min-width:95px;">
      <div style="background:linear-gradient(135deg,#8b5cf6,#7c3aed);color:#fff;padding:8px 10px;border-radius:10px 0 0 10px;font-size:11px;font-weight:600;text-align:center;">
        Benno<br><span style="font-size:9px;font-weight:400;">Planner</span>
      </div>
      <div style="background:linear-gradient(135deg,#10b981,#059669);color:#fff;padding:8px 10px;border-radius:10px 0 0 10px;font-size:11px;font-weight:600;text-align:center;">
        Chasperli<br><span style="font-size:9px;font-weight:400;">Planner &amp; Sec</span>
      </div>
      <div style="background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff;padding:8px 10px;border-radius:10px 0 0 10px;font-size:11px;font-weight:600;text-align:center;">
        Donald<br><span style="font-size:9px;font-weight:400;">Developer 1</span>
      </div>
      <div style="background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff;padding:8px 10px;border-radius:10px 0 0 10px;font-size:11px;font-weight:600;text-align:center;">
        Egon<br><span style="font-size:9px;font-weight:400;">Developer 2</span>
      </div>
      <div style="background:linear-gradient(135deg,#06b6d4,#0891b2);color:#fff;padding:8px 10px;border-radius:10px 0 0 10px;font-size:11px;font-weight:600;text-align:center;">
        Fridolin<br><span style="font-size:9px;font-weight:400;">Developer 3</span>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px;justify-content:center;padding:0 4px;">
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
    </div>
    <div style="flex:1;background:linear-gradient(180deg,#1e293b,#334155);color:#fff;padding:18px 14px;border-radius:14px;text-align:center;display:flex;flex-direction:column;justify-content:center;box-shadow:0 4px 18px rgba(30,41,59,0.35);margin:0 6px;">
      <div style="font-weight:700;font-size:15px;margin-bottom:4px;">nachrichten.md</div>
      <div style="font-size:12px;opacity:0.8;">Central Message Board</div>
      <div style="margin-top:10px;font-size:11px;opacity:0.7;border-top:1px solid rgba(255,255,255,0.15);padding-top:10px;">
        All agents read &amp; write<br>5-column format (Von/An/Projekt/Nachricht/Erledigt)
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px;justify-content:center;padding:0 4px;">
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
      <div style="color:#0091DC;font-size:18px;line-height:33px;text-align:center;">&#x27A1;&#xFE0E;</div>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px;justify-content:center;min-width:95px;">
      <div style="background:linear-gradient(135deg,#0091DC,#0077b6);color:#fff;padding:8px 10px;border-radius:0 10px 10px 0;font-size:11px;font-weight:600;text-align:center;">
        Anton<br><span style="font-size:9px;font-weight:400;">Orchestrator</span>
      </div>
      <div style="background:linear-gradient(135deg,#f97316,#ea580c);color:#fff;padding:8px 10px;border-radius:0 10px 10px 0;font-size:11px;font-weight:600;text-align:center;">
        Guschti<br><span style="font-size:9px;font-weight:400;">Quality Control</span>
      </div>
      <div style="background:linear-gradient(135deg,#ec4899,#db2777);color:#fff;padding:8px 10px;border-radius:0 10px 10px 0;font-size:11px;font-weight:600;text-align:center;">
        Wilma<br><span style="font-size:9px;font-weight:400;">Expert</span>
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
- `boards/<project>.md` is only edited by the orchestrator → **single writer**
- `nachrichten.md` is append-only → **minimal conflict risk**

> Think of it like a real team: Everyone has their own desk (status file), there's a whiteboard (boards/) that only the lead writes on, and a mailbox (nachrichten.md) where everyone can drop notes.

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
- Session-specific tasks (use `boards/<project>.md` for that)
- Temporary state
- Duplicates of CLAUDE.md content

> **Tip:** When the team discovers something important (e.g., "Prisma must be in dependencies, not devDependencies"), the orchestrator should save it in MEMORY.md — then all future sessions know it automatically.

---

### CLAUDE.md — Project Instructions

Every project gets its own `CLAUDE.md` file in the project root. Claude Code automatically loads this file at the start of every session — it's the project's instruction manual for agents.

**What belongs in CLAUDE.md:**
- Project description and purpose
- Tech stack (frameworks, languages, build tools)
- Important file paths and project structure
- Team conventions (naming, commit format, language)
- Build and test commands

**Example (from a real project):**

```markdown
# CLAUDE.md — Setup Guide

## Projekt
Interactive Setup Guide for Multi-Agent Development with Claude Code.

## Tech Stack
- **Static Site:** Jekyll + Cayman Theme + GitHub Pages
- **Content:** Markdown + inline HTML/CSS + SVG diagrams
- **URL:** https://example.github.io/setup-guide/

## Important Files
index.md          — All content (tabs, sub-tabs, sections)
_layouts/default.html — Layout template
assets/           — Images (screenshots, diagrams)
_config.yml       — Jekyll config

## Conventions
- **Language:** English
- **Styling:** Inline HTML/CSS in Markdown
- **Commits:** feat: / fix: + description
```

**CLAUDE.md vs MEMORY.md:**
- `CLAUDE.md` = **project-level** instructions, checked into the repo, shared with all agents
- `MEMORY.md` = **agent-level** auto-memory, stored in `.claude/`, personal learnings

---

### Expert Agents

For specialized domain knowledge (legal, security, architecture, procurement), the team uses **Expert Agents**. Instead of a developer guessing about compliance rules or database architecture, an expert agent provides a structured assessment.

#### How it Works

1. Anton sends a message using the `Expert:DOMAIN` pattern:
   ```markdown
   | Anton | Wilma | setup-guide | Expert:security — Review the authentication flow for OWASP Top 10 compliance. | ⬜ |
   ```
2. The orchestrator detects the `Expert:` prefix and loads the matching template from `experts/security.md`
3. Wilma (the Expert agent) analyzes the topic and writes a structured assessment
4. The assessment is saved to `experts/outputs/` for the team to reference

#### Expert Templates

Templates live in the `experts/` folder with YAML frontmatter:

```markdown
---
name: "Security Expert"
domain: "security"
keywords: ["owasp", "vulnerability", "authentication"]
description: "Security audits and vulnerability assessments"
max_budget_usd: 0.50
---

# Expert: Security

## Role
You are an experienced security expert. You are consulted for
specific security questions and deliver a written assessment.

## Knowledge Areas
- OWASP Top 10
- Authentication & Authorization
- Input Validation & Sanitization

## Response Rules
1. Structured response with clear headings
2. Practical recommendations, not theoretical essays
3. Stay within your domain
4. Reference provided context files
5. Flag risks and compliance requirements
6. Markdown format, no code changes — advisory only
```

Available expert domains include: `security`, `legal`, `react`, `sap`, `procurement`, `ui-ux`, `enterprise-architecture`, and `prisma`.

---

### Multi-Project Architecture

The agent-hub is designed to manage **multiple projects** from a single hub. The orchestrator, status files, and boards all live in the `agent-hub` repository, while project code lives in separate repos.

#### config.json — The Project Registry

The `config.json` in agent-hub defines all managed projects:

```json
{
  "projects": [
    { "name": "agent-hub",           "short": "AH", "prefix": "AH", "path": "..." },
    { "name": "supplieronboarding",  "short": "SO", "prefix": "SO", "path": "..." },
    { "name": "setup-guide",         "short": "SG", "prefix": "SG", "path": "..." },
    { "name": "react-ui-library",    "short": "RU", "prefix": "RU", "path": "..." },
    { "name": "inafit",              "short": "IF", "prefix": "IF", "path": "..." },
    { "name": "backline",            "short": "BL", "prefix": "BL", "path": "..." }
  ],
  "team": {
    "Anton": "Orchestrator",
    "Benno": "Planner",
    "Chasperli": "Planner & Security",
    "Donald": "Developer",
    "Egon": "Developer",
    "Fridolin": "Developer",
    "Guschti": "Quality Control",
    "Wilma": "Expert"
  },
  "experts": {
    "dir": "experts",
    "outputDir": "experts/outputs",
    "defaultBudget": 0.50
  }
}
```

#### Hub-and-Spoke Model

```
                    ┌──────────────┐
                    │  agent-hub   │
                    │              │
                    │  status/     │  ← Central coordination
                    │  boards/     │  ← One board per project
                    │  experts/    │  ← Expert templates
                    │  config.json │  ← Project registry
                    └──────┬───────┘
                           │
          ┌────────┬───────┼───────┬────────┬────────┐
          ▼        ▼       ▼       ▼        ▼        ▼
       ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
       │ AH  │ │ SO  │ │ SG  │ │ RU  │ │ IF  │ │ BL  │
       └─────┘ └─────┘ └─────┘ └─────┘ └─────┘ └─────┘
       agent-  supplier setup-  react-  inafit  backline
       hub     onboard. guide   ui-lib
```

**Key principles:**
- **One board per project** — `boards/setup-guide.md`, `boards/agent-hub.md`, etc.
- **Project-prefix IDs** — `SG-F-001`, `SO-F-002` to avoid collisions across projects
- **Central status/** — All agent status files and nachrichten.md live in agent-hub
- **Agents work across projects** — A developer can work on setup-guide in one task and supplieronboarding in the next

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
│  ④ Anton creates tasks in boards/<project>.md             │     │
│     ├── Task A → Donald                                   │     │
│     ├── Task B → Egon                                     │     │
│     └── Task C → Fridolin                                 │     │
│                    │         │         │                   │     │
│  ⑤ Developers     ▼         ▼         ▼    (parallel!)   │     │
│     implement + commit + push                             │     │
│                    │         │         │                   │     │
│  ⑥ Anton → Guschti ◀────────┴─────────┘                  │     │
│     "Quality check please"                                     │     │
│                    │                                       │     │
│  ⑦ Guschti → Anton                                       │     │
│     Quality report (OK or issues)                              │     │
│                    │                                       │     │
│  ⑧ Anton → Chasperli (planning or security audit)         │     │
│     Flex: analysis/planning or security review            │     │
│                    │                                       │     │
│  ⑨ Anton deploys to production ◀──────────────────────────┘     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

Shortcut (small tasks): Anton → Developer → Commit → Done (no Planner/Quality Control)
```
<div class="sub-tabs">
  <button class="sub-tab active" onclick="switchSubTab('classic', this)">Classic</button>
  <button class="sub-tab" onclick="switchSubTab('autonomous', this)">Autonomous</button>
</div>

<!-- ========== SUB-TAB: CLASSIC ========== -->
<div id="subtab-classic" class="sub-panel active" markdown="1">

### Classic Mode

In Classic mode, you manually open each terminal, start each Claude Code session, and paste in the role prompt yourself. This gives you full control over which sessions run and when. It's the simplest way to get started with team mode.

---


### Example Workflow

Here's a typical flow with three sessions:

**1. Orchestrator (Anton) starts and plans**

```
Terminal 1:
> claude --dangerously-skip-permissions
> "You are Anton, the Orchestrator. Read the board and distribute the open tasks."
```

Anton reads the task list, checks which developers are online, and distributes tasks via `nachrichten.md`:

```markdown
| Anton | Donald | setup-guide | Please do the responsive bugfixes. | ⬜ |
| Anton | Egon | setup-guide | Please set up the multilingual framework. | ⬜ |
```

**2. Developer (Donald) checks in and works**

```
Terminal 2:
> claude --dangerously-skip-permissions
> "You are Donald, Developer. Read the board and nachrichten.md."
```

Donald sees his task, updates `status/donald.md`, and starts working. He polls `nachrichten.md` regularly for new instructions.

**3. Developer (Egon) works in parallel**

```
Terminal 3:
> claude --dangerously-skip-permissions
> "You are Egon, Developer. Read the board and nachrichten.md."
```

Egon works on a different feature at the same time — no conflict because they work on different files (listed in status files).

**4. Donald finishes**

Donald writes in `nachrichten.md`:

```markdown
| Donald | Anton | setup-guide | Responsive bugfixes done! Changed files: src/index.css, SupplierDetail.tsx. Please commit. | ⬜ |
```

**5. Anton commits**

Anton reads the message, reviews the changes, and commits:

```
Terminal 1:
> "Commit Donald's responsive bugfixes and deploy."
```

Anton marks the message as done (✅) and the task in `boards/setup-guide.md` as completed.

**6. Next round**

Anton distributes the next task, or Benno asks: *"What's next?"*

---

### Quick Start Checklist

Here's how to set up team mode:

1. **Create the folders** (in your agent-hub repo):
   ```bash
   mkdir status boards
   ```

2. **Create `boards/<project>.md`** with a Kanban template:
   ```markdown
   # Kanban — My Project (MP)

   ### Idea
   | ID | Feature | Prio | Beschreibung |
   |----|---------|------|--------------|

   ### Analysis
   | ID | Feature | Prio | Zugewiesen | Beschreibung |
   |----|---------|------|------------|--------------|

   ### Implementation
   | ID | Feature/Task | Prio | Zugewiesen | Status |
   |----|--------------|------|------------|--------|

   ### Quality Control
   | ID | Feature/Task | Zugewiesen | Status |
   |----|--------------|------------|--------|

   ### Done
   | ID | Feature/Task | Abgeschlossen | Beschreibung |
   |----|--------------|---------------|--------------|
   ```

3. **Create `status/nachrichten.md`:**
   ```markdown
   # Messages

   > Everyone can append here. Newest message at the bottom.

   | From | To | Project | Message | Done |
   |------|-----|---------|---------|------|
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
   > You are Donald, Developer. Read the board and check in.
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

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left;">Aspect</th>
      <th style="padding:10px 14px; text-align:left;">Classic</th>
      <th style="padding:10px 14px; text-align:left;">Autonomous</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Starting sessions</strong></td>
      <td style="padding:8px 14px;">You open terminals manually</td>
      <td style="padding:8px 14px;">Script spawns sessions automatically</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Task distribution</strong></td>
      <td style="padding:8px 14px;">Copy-paste prompts</td>
      <td style="padding:8px 14px;">Write to nachrichten.md, script does the rest</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Supervision</strong></td>
      <td style="padding:8px 14px;">You watch each terminal</td>
      <td style="padding:8px 14px;">Agents work in the background</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Scaling</strong></td>
      <td style="padding:8px 14px;">Limited by your terminal tabs</td>
      <td style="padding:8px 14px;">Up to N concurrent agents (configurable)</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Best for</strong></td>
      <td style="padding:8px 14px;">Learning, small teams, one-off tasks</td>
      <td style="padding:8px 14px;">Larger projects, recurring tasks, batch processing</td>
    </tr>
  </tbody>
</table>

---

### Prerequisites

- **Node.js** installed (v18+)
- **Claude Code** installed and authenticated (`claude --version`)
- The `status/` folder set up in **agent-hub** as described above
- The orchestrator script (`orchestrator.cjs` in the agent-hub root)


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
  cwd: PROJECT_ROOT,   // cwd = current working directory
  stdio: ['pipe', 'pipe', 'pipe'],
  shell: true,
  env,  // with CLAUDECODE environment variable deleted!
});

// Send prompt via standard input (not as a command-line argument!)
proc.stdin.write(prompt);
proc.stdin.end();
```

**Key details:**

1. **`--dangerously-skip-permissions`** — Required for headless operation. Without it, Claude would prompt for permission on every file edit and command, which doesn't work in an unattended process.

2. **`-p` flag** — Runs Claude in "print mode" (non-interactive). Takes input, produces output, exits.

3. **`--verbose`** — Shows detailed progress in the error output stream so you can follow what the agent is doing.

#### Critical Learnings (from Production Use)

These are hard-won lessons from running autonomous agents in a real project:

**1. Delete the `CLAUDECODE` environment variable when spawning**

```javascript
const env = { ...process.env };
delete env.CLAUDECODE;
```

If Claude Code detects it's running inside another Claude Code session (via this environment variable), it may block or behave unexpectedly. Always delete it before spawning child sessions.

**2. Send the prompt via standard input, not as a command-line argument**

```javascript
// ✅ Correct — via standard input
proc.stdin.write(prompt);
proc.stdin.end();

// ❌ Wrong — as command-line argument
spawn('claude', ['-p', '--dangerously-skip-permissions', prompt]);
```

Long prompts with special characters (`|`, `!`, `"`, newlines) break when passed as shell arguments. Sending via standard input avoids all escaping issues.

**3. Use `.cjs` extension in ES Module projects**

If your project uses `"type": "module"` in `package.json`, Node.js treats all `.js` files as ES Modules (the modern JavaScript module system using `import`/`export`). The orchestrator uses `require()` (the older CommonJS module system), so it must have a `.cjs` extension to tell Node.js it uses the older format:

```
orchestrator.cjs  ← works (in agent-hub root)
orchestrator.js   ← fails with "require is not defined"
```

**4. Agents must update their status files regularly**

Every agent should update `status/<name>.md` after each major step — not just at the beginning and end. This lets the orchestrator (and monitoring dashboard) track progress in real-time. Include a timestamp on every update.

**5. Monitoring Dashboard on Port 3002**

A companion script (`scripts/dashboard.cjs` in agent-hub) runs an Express server on port 3002 that reads the `status/` and `boards/` folders and displays a live dashboard: who's online, what they're working on, recent messages, and Kanban boards for all projects. Auto-refreshes every 5 seconds.

```bash
node scripts/dashboard.cjs   # run from agent-hub directory
# Open http://localhost:3002
```

---

#### Role-Specific Prompts

The orchestrator sends different instructions based on the agent's role:

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left;">Role</th>
      <th style="padding:10px 14px; text-align:left;">Instructions</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Planner</strong></td>
      <td style="padding:8px 14px;">Read the project board, analyze affected files, create implementation plan, do NOT change code</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Developer</strong></td>
      <td style="padding:8px 14px;">Read the project board, implement the task, commit + push, report to orchestrator</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;"><strong>Quality Control</strong></td>
      <td style="padding:8px 14px;">Run TypeScript type checker (<code>tsc --noEmit</code>) and production build (<code>vite build</code>), review recent commits, check responsive design (mobile/tablet layout), report findings</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;"><strong>Planner &amp; Security</strong></td>
      <td style="padding:8px 14px;">Flex role: planning (analyze requirements, design plans) or security (check for the 10 most critical web security risks, run <code>npm audit</code> to find vulnerable packages, scan for exposed secrets, verify user input validation). Report findings</td>
    </tr>
  </tbody>
</table>

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
# Start the orchestrator (from agent-hub directory)
node orchestrator.cjs
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

Waiting for tasks in nachrichten.md...
```

The script runs indefinitely. It marks existing messages as "already processed" on startup (so it doesn't re-run old tasks). New messages trigger agent spawning.

Stop it with `Ctrl+C` — it will gracefully terminate all running agents.

---

### Writing Tasks

To assign a task, add a line to `nachrichten.md`:

```markdown
| Anton | Benno | supplieronboarding | Analyze the SupplierDetail page and plan the edit feature. | ⬜ |
```

The orchestrator picks this up within seconds and spawns a Benno session. The `⬜` marker indicates an unprocessed message.

**Format:**

```
| From | To | Task description | ⬜ |
```

- **From** must be `Anton` (the orchestrator only reacts to messages from Anton)
- **To** must be an agent name from the roster (Benno, Chasperli, Donald, Egon, Fridolin, Guschti)
- **Task** should be clear and self-contained — the agent sees only this plus the project board

---

### Agent Lifecycle

Each spawned agent follows this lifecycle:

```
  ┌───────────────────────────────────────────────────────────┐
  │                  Agent Lifecycle                           │
  ├───────────────────────────────────────────────────────────┤
  │                                                           │
  │   ┌─────────┐    Read board +       ┌──────────┐          │
  │   │  START   │───────────────────▶│ CHECK IN  │          │
  │   └─────────┘    nachrichten.md    │ (online)  │          │
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

The orchestrator shows live output (both regular output and error messages) from each agent, prefixed with the agent name:

```
🚀 Benno startet: Analyze the SupplierDetail page...
   [Benno] Reading project board...
   [Benno] Analyzing SupplierDetail.tsx...
   [Benno] Writing implementation plan...
✅ Benno fertig (completed successfully)
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

The dashboard auto-refreshes every 5 seconds by fetching new data and updating the page content directly (no full page reload).

---

### Classic vs. Autonomous — When to Use What

<table style="width:100%; border-collapse:collapse; font-size:15px;">
  <thead>
    <tr style="background:#1e293b; color:white;">
      <th style="padding:10px 14px; text-align:left;">Scenario</th>
      <th style="padding:10px 14px; text-align:left;">Recommended Mode</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">First time trying team mode</td>
      <td style="padding:8px 14px;"><strong>Classic</strong> — learn the coordination patterns</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">2-3 sessions, one-off tasks</td>
      <td style="padding:8px 14px;"><strong>Classic</strong> — manual control is fine</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">4+ parallel agents</td>
      <td style="padding:8px 14px;"><strong>Autonomous</strong> — manual terminal management gets unwieldy</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">Recurring task patterns</td>
      <td style="padding:8px 14px;"><strong>Autonomous</strong> — standardized prompts work great</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">Batch processing (e.g., 10 bug fixes)</td>
      <td style="padding:8px 14px;"><strong>Autonomous</strong> — write all tasks, let agents process them</td>
    </tr>
    <tr style="background:#f1f5f9;">
      <td style="padding:8px 14px;">Exploring / prototyping</td>
      <td style="padding:8px 14px;"><strong>Classic</strong> — you want interactive control</td>
    </tr>
    <tr style="background:#f8fafc;">
      <td style="padding:8px 14px;">Continuous Integration</td>
      <td style="padding:8px 14px;"><strong>Autonomous</strong> — script can be triggered by automated build/test pipelines (Continuous Integration)</td>
    </tr>
  </tbody>
</table>

---

### Quick Start: Autonomous Mode

```
┌────────────────────────────────────────────────────────────────┐
│  Your Setup — 3 Terminals (all in agent-hub directory)         │
├────────────────────┬────────────────────┬──────────────────────┤
│  Terminal 1        │  Terminal 2        │  Terminal 3          │
│                    │                    │  (optional)          │
│  claude            │  node              │  node scripts/       │
│  (Anton -          │  orchestrator.cjs  │  dashboard.cjs       │
│   interactive)     │  (auto-spawns     │  (monitoring on      │
│                    │   agents across   │   port 3002)         │
│  You talk to       │   all projects)   │  Shows who's         │
│  Anton, he writes  │  Watches          │  online, current     │
│  tasks to          │  nachrichten.md   │  tasks, Kanban       │
│  nachrichten.md    │  and spawns new   │  boards for all      │
│                    │  claude sessions  │  projects             │
└────────────────────┴────────────────────┴──────────────────────┘
```

1. **Set up agent-hub** with `status/` folder (nachrichten.md, agent status files) and `boards/` folder (one board per project)

2. **The orchestrator script** is `orchestrator.cjs` in the agent-hub root:
   ```bash
   # It parses nachrichten.md, spawns claude -p, pipes prompt via stdin
   # Agents are spawned in the target project's directory (from config.json)
   ```

3. **Start the orchestrator:**
   ```bash
   node orchestrator.cjs
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
   | Anton | Donald | setup-guide | Fix the responsive layout on the login page. | ⬜ |
   ```

6. **Watch the orchestrator** spawn Donald in the setup-guide project directory and process the task.

7. **Optionally start the dashboard** for monitoring:
   ```bash
   node scripts/dashboard.cjs
   # Open http://localhost:3002
   ```

</div>

---

### Lessons Learned

Real-world experience from running an 8-agent team on multiple production projects. These are patterns and pitfalls we discovered the hard way.

#### 1. Spawn agents via nachrichten.md, not boards/

The orchestrator script watches `nachrichten.md` for new messages from Anton to an agent name (marked with ⬜). It does **not** watch the board files. If you write a task only in `boards/<project>.md`, no agent will be spawned. The correct workflow:
1. Write the task description in `boards/<project>.md` (for tracking)
2. Write a message in `nachrichten.md` addressed to an agent name (this triggers the spawn)

#### 2. Assign tasks by role, not by name

Agents are short-lived — a "Chasperli" session that finishes its task goes offline, and the next available session gets a new name. Don't address tasks to "Chasperli" specifically. Instead, write the task for the **role** (e.g., "first available Developer") and let the orchestrator assign it to whoever comes online next.

#### 3. Clean up boards before adding new tasks

Move completed features to the "Done" column before writing new ones. A cluttered board with old tasks causes confusion — agents may pick up already-finished work or duplicates. Keep the "Implementation" column small and current.

#### 4. Short-lived agents need real-time monitoring

Some agents finish their task in under 2 minutes. If your monitoring dashboard only refreshes every 5 seconds, you might miss them entirely. Solutions:
- Add a "recently active" state (e.g., amber highlight for agents active within the last 5 minutes)
- Sort agents: online → recently active → offline
- Keep a history of completed sessions visible

#### 5. Token measurement requires `--output-format json`

The `claude -p` CLI outputs token usage only when you pass `--output-format json`. Without this flag, `parseTokenUsage()` in the orchestrator falls back to estimating tokens from output length — which gives wildly wrong numbers (e.g., 58 tokens instead of 50,000+). Always spawn with:
```bash
claude -p --dangerously-skip-permissions --output-format json
```

#### 6. useBlocker requires a Data Router

React Router's `useBlocker()` hook internally calls `useDataRouterContext()`, which requires a **Data Router** (`createBrowserRouter` + `RouterProvider`). If your app uses the classic `<BrowserRouter>`, `useBlocker` will crash with: *"useBlocker must be used within a data router"*. Workaround: use `window.confirm()` in a navigation wrapper and rely on `beforeunload` for browser refresh protection.

---

*v1.2 · March 5, 2026 · M. Suter, Switzerland · Built with Claude Code + Multi-Session Team Mode.*

</div>
