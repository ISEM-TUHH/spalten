# PE — Problemeingrenzung

**Auftrag:** Aus der Fülle der Situationsanalyse das herausfiltern, was das Problem
tatsächlich ausmacht. Ursache und Wirkung der Abweichung bestimmen, den Zielzustand
scharf formulieren. Ergebnis ist ein **hartes Gate**.

**Informationsmenge: sinkt.** Wenn dieses Dokument länger wird als `sa`, wurde nicht
eingegrenzt, sondern weitergesammelt.

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Ursachenanalytiker** | Bildet Hypothesen zur Ursache der Abweichung und prüft sie an den Fakten aus SA. Arbeitet destruktiv: sucht das Gegenbeispiel zur eigenen Hypothese. |
| **Zieldefinierer** | Formuliert den Zielzustand — abstrakt genug, um keine Lösung vorwegzunehmen, konkret genug, um prüfbar zu sein. |

## Vorgehen

### 1. Ist / Nicht-Ist / Ziel

Die Abweichung wird durch Abgrenzung schärfer. Für jede Dimension eintragen, **wo
das Problem auftritt und wo es ausdrücklich nicht auftritt**:

| Dimension | Ist (tritt auf) | Nicht-Ist (tritt nicht auf) |
|-----------|-----------------|------------------------------|
| Was | | |
| Wo | | |
| Wann / seit wann | | |
| Bei wem / womit | | |
| Wie stark / wie oft | | |

Die Nicht-Ist-Spalte ist der eigentliche Erkenntnisgewinn: Was unterscheidet die
Fälle, in denen das Problem auftritt, von denen, in denen es ausbleibt?

### 2. Ursachenhypothesen

Aus dem Unterschied Ist ↔ Nicht-Ist Hypothesen ableiten. Werkzeuge: 5-Why,
Ishikawa, Issue Tree (`references/methodenkoffer.md`).

Jede Hypothese bekommt einen **Prüfweg**: Faktenlage, Simulation, Experiment,
Rückfrage. Eine unbelegte Hypothese wird als unbelegt gekennzeichnet und nicht
zur Grundlage des Zielzustands gemacht.

### 3. Zielzustand

Zwei Teile, beide Pflicht:

- **Formulierung** — was soll gelten, wenn das Problem gelöst ist? Lösungsneutral.
  Falsch: „Skript X umschreiben". Richtig: „Der Vorgang läuft ohne manuelle
  Nacharbeit durch."
- **Prüfkriterium** — woran wird das später gemessen? Ohne prüfbares Kriterium
  kein Weiterarbeiten (IR-2). Wo sich nicht messen lässt, mindestens ein
  beobachtbares Ereignis benennen.

### 4. Weichenstellung

Explizit entscheiden, wie es weitergeht:

- Ursache eindeutig und Lösung folgt zwingend → AL und LA überspringen (IR-6)
- Lösungen liegen bereits vor → AL überspringen
- Ursache liegt außerhalb des eigenen Einflussbereichs (Lieferant, andere Stelle) →
  Problem übergeben statt lösen; das ist ein legitimes Ergebnis
- Problem lohnt den Aufwand nicht → Vorgang beenden

## Ausgang — Dokument `pe`

```markdown
## Ist / Nicht-Ist
(Tabelle)

## Ursachenhypothesen
| Hypothese | Beleg | Status: belegt / offen / widerlegt |

## Zielzustand
Formulierung: …
Prüfkriterium: …

## Weichenstellung
Empfohlener weiterer Lauf: … (Begründung)
```

## ★ Hartes Gate

Vorlage nach dem Gate-Format aus SKILL.md. Zur Entscheidung stehen:

- Zielzustand **so bestätigen** → weiter
- Zielzustand **anders fassen** → Nutzer formuliert um, PE aktualisieren
- **zurück zu SA** — die Faktenlage trägt die Eingrenzung nicht
- **Vorgang beenden** — Aufwand lohnt nicht, oder Problem gehört woandershin

Nach Bestätigung `zielzustand.bestaetigt: true` in `vorgang` setzen. Erst dann
darf AL starten.
