# Claude Code Setup

**Last Updated:** 2025-10-19
**Status:** Optimized for Vibe Coding

---

# Introduction

This reference documents a comprehensive Claude Code setup optimized for "vibe coding"—AI-assisted development where you describe what you want and AI handles the implementation details.

## What are Agents, Skills, Plugins, and MCPs?

### Agents

Specialized AI assistants with specific expertise (e.g., frontend-developer, code-reviewer).

- Invoked using the Task tool in Claude Code
- Handle specific jobs with focused expertise
- Installed via package managers like Leamas
- Standalone installations—not bundled in plugins

```typescript
// Invoke an agent to handle a specific task
Task({ subagent_type: "frontend-developer", prompt: "Build a responsive navbar component" })
// → Dispatches frontend-developer agent to create the component with best practices
```

### Skills

Process frameworks and workflows that guide how tasks should be done (e.g., test-driven-development, brainstorming).

- Activated automatically when relevant or via the Skill tool
- Come bundled in plugins
- Provide systematic approaches to development tasks

```typescript
// Explicitly invoke a skill to guide your process
Skill({ command: "superpowers:brainstorming" })
// → Launches Socratic refinement process before writing any code
```

### Plugins

Packages that provide collections of skills.

- Enabled in your Claude Code settings
- Provide additional capabilities like:
  - Superpowers (systematic workflows)
  - SEO-content-creation (SEO tools)
  - JavaScript/TypeScript development patterns

```json
// Enable plugins in ~/.claude/settings.json
{
  "enabledPlugins": {
    "superpowers@superpowers-marketplace": true
  }
}
// → Makes all superpowers skills available (TDD, debugging, code review, etc.)
```

### MCPs (Model Context Protocol servers)

Extend Claude's capabilities with external tools and data sources.

- Run as background services
- Provide additional functions:
  - Memory systems
  - Structured reasoning
  - External data access

```json
// Configure MCPs in ~/Library/Application Support/Claude/claude_desktop_config.json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
// → Enables structured reasoning for complex problem-solving
```

---

# Marketplaces

Claude Code has three primary plugin marketplaces that provide agents, skills, and workflows.

## Resources

- **Agent Kits:** https://leamas.sh/
- **Plugin Marketplace:** https://claudecodeplugins.io/
- **Plugin Toolkits:** https://claudemarketplaces.com/

## Superpowers Marketplace

Community-driven framework for systematic, quality-driven development workflows.

- Provides core skills system including:
  - Test-driven development (TDD)
  - Debugging workflows
  - Code review processes
  - Collaborative development patterns

**GitHub:** https://github.com/Ejb503/multiverse-of-multiagents

## Claude Code Workflows

Official Anthropic workflows for specialized development.

- Language-specific development:
  - JavaScript/TypeScript
  - Frontend/mobile
- Specialized tasks:
  - SEO optimization
  - Content creation
  - Documentation

**GitHub:** https://github.com/anthropics/claude-code-workflows

## Claude Code Plugins

Core utilities and integrations for version control.

- Git operations
- Commit workflows
- Version control helpers

**GitHub:** https://github.com/anthropics/claude-code-plugins

---

# Prerequisites

Before installing any tools, verify you have the required dependencies:

```bash
# Verify Node.js (18+)
node --version

# Verify Git
git --version

# Optional: GitHub CLI for PR workflows
gh --version
```

---

# Table of Contents

1. [Vibe Coding](#1-vibe-coding)
2. [Dev](#2-dev)
3. [Content & Marketing](#3-content--marketing)
4. [Tools & Utilities](#4-tools--utilities)

---

# 1. Vibe Coding

Orchestrate agents, develop skills, manage memory, and plan implementations.

## Agents

### agent-organizer

Helps you organize and manage multiple AI agents working together.

- Acts as your AI project manager
- Keeps track of which agents are doing what
- Coordinates efforts when running multiple specialized agents on complex tasks

**Model:** Sonnet
**Use Case:** Coordinating multiple agents for complex workflows

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### vibe-coding-coach

Your friendly coding mentor with personality.

- Provides guidance while you code
- Offers suggestions and explains concepts
- Helps you improve your skills with conversational, supportive approach
- Avoids dry technical explanations

**Model:** Sonnet
**Use Case:** Personalized coding guidance and mentorship

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### prompt-engineer

Your expert prompt architect using the most powerful model.

- Specializes in advanced prompting techniques:
  - Chain-of-Thought
  - Tree-of-Thoughts
- Always shows complete prompt text (never just describes it)
- Includes implementation notes
- Optimizes for specific models (Claude, GPT, open source)

**Model:** Opus (highest reasoning)
**Use Case:** Crafting and optimizing prompts for AI systems

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

### context-manager

Optimizes how context is used and managed across your conversations.

- Helps you make the most of available context windows
- Ensures important information is preserved
- Keeps information accessible when needed

**Model:** Sonnet
**Use Case:** Managing conversation context and memory

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

## Plugins

### superpowers@superpowers-marketplace

The core plugin that provides the entire Superpowers skills ecosystem.

- Includes:
  - Mandatory workflows
  - Agent orchestration
  - Planning tools
  - Collaborative development patterns

**Status:** ENABLED
**Provides:** 10 skills for systematic development

```bash
# Enable in ~/.claude/settings.json
# Add: "superpowers@superpowers-marketplace": true
```

#### → Skill: using-superpowers

Your mandatory starting point for any task.

- Forces you to search for and use existing skills before doing work
- Prevents reinventing the wheel
- Ensures you check if there's already a proven approach
- Process: Read → Announce → Follow

**Framework:** Mandatory skill discovery
**Triggers:** EVERY task (starting point)

#### → Skill: subagent-driven-development

Automatically dispatches fresh subagents to handle individual tasks from your plan.

- Code reviews between each task
- Enables fast iteration while maintaining quality
- Each task gets a fresh perspective and review before moving to the next

**Framework:** Task delegation with quality gates
**Triggers:** Executing implementation plans with independent tasks

#### → Skill: dispatching-parallel-agents

Launches multiple agents simultaneously to investigate different problems.

- Investigates problems that don't depend on each other
- Parallelizes problem-solving for much faster resolution
- Avoids debugging issues one at a time

**Framework:** Concurrent investigation
**Triggers:** Facing 3+ independent failures

#### → Skill: writing-skills

Applies test-driven development methodology to creating Claude skills.

- Test the skill with subagents first to see where it fails
- Write instructions that close those gaps
- Creates skills that actually work under pressure

**Framework:** TDD for process documentation
**Use Case:** Creating bulletproof Claude skills

#### → Skill: testing-skills-with-subagents

Runs your skills through actual subagent sessions to verify they work.

- Uses the RED-GREEN-REFACTOR cycle:
  1. Watch the skill fail without proper instructions
  2. Add those instructions
  3. Verify it passes
  4. Refine
- Ensures skills are bulletproof before deployment

**Framework:** RED-GREEN-REFACTOR for skills
**Use Case:** Validating skills resist rationalization

#### → Skill: sharing-skills

Guides you through contributing your skill back to the community.

- Handles branching, committing, pushing
- Creates pull request to upstream repository
- Makes it easy to share what you've created

**Framework:** Git PR workflow
**Use Case:** Contributing skills to upstream repositories

#### → Skill: commands

Provides utilities and helpers for command-line workflows.

- Streamlines common command-line operations
- Automates repetitive tasks

**Framework:** Command utilities
**Use Case:** Command-line workflow automation

#### → Skill: brainstorming

Refines rough ideas into fully-formed designs through structured questioning.

- Uses Socratic method to:
  - Explore alternatives
  - Validate assumptions
  - Incrementally refine your concept
- Prevents building the wrong thing by ensuring the design is solid first

**Framework:** Socratic method for design refinement
**Triggers:** Before writing code or implementation plans
**Slash Command:** `/superpowers:brainstorm`

#### → Skill: writing-plans

Creates detailed, step-by-step implementation plans.

- Includes:
  - Exact file paths
  - Complete code examples
  - Verification steps
  - Expected outcomes
- Designed for engineers with zero codebase context

**Framework:** Comprehensive implementation planning
**Triggers:** When design is complete
**Slash Command:** `/superpowers:write-plan`

#### → Skill: executing-plans

Loads a complete plan, reviews it critically, then executes tasks in controlled batches.

- Review checkpoints between each batch
- Ensures quality and correctness
- Pauses for review rather than blindly executing everything

**Framework:** Batch execution with review checkpoints
**Triggers:** When given a complete implementation plan
**Slash Command:** `/superpowers:execute-plan`

### claude-mem@thedotmack

Advanced memory system that remembers everything across sessions.

**Features:**
- Automatically captures what you do
- Processes content into searchable summaries
- Injects relevant context when you start new sessions
- Six specialized search tools to find past observations:
  - Search by concept
  - Search by file
  - Search by type
  - Full-text search
- Uses SQLite with FTS5 for fast searching

**Status:** ENABLED
**Provides:** Persistent memory with full-text search, 6 MCP search tools

```bash
# Follow installation guide at:
# https://github.com/thedotmack/claude-mem
# Then enable in ~/.claude/settings.json:
# "claude-mem@thedotmack": true
```

## MCPs

### sequential-thinking

Enables structured, step-by-step reasoning for complex problems.

- Helps break down challenges into manageable sequential steps
- Provides clear logical progression
- Instead of trying to solve everything at once

**Provider:** Official @modelcontextprotocol
**Use Case:** Breaking down complex problems into logical steps

```bash
# Edit ~/Library/Application Support/Claude/claude_desktop_config.json
# Add to mcpServers:
```

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
```

```bash
# Restart Claude Desktop after editing
```

---

# 2. Dev

Design, frontend, Next.js, and code review.

## Agents

### ui-designer

Creates beautiful, accessible interfaces using design principles.

**Capabilities:**
- Color theory, typography, and layout design
- Generates UI components with magic MCP
- Researches design patterns with context7
- Produces:
  - High-fidelity mockups
  - Interactive prototypes
  - Mood boards
  - Style guides
  - Complete design systems
- Ensures WCAG compliance for accessibility

**Model:** Sonnet
**MCP:** magic, context7
**Use Case:** Creating design systems and visual interfaces

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

### ux-designer

Your user advocate who focuses on making products intuitive.

**Capabilities:**
- User research and testing
- Creates user personas and journey maps
- Conducts usability testing
- Uses sequential-thinking for complex user flow analysis
- Uses playwright for browser testing
- Outputs:
  - Comprehensive research reports
  - Wireframes
  - Design specifications based on actual user needs

**Model:** Sonnet
**MCP:** context7, sequential-thinking, playwright
**Use Case:** User research, journey mapping, and usability testing

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

### frontend-developer

Your React specialist that builds complete, production-ready components.

**Capabilities:**
- TypeScript and Tailwind CSS
- Generates modern components using magic MCP
- Researches best practices with context7
- Can test with playwright
- Outputs include:
  - Component code
  - Tests
  - Accessibility checklist
  - Performance notes
  - Deployment checklist
- Follows component-driven development with performance optimization

**Model:** Sonnet
**MCP:** magic, context7, playwright
**Use Case:** Building production-ready React components

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

### ios-developer

iOS specialist covering Swift, SwiftUI, and UIKit.

- Builds native iOS applications
- Follows Apple's design guidelines
- Platform-specific patterns

**Model:** Sonnet
**Use Case:** Native iOS application development

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

### nextjs-pro

Next.js specialist covering server-side rendering, static site generation, API routes, and deployment.

- Understands Next.js-specific patterns and optimizations
- Best practices for performant applications

**Model:** Sonnet
**Use Case:** Next.js applications with SSR, SSG, and routing

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### code-reviewer

Your senior code reviewer that analyzes code for quality, security, performance, and maintainability.

**Capabilities:**
- Uses context7 to research coding standards
- Uses sequential-thinking for systematic analysis
- Provides terminal-optimized reports organized by priority:
  - Critical Issues (must fix)
  - Warnings (should fix)
  - Suggestions (nice to have)
- Educational approach with clear examples of how to fix issues

**Model:** Sonnet
**MCP:** context7, sequential-thinking
**Use Case:** Comprehensive code review before merging

```bash
# Install via claude-code-sub-agents kit
~/leamas/leamas agent@claude-code-sub-agents
```

## Plugins

### javascript-typescript@claude-code-workflows

Provides JavaScript and TypeScript development skills.

- Frontend patterns
- Backend Node.js support

**Status:** ENABLED
**Provides:** 3 skills (2 frontend, 1 backend)

```bash
# Enable in ~/.claude/settings.json
# Add: "javascript-typescript@claude-code-workflows": true
```

#### → Skill: modern-javascript-patterns

Covers modern JavaScript features and patterns.

**Features:**
- async/await
- Destructuring
- Spread operators
- Arrow functions
- Modules
- Functional programming patterns
- Helps refactor legacy code to modern standards

**Framework:** ES6+ features and patterns
**Use Case:** Implementing modern JavaScript in projects

#### → Skill: typescript-advanced-types

Masters advanced TypeScript type system.

**Features:**
- Generics
- Conditional types
- Mapped types
- Template literals
- Utility types
- Type-safe applications with sophisticated compile-time guarantees
- Type inference optimization

**Framework:** Advanced TypeScript type system
**Use Case:** Complex type logic and type safety

#### → Skill: nodejs-backend-patterns

Covers backend service patterns.

**Features:**
- Express/Fastify patterns
- Middleware
- Error handling
- Authentication
- Database integration
- Production-ready backend services

**Framework:** Express, Fastify, API design
**Use Case:** Building Node.js backend services

### frontend-mobile-development@claude-code-workflows

Provides workflow agents specialized in frontend and mobile development patterns and best practices.

**Status:** ENABLED
**Use Case:** Frontend and mobile development workflows

```bash
# Enable in ~/.claude/settings.json
# Add: "frontend-mobile-development@claude-code-workflows": true
```

### code-documentation@claude-code-workflows

Provides three agents specialized in documentation generation and code review workflows.

- Maintains quality and documentation standards

**Status:** ENABLED
**Use Case:** Code documentation and quality workflows

```bash
# Enable in ~/.claude/settings.json
# Add: "code-documentation@claude-code-workflows": true
```

---

# 3. Content & Marketing

SEO content creation, technical optimization, and writing.

## Plugins

### seo-content-creation@claude-code-workflows

Provides SEO content creation, planning, and auditing agents.

**Status:** ENABLED
**Provides:** 3 agents (writer, planner, auditor)

```bash
# Enable in ~/.claude/settings.json
# Add: "seo-content-creation@claude-code-workflows": true
```

#### → Agent: seo-content-writer

Writes content specifically optimized for search engines while maintaining quality.

**Features:**
- Integrates keywords naturally (0.5-1.5% density)
- Includes E-E-A-T signals:
  - Experience
  - Expertise
  - Authority
  - Trust
- Creates scannable content with clear structure
- Outputs complete package:
  - Article
  - Title variations
  - Meta description
  - FAQ section

**Model:** Sonnet
**Framework:** E-E-A-T signals
**Use Case:** SEO-optimized content for search rankings

#### → Agent: seo-content-planner

Plans comprehensive content strategies.

**Features:**
- Topic clusters
- Content calendars
- Detailed outlines
- Identifies content gaps
- Maps search intent
- Creates internal linking strategies
- Outputs:
  - Detailed outlines
  - 30-60 day calendars
  - Topic cluster maps showing how content pieces connect

**Model:** Haiku
**Framework:** Topic clusters
**Use Case:** Strategic content planning and calendars

#### → Agent: seo-content-auditor

Analyzes existing content for quality and optimization.

**Features:**
- E-E-A-T signals analysis
- Readability assessment
- Keyword optimization review
- Scores content on a 1-10 scale across multiple categories
- Provides specific, actionable recommendations
- Identifies:
  - Missing trust signals
  - Content depth opportunities

**Model:** Sonnet
**Framework:** E-E-A-T analysis
**Use Case:** Auditing existing content for improvement

### seo-technical-optimization@claude-code-workflows

Provides technical SEO optimization agents.

**Status:** ENABLED
**Provides:** 4 agents (keywords, meta, snippets, structure)

```bash
# Enable in ~/.claude/settings.json
# Add: "seo-technical-optimization@claude-code-workflows": true
```

#### → Agent: seo-keyword-strategist

Analyzes keyword usage and generates semantic variations.

**Features:**
- Analyzes keyword usage
- Calculates density
- Generates 20-30 LSI (Latent Semantic Indexing) keyword variations
- Maps entities and related concepts
- Detects over-optimization
- Suggests natural keyword integration strategies
- Creates comprehensive keyword packages

**Model:** Haiku
**Framework:** LSI keyword generation
**Use Case:** Keyword optimization and semantic analysis

#### → Agent: seo-meta-optimizer

Creates optimized meta titles, descriptions, and URL structures.

**Features:**
- Within character limits:
  - 50-60 for titles
  - 150-160 for descriptions
- Integrates:
  - Emotional triggers
  - CTAs
  - Power words
- Provides 3-5 variations per element for A/B testing
- Considers mobile truncation

**Model:** Haiku
**Framework:** Meta tag optimization
**Use Case:** Creating compelling metadata for clicks

#### → Agent: seo-snippet-hunter

Formats content specifically for featured snippets (position zero).

**Features:**
- Creates paragraph snippets (40-60 words)
- List formats
- Table structures optimized for snippet eligibility
- Includes schema markup:
  - FAQPage
  - HowTo
- Question-answer structures for People Also Ask boxes

**Model:** Haiku
**Framework:** Featured snippet formatting
**Use Case:** Targeting position zero in search results

#### → Agent: seo-structure-architect

Analyzes and optimizes content structure and schema markup.

**Features:**
- Optimizes header hierarchy (H1-H6)
- Implements schema markup:
  - Article
  - FAQ
  - HowTo
  - Review
  - Breadcrumbs
- Identifies internal linking opportunities
- Creates structure blueprints with:
  - Schema JSON-LD code
  - Internal linking matrices
- Ensures search-friendly content organization

**Model:** Haiku
**Framework:** Schema markup implementation
**Use Case:** Content structure and technical SEO

### seo-analysis-monitoring@claude-code-workflows

Provides SEO analysis and monitoring agents.

**Status:** ENABLED
**Provides:** 3 agents (authority, refresher, cannibalization)

```bash
# Enable in ~/.claude/settings.json
# Add: "seo-analysis-monitoring@claude-code-workflows": true
```

#### → Agent: seo-authority-builder

Analyzes content for all E-E-A-T signals.

**Features:**
- Experience:
  - First-hand examples
  - Case studies
- Expertise:
  - Credentials
  - Technical depth
- Authority:
  - Citations
  - Recognition
- Trust:
  - Contact info
  - Reviews
  - Security
- Creates enhancement plans with:
  - Author bio templates
  - Trust signal checklists
  - Topical authority maps
- Critical for Your Money Your Life (YMYL) topics

**Model:** Sonnet
**Framework:** E-E-A-T enhancement
**Use Case:** Building authority for YMYL topics

#### → Agent: seo-content-refresher

Scans content for outdated elements and prioritizes updates.

**Features:**
- Identifies outdated:
  - Statistics
  - Examples
  - Recent developments
  - Expired links
- Prioritizes updates based on:
  - Ranking decline
  - Traffic
- Creates refresh plans with:
  - Specific update checklists per page
  - Content expansion opportunities
- Maintains freshness

**Model:** Haiku
**Framework:** Freshness signals
**Use Case:** Updating outdated content

#### → Agent: seo-cannibalization-detector

Identifies when multiple pages compete for the same keywords.

**Features:**
- Detects internal conflict that hurts rankings
- Analyzes:
  - Keyword overlap
  - Topic similarity
  - Search intent across pages
- Provides resolution strategies:
  - Consolidate
  - Differentiate
  - Adjust targeting

**Model:** Haiku
**Framework:** Keyword conflict analysis
**Use Case:** Preventing internal keyword competition

### elements-of-style@superpowers-marketplace

Single-purpose plugin from the Superpowers marketplace.

- Provides the writing-clearly-and-concisely skill
- Brings Strunk & White's timeless writing principles to all your prose

**Status:** ENABLED
**Provides:** 1 skill

```bash
# Enable in ~/.claude/settings.json
# Add: "elements-of-style@superpowers-marketplace": true
```

#### → Skill: writing-clearly-and-concisely

Applies classic writing principles from Strunk & White to any text.

**Applies to:**
- Documentation
- Commit messages
- Error messages
- Reports
- UI text

**Benefits:**
- Makes writing clearer, stronger, and more professional
- Removes fluff
- Improves structure

**Framework:** Strunk's writing rules
**Use Case:** All prose humans will read

---

# 4. Tools & Utilities

Data analysis, databases, Git workflows, and learning extraction.

## Agents

### data-scientist

Handles data analysis, statistical modeling, and machine learning implementations.

**Model:** Sonnet
**Use Case:** Data analysis and machine learning

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### quant-analyst

Provides quantitative analysis and financial modeling expertise.

**Model:** Sonnet
**Use Case:** Quantitative and financial analysis

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### python-pro

Python specialist for data analysis, scripting, automation, and Python-specific best practices.

**Model:** Sonnet
**Use Case:** Python development and data analysis

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### database-admin

Manages database administration, setup, and ongoing maintenance.

**Model:** Sonnet
**Use Case:** Database setup, configuration, and management

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### database-optimizer

Optimizes database queries and overall database performance.

**Model:** Sonnet
**Use Case:** Query optimization and database performance

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

### payment-integration

Specializes in integrating payment systems.

- Stripe, PayPal, and other payment processors
- Handles payment workflows and security considerations

**Model:** Sonnet
**Use Case:** Implementing payment systems

```bash
# Install via wshobson kit
~/leamas/leamas agent@wshobson
```

## Plugins

### git@claude-code-plugins

Provides helpers and workflow improvements for Git operations.

**Status:** ENABLED
**Use Case:** Git version control workflows

```bash
# Enable in ~/.claude/settings.json
# Add: "git@claude-code-plugins": true
```

### commit-commands@claude-code-plugins

Enhances commit workflows with helpers and improved commit message handling.

**Status:** ENABLED
**Use Case:** Better commit processes

```bash
# Enable in ~/.claude/settings.json
# Add: "commit-commands@claude-code-plugins": true
```

## Skills (User-Created)

### article-extractor

Extracts clean article content from URLs.

**Features:**
- Removes ads, navigation, sidebars, and other clutter
- Returns just the readable text from:
  - Blog posts
  - Articles
  - Tutorials

**Framework:** Clean content extraction
**Triggers:** User provides article URL

```bash
# User-created skill, already in ~/.claude/skills/
# No installation needed
```

### ship-learn-next

Transforms learning content into actionable implementation plans.

**Features:**
- Converts advice and lessons into concrete action steps
- Practice reps
- Learning quests
- Works with:
  - Videos
  - Articles
  - Tutorials

**Framework:** Ship-Learn-Next methodology
**Use Case:** Turning learning into action

```bash
# User-created skill, already in ~/.claude/skills/
# No installation needed
```

### tapestry

Automatically detects content type, extracts content, and creates action plan.

**Features:**
- All in one step
- Unified workflow for extracting and planning from any learning material
- Detects:
  - YouTube videos
  - Articles
  - PDFs

**Framework:** Unified extraction + planning
**Triggers:**
- `tapestry <URL>`
- `weave <URL>`
- `make this actionable <URL>`

```bash
# User-created skill, already in ~/.claude/skills/
# No installation needed
```

### youtube-transcript

Downloads transcripts and captions from YouTube videos.

**Features:**
- For analysis
- Summarization
- Content extraction

**Framework:** YouTube transcript download
**Triggers:** User provides YouTube URL

```bash
# User-created skill, already in ~/.claude/skills/
# No installation needed
```

---

# Quick Reference

## File Locations

```
Agents: ~/.claude/agents/leamas/
Settings: ~/.claude/settings.json
MCP Config: ~/Library/Application Support/Claude/claude_desktop_config.json
User Skills: ~/.claude/skills/
Plugins: ~/.claude/plugins/marketplaces/
Claude-Mem Data: ${CLAUDE_PLUGIN_ROOT}/data/
```

## Complete settings.json

```json
{
  "enabledPlugins": {
    "commit-commands@claude-code-plugins": true,
    "elements-of-style@superpowers-marketplace": true,
    "superpowers@superpowers-marketplace": true,
    "javascript-typescript@claude-code-workflows": true,
    "code-documentation@claude-code-workflows": true,
    "frontend-mobile-development@claude-code-workflows": true,
    "seo-content-creation@claude-code-workflows": true,
    "seo-technical-optimization@claude-code-workflows": true,
    "seo-analysis-monitoring@claude-code-workflows": true,
    "claude-mem@thedotmack": true,
    "git@claude-code-plugins": true
  },
  "alwaysThinkingEnabled": false
}
```

---

## Summary

**Total Tools: 62** (down from 80)

- **Agents:** 19 (standalone, installed via Leamas)
- **Plugins:** 11 (provide skills and some agents)
- **Skills:** 21
  - 10 from superpowers
  - 3 from javascript-typescript
  - 1 from elements-of-style
  - 3 from SEO plugins
  - 4 user-created
- **MCPs:** 1
- **SEO Plugin Agents:** 10 (nested within SEO plugins)

**Removed:** 18 tools
- react-pro
- mobile-developer
- javascript-pro
- debugger
- security-auditor
- 4 business agents
- 4 duplicate data agents
- content-writer

---

**End of Reference Document**
