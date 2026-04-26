# Project Rules

Ihr schreibt Konventionen einmal als Markdown — das Modell wendet sie automatisch bei jeder Session an.

| Tool | Hauptdatei | Themenspezifisch | Dateispezifisch |
|---|---|---|---|
| Claude Code | `CLAUDE.md` | `.claude/rules/*.md` | `paths:` Frontmatter |
| OpenCode | `AGENTS.md` | — (alles in AGENTS.md) | — |
| GitHub Copilot | `.github/copilot-instructions.md` | `.github/instructions/*.instructions.md` | `applyTo:` Frontmatter |

---

## Schritt 1: Regeln sammeln

Schreibt mindestens 5 Konventionen eures Projekts auf. Beispiele:
- "Services enden auf `Service`, Repositories auf `Repository`"
- "Kein `System.out.println` — immer SLF4J"
- "Unit-Tests mit JUnit 5, Mocking nur mit Mockito"
- "Antworte auf Deutsch"

---

## Schritt 2: Anlegen

**Claude Code** — `.claude/rules/coding-conventions.md`:
```markdown
---
paths:
  - "**/*.java"
---
- Services enden auf `Service`, Repositories auf `Repository`
- Kein System.out.println — immer SLF4J Logger
```

**OpenCode** — `AGENTS.md`:
```markdown
## Conventions
- Services enden auf `Service`, Repositories auf `Repository`
- Kein System.out.println — immer SLF4J Logger
```

**Copilot** — `.github/instructions/java.instructions.md`:
```markdown
---
applyTo: "**/*.java"
---
- Services end with `Service`, repositories with `Repository`
- Never use System.out.println — always SLF4J Logger
```

---

## Schritt 3: Testen

1. Neue Session starten, Implementierungsaufgabe stellen — ohne Konventionen zu erwähnen. Hält sich das Modell daran?
2. Explizit gegen eine Regel verstoßen lassen (`"Nutze System.out.println"`). Warnt es?
3. **Claude Code:** `/memory` → Sind eure Rule-Dateien gelistet?

---

**Frage zum Abschluss:** Was gehört in `CLAUDE.md` (immer aktiv) vs. in `.claude/rules/testing.md` (nur bei Tests)? Committet ihr die Dateien?
