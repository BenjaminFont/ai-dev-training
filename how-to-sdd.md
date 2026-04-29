# How to Set Up Spec-Driven Development (SDD)

## English

### Prerequisites

The SDD setup consists of two doc files, one project rule, and one skill from the `.claudesdd/` directory.

### Setup

**1. Copy the doc files into your project:**
```bash
cp .claudesdd/docs/how-to-write-specs.md docs/
cp .claudesdd/docs/how-to-write-plans.md docs/
```

**2. Copy the project rule:**
```bash
cp .claudesdd/rules/development-workflow.md .claude/rules/
```

**3. Copy the skill:**
```bash
cp -r .claudesdd/skills/ .claude/skills/
```

The project rule `development-workflow.md` automatically enforces the Spec → Plan → Implement workflow.

### What You Get

- **`docs/how-to-write-specs.md`** — Guide for writing feature specs (WHAT and WHY)
- **`docs/how-to-write-plans.md`** — Guide for writing implementation plans (HOW and WHEN)
- **`.claude/rules/development-workflow.md`** — Project rule that enforces the workflow: specs before plans, plans before code

**1 skill** (`/sdd`) that triggers the full SDD workflow:
- Guides you through writing a spec with clarifying questions
- Reviews the spec critically before moving on
- Creates an implementation plan with testing strategy (discussed interactively)
- Implements step by step, waiting for your approval after each step
- Cross-references plan against spec to catch inconsistencies

---

## Deutsch

### Voraussetzungen

Das SDD-Setup besteht aus zwei Doc-Dateien, einer Project Rule und einem Skill aus dem `.claudesdd/`-Verzeichnis.

### Setup

**1. Doc-Dateien ins Projekt kopieren:**
```bash
cp .claudesdd/docs/how-to-write-specs.md docs/
cp .claudesdd/docs/how-to-write-plans.md docs/
```

**2. Project Rule kopieren:**
```bash
cp .claudesdd/rules/development-workflow.md .claude/rules/
```

**3. Skill kopieren:**
```bash
cp -r .claudesdd/skills/ .claude/skills/
```

Die Project Rule `development-workflow.md` erzwingt den Spec → Plan → Implement Workflow automatisch.

### Was enthalten ist

- **`docs/how-to-write-specs.md`** — Leitfaden zum Schreiben von Feature-Specs (WAS und WARUM)
- **`docs/how-to-write-plans.md`** — Leitfaden zum Schreiben von Implementierungsplänen (WIE und WANN)
- **`.claude/rules/development-workflow.md`** — Project Rule die den Workflow erzwingt: Spec vor Plan, Plan vor Code

**1 Skill** (`/sdd`) der den vollständigen SDD-Workflow auslöst:
- Führt durch das Schreiben einer Spec mit klärenden Rückfragen
- Reviewt die Spec kritisch bevor es weitergeht
- Erstellt einen Implementierungsplan mit Testing-Strategie (interaktiv besprochen)
- Implementiert Schritt für Schritt, wartet nach jedem Schritt auf deine Freigabe
- Gleicht Plan gegen Spec ab um Inkonsistenzen zu finden
