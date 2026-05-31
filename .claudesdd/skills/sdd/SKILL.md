---
name: sdd
description: >
  Trigger the Spec-Driven Development workflow: Spec → Plan →
  Implement. Guides the user through writing a feature spec,
  reviewing it, creating an implementation plan, and
  step-by-step implementation.
when_to_use: >
  When the user wants to build a new feature using the SDD
  workflow, or says "let's write a spec", "spec-driven",
  "plan this feature", or "I want to implement something
  with a spec first".
argument-hint: "[feature description]"
allowed-tools: Read Glob Grep Write Edit AskUserQuestion Bash
---

# Spec-Driven Development Workflow

Guide the user through Spec-Driven Development. The workflow
scales to the change: a small change stays lightweight
(in chat), a big or unclear one gets the full Spec → Plan →
Implement cycle. Each phase is a separate conversation step
with explicit user approval before moving on.

## Before Starting

1. Read `docs/how-to-write-specs.md` for the spec format
2. Read `docs/how-to-write-plans.md` for the plan format
3. Read `rules/development-workflow.md` for track selection
4. If these files don't exist, tell the user to copy them first

## Step 0: Choose the Track (always do this first)

Two questions decide everything. Ask them before any work.

**Question 1 — Is the business requirement (WHAT/WHY) clear
and uncontested?**
- NO  → **Spec-Track** (File-Pfad): go to Phase 1.
- YES → ask Question 2.

**Question 2 — Is the HOW trivial / obvious?**
- NO  → **Plan-Track** (fileless): skip Phase 1, go to Phase 2,
        but keep the plan *in chat* unless it must persist.
- YES → **Direkt-Track** (fileless): skip to Phase 3, implement
        directly.

Use **AskUserQuestion** to confirm the track when unsure. State
which track you picked and why before proceeding.

| Track | Spec? | Plan? | Where it lives |
|-------|-------|-------|----------------|
| Direkt | no | no | chat (fileless) |
| Plan | no | yes | chat, promote to file if it must persist |
| Spec | yes | yes | files in `specs/` |

**Litmus test** for "do I need a spec": delete a sentence — if it
changes what a *domain expert* agrees to, that's a spec (WHAT). If it
only changes what a *developer* builds, that's a plan (HOW). Bugfixes,
refactorings, config changes almost never need a spec.

## Fileless tracks (Direkt & Plan): keep it light

On the Direkt- and Plan-Track, do **not** create spec/plan files.

- **Direkt-Track:** restate the agreed intent in one line, implement,
  test, confirm. Done.
- **Plan-Track:** write the plan **as a short chat message** following
  `docs/how-to-write-plans.md` (steps + testing approach). Get approval
  in chat, then implement step by step (Phase 3). **Promote** it to
  `specs/<feature>-implementation-plan.md` only if it must persist or be
  handed over.

If, mid-work, a real business question appears, stop and escalate to the
Spec-Track (Phase 1).

## Phase 1: Write the Spec  (Spec-Track only)

### Step 1: Understand the Feature
- Ask the user to describe the feature they want to build
- Ask clarifying questions — do NOT assume:
  - "What problem does this solve?"
  - "Who is the user of this feature?"
  - "What are the inputs and expected outputs?"
  - "Are there security or performance requirements?"
  - "What should explicitly NOT be included?"
- Use **AskUserQuestion** for structured questions

### Step 2: Explore the Codebase
- Use Glob and Grep to find related existing code
- Read relevant files to understand current patterns
- Identify where the feature integrates

### Step 3: Draft the Spec
Write the spec following `docs/how-to-write-specs.md`. Stay in
**domain language** — WHAT and WHY only, no architecture:
- **Overview** (2-4 sentences: what and why)
- **Business Constraints & Guardrails** (domain rules, not tech —
  frameworks/data structures/algorithms belong in the plan)
- **Usage** (1-2 concrete examples, behaviour the user sees)
- Keep it to 1-2 pages maximum
- Run the litmus test on each sentence: business stays, technical
  moves to the plan

### Step 4: Save the Spec
- Save to `specs/<feature-name>.md`
- Present a summary to the user
- **STOP — ask for user approval before continuing**

## Phase 1.5: Spec Review 

### Critical Review
Review the spec as if you were a critical colleague:
- What is unclear or ambiguous?
- What is missing?
- What is not testable?
- Are the constraints sufficient?
- Are the examples concrete enough?

Present findings to the user using **AskUserQuestion**
for each issue that needs a decision.

Update the spec based on the review.

**STOP — ask the user to confirm the spec is ready
before moving to the plan.**

## Phase 2: Write the Plan 

### Step 1: Read the Spec and Codebase
- Re-read the approved spec
- Read relevant source files referenced by the spec
- Understand existing patterns and architecture

### Step 2: Draft the Plan
Write the plan following `docs/how-to-write-plans.md`:
- **Implementation Steps** (ordered, with dependencies)
- **Testing approach for each step** — discuss interactively
  with the user, do not decide alone:
  - Real dependencies vs mocks?
  - Integration vs unit tests?
  - What to stub?
- **Key Decision Points**
- **Risks and Unknowns**

### Step 3: Cross-Reference Against Spec
Before presenting the plan, verify:
- [ ] All operations from spec are covered
- [ ] File formats and paths match spec
- [ ] Error cases have corresponding handling
- [ ] Constants match between spec and plan

### Step 4: Save the Plan
- Save to `specs/<feature-name>-implementation-plan.md`
- Present a summary to the user
- **STOP — ask for user approval before implementing**

## Phase 3: Implement (Step by Step)

### For Each Step in the Plan:

1. **Announce** which step you're implementing
2. **Implement** the step — minimal code, follow existing
   patterns, respect spec constraints
3. **Test** according to the agreed testing approach
4. **STOP — ask the user to confirm** before moving to the
   next step

### During Implementation
- Use the plan as a guide, not a rigid checklist
- If you discover something that contradicts the plan or
  spec, **stop and discuss** with the user
- Update the plan if new insights emerge
- Reference spec sections by header name for traceability

### After Implementation
- Verify all spec requirements are met
- Run all tests
- Ask the user if the feature is complete

## Important Rules

- **Pick the track first** (Step 0) — don't default to the full
  workflow for every change
- **A spec is only for business clarification** (WHAT/WHY); never
  put architecture in it
- **Every phase requires user approval** before moving on
- **Never assume** — ask when something is unclear
- **Keep specs short** — 1-2 pages max, domain language
- **Plans evolve** — update them as you learn; the plan never
  re-negotiates the WHAT
- **Stay fileless when you can** — only the Spec-Track always uses
  files; promote a fileless plan only when it must persist
- **Step-by-step implementation** — one step at a time,
  wait for confirmation
- **Language**: Follow the user's language (German/English)

## Track Selection (summary)

| Change | Business req. clear? | HOW trivial? | Track |
|--------|:---:|:---:|-------|
| New feature / new entity, unclear WHAT | no | — | **Spec** |
| Migration with open business questions | no | — | **Spec** |
| Refactoring across multiple files | yes | no | **Plan** (fileless) |
| Larger bugfix (unclear cause, multi-file) | yes | no | **Plan** (fileless) |
| Small bugfix (known cause, 1-2 files) | yes | yes | **Direkt** |
| Config change, typo, dependency update | yes | yes | **Direkt** |

The WHAT being clear is what removes the spec. The HOW being trivial is
what removes the plan. See `rules/development-workflow.md`.