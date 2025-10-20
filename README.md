[![Agents](https://img.shields.io/badge/agents-19-blue)](#agents)
[![Plugins](https://img.shields.io/badge/plugins-11-green)](#plugins)
[![Skills](https://img.shields.io/badge/skills-21-orange)](#plugins)
[![MCPs](https://img.shields.io/badge/MCPs-1-purple)](#mcps)

# Claude Code Setup

**Optimized for vibe coding** — Describe what you want, AI handles implementation. Uses 62 specialized tools (agents, skills, plugins, MCPs) organized by what you're building, not where they came from.

---

## How Claude Code Works

```
┌─────────────────────────────────────────────────────────────┐
│                    CLAUDE CODE ECOSYSTEM                    │
└─────────────────────────────────────────────────────────────┘


MARKETPLACE FLOW
────────────────

🏪 MARKETPLACE
   │  Collection of related plugins
   │  Examples: superpowers-marketplace, claude-code-workflows
   ↓
🔧 PLUGIN
   │  Bundle of skills (or agents in SEO case)
   │  Enabled in: ~/.claude/settings.json
   │  Format: "plugin-name@marketplace-name"
   ↓
⚡ SKILL
   │  Workflow framework that guides how Claude works
   │  Auto-triggers OR slash commands
   │
   Examples:
   • brainstorming → Socratic questioning before design
   • test-driven-development → Write tests first
   • requesting-code-review → Spawn code-reviewer


AGENT KIT FLOW
───────────────

📦 AGENT KIT
   │  Installed via CLI (I use Leamas)
   │  Command: ~/leamas/leamas agent@kit-name
   ↓
🤖 AGENT
   │  Fresh Claude instance with domain expertise
   │  Auto-invoked OR called via Task()
   │
   Examples:
   • frontend-developer → Builds React components
   • ui-designer → Creates design systems
   • code-reviewer → Reviews code quality

MCP FLOW
────────

🔌 MCP SERVER
   │  External service (NOT AI)
   │  Configured in: claude_desktop_config.json
   ↓
🛠️ TOOL/CAPABILITY
   │  Claude queries these for enhanced capabilities
   │
   Examples:
   • sequential-thinking → Step-by-step reasoning
   • playwright → Browser automation
```

---

## Example: How Tools Work Together

```
USER: "Add authentication to my app"
  │
  ▼ Claude analyzes → Identifies: auth, OAuth, sessions
  │
  ├─ ⚡ brainstorming
  │  └─ Socratic questions: OAuth providers? Password reset? Sessions?
  │
  ├─ ⚡ test-driven-development
  │  └─ Write failing tests: login✗ logout✗ OAuth✗
  │
  ├─ Parallel execution ───────────────────────────────────────────────────────┐
  │  🤖 frontend-developer       🤖 database-admin          🔌 context7        │
  │     Build login UI              Create users table         Lookup Auth0/   │
  │     (React + TypeScript)        (oauth, sessions)          Supabase docs   │
  │
  ├─ ⚡ requesting-code-review
  │  └─ Spawn code-reviewer agent: Check SQL injection, auth bypass
  │
  ├─ ⚡ verification-before-completion
  │  └─ Run tests: login✓ logout✓ OAuth✓
  │
  ✅ Feature complete & secure
```

---



## Installation

### How to Install Agents

I use **Leamas** to install agent kits. Each kit bundles multiple related agents.

```bash
# Install Leamas (if not already installed)
# Visit: https://leamas.sh/

# Install agent kits I use:
~/leamas/leamas agent@claude-code-sub-agents  # 6 development agents
~/leamas/leamas agent@wshobson                # 10 vibe coding + utility agents
```

**Available Agent Kits:**
- `claude-code-sub-agents` — 6 agents (ui-designer, ux-designer, frontend-developer, ios-developer, code-reviewer, prompt-engineer)
- `wshobson` — 10 agents (agent-organizer, vibe-coding-coach, context-manager, nextjs-pro, data-scientist, quant-analyst, python-pro, database-admin, database-optimizer, payment-integration)



  
### How to Get Plugin Marketplaces

Plugins come from **marketplaces** — collections of related plugins.

**Marketplaces I Use:**

1. **[Superpowers Marketplace](https://github.com/Ejb503/multiverse-of-multiagents)**
   - Community-driven framework for systematic development workflows
   - Contains: superpowers plugin, elements-of-style plugin

2. **[Claude Code Workflows](https://github.com/anthropics/claude-code-workflows)**
   - Official Anthropic workflows for specialized tasks
   - Contains: javascript-typescript, frontend-mobile-development, code-documentation, SEO plugins (3 total)

3. **[Claude Code Plugins](https://github.com/anthropics/claude-code-plugins)**
   - Core utilities and integrations
   - Contains: git, commit-commands

4. **[Claude Mem by thedotmack](https://github.com/thedotmack/claude-mem)**
   - Persistent memory system using SQLite
   - Standalone plugin with MCP integration



---

# Agents

Agents are installed to: `~/.claude/agents/leamas/{kit-name}/`


### 🧠 Agent Organizer

```yaml
---
name: agent-organizer
description: Coordinates multiple agents working together on complex workflows
works-with: all agents
use-when: Running complex multi-agent workflows
kit: wshobson
---
```

**Key Capabilities:**
- Acts as your AI project manager
- Tracks which agents handle what
- Ensures work doesn't overlap

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 🎯 Vibe Coding Coach

```yaml
---
name: vibe-coding-coach
description: Your friendly coding mentor with personality
works-with: all development agents
kit: wshobson
---
```

**Key Capabilities:**
- Provides guidance while you code
- Explains concepts in approachable ways
- Helps improve your skills conversationally

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 📦 Context Manager

```yaml
---
name: context-manager
description: Optimizes how context is used across conversations
use-when: Working on large codebases or long sessions
kit: wshobson
---
```

**Key Capabilities:**
- Maximizes available context windows
- Ensures important information is preserved when needed
- Prevents context overflow

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 🎨 Prompt Engineer

```yaml
---
name: prompt-engineer
description: Expert prompt architect using Opus model for maximum reasoning
use-when: Building AI features or optimizing prompts
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- Specializes in Chain-of-Thought and Tree-of-Thoughts techniques
- Essential when building AI features
- Optimizes prompts for LLM performance

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### 🎨 UI Designer

```yaml
---
name: ui-designer
description: Creates design systems and visual interfaces with WCAG accessibility
requires: magic MCP, context7 MCP
works-with: frontend-developer, ux-designer
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- Color palettes, typography, spacing systems
- Component libraries
- WCAG accessibility compliance

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### 👤 UX Designer

```yaml
---
name: ux-designer
description: Conducts user research, creates journey maps, and designs usability tests
requires: context7 MCP, sequential-thinking MCP, playwright MCP
works-with: ui-designer, frontend-developer
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- User flows, pain points, and interaction patterns
- Wireframes and prototypes
- Design validation with users

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### ⚛️ Frontend Developer

```yaml
---
name: frontend-developer
description: Builds production-ready React components with TypeScript and Tailwind
requires: magic MCP, context7 MCP, playwright MCP
works-with: ui-designer, code-reviewer, nextjs-pro
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- State management, hooks, responsive design
- Accessibility best practices
- Testing with React Testing Library

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### 📱 iOS Developer

```yaml
---
name: ios-developer
description: Native iOS development using Swift, SwiftUI, and UIKit
works-with: ui-designer
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- iOS-specific patterns and navigation
- Platform conventions
- App Store optimization

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### 👁️ Code Reviewer

```yaml
---
name: code-reviewer
description: Reviews code for quality, security, performance, and maintainability
requires: context7 MCP, sequential-thinking MCP
works-with: all development agents
kit: claude-code-sub-agents
---
```

**Key Capabilities:**
- Actionable feedback with line-by-line suggestions
- Security vulnerability detection
- Best practices enforcement

```bash
# Included in claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

---

### ⚡ Next.js Pro

```yaml
---
name: nextjs-pro
description: Next.js specialist covering SSR, SSG, routing, and Next.js patterns
works-with: frontend-developer
kit: wshobson
---
```

**Key Capabilities:**
- App Router, Server Components
- Deployment best practices
- Performance optimization

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 📊 Data Scientist

```yaml
---
name: data-scientist
description: Handles data analysis, statistical modeling, SQL queries, BigQuery operations
works-with: python-pro, database-optimizer
kit: wshobson
---
```

**Key Capabilities:**
- Machine learning implementations
- Data transformation or analysis
- Statistical analysis

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 📈 Quant Analyst

```yaml
---
name: quant-analyst
description: Quantitative analysis and financial modeling
kit: wshobson
---
```

**Key Capabilities:**
- Statistical analysis
- Risk modeling
- Financial calculations

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 🐍 Python Pro

```yaml
---
name: python-pro
description: Python development specialist
works-with: data-scientist
kit: wshobson
---
```

**Key Capabilities:**
- Data analysis, scripting, automation
- Python-specific best practices
- Knows pandas, numpy, requests

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 🗄️ Database Admin

```yaml
---
name: database-admin
description: Database setup, configuration, and ongoing management
works-with: database-optimizer
kit: wshobson
---
```

**Key Capabilities:**
- Schema design, migrations, backups
- Database administration tasks

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### ⚡ Database Optimizer

```yaml
---
name: database-optimizer
description: Optimizes database queries and overall database performance
works-with: database-admin, data-scientist
kit: wshobson
---
```

**Key Capabilities:**
- Analyzes slow queries
- Suggests indexes
- Improves database efficiency

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 💳 Payment Integration

```yaml
---
name: payment-integration
description: Integrating payment systems like Stripe and PayPal
kit: wshobson
---
```

**Key Capabilities:**
- Payment workflows, webhooks
- Security considerations
- Checkout flows

```bash
# Included in wshobson kit
~/leamas/leamas agent@wshobson
```

---

### 📰 SEO Content Writer

```yaml
---
name: seo-content-writer
description: Writes E-E-A-T optimized articles with proper keyword density
model: Sonnet (high-quality long-form content)
plugin: seo-content-creation@claude-code-workflows
---
```

**Key Capabilities:**
- 0.5-1.5% keyword density
- Structures content for readability and ranking

```bash
# Enable plugin in ~/.claude/settings.json:
"seo-content-creation@claude-code-workflows": true
```

---

### 📅 SEO Content Planner

```yaml
---
name: seo-content-planner
description: Creates content calendars, topic clusters, and search intent mappings
model: Haiku (fast planning)
plugin: seo-content-creation@claude-code-workflows
---
```

**Key Capabilities:**
- Plans content strategy
- Topic clustering and search intent mapping

```bash
# Enable plugin in ~/.claude/settings.json:
"seo-content-creation@claude-code-workflows": true
```

---

### 📊 SEO Content Auditor

```yaml
---
name: seo-content-auditor
description: Scores content quality 1-10 and provides improvement recommendations
model: Sonnet (thorough analysis)
plugin: seo-content-creation@claude-code-workflows
---
```

**Key Capabilities:**
- Actionable improvement recommendations
- Quality scoring system

```bash
# Enable plugin in ~/.claude/settings.json:
"seo-content-creation@claude-code-workflows": true
```

---

# Plugins
**How to Enable Plugins:**

Edit `~/.claude/settings.json` and add plugins to `enabledPlugins`:

```json
{
  "enabledPlugins": {
    "superpowers@superpowers-marketplace": true,
    "claude-mem@thedotmack": true,
    "javascript-typescript@claude-code-workflows": true,
    "seo-content-creation@claude-code-workflows": true,
    "git@claude-code-plugins": true
  }
}
```

**Plugin Locations:**
- Installed to: `~/.claude/plugins/marketplaces/{marketplace-name}/{plugin-name}/`
- Settings: `~/.claude/settings.json`



```json
{
  "enabledPlugins": {

    // ═══════════════════════════════════════════════════════════════════
    // 🔧 CORE DEVELOPMENT WORKFLOWS
    // ═══════════════════════════════════════════════════════════════════

    // superpowers@superpowers-marketplace
    // Foundation of vibe coding with 10 systematic development skills
    // Skills: using-superpowers, brainstorming, writing-plans,
    //         executing-plans, subagent-driven-development,
    //         dispatching-parallel-agents, writing-skills,
    //         testing-skills-with-subagents, sharing-skills
    // Repo: https://github.com/Ejb503/multiverse-of-multiagents
    "superpowers@superpowers-marketplace": true,


    // ═══════════════════════════════════════════════════════════════════
    // 🧠 MEMORY & CONTEXT
    // ═══════════════════════════════════════════════════════════════════

    // claude-mem@thedotmack
    // Persistent memory system using SQLite with full-text search
    // Provides: 6 MCP search tools for querying stored knowledge
    // Automatically captures work, processes into summaries
    // Repo: https://github.com/thedotmack/claude-mem
    "claude-mem@thedotmack": true,


    // ═══════════════════════════════════════════════════════════════════
    // 💻 JAVASCRIPT / TYPESCRIPT / FRONTEND
    // ═══════════════════════════════════════════════════════════════════

    // javascript-typescript@claude-code-workflows
    // 4 skills covering modern JS patterns and TypeScript
    // Skills: modern-javascript-patterns, javascript-testing-patterns,
    //         nodejs-backend-patterns, typescript-advanced-types
    "javascript-typescript@claude-code-workflows": true,

    // frontend-mobile-development@claude-code-workflows
    // 2 skills for building React and mobile apps
    // Skills: frontend-developer, mobile-developer
    "frontend-mobile-development@claude-code-workflows": true,

    // code-documentation@claude-code-workflows
    // 3 skills covering code review and documentation
    // Skills: code-reviewer, docs-architect, tutorial-engineer
    "code-documentation@claude-code-workflows": true,


    // ═══════════════════════════════════════════════════════════════════
    // 📝 SEO & CONTENT CREATION
    // ═══════════════════════════════════════════════════════════════════

    // seo-content-creation@claude-code-workflows
    // Content writing optimized for search engines with E-E-A-T signals
    // Agents: seo-content-writer, seo-content-planner, seo-content-auditor
    "seo-content-creation@claude-code-workflows": true,

    // seo-technical-optimization@claude-code-workflows
    // Technical SEO optimization covering keywords, meta tags, snippets
    // Agents: seo-keyword-strategist, seo-meta-optimizer,
    //         seo-snippet-hunter, seo-structure-architect
    "seo-technical-optimization@claude-code-workflows": true,

    // seo-analysis-monitoring@claude-code-workflows
    // SEO analysis and monitoring for authority building
    // Agents: seo-authority-builder, seo-content-refresher,
    //         seo-cannibalization-detector
    "seo-analysis-monitoring@claude-code-workflows": true,

    // elements-of-style@superpowers-marketplace
    // Applies Strunk & White's timeless writing principles
    // Skills: writing-clearly-and-concisely
    // Works on: documentation, commit messages, error messages
    "elements-of-style@superpowers-marketplace": true,


    // ═══════════════════════════════════════════════════════════════════
    // 🔧 GIT & VERSION CONTROL
    // ═══════════════════════════════════════════════════════════════════

    // git@claude-code-plugins
    // 4 slash commands for Git operations
    // Commands: /git:commit-push, /git:compact-commits,
    //           /git:create-worktree, /git:rebase-pr
    "git@claude-code-plugins": true,

    // commit-commands@claude-code-plugins
    // Enhanced Git commit workflows with automated conventions
    // Improves commit message formatting, conventional commit support
    "commit-commands@claude-code-plugins": true

  },
  "alwaysThinkingEnabled": false
}
```

**Plugin Breakdown by Category:**

**Core Development Workflows (2 plugins):**
- superpowers@superpowers-marketplace
- claude-mem@thedotmack

**JavaScript/TypeScript/Frontend (3 plugins):**
- javascript-typescript@claude-code-workflows
- frontend-mobile-development@claude-code-workflows
- code-documentation@claude-code-workflows

**SEO & Content Creation (4 plugins):**
- seo-content-creation@claude-code-workflows
- seo-technical-optimization@claude-code-workflows
- seo-analysis-monitoring@claude-code-workflows
- elements-of-style@superpowers-marketplace

**Git & Version Control (2 plugins):**
- git@claude-code-plugins
- commit-commands@claude-code-plugins

---

# MCPs

### 🔌 Sequential Thinking

```yaml
---
name: sequential-thinking
description: Step-by-step reasoning for complex problems
used-by: All agents and workflows
documentation: https://github.com/modelcontextprotocol/servers/tree/main/src/sequential-thinking
---
```

**Key Capabilities:**
- Claude invokes this when thinking through multi-step solutions
- Structured reasoning framework
- Helps with complex debugging and planning

```bash
# Add to ~/Library/Application Support/Claude/claude_desktop_config.json:
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
```

---

## User-Created Skills

Custom skills you can add to `~/.claude/skills/` for specialized workflows:

**📰 article-extractor** — Extracts clean article content from URLs
**🚀 ship-learn-next** — Transforms learning content into actionable implementation plans
**🧵 tapestry** — Unified workflow for any learning material (auto-detects YouTube, articles, PDFs)
**🎥 youtube-transcript** — Downloads transcripts and captions from YouTube videos

```bash
# Add to ~/.claude/skills/
# Manual installation from user repository
```

---

## Configuration

### File Locations

```
Agents       ~/.claude/agents/leamas/
Settings     ~/.claude/settings.json
MCP Config   ~/Library/Application Support/Claude/claude_desktop_config.json
Skills       ~/.claude/skills/
Plugins      ~/.claude/plugins/marketplaces/
Claude-Mem   ${CLAUDE_PLUGIN_ROOT}/data/
```

---

## Quick Start (15 Minutes)

```bash
# ============================================================================
# QUICK START (15 Minutes)
# ============================================================================

# Step 1: Prerequisites (2 min)
# Verify you have the basics
node --version  # Need 18+
git --version

# Step 2: Install Essentials (8 min)

# 2a. superpowers - Core workflow skills (TDD, code review, planning)
# 2b. claude-mem - Persistent memory across sessions
# Add to ~/.claude/settings.json:
{
  "enabledPlugins": {
    "superpowers@superpowers-marketplace": true,
    "claude-mem@thedotmack": true
  }
}

# 2c. sequential-thinking - Structured reasoning for complex problems
# Add to ~/Library/Application Support/Claude/claude_desktop_config.json:
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}

# Step 3: Verify (2 min)
# Restart Claude Desktop, then verify:
cat ~/.claude/settings.json | grep enabledPlugins
cat ~/Library/Application\ Support/Claude/claude_desktop_config.json

# Step 4: Try It (3 min)
# Ask Claude: "Use brainstorming to help me design a navbar component"
# ✅ Expected: Claude invokes brainstorming skill and asks Socratic questions
```

---

