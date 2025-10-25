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

# Vibe Code | Claude Code

> **🚧 /ORCA** 
> 
An intelligent auto-orchestration system for Claude Code that will detect your project, understand your intent, and dispatch the right specialists automatically - with **Response Awareness verification** to prevent false completions.

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

**With Orca:**
```
You: "Add authentication"
Claude: *detects Next.js project*
        *dispatches system-architect → designs OAuth flow*
        *dispatches backend-engineer → builds API*
        *dispatches nextjs-14-specialist → implements Next.js auth*
        *dispatches design-system-architect → creates auth UI components*
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
┌──────────────────────────────────────────────────────────┐
│                      SESSION START                       │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              ┌────────────────────────────────────────┐
              │        Project Detection Hook          │
              │            (< 50ms)                    │
              └──────────────────┬─────────────────────┘
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                      │
          ▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│   *.xcodeproj    │   │   package.json   │   │ requirements.txt │
└────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│ iOS Team (8-16)  │   │ Frontend (10-15) │   │ Backend Team (6) │
└────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
         │                      │                      │
         └──────────────────────┴──────────────────────┘
                                │
                                ▼
              ┌────────────────────────────────────────┐
              │    Context Loaded Automatically        │
              └────────────────────────────────────────┘
```

**Supported Project Types:**
- iOS/Swift → 8-16 agents (requirement-analyst, system-architect, 2-10 iOS specialists, 1-2 design specialists, test-engineer, verification-agent, quality-validator)
- Next.js/React → 10-15 agents (requirement-analyst, system-architect, 3-5 design specialists, 2-4 frontend specialists, test-engineer, verification-agent, quality-validator)
- Python/Backend → 6 base agents (or 10 with admin UI including design specialists)
- Flutter/React Native → 10-13 agents (requirement-analyst, system-architect, 3-5 design specialists, cross-platform-mobile, test-engineer, verification-agent, quality-validator)
- Unknown → General purpose team (system-architect, test-engineer, verification-agent, quality-validator)

### 2. Smart Request Routing

Every request is automatically classified and routed:

```
┌──────────────────────────────────────────────────────────┐
│                      YOUR REQUEST                        │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              ┌────────────────────────────────────────┐
              │          Intent Classifier             │
              │            (< 1 second)                │
              └──────────────────┬─────────────────────┘
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                      │
          ▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│   CODE CHANGE    │   │    IDEATION      │   │     QUESTION     │
└────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
         │                      │                      │
         │                      │                      │
         │                      └────────────────┐     │
         │                                       │     │
         │                                       ▼     ▼
         │                      ┌──────────────────────────────────────┐
         │                      │  Suggest: /concept, /enhance         │
         │                      │  Answer directly                     │
         │                      └──────────────────────────────────────┘
         │
         └──────────────────────────────┐
                                        │
                                        ▼
                        ┌────────────────────────────────────────┐
                        │        Auto-Orchestrate                │
                        └──────────────────┬─────────────────────┘
                                           │
                                           ▼
                        ┌────────────────────────────────────────┐
                        │         Dispatch Agents                │
                        │          (parallel)                    │
                        └──────────────────┬─────────────────────┘
                                           │
                    ┌──────────────────────┼──────────────────────┐
                    │                      │                      │
                    ▼                      ▼                      ▼
          ┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
          │     Frontend     │   │     Backend      │   │      Tests       │
          │     Engineer     │   │     Engineer     │   │     Engineer     │
          └────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
                   │                      │                      │
                   └──────────────────────┴──────────────────────┘
                                          │
                                          ▼
                        ┌────────────────────────────────────────┐
                        │  VERIFIED RESULTS + EVIDENCE           │
                        └────────────────────────────────────────┘
```

### 3. Response Awareness: How Quality Gates Actually Work

Traditional AI coding had a critical flaw: agents would claim "I built X" without actually verifying the files exist. Why? **LLMs can't stop mid-generation to check.** Once generating a response, they must complete it even if uncertain.

**Solution: Response Awareness**

We separate generation (agents code) from verification (separate agent checks). This prevents 99% of false completions.

```
┌──────────────────────────────────────────────────────────┐
│                  IMPLEMENTATION PHASE                    │
└────────────────────────────┬─────────────────────────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
          ▼                  ▼                  ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│     Frontend     │ │     Backend      │ │      Tests       │
│     Engineer     │ │     Engineer     │ │     Engineer     │
└────────┬─────────┘ └────────┬─────────┘ └────────┬─────────┘
         │                    │                    │
         │  (Agents mark assumptions with tags)   │
         │                    │                    │
         ▼                    ▼                    ▼
┌──────────────────────────────────────────────────────────┐
│         Implementation Log with Assumption Tags          │
│  #FILE_CREATED: src/Calculator.tsx                       │
│  #COMPLETION_DRIVE: Assuming theme.colors exists         │
│  #SCREENSHOT_CLAIMED: evidence/before.png                │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              ┌────────────────────────────────────────┐
              │        Verification Agent              │
              │    (grep/ls/Read - SEARCH mode)       │
              └──────────────────┬─────────────────────┘
                                 │
                                 │
           Runs ACTUAL commands: │
           ls src/Calculator.tsx → ✓ or ✗
           ls evidence/before.png → ✓ or ✗
           grep "theme.colors" → ✓ or ✗
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │         Verification Report            │
              │          (findings.md)                 │
              └──────────────────┬─────────────────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
                    ▼                         ▼
          ┌──────────────────┐      ┌──────────────────┐
          │  ANY Failed?     │      │  All Verified?   │
          └────────┬─────────┘      └────────┬─────────┘
                   │                         │
                   ▼                         ▼
          ┌──────────────────┐      ┌──────────────────┐
          │    🚫 BLOCK      │      │     ✅ PASS      │
          │  Report failures │      │  Continue to     │
          │                  │      │ quality-validator│
          └────────┬─────────┘      └────────┬─────────┘
                   │                         │
                   └────────────┬────────────┘
                                │
                                ▼
              ┌────────────────────────────────────────┐
              │      User gets TRANSPARENCY:           │
              │  Either verified proof ✓               │
              │  or specific failures ✗                │
              └────────────────────────────────────────┘
```

**Key Innovation:** verification-agent operates in **search mode** (grep/ls), not generation mode. It can't rationalize "file probably exists" - it either finds it or doesn't.

**Result:** <5% false completion rate (down from ~80% before for complex multi-agent tasks)

See `docs/METACOGNITIVE_TAGS.md` for complete documentation.

---

## ACE Playbook System: Self-Improving Orchestration

**/orca now learns from every session** using Agentic Context Engineering (ACE).

### The Problem: Every Session Started From Zero

Before playbooks:
```
Session 1: "Build iOS app" → /orca guesses specialists
Session 50: "Build iOS app" → /orca guesses same specialists (no learning)
```

**Result:** Repeating solved problems, no accumulated knowledge.

### The Solution: Pattern-Based Learning

With ACE playbooks:
```
Session 1: Uses template patterns → Success
          → orchestration-reflector analyzes "why it worked"
          → playbook-curator updates helpful_count

Session 2: Loads updated playbook → Sees pattern helpful_count: 1
          → Higher confidence → Uses proven strategy
          → Success again → helpful_count: 2

Session 10: Pattern now has helpful_count: 9 (proven)
           → /orca confidently applies this strategy
           → Each session builds on accumulated knowledge
```

**Result:** **+10-15% performance improvement** (proven in research), fewer mistakes over time.

### How It Works: Three-Agent Architecture

```
┌──────────────────────────────────────────────────────────┐
│                      USER REQUEST                        │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              ┌────────────────────────────────────────┐
              │         SessionStart Hook              │
              │         Loads Playbooks                │
              └──────────────────┬─────────────────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
                    ▼                         ▼
          ┌──────────────────┐      ┌──────────────────┐
          │   iOS Playbook   │      │    Universal     │
          │  (25 patterns)   │      │    Patterns      │
          └────────┬─────────┘      └────────┬─────────┘
                   │                         │
                   └────────────┬────────────┘
                                │
                                ▼
              ┌────────────────────────────────────────┐
              │         /orca (Generator)              │
              │   Matches patterns to user request     │
              └──────────────────┬─────────────────────┘
                                 │
                                 │
    Pattern: "SwiftUI + SwiftData for iOS 17+"
    Strategy: Dispatch swiftui-developer + swiftdata-specialist
    Evidence: Proven across 9 sessions
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │       Specialists Execute              │
              └──────────────────┬─────────────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │      Quality Gates Pass                │
              │      Session Completes                 │
              └──────────────────┬─────────────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │    orchestration-reflector             │
              │ (Analyzes: "why did it work?")         │
              │  - Which patterns used?                │
              │  - Did they succeed?                   │
              │  - New patterns discovered?            │
              └──────────────────┬─────────────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │       playbook-curator                 │
              │     (Updates playbooks)                │
              │  - Increment helpful_count             │
              │  - Add new patterns                    │
              │  - Delete failing patterns             │
              └──────────────────┬─────────────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │       Playbooks Updated                │
              │       Next session smarter             │
              └────────────────────────────────────────┘
```

### What Gets Learned

**Successful Patterns (✓):**
- "SwiftUI + SwiftData + State-First works for iOS 17+ apps" → helpful_count++
- "Parallel dispatch saves 40% time for independent tasks" → helpful_count++
- "design-reviewer catches visual bugs before QA" → helpful_count++

**Anti-Patterns (✗):**
- "Skipping design-reviewer leads to App Store rejections" → harmful_count++
- "Using XCTest instead of Swift Testing for iOS 17+" → harmful_count++

**Apoptosis (Self-Cleaning):**
- If `harmful_count > helpful_count × 3` → Pattern deleted after 7-day grace period
- Bad patterns are automatically removed

### Playbook Templates (59 Seed Patterns)

**Included Templates:**
- **iOS Development** (25 patterns): SwiftUI, SwiftData, testing, architecture, CI/CD
- **Next.js** (18 patterns): App Router, Server Components, Server Actions, performance
- **Universal** (16 patterns): Parallel dispatch, verification, quality gates, orchestration

**Commands:**
- `/playbook-review` - Manually trigger reflection and curation after a session
- `/playbook-pause` - Temporarily disable playbooks for debugging

### Research Foundation

Based on **arXiv-2510.04618v1** (Agentic Context Engineering):
- Generator-Reflector-Curator architecture
- Delta updates (not full rewrites)
- Apoptosis for self-cleaning
- **Proven: +10.6% performance improvement**

Patterns from:
- **kayba-ai/agentic-context-engine** - JSON+Markdown dual format, ✓/✗/○ markers
- **bmad-code-org/BMAD-METHOD** - Work orders, context containers
- **Aloim/Cybergenic** - Signal logging, cost tracking, apoptosis

**Location:** `.orchestration/playbooks/` (see README.md there for complete documentation)

---

## What's Included

### 🤖 Agents (47 Total)

**Active agents: 11 base + 21 iOS + 5 frontend + 8 design + 2 orchestration/learning = 47 total**

```
┌──────────────────────────────────────────────────────────┐
│               AGENT ECOSYSTEM (47 Total)                 │
└────────────────────────────┬─────────────────────────────┘
                             │
      ┌──────────────────────┼──────────────────────┐
      │                      │                      │
      ▼                      ▼                      ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│   BASE AGENTS    │ │  iOS SPECIALISTS │ │ FRONTEND/DESIGN  │
│      (11)        │ │       (21)       │ │    (5 + 8)       │
└────────┬─────────┘ └────────┬─────────┘ └────────┬─────────┘
         │                    │                    │
         ▼                    ▼                    ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│  Planning (3)    │ │  UI (3)          │ │  React (2)       │
│  Quality (3)     │ │  Data (2)        │ │  State (1)       │
│  Backend (1)     │ │  Network (3)     │ │  Performance (1) │
│  Mobile (2)      │ │  Arch (3)        │ │  Testing (1)     │
│  Specialized (2) │ │  Testing (3)     │ │                  │
│                  │ │  Quality (2)     │ │  Design (8)      │
│                  │ │  DevOps (2)      │ │   System (2)     │
│                  │ │  Perf (1)        │ │   Visual (1)     │
│                  │ │  Security (2)    │ │   Build (3)      │
│                  │ │                  │ │   Review (2)     │
└──────────────────┘ └──────────────────┘ └──────────────────┘
         │                    │                    │
         │                    │                    ▼
         │                    │          ┌──────────────────┐
         │                    │          │  ORCHESTRATION   │
         │                    │          │  & LEARNING (2)  │
         │                    │          │                  │
         │                    │          │ orchestration-   │
         │                    │          │   reflector      │
         │                    │          │                  │
         │                    │          │ playbook-curator │
         │                    │          │                  │
         │                    │          │ Learns from      │
         │                    │          │ every session    │
         │                    │          └──────────────────┘
         │                    │
         └────────────────────┴─────────────────────────────┐
                                                            │
                                                            ▼
                              ┌────────────────────────────────────────┐
                              │  All agents organized by function      │
                              └────────────────────────────────────────┘
```

All agents live in `agents/` and are organized by function.

**System Architecture: 47 Total Agents**

- **iOS Specialists** (21 agents in `ios-specialists/`) - SwiftUI, SwiftData, networking, testing, architecture, performance, security, deployment
- **Frontend Specialists** (5 agents in `frontend-specialists/`) - React 18, Next.js 14, state management, performance optimization, testing
- **Design Specialists** (8 agents in `design-specialists/`) - Design systems, UX strategy, Tailwind v4, UI engineering, CSS, accessibility, design review, visual design
- **ACE Learning System** (2 agents in `specialized/`) - orchestration-reflector (analyzes outcomes), playbook-curator (updates learned patterns)
- **Base Agents** (11 agents):
  - **Planning**: requirement-analyst, system-architect, plan-synthesis-agent
  - **Quality**: verification-agent (🆕 meta-cognitive tag verification), test-engineer, quality-validator
  - **Implementation**: backend-engineer, android-engineer, cross-platform-mobile
  - **DevOps**: infrastructure-engineer
  - **Orchestration**: workflow-orchestrator

See the `agents/` directory for detailed agent specifications and the complete file structure below.

### ⚡ Commands (11 Total)

All commands live in `commands/` and extend Claude Code workflows:

#### Core Orchestration

| Command | Description | File |
|---------|-------------|------|
| **/orca** | Smart multi-agent orchestration with tech stack detection and team confirmation | `orca.md` |
| **/enhance** | Transform vague requests into well-structured prompts and execution | `enhance.md` |
| **/ultra-think** | Deep analysis and problem solving with multi-dimensional thinking | `ultra-think.md` |

#### ACE Playbook System (Self-Improving Orchestration)

| Command | Description | File |
|---------|-------------|------|
| **/playbook-review** | Manually trigger reflection and curation to update playbooks with learned patterns | `playbook-review.md` |
| **/playbook-pause** | Temporarily disable playbook system to run /orca without pattern influence | `playbook-pause.md` |

#### Design Workflow

| Command | Description | File |
|---------|-------------|------|
| **/concept** | Creative exploration phase - study references, extract patterns, get approval BEFORE building | `concept.md` |
| **/visual-review** | Visual QA review of implemented UI using chrome-devtools to screenshot and analyze | `visual-review.md` |

#### Workflow & Utilities

| Command | Description | File |
|---------|-------------|------|
| **/clarify** | Quick focused clarification for mid-workflow questions | `clarify.md` |
| **/completion-drive** | Meta-cognitive strategy for two-tier assumption tracking during implementation | `completion-drive.md` |
| **/session-save** | Save current session context for automatic resumption | `session-save.md` |
| **/session-resume** | Manually reload session context (normally auto-loads) | `session-resume.md` |

### 🪝 Hooks

| Hook | Description | File |
|------|-------------|------|
| **detect-project-type.sh** | Auto-detects project type on session start (< 50ms) and loads appropriate agent team | `hooks/detect-project-type.sh` |
| **load-playbooks.sh** | Auto-loads playbooks on session start - provides pattern-guided orchestration to /orca | `hooks/load-playbooks.sh` |

### 🎯 Skills

Skills from the superpowers plugin are available. See `skills/` directory for the complete list.

---

## Why Response Awareness Matters

### The Problem: LLMs Can't Verify Mid-Generation

**Anthropic Research Finding:** Once an LLM starts generating a response, it cannot stop to verify assumptions. It must complete the output.

**What this means in practice:**

```python
# Agent in generation mode:
"I created Calculator.tsx with full functionality ✓"
# Agent CANNOT stop here to run: ls Calculator.tsx
# Must complete the response → Claims success without checking
```

**Real failure (before Response Awareness):**
```
User: "Build calculator view"
swiftui-developer: "✓ Created CalculatorView.swift (245 lines)"
quality-validator: "✓ All requirements met"
User runs app: 💥 File doesn't exist, app crashes
```

### The Solution: Separate Phases

**Phase 3: Implementation (Generation Mode)**
- Agents write code
- Mark ALL assumptions with tags: `#FILE_CREATED`, `#COMPLETION_DRIVE`
- Cannot verify (still generating)

**Phase 4: Verification (Search Mode)**
- verification-agent runs AFTER generation completes
- Searches for tags via grep
- Runs actual commands: `ls`, `grep`, `file`
- Cannot rationalize ("file probably exists") - either finds it or doesn't
- Creates verification-report.md

**Phase 5: Quality Validation**
- quality-validator reads verification report
- If verification failed → BLOCKS → User sees specific failures
- If verification passed → Proceeds with quality assessment

**Result:**
- Before: ~80% false completion rate
- After: <5% false completion rate (target)
- User gets **transparency**: verified proof ✓ or specific failures ✗

### Research Backing

1. **Anthropic:** Models can't stop mid-generation to verify
2. **Li et al.:** Models can monitor internal states via explicit tokens (`#COMPLETION_DRIVE` tags)
3. **Didolkar et al.:** Metacognitive behaviors can be systematized (46% token reduction)
4. **Typhren:** Tag-based verification achieved 99.2% accuracy in production

---

## Complete Workflow Visualization

```
┌──────────────────────────────────────────────────────────┐
│              USER REQUEST: "Add dark mode"               │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              ┌────────────────────────────────────────┐
              │          AUTO-DETECT                   │
              │         Project Type                   │
              └──────────────────┬─────────────────────┘
                                 │
                                 ▼
              ┌────────────────────────────────────────┐
              │        LOAD AGENT TEAM                 │
              │    iOS: 8-16 agents                    │
              │    Frontend: 10-15 agents              │
              │    Mobile: 10-13 agents                │
              └──────────────────┬─────────────────────┘
                                 │
          ┌──────────────────────┼──────────────────────┐
          │                      │                      │
          ▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│    PHASE 1       │   │    PHASE 2       │   │    PHASE 3       │
│    PLANNING      │   │    DESIGN        │   │     CODE         │
└────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│ requirement-     │   │ design-system-   │   │ Implementation   │
│ analyst          │   │ architect        │   │ agents (parallel)│
│                  │   │                  │   │                  │
│ system-          │   │ ux-strategist    │   │ + Meta tags      │
│ architect        │   │                  │   │                  │
│                  │   │ visual-designer  │   │                  │
└────────┬─────────┘   └────────┬─────────┘   └────────┬─────────┘
         │                      │                      │
         └──────────────────────┴──────────────────────┘
                                │
                                ▼
              ┌────────────────────────────────────────┐
              │           PHASE 4                      │
              │         VERIFICATION                   │
              │    (Response Awareness)                │
              └──────────────────┬─────────────────────┘
                                 │
                                 │
            Runs actual commands: │
            ls, grep, build, test
                                 │
                    ┌────────────┴────────────┐
                    │                         │
                    ▼                         ▼
          ┌──────────────────┐      ┌──────────────────┐
          │  Files exist?    │      │  Tests pass?     │
          └────────┬─────────┘      └────────┬─────────┘
                   │                         │
                   └────────────┬────────────┘
                                │
                    ┌───────────┴───────────┐
                    │                       │
                    ▼                       ▼
          ┌──────────────────┐    ┌──────────────────┐
          │     ✅ PASS      │    │     ❌ FAIL      │
          └────────┬─────────┘    └────────┬─────────┘
                   │                       │
                   │                       └────────────────┐
                   │                                        │
                   ▼                                        ▼
         ┌────────────────────────────────────────┐  ┌──────────────────┐
         │            PHASE 5                     │  │  BLOCK, report   │
         │       QUALITY-VALIDATOR                │  │     issues       │
         └──────────────────┬─────────────────────┘  └──────────────────┘
                            │
            Evidence validation:
            - Screenshots ✓
            - Tests ✓
            - Build ✓
            - Requirements ✓
                            │
                            ▼
              ┌────────────────────────────────────────┐
              │         DELIVERY TO USER               │
              │         + Evidence                     │
              └────────────────────────────────────────┘
```

## Real-World Examples

### Example 1: "Fix the broken calculator"

**Traditional approach:** You debug, write fix, hope it works

**/orca Vibe Code:**

```
You: "The calculator buttons are broken on mobile"

┌─ Session Start ────────────────────────────────────────┐
│ Detected: iOS project (*.xcodeproj found)              │
│ Agent Team: swiftui-developer, ui-testing-expert,      │
│             accessibility-specialist                   │
│ Evidence: iOS Simulator screenshots required           │
└────────────────────────────────────────────────────────┘

┌─ Auto-Orchestration ───────────────────────────────────┐
│                                                        │
│  Phase 1: Investigation                                │
│  ├─ Read CalcView.swift                                │
│  ├─ Identified: Button tap targets too small (30pt)    │
│  └─ iOS HIG requires 44pt minimum                      │
│                                                        │
│  Phase 2: Fix (swiftui-developer)                      │
│  ├─ Update button frame: .frame(height: 44)            │
│  ├─ Add padding for visual balance                     │
│  └─ Test on iPhone 15 simulator                        │
│                                                        │
│  Phase 3: Validation (quality-validator)               │
│  ├─ Screenshot: Before (30pt) vs After (44pt)          │
│  ├─ Build: ✓ Compiles successfully                     │
│  ├─ Runtime: ✓ No crashes                              │
│  └─ A11y: ✓ VoiceOver compatible                       │
│                                                        │
└────────────────────────────────────────────────────────┘

Result: CalcView.swift:42 updated
Evidence: before.png, after.png, build.log
All tests: ✓ PASSING
```

### Example 2: "Add dark mode"

**Traditional approach:** Multiple back-and-forth about implementation details

**/orca Vibe Code:**

```
You: "Add dark mode toggle"

┌─ Detected: Next.js project ────────────────────────────┐
│ Agent Team: nextjs-14-specialist, state-management-    │
│             specialist, design-system-architect        │
│ Evidence: Browser screenshots required                 │
└────────────────────────────────────────────────────────┘

┌─ Parallel Orchestration ─────────────────────────────┐
│                                                      │
│  Agent: system-architect (2 min)                     │
│  └─ Design: Context API + CSS variables approach     │
│                                                      │
│  Agent: nextjs-14-specialist (8 min)                 │
│  ├─ ThemeContext.tsx (React Context)                 │
│  ├─ ThemeToggle.tsx (Toggle component)               │
│  ├─ globals.css (dark mode variables)                │
│  └─ _app.tsx (provider wrapper)                      │
│                                                      │
│  Agent: test-engineer (5 min)                        │
│  ├─ ThemeToggle.test.tsx (user interactions)         │
│  ├─ ThemeContext.test.tsx (state management)         │
│  └─ Integration test (localStorage persistence)      │
│                                                      │
│  Agent: quality-validator (3 min)                    │
│  ├─ Screenshot: Light mode ✓                         │
│  ├─ Screenshot: Dark mode ✓                          │
│  ├─ Screenshot: Toggle transition ✓                  │
│  ├─ Test output: 12/12 passing ✓                     │
│  ├─ Build: npm run build ✓                           │
│  └─ No console errors ✓                              │
│                                                      │
└──────────────────────────────────────────────────────┘

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

**/orca Vibe Code:**

```
You: "Why does the app feel slow?"

┌─ Intent Classification ────────────────────────────────┐
│ Type: QUESTION (not code change)                       │
│ Route: Answer directly (no orchestration needed)       │
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

### 4. Install agents, commands, and scripts

```bash
# Copy all agents (organized by function)
cp -r agents/* ~/.claude/agents/

# Copy all commands
cp commands/*.md ~/.claude/commands/

# Copy custom scripts (statusline, design tools)
cp -r scripts/* ~/.claude/scripts/

# Optional: Copy skills
cp -r skills/* ~/.claude/skills/
```

**What you get:**
- **47 specialized agents** (11 base + 21 iOS + 5 frontend + 8 design + 2 orchestration/learning) for implementation, planning, quality, and self-improvement
- **17 slash commands** for enhanced workflows (including ACE playbook commands)
- **ACE Playbook System** with 59 seed patterns for self-improving orchestration
- **Response Awareness verification** system (meta-cognitive tags + verification)
- **Project-specific skills** from the superpowers plugin

### 5. Verify installation

```bash
# Start a new Claude Code session in any project
# You should see:

┌─ Session Start ───────────────────────────────────────┐
│ Detected: [your-project-type]                         │
│ Agent Team: [specialized-agents]                      │
│ Auto-Orchestration: ACTIVE                            │
└───────────────────────────────────────────────────────┘
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
┌──────────────────────────────────────────────────────────┐
│                  Claude Code Pricing                     │
├──────────────────────────────────────────────────────────┤
│  Input:   $0.003 / 1K tokens  (cheap)                    │
│  Output:  $0.015 / 1K tokens  (5x expensive)             │
│                                                           │
│  Strategy: Send detailed context, get concise results    │
└──────────────────────────────────────────────────────────┘

Example: "Add authentication"

┌──────────────────────────────────────────────────────────┐
│              Sequential Approach (BAD)                   │
├──────────────────────────────────────────────────────────┤
│ 1. Backend agent:  10K input →  5K output                │
│ 2. Frontend agent: 10K input →  5K output                │
│ 3. Test agent:     10K input →  4K output                │
│                                                           │
│ Total: 30K input ($0.09) + 14K output ($0.21) = $0.30    │
│ Time: 15 minutes (sequential)                            │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│              Parallel Approach (GOOD)                    │
├──────────────────────────────────────────────────────────┤
│ Task 1: Backend agent   → 10K input,  5K output          │
│ Task 2: Frontend agent  → 10K input,  5K output          │
│ Task 3: Test agent      → 10K input,  4K output          │
│ (All run simultaneously)                                 │
│                                                           │
│ Total: 30K input ($0.09) + 14K output ($0.21) = $0.30    │
│ Time: 5 minutes (parallelized, 3x faster!)               │
└──────────────────────────────────────────────────────────┘
```

**Parallel dispatch:**
```javascript
// All in ONE message with multiple Task tool calls
Task(subagent_type="backend-engineer", prompt="Build API...")
Task(subagent_type="nextjs-14-specialist", prompt="Build Next.js UI...")
Task(subagent_type="test-engineer", prompt="Write tests...")

// Each agent gets its own context
// Results collected when all complete
// Then quality-validator reviews everything
```

### Quality Gates

Three mandatory validation checkpoints:

```
┌──────────────────────────────────────────────────────────┐
│         Quality Gate 1: Planning (95% threshold)         │
├──────────────────────────────────────────────────────────┤
│ ☑ Requirements documented?                               │
│ ☑ Architecture designed?                                 │
│ ☑ APIs specified?                                        │
│ ☑ User stories clear?                                    │
│ ☑ Tech stack decided?                                    │
│                                                           │
│ If < 95%: Loop back with specific gaps identified        │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│       Quality Gate 2: Implementation (80% threshold)     │
├──────────────────────────────────────────────────────────┤
│ ☑ Code matches specs?                                    │
│ ☑ Tests written?                                         │
│ ☑ Tests passing?                                         │
│ ☑ Build succeeds?                                        │
│ ☑ No critical bugs?                                      │
│                                                           │
│ If < 80%: Identify failures, re-dispatch agents          │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│        Quality Gate 3: Production (85% threshold)        │
├──────────────────────────────────────────────────────────┤
│ ☑ Security validated?                                    │
│ ☑ Performance acceptable?                                │
│ ☑ Accessibility compliant?                               │
│ ☑ Documentation complete?                                │
│ ☑ Evidence provided?                                     │
│                                                           │
│ If < 85%: Block deployment, fix issues                   │
└──────────────────────────────────────────────────────────┘
```

### Evidence Collection

**What counts as evidence:**

```
┌──────────────────────────────────────────────────────────┐
│                    EVIDENCE REQUIRED                     │
└────────────────────────────┬─────────────────────────────┘
                             │
      ┌──────────────────────┼──────────────────────┐
      │                      │                      │
      ▼                      ▼                      ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│   UI Changes     │ │  Functionality   │ │  Performance     │
└────────┬─────────┘ └────────┬─────────┘ └────────┬─────────┘
         │                    │                    │
         ├─ before.png        ├─ test-output.log  ├─ benchmark-
         ├─ after.png         ├─ coverage.txt     │   before.txt
         └─ console.log        └─ integration-    ├─ benchmark-
            (no errors)           test.log        │   after.txt
                                                  └─ lighthouse.json
         │                    │                    │
         └────────────────────┴────────────────────┘
                              │
                              ▼
              ┌────────────────────────────────────────┐
              │         Build Changes                  │
              ├────────────────────────────────────────┤
              │ ├─ build.log                           │
              │ ├─ bundle-size.txt                     │
              │ └─ deploy.log                          │
              └────────────────────────────────────────┘
```

**What does NOT count:**
- "Looks good to me"
- "Should work"
- "I tested it" (without logs)
- "Probably fine"

---

## Available Agents

**47 Total Agents organized into specialized teams:**

### iOS Specialists (21 agents)
SwiftUI, SwiftData, Core Data, networking (URLSession), testing (Swift Testing, XCTest, XCUITest), architecture (State-first, TCA), performance optimization, security, code review, debugging, deployment (Xcode Cloud, Fastlane), accessibility, and API design.

### Frontend Specialists (5 agents)
React 18+ (Server Components, Suspense, hooks), Next.js 14 (App Router, Server Actions), state management (strategic separation), performance optimization (code splitting, Core Web Vitals), and user-behavior-focused testing.

### Design Specialists (8 agents)
Design system architecture, UX strategy, Tailwind CSS v4 + daisyUI 5, UI engineering, pure CSS (when Tailwind insufficient), accessibility (WCAG 2.1 AA), design review (visual QA with Playwright), and visual design (hierarchy, typography, composition).

### Base Agents (11 agents)
- **Planning**: requirement-analyst, system-architect, plan-synthesis-agent
- **Quality**: verification-agent (meta-cognitive tag verification), test-engineer, quality-validator
- **Implementation**: backend-engineer, android-engineer, cross-platform-mobile
- **DevOps**: infrastructure-engineer
- **Orchestration**: workflow-orchestrator

For detailed agent specifications, see the `agents/` directory.

---

## Team Compositions

### iOS Development

**Total System: 45 Agents** (11 base + 21 iOS + 5 frontend + 8 design)

**iOS Team**: Dynamic composition (8-16 agents) based on app complexity:

```
┌──────────────────────────────────────────────────────────┐
│          iOS TEAM COMPOSITION (Dynamic 8-16)             │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│                   CORE PLANNING (2)                      │
│          requirement-analyst → system-architect          │
│                            ↓                             │
│       (Analyzes complexity, recommends specialists)      │
└────────────────────────────┬─────────────────────────────┘
                             │
      ┌──────────────────────┼──────────────────────┐
      │                      │                      │
      ▼                      ▼                      ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│   DESIGN (1-2)   │ │  iOS (2-10)      │ │  QUALITY (2)     │
└────────┬─────────┘ └────────┬─────────┘ └────────┬─────────┘
         │                    │                    │
         ▼                    ▼                    ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│ design-system    │ │ UI               │ │ verification-    │
│ ux-strategist    │ │ Data             │ │ agent            │
│ visual-designer  │ │ Network          │ │                  │
│ tailwind-spec    │ │ Architecture     │ │ quality-         │
│ accessibility    │ │ Testing          │ │ validator        │
│ design-reviewer* │ │ Quality          │ │                  │
│ (MANDATORY for   │ │ DevOps           │ │                  │
│  production)     │ │ Performance      │ │                  │
│                  │ │ Security         │ │                  │
└──────────────────┘ └──────────────────┘ └──────────────────┘
    OPTIONAL           CHOOSE 2-10         MANDATORY
    (design-reviewer   FROM 21 TOTAL      (verification-agent
     MANDATORY for     SPECIALISTS         quality-validator)
     production)
```

- **Core Planning (2)**: requirement-analyst, system-architect
- **Design Specialists (1-2)**: design-system-architect, ux-strategist, visual-designer, tailwind-specialist, accessibility-specialist, design-reviewer (MANDATORY for production)
- **iOS Specialists (2-10)**: Chosen from 21 specialists:
  - UI: swiftui-developer, uikit-specialist, ios-accessibility-tester
  - Data: swiftdata-specialist, coredata-expert
  - Networking: urlsession-expert, combine-networking, ios-api-designer
  - Architecture: state-architect, tca-specialist, observation-specialist
  - Testing: swift-testing-specialist, xctest-pro, ui-testing-expert
  - Quality: swift-code-reviewer, ios-debugger
  - DevOps: xcode-cloud-expert, fastlane-specialist
  - Performance & Security: ios-performance-engineer, ios-security-tester, ios-penetration-tester

- **Quality Gates (2)**: verification-agent (MANDATORY), quality-validator (MANDATORY)

**Team Scaling by App Complexity:**

```
┌──────────────────────────────────────────────────────────┐
│              iOS TEAM SCALING BY COMPLEXITY              │
└──────────────────────────────────────────────────────────┘

┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│   SIMPLE     │  │   MEDIUM     │  │   COMPLEX    │  │  ENTERPRISE  │
│ (Calculator) │  │ (Notes App)  │  │  (Social)    │  │  (Banking)   │
│      8       │  │      10      │  │      14      │  │      16+     │
└──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
       │                 │                 │                 │
┌──────┴───────┐  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────┴───────┐
│ Plan: 2      │  │ Plan: 2      │  │ Plan: 2      │  │ Plan: 2      │
│ iOS:  2      │  │ iOS:  4      │  │ iOS:  7      │  │ iOS:  10+    │
│ Design: 1    │  │ Design: 1    │  │ Design: 2    │  │ Design: 2    │
│ Quality: 2   │  │ Quality: 2   │  │ Quality: 2   │  │ Quality: 2   │
│              │  │              │  │              │  │              │
│ SwiftUI      │  │ + Data       │  │ + Network    │  │ + Security   │
│ Testing      │  │ + State      │  │ + TCA        │  │ + DevOps     │
│              │  │ + Review     │  │ + UITest     │  │ + Perf       │
│              │  │              │  │ + Perf       │  │ + PenTest    │
│              │  │              │  │ + Visual     │  │ + Advanced   │
└──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘
```

**Examples**:
- Simple app (calculator): 8 agents (planning 2 + iOS 2 + design 1 + quality 2)
- Medium app (notes): 10 agents (planning 2 + iOS 4 + design 1 + quality 2)
- Complex app (social network): 14 agents (planning 2 + iOS 7 + design 2 + quality 2)
- Enterprise app (banking): 16+ agents (planning 2 + iOS 10+ + design 2 + quality 2)

**Capabilities**:
- Swift 6.2 native patterns (@Observable, approachable concurrency)
- Modern architecture (state-first, not MVVM)
- SwiftData (iOS 17+) and Core Data (iOS 16 and earlier)
- Swift Testing framework (modern) and XCTest (legacy)
- Performance profiling with Instruments
- Security testing with CryptoKit, Keychain, biometric auth
- CI/CD with Xcode Cloud and Fastlane
- Accessibility compliance (WCAG 2.1 AA)
- iOS simulator integration (96-99% token efficiency)

See `QUICK_REFERENCE.md` for full specialist list and `/orca` for team composition logic.

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
├── agents/                            # All active agents (47 total)
│   ├── implementation/                # 3 implementation specialists
│   │   ├── backend-engineer.md
│   │   ├── android-engineer.md
│   │   └── cross-platform-mobile.md
│   ├── planning/                      # 2 planning specialists
│   │   ├── requirement-analyst.md
│   │   └── system-architect.md
│   ├── quality/                       # 3 quality specialists
│   │   ├── test-engineer.md
│   │   ├── verification-agent.md       # NEW: Response Awareness verification
│   │   └── quality-validator.md
│   ├── specialized/                   # 1 specialized agent
│   │   └── infrastructure-engineer.md
│   ├── orchestration/                 # 2 orchestrators
│   │   ├── workflow-orchestrator.md
│   │   └── plan-synthesis-agent.md
│   ├── ios-specialists/               # 21 iOS specialists (NEW)
│   │   ├── ui/                        # swiftui-developer, uikit-specialist, ios-accessibility-tester
│   │   ├── data/                      # swiftdata-specialist, coredata-expert
│   │   ├── networking/                # urlsession-expert, combine-networking, ios-api-designer
│   │   ├── architecture/              # state-architect, tca-specialist, observation-specialist
│   │   ├── testing/                   # swift-testing-specialist, xctest-pro, ui-testing-expert
│   │   ├── quality/                   # swift-code-reviewer, ios-debugger
│   │   ├── devops/                    # xcode-cloud-expert, fastlane-specialist
│   │   ├── performance/               # ios-performance-engineer
│   │   └── security/                  # ios-security-tester, ios-penetration-tester
│   ├── frontend-specialists/          # 5 frontend specialists (NEW)
│   │   ├── frameworks/                # react-18-specialist, nextjs-14-specialist
│   │   ├── state/                     # state-management-specialist
│   │   ├── performance/               # frontend-performance-specialist
│   │   └── testing/                   # frontend-testing-specialist
│   └── design-specialists/            # 8 design specialists (NEW)
│       ├── foundation/                # design-system-architect, ux-strategist
│       ├── visual/                    # visual-designer
│       ├── implementation/            # tailwind-specialist, css-specialist, ui-engineer
│       └── quality/                   # accessibility-specialist, design-reviewer
│
├── commands/                          # All slash commands (17 total)
│   ├── orca.md                       # Multi-agent orchestration
│   ├── enhance.md                    # Smart task execution
│   ├── ultra-think.md                # Deep analysis
│   ├── concept.md                    # Design exploration
│   ├── design.md                     # Design brainstorming
│   ├── discover.md                   # Browse design collections
│   ├── inspire.md                    # Design inspiration
│   ├── save-inspiration.md           # Save design examples
│   ├── visual-review.md              # Visual QA
│   ├── agentfeedback.md              # Feedback processing
│   ├── clarify.md                    # Quick questions
│   ├── completion-drive.md           # Assumption tracking
│   ├── nav.md                        # View setup
│   ├── session-save.md               # Save session
│   ├── session-resume.md             # Resume session
│   └── all-tools.md                  # Utility
│
├── hooks/                             # Auto-orchestration hooks
│   └── detect-project-type.sh        # < 50ms project detection
│
└── .claude/                           # Local Claude Code config
    ├── settings.local.json           # Hook configuration
    └── commands/                     # Project-specific overrides
        ├── enhance.md
        └── ultra-think.md
```

**Key Directories:**
- `agents/` - Copy to `~/.claude/agents/` for active use (47 total agents)
- `commands/` - Copy to `~/.claude/commands/` for slash commands (17 total)
- `hooks/` - Copy to `~/.claude/hooks/` for auto-detection hook
- `scripts/` - Copy to `~/.claude/scripts/` for custom utilities (statusline, design tools)
- `docs/` - Permanent system documentation (7 current files)

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

## Development Status

**Current Status:** Production Ready

This repository contains a complete multi-agent orchestration system for Claude Code with 47 specialized agents, 17 slash commands, and auto-detection hooks with self-improving playbook system.

**Complete and Deployed:**
- ✅ 47 specialized agents (11 base + 21 iOS + 5 frontend + 8 design + 2 orchestration/learning)
- ✅ 17 slash commands with quality gates
- ✅ ACE Playbook System (59 seed patterns across 3 templates)
- ✅ Auto-detection and orchestration system (/orca)
- ✅ Response Awareness verification framework
- ✅ Quality gate protocols and validation
- ✅ Project-specific agent team selection
- ✅ Parallel agent execution and coordination

**Active Development:**
- 🔨 Additional design inspiration collections
- 🔨 Extended platform support (Android, Go, Python)
- 🔨 Enhanced visual review capabilities

The system is fully functional and ready for use. Clone, install, and start building.

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
