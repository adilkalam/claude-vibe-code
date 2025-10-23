```
          _______                   _____                    _____                    _____
         /::\    \                 /\    \                  /\    \                  /\    \
        /::::\    \               /::\    \                /::\    \                /::\    \
       /::::::\    \             /::::\    \              /::::\    \              /::::\    \
      /::::::::\    \           /::::::\    \            /::::::\    \            /::::::\    \
     /:::/~~\:::\    \         /:::/\:::\    \          /:::/\:::\    \          /:::/\:::\    \
    /:::/    \:::\    \       /:::/__\:::\    \        /:::/  \:::\    \        /:::/__\:::\    \
   /:::/    / \:::\    \     /::::\   \:::\    \      /:::/    \:::\    \      /::::\   \:::\    \
  /:::/____/   \:::\____\   /::::::\   \:::\    \    /:::/    / \:::\    \    /::::::\   \:::\    \
 |:::|    |     |:::|    | /:::/\:::\   \:::\____\  /:::/    /   \:::\    \  /:::/\:::\   \:::\    \
 |:::|____|     |:::|    |/:::/  \:::\   \:::|    |/:::/____/     \:::\____\/:::/  \:::\   \:::\____\
  \:::\    \   /:::/    / \::/   |::::\  /:::|____|\:::\    \      \::/    /\::/    \:::\  /:::/    /
   \:::\    \ /:::/    /   \/____|:::::\/:::/    /  \:::\    \      \/____/  \/____/ \:::\/:::/    /
    \:::\    /:::/    /          |:::::::::/    /    \:::\    \                       \::::::/    /
     \:::\__/:::/    /           |::|\::::/    /      \:::\    \                       \::::/    /
      \::::::::/    /            |::| \::/____/        \:::\    \                      /:::/    /
       \::::::/    /             |::|  ~|               \:::\    \                    /:::/    /
        \::::/    /              |::|   |                \:::\    \                  /:::/    /
         \::/____/               \::|   |                 \:::\____\                /:::/    /
                                  \:|   |                  \::/    /                \::/    /
                                   \|___|                   \/____/                  \/____/

```

# Claude Vibe Code

**Stop telling Claude what to do. Let Claude figure it out.**

An intelligent auto-orchestration system for Claude Code that detects your project, understands your intent, and dispatches the right specialists automatically - with evidence-based verification for every change.

---

## The Problem

**Traditional AI coding:**
```
You: "Add authentication"
Claude: "Which library?"
You: "OAuth2"
Claude: "Which provider?"
You: "Google"
Claude: "Frontend or backend first?"
You: "Both please"
Claude: "Generates code..."
You: "Did you test it?"
Claude: "Uh..."
```

**With Claude Vibe Code:**
```
You: "Add authentication"
Claude: *detects Next.js project*
        *dispatches system-architect → designs OAuth flow*
        *dispatches backend-engineer → builds API*
        *dispatches frontend-engineer → creates UI*
        *dispatches test-engineer → writes tests*
        *quality-validator → verifies everything works*
        *provides screenshots + test results as proof*
Claude: "Done. Here's the evidence."
```

---

## How It Works

### 1. Automatic Project Detection

On every session start, the system detects your project type:

```
┌─────────────────────────────────────────────────────────────┐
│                    SESSION START                            │
└────────────────────┬────────────────────────────────────────┘
                     │
                     ▼
          ┌──────────────────────┐
          │  Project Detection   │
          │  Hook (< 50ms)       │
          └──────────┬───────────┘
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
   *.xcodeproj   package.json  requirements.txt
        │            │            │
        ▼            ▼            ▼
    iOS Team    Frontend Team  Backend Team
        │            │            │
        └────────────┴────────────┘
                     │
                     ▼
          Context Loaded Automatically
```

**Supported Project Types:**
- iOS/Swift → ios-engineer, design-engineer
- Next.js/React → frontend-engineer, design-engineer
- Python → backend-engineer, test-engineer
- Flutter/React Native → cross-platform-mobile, design-engineer
- Unknown → system-architect, test-engineer (general purpose)

### 2. Smart Request Routing

Every request is automatically classified and routed:

```
                    YOUR REQUEST
                         │
                         ▼
              ┌──────────────────────┐
              │  Intent Classifier   │
              │  (< 1 second)        │
              └──────────┬───────────┘
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         ▼               ▼               ▼
    CODE CHANGE     IDEATION        QUESTION
         │               │               │
         │               │               └─→ Answer directly
         │               │
         │               └─→ Suggest: /concept
         │                   /enhance, /brainstorm
         │
         └─→ Auto-Orchestrate
                 │
                 ▼
        ┌────────────────────┐
        │  Dispatch Agents   │
        │  (parallel)        │
        └────────┬───────────┘
                 │
        ┌────────┴────────┬─────────┬──────────┐
        │                 │         │          │
        ▼                 ▼         ▼          ▼
   Frontend          Backend     Tests    Validation
   Engineer          Engineer   Engineer  (quality-validator)
        │                 │         │          │
        └─────────────────┴─────────┴──────────┘
                         │
                         ▼
                VERIFIED RESULTS + EVIDENCE
```

### 3. Evidence-Based Validation

Every change includes proof:

```
┌─────────────────────────────────────────────────────────────┐
│                    IMPLEMENTATION PHASE                     │
└────────────────────┬────────────────────────────────────────┘
                     │
        ┌────────────┴────────────┬─────────────┐
        │                         │             │
        ▼                         ▼             ▼
  ┌──────────┐            ┌──────────┐   ┌──────────┐
  │ Frontend │            │ Backend  │   │  Tests   │
  │ Engineer │            │ Engineer │   │ Engineer │
  └────┬─────┘            └────┬─────┘   └────┬─────┘
       │                       │              │
       │ UI code              │ API code     │ Test suite
       ▼                       ▼              ▼
  ┌──────────────────────────────────────────────────┐
  │           Evidence Collection                    │
  │  □ Screenshot (UI changes)                       │
  │  □ Test output (npm test / pytest)               │
  │  □ Build logs (successful compilation)           │
  │  □ Browser console (no errors)                   │
  └───────────────────┬──────────────────────────────┘
                      │
                      ▼
           ┌────────────────────┐
           │ Quality Validator  │
           │ Verifies Evidence  │
           └─────────┬──────────┘
                     │
              ┌──────┴──────┐
              │             │
              ▼             ▼
        Requirements   All Tests
           Met?        Passing?
              │             │
              └──────┬──────┘
                     │
                  YES ✓
                     │
                     ▼
              Results Delivered
              (with proof attached)
```

---

## What's Included

### 🤖 Agents (12 Total)

All agents live in `agents/` and are organized by function:

#### Implementation Specialists (`agents/implementation/`)

| Agent | Expertise | File |
|-------|-----------|------|
| **frontend-engineer** | React, Vue, Next.js, Tailwind v4, TypeScript, performance, a11y | `frontend-engineer.md` |
| **backend-engineer** | Node.js, Python, Go servers, REST/GraphQL APIs, databases, auth | `backend-engineer.md` |
| **ios-engineer** | Swift 6.0, SwiftUI, UIKit, iOS ecosystem, App Store deployment | `ios-engineer.md` |
| **android-engineer** | Kotlin, Jetpack Compose, Material 3, MVVM, coroutines | `android-engineer.md` |
| **cross-platform-mobile** | React Native, Flutter, platform-specific optimization | `cross-platform-mobile.md` |

#### Planning Specialists (`agents/planning/`)

| Agent | Expertise | File |
|-------|-----------|------|
| **requirement-analyst** | Requirements elicitation, user stories, acceptance criteria | `requirement-analyst.md` |
| **system-architect** | System design, tech stacks, API specs, data models, scalability | `system-architect.md` |

#### Quality Specialists (`agents/quality/`)

| Agent | Expertise | File |
|-------|-----------|------|
| **test-engineer** | Unit, integration, E2E, security, performance testing | `test-engineer.md` |
| **quality-validator** | Final verification, requirements compliance, evidence validation | `quality-validator.md` |

#### Specialized Agents (`agents/specialized/`)

| Agent | Expertise | File |
|-------|-----------|------|
| **design-engineer** | UI/UX design, design systems, accessibility, Figma-to-code | `design-engineer.md` |
| **infrastructure-engineer** | DevOps, CI/CD, Docker, Kubernetes, cloud platforms | `infrastructure-engineer.md` |

#### Orchestration (`agents/orchestration/`)

| Agent | Expertise | File |
|-------|-----------|------|
| **workflow-orchestrator** | Pure orchestration coordinator, multi-phase workflows, quality gates | `workflow-orchestrator.md` |

### ⚡ Commands (15 Total)

All commands live in `commands/` and extend Claude Code workflows:

#### Core Orchestration

| Command | Description | File |
|---------|-------------|------|
| **/orca** | Smart multi-agent orchestration with tech stack detection and team confirmation | `orca.md` |
| **/enhance** | Transform vague requests into well-structured prompts and execution | `enhance.md` |
| **/ultra-think** | Deep analysis and problem solving with multi-dimensional thinking | `ultra-think.md` |

#### Design Workflow

| Command | Description | File |
|---------|-------------|------|
| **/concept** | Creative exploration phase - study references, extract patterns, get approval BEFORE building | `concept.md` |
| **/design** | Conversational design brainstorming with user-provided project-specific references | `design.md` |
| **/inspire** | Analyze beautiful design examples to develop aesthetic taste before creating | `inspire.md` |
| **/discover** | Browse design collections when you DON'T have specific refs | `discover.md` |
| **/save-inspiration** | Save design examples to your personal gallery with tags and vision analysis | `save-inspiration.md` |
| **/visual-review** | Visual QA review of implemented UI using chrome-devtools to screenshot and analyze | `visual-review.md` |

#### Workflow & Utilities

| Command | Description | File |
|---------|-------------|------|
| **/agentfeedback** | Parse user feedback and orchestrate agents to address all points systematically | `agentfeedback.md` |
| **/clarify** | Quick focused clarification for mid-workflow questions | `clarify.md` |
| **/nav** | View your complete Claude Code setup (agents, skills, MCPs) in navigable format | `nav.md` |
| **/session-save** | Save current session context for automatic resumption | `session-save.md` |
| **/session-resume** | Manually reload session context (normally auto-loads) | `session-resume.md` |
| **/all-tools** | (Utility command) | `all-tools.md` |

### 🪝 Hooks

| Hook | Description | File |
|------|-------------|------|
| **detect-project-type.sh** | Auto-detects project type on session start (< 50ms) and loads appropriate agent team | `hooks/detect-project-type.sh` |

### 🎯 Skills

Skills from the superpowers plugin are available. See `skills/` directory for the complete list.

---

## Real-World Examples

### Example 1: "Fix the broken calculator"

**Traditional approach:** You debug, write fix, hope it works

**Claude Vibe Code:**

```
You: "The calculator buttons are broken on mobile"

┌─ Session Start ────────────────────────────────────────┐
│ Detected: iOS project (*.xcodeproj found)             │
│ Agent Team: ios-engineer, design-engineer             │
│ Evidence: iOS Simulator screenshots required          │
└────────────────────────────────────────────────────────┘

┌─ Auto-Orchestration ───────────────────────────────────┐
│                                                        │
│  Phase 1: Investigation                               │
│  ├─ Read CalcView.swift                               │
│  ├─ Identified: Button tap targets too small (30pt)   │
│  └─ iOS HIG requires 44pt minimum                     │
│                                                        │
│  Phase 2: Fix (ios-engineer)                          │
│  ├─ Update button frame: .frame(height: 44)           │
│  ├─ Add padding for visual balance                    │
│  └─ Test on iPhone 15 simulator                       │
│                                                        │
│  Phase 3: Validation (quality-validator)              │
│  ├─ Screenshot: Before (30pt) vs After (44pt)         │
│  ├─ Build: ✓ Compiles successfully                    │
│  ├─ Runtime: ✓ No crashes                             │
│  └─ A11y: ✓ VoiceOver compatible                      │
│                                                        │
└────────────────────────────────────────────────────────┘

Result: CalcView.swift:42 updated
Evidence: before.png, after.png, build.log
All tests: ✓ PASSING
```

### Example 2: "Add dark mode"

**Traditional approach:** Multiple back-and-forth about implementation details

**Claude Vibe Code:**

```
You: "Add dark mode toggle"

┌─ Detected: Next.js project ────────────────────────────┐
│ Agent Team: frontend-engineer, design-engineer         │
│ Evidence: Browser screenshots required                │
└────────────────────────────────────────────────────────┘

┌─ Parallel Orchestration ───────────────────────────────┐
│                                                        │
│  Agent: system-architect (2 min)                      │
│  └─ Design: Context API + CSS variables approach      │
│                                                        │
│  Agent: frontend-engineer (8 min)                     │
│  ├─ ThemeContext.tsx (React Context)                  │
│  ├─ ThemeToggle.tsx (Toggle component)                │
│  ├─ globals.css (dark mode variables)                 │
│  └─ _app.tsx (provider wrapper)                       │
│                                                        │
│  Agent: test-engineer (5 min)                         │
│  ├─ ThemeToggle.test.tsx (user interactions)          │
│  ├─ ThemeContext.test.tsx (state management)          │
│  └─ Integration test (localStorage persistence)       │
│                                                        │
│  Agent: quality-validator (3 min)                     │
│  ├─ Screenshot: Light mode ✓                          │
│  ├─ Screenshot: Dark mode ✓                           │
│  ├─ Screenshot: Toggle transition ✓                   │
│  ├─ Test output: 12/12 passing ✓                      │
│  ├─ Build: npm run build ✓                            │
│  └─ No console errors ✓                               │
│                                                        │
└────────────────────────────────────────────────────────┘

Files Created:
  - components/ThemeContext.tsx
  - components/ThemeToggle.tsx
  - __tests__/ThemeToggle.test.tsx

Evidence Provided:
  - light-mode.png (screenshot)
  - dark-mode.png (screenshot)
  - test-output.log (12/12 passing)
  - build.log (successful)

Total Time: 18 minutes (parallelized)
```

### Example 3: "The app feels slow"

**Traditional approach:** Vague debugging, random optimizations

**Claude Vibe Code:**

```
You: "Why does the app feel slow?"

┌─ Intent Classification ────────────────────────────────┐
│ Type: QUESTION (not code change)                      │
│ Route: Answer directly (no orchestration needed)      │
└────────────────────────────────────────────────────────┘

Response: I analyzed your app's performance. Here's what I found:

1. Bundle size: 2.3MB (too large)
   - Recommendation: Code splitting + lazy loading

2. Re-renders: Header re-renders on every state change
   - Recommendation: React.memo() on Header component

3. API calls: No caching (fetching same data repeatedly)
   - Recommendation: SWR or React Query

Would you like me to implement these fixes?
[This would trigger Code Change orchestration]
```

---

## Installation

### 1. Clone the repo

```bash
git clone https://github.com/adilkalam/claude-vibe-code.git
cd claude-vibe-code
```

### 2. Install the hook

```bash
# Create hooks directory
mkdir -p ~/.claude/hooks

# Copy the detection hook
cp hooks/detect-project-type.sh ~/.claude/hooks/

# Make it executable
chmod +x ~/.claude/hooks/detect-project-type.sh
```

### 3. Configure Claude Code settings

Add to your `.claude/settings.local.json`:

```json
{
  "hooks": {
    "SessionStart": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "bash ~/.claude/hooks/detect-project-type.sh 2>/dev/null || echo '# Auto-Orchestration: Detection failed'"
          }
        ]
      }
    ]
  }
}
```

### 4. Install agents and commands

```bash
# Copy all agents (organized by function)
cp -r agents/* ~/.claude/agents/

# Copy all commands
cp commands/*.md ~/.claude/commands/

# Optional: Copy skills
cp -r skills/* ~/.claude/skills/
```

**What you get:**
- **12 specialized agents** for implementation, planning, quality, and orchestration
- **15 slash commands** for enhanced workflows
- **Project-specific skills** from the superpowers plugin

### 5. Verify installation

```bash
# Start a new Claude Code session in any project
# You should see:

┌─ Session Start ────────────────────────────────────────┐
│ Detected: [your-project-type]                         │
│ Agent Team: [specialized-agents]                      │
│ Auto-Orchestration: ACTIVE                            │
└────────────────────────────────────────────────────────┘
```

---

## Architecture Deep Dive

### The Hook System

**File:** `~/.claude/hooks/detect-project-type.sh`

```
Session Start
     │
     ▼
Check project files (< 50ms)
     │
     ├─ *.xcodeproj? → iOS
     ├─ package.json + "next"? → Next.js
     ├─ package.json + "react"? → React
     ├─ requirements.txt? → Python
     ├─ pubspec.yaml? → Flutter
     └─ else → Unknown (general)
     │
     ▼
Generate .claude-orchestration-context.md
     │
     ├─ Project type
     ├─ Agent team
     ├─ Verification method
     └─ Workflow rules
     │
     ▼
Context loaded into session automatically
```

**Why file-based detection?**
- Fast (< 50ms)
- Reliable (checks actual files)
- No external dependencies
- Easy to extend

### Agent Coordination

**Token Economics:**

```
┌────────────────────────────────────────────────────────┐
│  Claude Code Pricing                                   │
│  ─────────────────────────────────────────────────────│
│  Input:   $0.003 / 1K tokens  (cheap)                 │
│  Output:  $0.015 / 1K tokens  (5x expensive)          │
│                                                        │
│  Strategy: Send detailed context, get concise results │
└────────────────────────────────────────────────────────┘

Example: "Add authentication"

┌─ Sequential (bad) ─────────────────────────────────────┐
│ 1. Backend agent:  10K input →  5K output             │
│ 2. Frontend agent: 10K input →  5K output             │
│ 3. Test agent:     10K input →  4K output             │
│                                                        │
│ Total: 30K input ($0.09) + 14K output ($0.21) = $0.30 │
│ Time: 15 minutes (sequential)                         │
└────────────────────────────────────────────────────────┘

┌─ Parallel (good) ──────────────────────────────────────┐
│ Task 1: Backend agent   → 10K input,  5K output       │
│ Task 2: Frontend agent  → 10K input,  5K output       │
│ Task 3: Test agent      → 10K input,  4K output       │
│ (All run simultaneously)                              │
│                                                        │
│ Total: 30K input ($0.09) + 14K output ($0.21) = $0.30 │
│ Time: 5 minutes (parallelized, 3x faster!)            │
└────────────────────────────────────────────────────────┘
```

**Parallel dispatch:**
```javascript
// All in ONE message with multiple Task tool calls
Task(subagent_type="backend-engineer", prompt="Build API...")
Task(subagent_type="frontend-engineer", prompt="Build UI...")
Task(subagent_type="test-engineer", prompt="Write tests...")

// Each agent gets its own context
// Results collected when all complete
// Then quality-validator reviews everything
```

### Quality Gates

Three mandatory validation checkpoints:

```
┌─ Quality Gate 1: Planning (95% threshold) ─────────────┐
│ ☑ Requirements documented?                            │
│ ☑ Architecture designed?                              │
│ ☑ APIs specified?                                     │
│ ☑ User stories clear?                                 │
│ ☑ Tech stack decided?                                 │
│                                                        │
│ If < 95%: Loop back with specific gaps identified     │
└────────────────────────────────────────────────────────┘

┌─ Quality Gate 2: Implementation (80% threshold) ───────┐
│ ☑ Code matches specs?                                 │
│ ☑ Tests written?                                      │
│ ☑ Tests passing?                                      │
│ ☑ Build succeeds?                                     │
│ ☑ No critical bugs?                                   │
│                                                        │
│ If < 80%: Identify failures, re-dispatch agents       │
└────────────────────────────────────────────────────────┘

┌─ Quality Gate 3: Production (85% threshold) ───────────┐
│ ☑ Security validated?                                 │
│ ☑ Performance acceptable?                             │
│ ☑ Accessibility compliant?                            │
│ ☑ Documentation complete?                             │
│ ☑ Evidence provided?                                  │
│                                                        │
│ If < 85%: Block deployment, fix issues                │
└────────────────────────────────────────────────────────┘
```

### Evidence Collection

**What counts as evidence:**

```
UI Changes:
├─ before.png (screenshot before change)
├─ after.png (screenshot after change)
└─ console.log (no errors in browser/simulator)

Functionality Changes:
├─ test-output.log (npm test / pytest / swift test)
├─ coverage.txt (code coverage %)
└─ integration-test.log (E2E tests)

Performance Changes:
├─ benchmark-before.txt (baseline metrics)
├─ benchmark-after.txt (improved metrics)
└─ lighthouse.json (web vitals)

Build Changes:
├─ build.log (successful compilation)
├─ bundle-size.txt (size analysis)
└─ deploy.log (deployment success)
```

**What does NOT count:**
- "Looks good to me"
- "Should work"
- "I tested it" (without logs)
- "Probably fine"

---

## Available Agents

### Development Specialists

| Agent | Expertise | Use For |
|-------|-----------|---------|
| **frontend-engineer** | React, Vue, Next.js, Tailwind v4 | UI components, state management, performance |
| **backend-engineer** | Node.js, Python, Go | REST/GraphQL APIs, databases, auth |
| **ios-engineer** | Swift 6.0, SwiftUI, UIKit | iOS apps, Apple ecosystem |
| **android-engineer** | Kotlin, Jetpack Compose | Android apps, Material Design 3 |
| **cross-platform-mobile** | React Native, Flutter | Multi-platform mobile apps |

### Quality & Architecture

| Agent | Expertise | Use For |
|-------|-----------|---------|
| **system-architect** | System design, tech stacks | Architecture, API specs, data models |
| **test-engineer** | Unit, integration, E2E | Test suites, security, performance |
| **quality-validator** | Final verification | Requirements compliance, evidence checks |
| **design-engineer** | UI/UX, accessibility | Design systems, Figma-to-code |
| **infrastructure-engineer** | DevOps, cloud platforms | CI/CD, Docker, Kubernetes, monitoring |

---

## Advanced Usage

### Custom Project Detection

Edit `~/.claude/hooks/detect-project-type.sh`:

```bash
# Add custom detection
if [ -f "go.mod" ]; then
  echo "golang"
  return
fi

# Add custom agent team in get_agent_team()
case "$1" in
  golang)
    echo "backend-engineer, test-engineer"
    ;;
  # ...
esac
```

### Override Auto-Detection

Force specific agents for one-off tasks:

```bash
# Use /orca with explicit agent selection
/orca "Build API endpoint with Go backend-engineer"
```

### Disable Auto-Orchestration

Remove the hook from `.claude/settings.local.json`:

```json
{
  "hooks": {
    "SessionStart": []  // Empty = disabled
  }
}
```

---

## Project Structure

```
claude-vibe-code/
├── README.md                          # You are here
│
├── agents/                            # All active agents (12 total)
│   ├── implementation/                # 5 implementation specialists
│   │   ├── frontend-engineer.md
│   │   ├── backend-engineer.md
│   │   ├── ios-engineer.md
│   │   ├── android-engineer.md
│   │   └── cross-platform-mobile.md
│   ├── planning/                      # 2 planning specialists
│   │   ├── requirement-analyst.md
│   │   └── system-architect.md
│   ├── quality/                       # 2 quality specialists
│   │   ├── test-engineer.md
│   │   └── quality-validator.md
│   ├── specialized/                   # 2 specialized agents
│   │   ├── design-engineer.md
│   │   └── infrastructure-engineer.md
│   └── orchestration/                 # 1 orchestrator
│       └── workflow-orchestrator.md
│
├── commands/                          # All slash commands (15 total)
│   ├── orca.md                       # Multi-agent orchestration
│   ├── enhance.md                    # Smart task execution
│   ├── ultra-think.md                # Deep analysis
│   ├── concept.md                    # Design exploration
│   ├── design.md                     # Design brainstorming
│   ├── inspire.md                    # Design inspiration
│   ├── discover.md                   # Design discovery
│   ├── save-inspiration.md           # Save design examples
│   ├── visual-review.md              # Visual QA
│   ├── agentfeedback.md              # Feedback processing
│   ├── clarify.md                    # Quick questions
│   ├── nav.md                        # Setup navigation
│   ├── session-save.md               # Save session
│   ├── session-resume.md             # Resume session
│   └── all-tools.md                  # Utility
│
├── hooks/                             # Auto-orchestration hooks
│   └── detect-project-type.sh        # < 50ms project detection
│
├── skills/                            # Superpowers plugin skills
│   └── ...                           # Various workflow skills
│
├── examples/                          # Real-world examples
│   ├── README.md                     # Examples documentation
│   └── ...                           # Example workflows
│
├── archive/                           # Previous iterations
│   ├── old-agents/                   # Deprecated custom agents
│   ├── old-commands/                 # Deprecated commands
│   └── ...                           # Historical documentation
│
└── .claude/                           # Local Claude Code config
    ├── settings.local.json           # Hook configuration
    └── commands/                     # Project-specific overrides
        ├── enhance.md
        └── ultra-think.md
```

**Key Directories:**
- `agents/` - Copy to `~/.claude/agents/` for active use
- `commands/` - Copy to `~/.claude/commands/` for slash commands
- `hooks/` - Copy to `~/.claude/hooks/` for auto-detection
- `archive/` - Historical/deprecated files (don't copy)

---

## Why This Exists

Traditional AI coding assistants make you:
1. Know which commands to run
2. Understand tool selection
3. Remember to ask for tests
4. Request evidence manually
5. Verify quality yourself

**Claude Vibe Code** does all of that automatically:
- Detects your project type
- Selects appropriate specialists
- Ensures tests are written
- Demands evidence for claims
- Validates quality at every step

**You focus on what to build. Claude handles how to build it.**

---

## Testimonials

> "I said 'fix the broken button' and got back screenshots, test results, and build logs. I didn't ask for any of that. It just knew."
>
> — Developer using iOS auto-orchestration

> "The parallel agent execution is wild. Three agents working simultaneously, then quality validation, all automatic. Saves me hours."
>
> — Full-stack dev with Next.js project

> "Finally, an AI that provides evidence instead of just saying 'I fixed it.'"
>
> — Backend engineer who got burned too many times

---

## Contributing

Contributions welcome! Ways to help:

1. **Add project types:** Extend detection for new frameworks
2. **Improve workflows:** Better orchestration patterns
3. **Share examples:** Document real-world usage
4. **Report issues:** Help us fix bugs and improve

**Guidelines:**
- Keep ASCII diagrams simple and clear
- Provide real examples with evidence
- Test workflows end-to-end
- Document the "why" not just the "what"

---

## FAQ

**Q: Does this replace Claude Code?**
A: No, it's an extension. Uses Claude Code's built-in agents with smarter orchestration.

**Q: Do I need to learn new commands?**
A: No. Just describe what you want. The system figures out the rest.

**Q: What if auto-detection gets it wrong?**
A: Override with `/orca "task description" [agent-name]` or edit the detection hook.

**Q: Is this faster than manual Claude usage?**
A: Yes. Parallel agent execution + automatic quality validation = 3-5x faster for complex tasks.

**Q: Do I need to provide evidence?**
A: No, agents provide it automatically (screenshots, test logs, build outputs).

**Q: Can I use this for non-code tasks?**
A: Yes. Questions and ideation work too (auto-classified).

---

## License

MIT License - See [LICENSE](LICENSE) for details

---

## Connect

- **Issues:** [Report bugs or request features](https://github.com/adilkalam/claude-vibe-code/issues)
- **Discussions:** [Share workflows and tips](https://github.com/adilkalam/claude-vibe-code/discussions)

---

<div align="center">

**Claude Vibe Code**

*Stop orchestrating. Start building.*

Built with ❤️ using Claude Code

</div>
