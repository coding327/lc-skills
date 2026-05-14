---
name: skill-fullstack
description: >
  Solo full-stack development with AI coding agents — 7-step proven methodology
  from two shipped products (47K LoC). Build complete projects with AI generating
  all code while you define requirements, control flow, and verify quality.
  Triggers: 全栈开发, full-stack, build a project, 构建应用, solo developer,
  独立开发, 上架产品, 从零开发, PRD to production, AI coding workflow,
  AI development methodology, 7-step, 需求文档, 技术文档, product launch,
  部署上线, ship a product, develop with AI. Actions: plan, build,
  develop, create, deploy, ship, launch a product.
---

# Fullstack — AI-Driven Solo Development

IRON LAW: NEVER skip Step 3 (Technical Document). It is the bridge between
requirements and code — the single highest-leverage step. Without it, AI
output quality drops dramatically and debugging cost multiplies.

Red Flags (return to Step 3 if any appear):
- AI writing code that does not match the expected architecture
- Frequent misunderstandings about what to build
- Inconsistent code style or tech choices across files
- AI inventing features not in the PRD

## Workflow

Copy this checklist and check off items as you complete them:

```
Fullstack Progress:

- [ ] Step 1: Tool Preparation ⛔ BLOCKING
  - [ ] 1.1 Set up AI coding agent + configure strongest model
  - [ ] 1.2 Set up multi-tab terminal + Git
  - [ ] 1.3 Enable file-based progress tracking + resource monitor
  - [ ] 1.4 Configure optional: Figma integration, browser automation
- [ ] Step 2: Requirements Document (PRD)
  - [ ] 2.1 Write PRD in Markdown
  - [ ] 2.2 Run AI brainstorming to fill gaps
  - [ ] 2.3 Prepare design assets (Figma or AI-generated)
- [ ] Step 3: Technical Document ⚠️ REQUIRED — MOST CRITICAL
  - [ ] 3.1 Define tech stack explicitly
  - [ ] 3.2 List all pages/routes with design links
  - [ ] 3.3 Document functional logic and interactions
  - [ ] 3.4 Define API contracts (request/response structures)
  - [ ] 3.5 Design database schema (tables, fields, relationships)
  - [ ] 3.6 Add mandatory constraints: logging, compile checks, timing
- [ ] Step 4: First Round Coding (sustained session, maximize breadth)
  - [ ] 4.1 Start with file-based progress tracking enabled
  - [ ] 4.2 Use sub-agents / agent teams for parallel work
  - [ ] 4.3 Set up self-verification mechanism
  - [ ] 4.4 Monitor context window with resource monitor
- [ ] Step 5: Independent Module Completion
  - [ ] 5.1 Identify standalone modules (auth, payment, i18n)
  - [ ] 5.2 Create git worktrees for parallel development
  - [ ] 5.3 Merge completed modules to main
- [ ] Step 6: Bug Fixing
  - [ ] 6.1 Collect context (logs, screenshots, browser traces)
  - [ ] 6.2 Fix bugs in parallel AI agent sessions
  - [ ] 6.3 Verify each fix before closing
- [ ] Step 7: Deployment & Release
  - [ ] 7.1 SSH auto-deploy to server
  - [ ] 7.2 Run pre-release cleanup scan
  - [ ] 7.3 Submit to distribution platforms
```

## Step 1: Tool Preparation ⛔ BLOCKING

Must have:
- **AI coding agent** (Claude Code, Cursor, Copilot Chat, etc.) with the
  **strongest available model** for complex work, lighter model for simple tasks
- **Git** — commit after every completed module, prevents AI from breaking code
- **Markdown** — all documents in Markdown, AI parses it most efficiently

Strongly recommended:
- **File-based progress tracking** (e.g., planning-with-files) — persists progress
  to files, enables session resume after crash
- **Resource monitor** (e.g., Claude HUD) — real-time token usage, task progress,
  model and cost tracking across sessions
- **Multi-tab terminal** (e.g., Ghostty, Kaku, iTerm, Warp) — manage multiple AI
  sessions in parallel without losing context

Optional (project-dependent):
- **Figma integration** (e.g., Figma MCP) — when a designer provides Figma files
- **Browser automation** (e.g., Chrome CDP, Playwright MCP) — for web projects,
  AI auto-verifies pages in browser
- **Brainstorming tools** (e.g., BMAD, Superpowers) — for PRD gap analysis

Model selection rule: Complex modules MUST use the strongest model available.
Using cheaper models on architecture-level work produces more rework cost than
the token savings.

## Step 2: Requirements Document (PRD)

Goal: write a PRD that AI can fully understand without guessing.

1. **Use Markdown, not Word** — structured natural language, highest AI parse efficiency
2. **Record meetings → AI transcribes → update doc** — feed transcripts to AI to
   extract requirements, no detail is lost
3. **Brainstorm with AI** — after draft, use brainstorming tools to discover edge
   cases and missing interaction states
4. **Design assets, two paths**:
   - Path A: AI generates UI directly — good enough for internal tools
   - Path B: Designer creates Figma → design integration → AI reads metadata
     Requires semantic layer naming in design files or fidelity drops to ~40%

Ask: Does the PRD describe WHAT the user wants, not HOW to build it?
Ask: Would a new developer understand every feature from this document alone?

## Step 3: Technical Document ⚠️ REQUIRED — MOST CRITICAL

Feed the PRD to AI, ask it to generate a technical implementation document.
Human reviews and supplements. This is the highest-ROI step in the entire process.

### Five Core Modules

1. **Tech Stack** — be explicit: "Flutter for client, Go for server, MySQL for
   database, Docker for deployment." If you do not specify, AI guesses — and
   inconsistent guesses are hard to unify later.

2. **Page/Route List + Design Links** — every page or route listed with its
   design reference. AI loads the corresponding design data when building each one.

3. **Functional Logic & Interaction Flow** — complete business rules for each
   feature. Prevents AI from "inventing" its own logic.

4. **API Contracts** — request/response field structures for every endpoint.
   This is the binding contract between frontend and backend.

5. **Database Schema** — tables, fields, relationships. AI generates data layer
   code from this. Avoids costly schema changes mid-development.

### Mandatory Constraints

Write these into the technical document or project rules file:

- **Logging**: "All critical flow nodes MUST have log output."
  Without logs, debugging production issues is blind. This is a hard-learned lesson.
- **Compile verification**: "After completing each module, ensure compilation passes."
  AI will self-check instead of delivering broken code.
- **Task timing**: "Output start time when beginning a task, end time when done."
  Know the progress and cost of each parallel task.

### Project Rules File

Most AI coding agents support a project-level config file (CLAUDE.md, .cursorrules,
.copilot-instructions.md, etc.). Keep under 500 lines. Essential rules:
- Commit after every completed module
- All functions must include logging at key decision points
- Design-to-code reads must target 100% fidelity
- Pin specific versions of all dependencies

## Step 4: First Round Coding

Goal: one sustained session to complete the bulk of the project skeleton —
main pages/routes, backend APIs, database tables, and navigation all done here.
Actual duration depends on project size, model performance, and context
window limits. The mechanisms below are what make broad progress possible.

### Three Key Mechanisms

**1. File-Based Progress Tracking**

Writes the development plan and real-time progress to a file (e.g., `progress.md`).
If the session crashes (network, tokens, terminal close), use the agent's resume
command to recover state. This solves the #1 pain point of long-running tasks:
losing everything on interruption.

**2. Sub-Agents / Agent Teams — Parallel Execution**

- **Sub-agents**: main AI splits work across sub-agents, each with independent
  context. Main agent monitors, sub-agents execute, results merge at the end.
- **Agent teams**: agents work in parallel AND communicate with each other.
  Frontend agent asks backend agent "is this API field finalized?" — prevents
  frontend/backend misalignment.

Without parallel mechanisms, broad completion in a single session is nearly
impossible — each file waits for the last, context fills with trivia, and
progress stalls while the model handles one thing at a time.

**3. Self-Verification**

Require AI to prove its code works:
- Web projects: browser automation — AI opens browser, takes screenshots,
  verifies behavior
- Client projects: compile and capture logs, confirm key flows have no errors
- Without this, AI claims "done" but the code may not even compile

### The Four Enemies of Long-Running Dev

| Enemy | Symptom | Solution |
|-------|---------|----------|
| Context Explosion | AI forgets code, contradicts itself, loops on errors, freezes | Sub-agent partitioning: split before window fills |
| Task Interruption | Network down, tokens exhausted, session crash | File-persisted state, resume via session resume command |
| Scheduling Chaos | AI mixes up dependency order, works on B before A is done | Plan mode: explicit task list with dependencies |
| Lack of Verification | Code is written but correctness unknown, bugs accumulate | Browser automation or compile+log verification at every step |

### Context Window Management

Monitor token/context usage with a resource monitor. When approaching the limit:
- Split remaining work into sub-agents BEFORE the window fills
- Sub-agents get fresh context; main agent only monitors progress
- Sub-agent crash → main agent retries. Main agent crash = the real problem.

## Step 5: Independent Module Completion

Auth, payment, i18n — handle these SEPARATELY from the first coding round.
Reasons:
- Complex self-contained logic (payment = third-party SDK + callbacks + errors)
- Cannot be tested until the main project skeleton is complete
- Need dedicated documentation for full AI focus

### Git Worktree Parallel Development

```bash
git worktree add ../feature-auth auth-branch
git worktree add ../feature-payment payment-branch
git worktree add ../feature-i18n i18n-branch
```

One AI agent session per worktree, all running in parallel. Merge when done.
Same pattern works for bug fixing — dramatic speedup vs serial.

## Step 6: Bug Fixing

Core principle: **AI must "see" the problem to fix it.** AI cannot guess from
vague descriptions — it needs concrete evidence.

### Three Ways to Convey Problem Context

| Method | Best For | How To |
|--------|----------|--------|
| Error logs | Backend logic errors, API failures | Paste the full stack trace |
| Screenshots | UI layout issues, visual bugs | Send screenshot directly |
| Browser automation | Web page functional verification | AI opens browser and tests |

### Mid-Task Prompting

With agents that support streaming interaction, you can append prompts while
the agent is working. It adjusts direction immediately — discover a more
critical bug while fixing another? Just add the prompt, no need to queue.

### Multi-Session Parallel Fixing

Found 5 bugs → open 5 AI agent sessions, one per bug. A multi-tab terminal
makes this manageable — see at a glance what each session is doing.
Do not fix bugs one at a time — parallel is dramatically faster.

## Step 7: Deployment & Release

### 7.1 SSH Auto-Deploy

Give AI: server IP, username, password. It SSHes in, checks environment,
installs dependencies, writes Docker config, configures Nginx, starts service.
You judge whether it did the right things — you do not need to know Docker or
Nginx syntax.

### 7.2 Pre-Release Checklist

AI must scan and remove before submission:
- Test code and debug log statements
- Test data and mock endpoints
- Development-only configuration flags
Use AI memory during development to track test code locations for cleanup.

### 7.3 Distribution Platform Submission

**Mobile app stores** (examples):
- **iOS App Store**: Strict review. Permission descriptions must specify WHEN
  and WHY (not just "needs camera"). Flutter plugins need privacy manifest
  files — always use latest plugin versions.
- **Google Play**: First release requires 12 testers completing a 14-day closed
  test. More complex process than iOS for initial submission.

**Web / other platforms**: AI can help with Vercel/Netlify deploy, Docker Hub
publish, npm/pip package registry, or any other distribution channel.

**Browser Automation Auto-Fill**: AI knows the entire project. For platforms
with web forms (App Store Connect, Google Play Console), let AI auto-fill
name, description, keywords, and other metadata via browser automation.
You only need to confirm.

### Preparation
- [ ] Developer accounts for target platforms (budget accordingly)
- [ ] Privacy policy URL (hosted, accessible)
- [ ] Product screenshots in required dimensions
- [ ] Third-party SDK compliance docs (privacy manifests, etc.)

## Common Pitfalls

### Pitfall 1: Context Explosion
**Symptom**: AI forgets code, contradicts itself, loops on same error, freezes.
**Cause**: Context window is full — the "workbench is cluttered and nothing can
be found."
**Fix**: Sub-agent partitioning from the start. Monitor with resource monitor.
Split BEFORE the window fills, not after.

### Pitfall 2: Design-to-Code Fidelity Gap
**Symptom**: UI fidelity only ~40% — positions, spacing, fonts are wrong.
**Cause**: Design integrations read component metadata, not rendered images.
Information loss occurs when converting to native code.
**Fix**: Use a dedicated design-to-framework workflow (extract info → analyze
hierarchy → generate code). Semantic naming in design files is critical.
Can improve fidelity to 80%+.

### Pitfall 3: Wrong Model Choice
**Symptom**: Frequent logic errors, constant rework, total time INCREASES.
**Cause**: Weak models cannot handle complex architecture and multi-file context.
**Fix**: Use the strongest available model for complex modules. The cost of
rework exceeds the cost of a better model.

### Pitfall 4: No Logging
**Symptom**: Production error with zero visibility — guessing in the dark.
**Cause**: Logging was not required in the technical document phase.
**Fix**: Add "all critical flow nodes MUST have log output" to Step 3. It is
much cheaper to add logging during development than after.

## Anti-Patterns

- Skipping the technical document and jumping straight to coding
- Using weak models on complex architecture to save token cost
- Running one massive session without progress persistence — one crash = total loss
- Mixing auth, payment, or i18n into the first coding round
- Asking AI to fix bugs without providing logs or screenshots
- Serial bug fixing when parallel sessions would be dramatically faster
- Deploying without running the pre-release cleanup scan

## Pre-Delivery Checklist

Before telling the user any step is complete, verify:
- [ ] Step 3 technical document covers all 5 core modules
- [ ] Project rules file exists with logging, commit-frequency, and compile-check rules
- [ ] Progress tracking is active before starting Step 4
- [ ] Each independent module (Step 5) runs in its own git worktree
- [ ] All bug fixes are verified with concrete evidence (logs/screenshots/browser)
- [ ] Pre-release scan completed and confirmed clean before Step 7 submission
- [ ] No placeholder text or TODO markers remain in any generated output
