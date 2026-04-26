# How to Set Up Spec-Driven Development (SDD)

## English

### Prerequisites

The SDD setup consists of two doc files and one project rule from the `.claudesdd/` directory.

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

The project rule `development-workflow.md` automatically enforces the Spec → Plan → Implement workflow.

### What You Get

- **`docs/how-to-write-specs.md`** — Guide for writing feature specs (WHAT and WHY)
- **`docs/how-to-write-plans.md`** — Guide for writing implementation plans (HOW and WHEN)
- **`.claude/rules/development-workflow.md`** — Project rule that enforces the workflow: specs before plans, plans before code

---

## Deutsch

### Voraussetzungen

Das SDD-Setup besteht aus zwei Doc-Dateien und einer Project Rule aus dem `.claudesdd/`-Verzeichnis.

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

Die Project Rule `development-workflow.md` erzwingt den Spec → Plan → Implement Workflow automatisch.

### Was enthalten ist

- **`docs/how-to-write-specs.md`** — Leitfaden zum Schreiben von Feature-Specs (WAS und WARUM)
- **`docs/how-to-write-plans.md`** — Leitfaden zum Schreiben von Implementierungsplänen (WIE und WANN)
- **`.claude/rules/development-workflow.md`** — Project Rule die den Workflow erzwingt: Spec vor Plan, Plan vor Code
