k# How to Set Up Test-Driven Development (TDD)

## English

### Prerequisites

The TDD setup consists of four agents, one project rule, and one skill from the `.claudetdd/` directory.

### Setup

**1. Copy the agents into your project:**
```bash
cp -r .claudetdd/agents/ .claude/agents/
```

**2. Copy the project rule:**
```bash
cp .claudetdd/rules/tdd.md .claude/rules/
```

**3. Copy the skills:**
```bash
cp -r .claudetdd/skills/ .claude/skills/
```

### What You Get

**4 specialized TDD agents** that enforce the Red-Green-Refactor cycle:

| Agent | Phase | What it does |
|-------|-------|-------------|
| **test-list** | Planning | Creates a test list with `@Disabled("todo")` placeholders, ordered simple to complex, base functionality only |
| **red** | Red | Activates ONE test, makes predictions about how it will fail (compilation error, then runtime error), stops for approval |
| **green** | Green | Implements the minimal code to make the failing test pass — hardcoded returns are fine, no future features |
| **refactor** | Refactor | Evaluates naming, applies Simple Design Rules, calculates APP (Absolute Priority Premise) mass, documents decisions |

**1 project rule** (`.claude/rules/tdd.md`) that enforces:
- Mandatory use of TDD agents for every phase
- Human-in-the-loop checkpoints after each phase
- The Red → Green → Refactor cycle is non-negotiable, even in autonomous mode
- Tests run via `mvn test` (Java/JUnit setup)

**1 skill** (`/example-mapping`) for feature discovery:
- Interactive session that explores a feature BEFORE writing tests
- Discovers business rules, concrete examples, and open questions collaboratively
- You provide the domain knowledge, Claude facilitates and asks questions
- Outputs a structured markdown file with rules, examples, and open questions
- Bridges the gap between requirements and the test list

### How the Cycle Works

1. (Optional) Run `/example-mapping` → discover rules and examples for the feature
2. Launch `test-list` agent → creates test placeholders (from the examples discovered above)
3. Launch `red` agent → activates one test, makes predictions, verifies it fails
4. Launch `green` agent → writes minimal code to pass the test
5. Launch `refactor` agent → improves code quality while keeping tests green
6. Repeat from step 3 for the next test

Each agent stops after its phase and waits for your approval before proceeding.

---

## Deutsch

### Voraussetzungen

Das TDD-Setup besteht aus vier Agents, einer Project Rule und einem Skill aus dem `.claudetdd/`-Verzeichnis.

### Setup

**1. Agents ins Projekt kopieren:**
```bash
cp -r .claudetdd/agents/ .claude/agents/
```

**2. Project Rule kopieren:**
```bash
cp .claudetdd/rules/tdd.md .claude/rules/
```

**3. Skill kopieren:**
```bash
cp -r .claudetdd/skills/ .claude/skills/
```

### Was enthalten ist

**4 spezialisierte TDD-Agents** die den Red-Green-Refactor-Zyklus erzwingen:

| Agent | Phase | Was er tut |
|-------|-------|-----------|
| **test-list** | Planung | Erstellt eine Test-Liste mit `@Disabled("todo")`-Platzhaltern, geordnet von einfach nach komplex, nur Basisfunktionalität |
| **red** | Red | Aktiviert EINEN Test, macht Vorhersagen wie er fehlschlägt (Kompilierfehler, dann Laufzeitfehler), stoppt für Freigabe |
| **green** | Green | Implementiert den minimalen Code um den fehlschlagenden Test zu bestehen — hartcodierte Rückgabewerte sind erlaubt, keine zukünftigen Features |
| **refactor** | Refactor | Bewertet Naming, wendet Simple Design Rules an, berechnet APP (Absolute Priority Premise) Mass, dokumentiert Entscheidungen |

**1 Project Rule** (`.claude/rules/tdd.md`) die erzwingt:
- Verpflichtende Nutzung der TDD-Agents für jede Phase
- Human-in-the-Loop-Checkpoints nach jeder Phase
- Der Red → Green → Refactor-Zyklus ist nicht verhandelbar, auch im autonomen Modus
- Tests laufen über `mvn test` (Java/JUnit-Setup)

**1 Skill** (`/example-mapping`) zur Feature-Erkundung:
- Interaktive Session die ein Feature VOR dem Testen erforscht
- Entdeckt Business-Regeln, konkrete Beispiele und offene Fragen gemeinsam mit dir
- Du lieferst das Domänenwissen, Claude moderiert und stellt Fragen
- Erzeugt eine strukturierte Markdown-Datei mit Regeln, Beispielen und offenen Fragen
- Brücke zwischen Anforderungen und der Test-Liste

### Wie der Zyklus funktioniert

1. (Optional) `/example-mapping` ausführen → Regeln und Beispiele für das Feature entdecken
2. `test-list`-Agent starten → erstellt Test-Platzhalter (aus den entdeckten Beispielen)
3. `red`-Agent starten → aktiviert einen Test, macht Vorhersagen, verifiziert dass er fehlschlägt
4. `green`-Agent starten → schreibt minimalen Code um den Test zu bestehen
5. `refactor`-Agent starten → verbessert Code-Qualität, Tests bleiben grün
6. Ab Schritt 3 für den nächsten Test wiederholen

Jeder Agent stoppt nach seiner Phase und wartet auf deine Freigabe bevor er fortfährt.
