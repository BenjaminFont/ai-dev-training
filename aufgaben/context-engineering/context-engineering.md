# Explore → Plan → Implement

Statt sofort Code schreiben zu lassen: drei Phasen, drei Sessions.

**Tool:** Claude Code (`claude`) oder OpenCode (`opencode`) | **~45 Min**

---

## Phase 1: Explore

Neue Session. Kein Code — nur Analyse.

> "Ich plane: [Feature-Beschreibung].
> Schau dir OrderService.java und OrderRepository.java an.
> Beantworte — noch kein Code:
> 1. Wo wird das Feature eingebaut?
> 2. Was existiert bereits, das ich nutzen kann?
> 3. Was fehlt?
> Stelle Rückfragen, wenn du etwas brauchst."

Beantwortet die Fragen des Modells. Überraschungen in der Analyse?

---

## Phase 2: Plan

Gleiche Session (Kontext bleibt erhalten).

> "Erstelle einen Implementierungsplan:
> 1. Welche Dateien werden erstellt/geändert?
> 2. Reihenfolge?
> 3. Risiken?
> 4. Wie wird getestet?
> Noch kein Code."

Reviewt den Plan, korrigiert per Prompt. Dann:

> "Schreib den finalen Plan nach plans/[feature-name]-plan.md."

---

## Phase 2.5: Plan-Review mit frischem Blick

**Neue Session.** Der Plan kommt als Werk eines Junior-Devs:

> "Ein Junior hat diesen Plan geschrieben: plans/[feature-name]-plan.md
> Schau auch OrderService.java an.
> Was sind Pros/Cons, Risiken, blinde Flecken?"

Passt den Plan an, bevor ihr implementiert.

---

## Phase 3: Implement

**Neue Session.** Schritt für Schritt, nicht alles auf einmal:

> "Implementierungsplan: plans/[feature-name]-plan.md
> Implementiere nur Schritt 1. Dann warte."

Nach Review: `"Gut. Weiter mit Schritt 2."`

Weicht das Modell vom Plan ab? Fragt nach dem Warum — und ob der Plan aktualisiert werden soll.

---

**Warum neue Sessions?** Der Kontext in CLI-Tools ist kumulativ. Neue Sessions erzwingen Klarheit: ihr gebt nur rein, was wirklich relevant ist.

**Reflexion:** Was wäre passiert, wenn ihr direkt mit Phase 3 gestartet hättet?
