# Schliff Launch-Umsetzung — Claude Code Anweisungen

> Kopiere die einzelnen Prompt-Blöcke nacheinander in dein Claude Code Terminal im Schliff-Projekt.
> Jeder Block ist ein eigenständiger Auftrag. Reihenfolge = Priorität.

---

## Phase 1: Positionierung & README (Tag 1, Vormittag)

### Prompt 1 — README komplett neu schreiben

```
Schreibe die README.md komplett neu. Schliff muss sich klar von der Konkurrenz abheben.

KONTEXT:
- Schliff ist ein autonomer Improvement-Loop für Claude Code Skills (inspiriert von Karpathys autoresearch)
- Der Markt ist extrem gesättigt: 76+ Projekte im autoresearch-Ökosystem, Hauptkonkurrent uditgoenka/autoresearch hat 2.100 Stars
- Anthropic hat einen nativen /loop Command shipped — der Basis-Loop ist commoditized
- "Schliff" ist deutsch und für internationale Devs nicht verständlich

POSITIONIERUNG — "Ruff for Claude Code Skills":
- Schliff ist KEIN weiterer autoresearch-Klon
- Schliff ist der deterministische Skill-Linter und Scoring-Engine
- Tagline: "The finishing cut for Claude Code skills — deterministic linting, not just LLM guessing"
- Subtitle prominent: "The deterministic skill linter & scoring engine"

STRUKTUR der neuen README:
1. Hero-Section mit Logo, Tagline, Badges (Score, Stars, Tests, License)
2. "Why Schliff?" — 3 Bullet-Points die den Unterschied zu autoresearch klar machen:
   - 60-70% rule-based/deterministic patches vs. 100% LLM-generated bei Konkurrenz
   - 7-Dimension Scoring mit Anti-Gaming/Contradiction Detection vs. single scalar metric
   - Cross-Session Episodic Memory vs. stateless competitors
3. Quick Start — `schliff score` in 3 Zeilen lauffähig
4. "How it differs from autoresearch" — Vergleichstabelle:
   | Feature | autoresearch (Karpathy) | autoresearch (uditgoenka) | Schliff |
   Zeilen: Patch-Typ, Scoring-Dimensionen, Anti-Gaming, Memory, Dependencies, Tests
5. Commands — kurze Übersicht aller CLI-Commands
6. Architecture — Mermaid-Diagramm des Scoring-Flows
7. Results — "56.9 → 99.9 in 18 iterations, zero human input" mit Details
8. Contributing + License

STIL:
- Englisch, knapp, technisch
- Keine Emojis im Fließtext (nur in Badges)
- Jeder Satz muss Informationswert haben
- Inspiriert von der Ruff-README (ruff.rs) — clean, confident, facts-first
```

---

### Prompt 2 — SKILL.md Subtitle und Discoverability

```
Öffne die SKILL.md (oder das Äquivalent für die Claude Code Skill-Registration).

Ergänze folgende Felder falls nicht vorhanden:
- description: "Deterministic skill linter and scoring engine for Claude Code. 7-dimension scoring, anti-gaming detection, 60-70% rule-based patches. The Ruff for Claude Code skills."
- tags/keywords: ["skill-linter", "autoresearch", "scoring", "deterministic", "quality", "autonomous-improvement", "code-quality", "linting"]
- Stelle sicher dass "autoresearch" und "linter" in der Description vorkommen — das sind die Suchbegriffe die Leute nutzen

Falls es eine skills.json, package.json oder pyproject.toml mit Metadaten gibt, aktualisiere die Description dort ebenfalls.
```

---

## Phase 2: Cold-Start & Developer Experience (Tag 1, Nachmittag)

### Prompt 3 — `schliff init` Command implementieren

```
Implementiere einen neuen `schliff init` Command.

PROBLEM: Neue User wissen nicht, wie sie Schliff auf ein bestehendes Projekt anwenden.
Die Konkurrenz (uditgoenka/autoresearch) hat einen interaktiven /autoresearch:plan Wizard.

LÖSUNG — `schliff init` soll:
1. Das aktuelle Verzeichnis scannen (Sprache erkennen, Testrunner finden, Linter finden)
2. Eine schliff.toml oder .schliff/config.toml generieren mit:
   - Erkannte Sprache und Dateimuster
   - Vorgeschlagene Scoring-Dimensionen (aus den 7 verfügbaren)
   - Pfade zu Tests/Linter
   - Vorgeschlagener Improvement-Scope
3. Kurze Zusammenfassung ausgeben: "Found Python project with pytest. Generated config targeting 4 dimensions. Run `schliff score` to get your baseline."

CONSTRAINTS:
- Kein interaktiver Wizard (Schliff ist non-interactive by design)
- Zero external dependencies beibehalten
- Bestehende Code-Patterns und Architektur des Projekts folgen
- Unit Tests für den neuen Command schreiben
```

---

### Prompt 4 — `schliff score` Output verbessern

```
Verbessere den Output von `schliff score` so, dass er sofort als Demo/Screenshot taugt.

Der Score-Output ist das wichtigste Marketing-Asset. Er muss auf den ersten Blick beeindrucken und den Unterschied zu Konkurrenten zeigen.

ANFORDERUNGEN:
1. Kompakte Terminal-Ausgabe mit allen 7 Dimensionen
2. Jede Dimension mit Score (0-100), einem kurzen Status-Wort, und einem visuellen Balken (Unicode blocks: ░▒▓█)
3. Gesamt-Score prominent am Ende
4. Falls Anti-Gaming-Detection Contradictions findet: rot markierte Warning-Zeile
5. Am Ende eine Zeile: "X deterministic fixes available. Run `schliff fix` to apply."

BEISPIEL-OUTPUT (ungefähr):
```
schliff score v6.0.0

  Structure    ████████░░  82/100  good
  Security     ██████████  98/100  excellent
  Robustness   ███████░░░  71/100  fair
  Performance  █████░░░░░  54/100  needs work
  Readability  ████████░░  85/100  good
  Testability  ██████░░░░  63/100  fair
  Maintainab.  ███████░░░  76/100  good

  Overall      ████████░░  75.6/100

  ⚠ 2 contradictions detected (score-inflation blocked)
  → 14 deterministic fixes available. Run `schliff fix` to apply.
```

Passe den bestehenden Score-Output-Code entsprechend an. Keine neuen Dependencies.
```

---

## Phase 3: Integration mit /loop (Tag 1, Abend)

### Prompt 5 — Schliff als Scoring-Backend für Anthropics /loop

```
Implementiere eine Integration, sodass Schliff als Scoring-Backend für Anthropics nativen /loop Command funktioniert.

KONTEXT: Anthropic hat im März 2026 einen nativen /loop Command in Claude Code eingebaut.
Statt gegen /loop zu konkurrieren, soll Schliff sich als das Scoring/Verification-Backend positionieren.

IMPLEMENTIERUNG:
1. Erstelle ein `schliff loop-hook` oder `schliff verify` Command der:
   - Den aktuellen Score misst
   - Mit dem vorherigen Score vergleicht (aus .schliff/history.json oder ähnlich)
   - Exit-Code 0 zurückgibt wenn Score gleich oder besser, Exit-Code 1 wenn schlechter
   - Eine einzeilige Zusammenfassung auf stdout gibt: "Score: 75.6 → 78.2 (+2.6) ✓" oder "Score: 75.6 → 74.1 (-1.5) ✗ Regression detected"
2. Dokumentiere in der README wie man Schliff mit /loop kombiniert:
   ```
   /loop schliff verify && schliff fix --auto
   ```
3. Das ermöglicht: /loop macht den autonomen Loop, Schliff macht das deterministische Scoring und Verification

CONSTRAINTS:
- Muss als einfacher CLI-Aufruf funktionieren (kein Daemon, kein Server)
- Score-History in einer lokalen JSON-Datei persistieren
- Bestehende Architektur-Patterns folgen
```

---

## Phase 4: Vergleichs-Benchmark (Tag 2, Vormittag)

### Prompt 6 — Anti-Gaming Benchmark erstellen

```
Erstelle ein Benchmark-Verzeichnis `benchmarks/anti-gaming/` das Schliffs Anti-Gaming-Detection demonstriert.

KONTEXT: Das ist der stärkste Differentiator. Dokumentierte Fälle aus der Community:
- User berichten dass autoresearch "fake improvements" produziert durch cached metadata
- LLM-only Ansätze können Training-Dynamics manipulieren ohne die Eval zu ändern
- Karpathys Original hat bewusst die Constraint "Agent kann Eval-Metrik nicht editieren" — aber indirekte Gaming-Vektoren bleiben

IMPLEMENTIERUNG:
1. Erstelle 5-8 synthetische Test-Skills in `benchmarks/anti-gaming/skills/`:
   - Ein Skill der seinen eigenen Test mockt (fake green tests)
   - Ein Skill mit aufgeblähtem Docstring der Readability-Score inflated
   - Ein Skill der unused imports hinzufügt um Lines-of-Code zu inflaten
   - Ein Skill mit copy-paste Code der Structure-Score senken sollte
   - Ein Skill mit hardcoded Secrets (Security-Dimension)
2. Erstelle `benchmarks/anti-gaming/run.py`:
   - Lässt `schliff score` auf jeden Skill laufen
   - Zeigt wo Schliff die Contradictions/Gaming erkennt
   - Gibt einen Markdown-Report aus
3. Erstelle `benchmarks/anti-gaming/README.md`:
   - Erklärt das Problem (mit Zitaten aus der Community)
   - Zeigt Schliffs Detection-Ergebnisse
   - Vergleicht konzeptionell mit single-metric Ansätzen

Das wird der Show HN Begleitcontent.
```

---

## Phase 5: Distribution vorbereiten (Tag 2, Nachmittag)

### Prompt 7 — awesome-list und Registry Submissions vorbereiten

```
Erstelle ein Verzeichnis `.github/submissions/` mit vorbereiteten Texten für Community-Listings:

1. `.github/submissions/awesome-autoresearch.md`:
   - Fertig formatierter Eintrag für https://github.com/alvinunreal/awesome-autoresearch
   - Kategorie: "General-Purpose Descendants" oder neue Kategorie "Scoring & Verification"
   - Format: `- [Schliff](https://github.com/Zandereins/schliff) - Deterministic skill linter with 7-dimension scoring, anti-gaming detection, and cross-session memory. 60-70% rule-based patches. Zero external dependencies. (MIT)`

2. `.github/submissions/awesome-claude-code-skills.md`:
   - Eintrag für relevante awesome-claude-code Listen
   - Gleicher Stil, angepasst an jeweiliges Format

3. `.github/submissions/show-hn.md`:
   - Vorbereiter Show HN Post:
   - Title: "Show HN: Schliff – Deterministic linter for Claude Code skills (anti-gaming scoring)"
   - Body: 4-5 Absätze — Problem, Lösung, Ergebnisse, Link, Ask
   - Erwähne die Community-Probleme mit reward hacking als Motivation
   - Verlinke den Anti-Gaming Benchmark

4. `.github/submissions/skillsllm.md`:
   - Eintrag für https://skillsllm.com
   - Alle relevanten Metadaten

Schreibe alle Texte auf Englisch, knapp, technisch, ohne Marketing-Fluff.
```

---

### Prompt 8 — GitHub Repo Metadata optimieren

```
Optimiere die GitHub Repository-Einstellungen für maximale Discoverability:

1. Stelle sicher dass folgende GitHub Topics gesetzt sind (in der repo description oder README):
   claude-code, skill, autoresearch, linter, scoring, deterministic, autonomous, code-quality, ai-agent

2. Prüfe ob eine GitHub Description gesetzt ist. Falls nicht, schlage vor:
   "Deterministic skill linter for Claude Code — 7-dimension scoring, anti-gaming detection, 60-70% rule-based patches"

3. Erstelle/aktualisiere `.github/FUNDING.yml` falls gewünscht

4. Prüfe ob Issues und Discussions aktiviert sind

5. Erstelle ein GitHub Issue Template `.github/ISSUE_TEMPLATE/bug_report.md` und `.github/ISSUE_TEMPLATE/feature_request.md` — kurz und standard

6. Stelle sicher dass die LICENSE Datei vorhanden und MIT ist
```

---

## Schnellreferenz — Reihenfolge

| # | Prompt | Zeitbedarf | Priorität |
|---|--------|-----------|-----------|
| 1 | README neu schreiben | 15-20 min | P0 |
| 2 | SKILL.md Discoverability | 5 min | P0 |
| 3 | `schliff init` Command | 30-45 min | P1 |
| 4 | `schliff score` Output | 20-30 min | P0 |
| 5 | /loop Integration | 20-30 min | P1 |
| 6 | Anti-Gaming Benchmark | 30-45 min | P1 |
| 7 | Submission-Texte | 15 min | P1 |
| 8 | Repo Metadata | 10 min | P2 |

**Gesamtaufwand: ~3-4 Stunden Claude Code Arbeit über 2 Tage.**

---

## Wichtige Constraints für alle Prompts

- Zero external Python dependencies beibehalten
- Bestehende Code-Patterns und Architektur respektieren
- Unit Tests für jeden neuen Command/Feature
- Alles auf Englisch (Code, Docs, README)
- Keine Emojis im Code oder Docs
- Atomic Commits mit klaren Messages
