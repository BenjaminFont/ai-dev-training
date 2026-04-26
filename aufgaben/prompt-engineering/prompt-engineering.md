# Prompt Engineering

**~40 Min | Tool:** Claude Code (`claude`) oder OpenCode (`opencode`)

---

## Übung 1: Rolle, Kontext, Aufgabe, Format

Stellt dieselbe Frage zweimal — einmal schlecht, einmal gut:

**Schlecht:**
> "Was ist falsch an diesem Code?"

**Gut** (neue Session):
> "Du bist Senior Backend-Entwickler. Wir nutzen Spring Boot + Java 21.
> Reviewe OrderService.java auf Fehlerbehandlung.
> Gib max. 5 konkrete Verbesserungsvorschläge als nummerierte Liste."

Was hat sich verändert?

---

## Übung 2: Einmalig vs. persistent

Wenn ihr euch denselben Satz in jedem Prompt wiederholt, gehört er in die Konfigurationsdatei:

| Tool | Datei |
|---|---|
| Claude Code | `CLAUDE.md` (oder `/init` ausführen) |
| OpenCode | `AGENTS.md` (oder `/init` ausführen) |
| GitHub Copilot | `.github/copilot-instructions.md` |

Tragt mindestens zwei projektspezifische Infos ein (Sprache, Framework, Konventionen). Startet dann eine neue Session und fragt etwas Relevantes — ohne die Infos zu wiederholen.

> **Claude Code:** `/memory` zeigt, welche Dateien geladen wurden.

---

## Übung 3: Iteratives Prompting

Startet vage, präzisiert schrittweise:

1. `"Verbessere OrderService.java."`
2. `"Refactore so, dass die Klasse dem Single-Responsibility-Prinzip folgt. Erkläre kurz was und warum."`
3. `"Nur die Methode processOrder — Code ohne Erklärung."`

Nach jedem Schritt: War die Antwort nutzbar? Ab wann?
