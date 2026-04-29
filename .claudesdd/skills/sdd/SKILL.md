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

Guide the user through the full Spec → Plan → Implement
cycle. Each phase is a separate conversation step with
explicit user approval before moving on.

## Before Starting

1. Read `docs/how-to-write-specs.md` for the spec format
2. Read `docs/how-to-write-plans.md` for the plan format
3. If these files don't exist, tell the user to copy them
   first (see how-to-sdd.md)

## Phase 1: Write the Spec 

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
Write the spec following `docs/how-to-write-specs.md`:
- **Overview** (2-4 sentences: what and why)
- **Key Constraints & Design Decisions**
- **Usage** (1-2 concrete examples)
- Keep it to 1-2 pages maximum

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

- **Every phase requires user approval** before moving on
- **Never skip the spec** for non-trivial features
- **Never assume** — ask when something is unclear
- **Keep specs short** — 1-2 pages max, focus on guardrails
- **Plans evolve** — update them as you learn
- **Step-by-step implementation** — one step at a time,
  wait for confirmation
- **Language**: Follow the user's language (German/English)

## When to Use the Full Workflow

| Change | Workflow |
|--------|----------|
| New feature, new API, new entity | Spec → Plan → Implement |
| Migration (DB, Framework, Library) | Spec → Plan → Implement |
| Larger bugfix (unclear cause, multiple files) | Plan → Implement (Spec optional) |
| Refactoring across multiple files | Plan → Implement |
| Small bugfix (known cause, 1-2 files) | Implement directly |
| Config change, typo, dependency update | Implement directly |

## Rule of Thumb

If the change touches more than 3 files or the approach
isn't immediately clear, write at least a plan. If the
feature is new and others need to understand it, write
a spec.