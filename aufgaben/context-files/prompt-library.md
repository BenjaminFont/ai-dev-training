# Wiederverwendbare Prompts

Prompts die ihr immer wieder tippt → einmal anlegen, immer abrufbar.

| Tool | Mechanismus | Aufruf |
|---|---|---|
| Claude Code | Skills in `.claude/skills/*.md` | `/skillname` im Chat |
| OpenCode | Workflows in `AGENTS.md` beschreiben | Natürlichsprachlich triggern |
| GitHub Copilot | `.github/prompts/*.prompt.md` | `#file:` Referenz oder "Run Prompt" in VS Code |

---

## Schritt 1: Drei Kandidaten finden

Welche Prompts tippt ihr täglich? Häufige Beispiele:
- Code Review (Fehlerbehandlung, Edge Cases, Lesbarkeit)
- Test-Skeleton generieren
- PR-Beschreibung schreiben

---

## Schritt 2: Anlegen

**Claude Code** — `.claude/skills/review.md`:
```markdown
# Code Review

Reviewe $ARGUMENTS als Senior-Entwickler.
Fokus: Fehlerbehandlung, Edge Cases, Lesbarkeit.
Ausgabe: nummerierte Liste mit konkreten Verbesserungen.
```
Aufruf: `/review OrderService.java`

**Copilot** — `.github/prompts/review.prompt.md`:
```markdown
Reviewe den folgenden Code als Senior-Entwickler.
Fokus: Fehlerbehandlung, Edge Cases, Lesbarkeit.
Ausgabe: nummerierte Liste.

Code: #file:${input:Dateiname}
```

**OpenCode** — in `AGENTS.md`:
```markdown
## Workflows
Wenn ich "review [Datei]" sage: Analysiere als Senior-Entwickler,
Fokus Fehlerbehandlung + Edge Cases, nummerierte Verbesserungsliste.
```

---

## Schritt 3: Testen & verfeinern

Testet jeden Prompt auf echtem Code. Ist der Output direkt nutzbar oder fehlt Kontext? Passt an bis er passt.

**Lohnt sich:** Welche dieser Prompts würden alle im Team nutzen? → Ins Repository committen.
