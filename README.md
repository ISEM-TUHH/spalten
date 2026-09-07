# SPALTEN — Skill für Claude Code

[![Lizenz: MIT](https://img.shields.io/badge/Lizenz-MIT-blue.svg)](LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-8A63D2)](https://docs.claude.com/en/docs/claude-code/skills)
[![Sprache: Deutsch](https://img.shields.io/badge/Sprache-Deutsch-informational)](#)
[![Methodik: ICED 05](https://img.shields.io/badge/Methodik-Albers%20et%20al.%2C%20ICED%2005-004488)](#quellen)

**Strukturierte Problemlösung in sieben Modulen — mit Gates, an denen ein Mensch entscheidet.**

`/spalten` bringt die SPALTEN-Methodik von Albers et al. (KIT, ICED 05) nach Claude
Code. Der Skill arbeitet das Problem selbst durch, hält aber an den Stellen an, an
denen eine Entscheidung fällt, statt sich durchzuwinken.

---

## Warum

Die üblichen Antworten auf ein Problem sind zwei schlechte Extreme. Entweder der
Agent löst sofort los und liefert die erstbeste Lösung, ohne je die Ursache
angesehen zu haben. Oder er fragt bei jedem Schritt nach und schiebt die Denkarbeit
zurück zum Menschen.

SPALTEN löst das seit 2005 — mit einem Mechanismus, den die Human-in-the-Loop-
Literatur zwanzig Jahre später unabhängig noch einmal gefunden hat: einem
**Informationscheck zwischen je zwei Arbeitsschritten**, der prüft, ob die Grundlage
trägt und ob der Aufwand den Nutzen noch rechtfertigt. Genau dieser Check ist hier
die Gate-Logik.

## Die sieben Module

| Modul | Name | Was passiert | Informationsmenge |
|-------|------|--------------|-------------------|
| **SA** | Situationsanalyse | Lage erfassen, Systemgrenze ziehen, Fakten nach Herkunft trennen | steigt |
| **PE** | Problemeingrenzung | Ist / Nicht-Ist, Ursachenhypothesen, **prüfbarer Zielzustand** | sinkt |
| **AL** | Alternative Lösungssuche | zwei unabhängige Ideengeber, Pflicht zur Null-Variante | steigt |
| **LA** | Lösungsauswahl | Kriterien vorab, Nutzwertanalyse, Advocatus Diaboli | sinkt |
| **TA** | Tragweitenanalyse | Risiken **und** Chancen, jeweils mit Maßnahme | steigt |
| **EU** | Entscheiden / Umsetzen | FOR-DEC, Plan, Durchführung, Abschluss am Prüfkriterium | sinkt |
| **NL** | Nacharbeiten / Lernen | Zielabgleich, übertragbare Erkenntnisse, Rückfluss ins Wissen | steigt |

Die rechte Spalte ist das **Honigwabenmodell** und dient als Selbstkontrolle: Ein
PE-Ergebnis, das länger ausfällt als das SA-Ergebnis, hat nicht eingegrenzt,
sondern weitergesammelt.

## Was den Skill von einem Prompt unterscheidet

**Der Informationscheck läuft nach jedem Modul — hält aber nur an, wenn nötig.**
Er prüft dreierlei: Wurde die vorhandene Wissensbasis befragt? Reicht die
Information für den nächsten Schritt? Steht der Aufwand noch im Verhältnis zum
Nutzen? Grün heißt weiter, Gelb und Rot heißen Stopp mit einer *konkreten* Frage —
nie mit „soll ich weitermachen?".

**Die Reihenfolge der Quellen ist bindend: Wissensbasis → Nutzer → Web.** Der Skill
stellt keine Frage, deren Antwort er selbst hätte finden können. Was er gefunden
hat, protokolliert er — auch das „nichts gefunden", damit der nächste Lauf nicht
zweimal sucht.

**Das Problemlösungsteam wechselt modulweise und läuft als echte Subagenten.** In
AL arbeiten zwei voneinander abgeschottete Ideengeber mit verschiedenen Techniken;
in LA greift ein Advocatus Diaboli die fertige Bewertung an, ohne die Begründung
des Bewerters zu kennen. Perspektiven im selben Kontext kontaminieren sich —
getrennte Agenten tun das nicht.

**Was sich nicht simulieren lässt, wird gemeldet statt erfunden.** Betriebswissen,
Rechtsfragen, Zahlen, die niemand erhoben hat, Entscheidungen, die einer bestimmten
Person zustehen: solche Lücken landen als PLT-Lücke im Vorgang und werden am Gate
ausgesprochen — nicht durch eine plausible Annahme ersetzt.

**Der Vorgang ist fortsetzbar.** Jeder Lauf schreibt ein State-Dokument, bevor das
erste Modul startet. `/spalten` ohne Argument findet offene Vorgänge und macht
dort weiter, wo abgebrochen wurde.

## Installation

Voraussetzung: [Claude Code](https://claude.com/claude-code). Sonst nichts.

```bash
git clone https://github.com/ISEM-TUHH/spalten.git ~/.claude/skills/spalten
```

Unter Windows (PowerShell):

```powershell
git clone https://github.com/ISEM-TUHH/spalten.git "$env:USERPROFILE\.claude\skills\spalten"
```

Für einen einzelnen Arbeitsbereich statt global: nach `.claude/skills/spalten`
im Projekt klonen. Claude Code lädt den Skill beim nächsten Start.

## Benutzung

```
/spalten "Der nächtliche Import bricht seit zwei Wochen unregelmäßig ab"
/spalten                 # offenen Vorgang fortsetzen
```

Der Skill entscheidet selbst, welche Module das Problem braucht. Steht die Ursache
nach PE fest, überspringt er die Lösungssuche. Liegen die Lösungsvorschläge schon
auf dem Tisch, beginnt er bei der Bewertung. Jeder Übersprung wird begründet und
protokolliert.

## Wo die Ergebnisse landen

Der Ablageort wird zu Beginn bestimmt:

| Bedingung | Modus | Ziel |
|-----------|-------|------|
| `SPALTEN_ABLAGE` gesetzt | konfiguriert | dieser Pfad |
| `OBSIDIAN_VAULT_PATH` gesetzt und vorhanden | Vault | Ordner nach den Konventionen des Vaults |
| sonst | **Projekt (Standard)** | `./spalten/<slug>/` |

Drei Artefakte, in jedem Modus gleich:

- **Vorgang** — State, IC-Protokoll, Entscheidungslog. Macht den Lauf fortsetzbar.
- **PCIR** — die kontinuierliche Ideen- und Informationssammlung aus dem Original:
  alles, was unterwegs auffällt, aber gerade nicht ins laufende Modul gehört.
  AL und TA lesen sie verpflichtend wieder aus. Ohne sie geht genau das verloren,
  was ein Mensch beim Nachdenken nebenbei bemerkt.
- **je Modul ein Ergebnisdokument.**

### Konfiguration

| Variable | Wirkung | Standard |
|----------|---------|----------|
| `SPALTEN_ABLAGE` | erzwingt einen Ablagepfad | — |
| `OBSIDIAN_VAULT_PATH` | aktiviert den Vault-Modus | — |
| `SPALTEN_VAULT_ORDNER` | Zielordner im Vault | `00 Inbox/`, sonst `SPALTEN/` |

Im Vault-Modus liest der Skill zuerst die Konventionsdatei des Vaults
(`_CLAUDE.md`, `CLAUDE.md`, `AGENTS.md`). Deren Folder Map und Namensregeln haben
Vorrang; ein nicht auflösbarer Ordner wird erfragt, nie erfunden.

## Die harten Regeln

Acht Regeln, die der Skill nicht verhandelt. Die vier wichtigsten:

- **Kein Weiterarbeiten ohne prüfbaren Zielzustand.** Ohne Kriterium kann am Ende
  niemand sagen, ob es funktioniert hat.
- **Keine Bewertung vor drei echten Alternativen plus Null-Variante.** Schutz gegen
  Frühfixierung auf die erstbeste Idee.
- **Bewertungskriterien werden vor der Bewertung offengelegt und gewichtet.** Wer
  gewichtet, entscheidet — also gehört die Gewichtung auf den Tisch, nicht ins
  Kleingedruckte.
- **Keine schwer umkehrbare Umsetzung ohne Gate.** Entwürfe und lokale Änderungen
  laufen durch; alles, was nach außen wirkt, wartet auf eine Entscheidung.

Die vollständige Liste steht in [`SKILL.md`](SKILL.md).

## Aufbau

```
SKILL.md                      Routing, IRON RULES, Ablage, Modulkette, Gate-Format
agents/ic_check.md            Informationscheck + Teambesetzung
agents/sa_agent.md … nl_agent.md
references/methodenkoffer.md  Werkzeuge je Modul, mit „nimm, wenn"-Spalte
DESIGN.md                     Designentscheidungen samt Verworfenem
```

## Quellen

- Albers, Albert; Burkardt, Norbert; Meboldt, Mirko; Saak, Marcus: *SPALTEN Problem
  Solving Methodology in the Product Development.* In: Samuel, A.; Lewis, W. (Hrsg.):
  DS 35 — Proceedings of ICED 05, the 15th International Conference on Engineering
  Design, Melbourne, 15.–18.08.2005, S. 553–554 (Executive Summary; Volltext auf dem
  Konferenzmedium als `DS35_317.49`).
  [Design Society](https://www.designsociety.org/publication/23010/spalten_problem_solving_methodology_in_the_product_development)
- [SPALTEN-Methode — consulting-life.de](https://www.consulting-life.de/spalten-methode/):
  Werkzeugzuordnung je Schritt.

Die Methodik stammt vom IPEK — Institut für Produktentwicklung, zur Zeit der
Veröffentlichung an der Universität Karlsruhe (TH), heute Teil des KIT. Dieser Skill
ist eine eigenständige Umsetzung für Claude Code und steht in keiner Verbindung zum
KIT.

## Mitwirken

Fehlerberichte und Vorschläge über die
[Issues](https://github.com/ISEM-TUHH/spalten/issues), Änderungen über Pull Requests —
siehe [CONTRIBUTING.md](CONTRIBUTING.md). Der Skill besteht ausschließlich aus
Prosa: wer eine Regel ändert, sollte sagen können, welcher reale Fehllauf sie
nötig gemacht hat.

## Lizenz

[MIT](LICENSE) © Felix Förster
