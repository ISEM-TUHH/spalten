---
name: spalten
description: Strukturierte Problemlösung nach der SPALTEN-Methodik (Albers et al., ICED 05) — sieben Module von der Situationsanalyse bis zum Lernen, mit automatischem Informationscheck, modulweise wechselndem Problemlösungsteam und harten Entscheidungs-Gates. Auslöser: /spalten, "spalte das Problem", "SPALTEN-Vorgang", "systematisch durchdenken", "Problem strukturiert lösen", "Alternativen bewerten und entscheiden", "Tragweite analysieren", "Lessons Learned festhalten".
model: inherit
---

# /spalten — Problemlösung nach SPALTEN

## Was dieser Skill ist

SPALTEN (Albers/Burkardt/Meboldt/Saak, ICED 05) zerlegt ein Problem in sieben Module.
Der Skill **arbeitet die Module selbst durch** und holt den Nutzer an definierten
Gates ab. Er ist kein Protokollant und kein Fragebogen.

Ein Problem ist dabei definiert als: *Abweichung zwischen einem beliebig wenig
bekannten Ist-Zustand und einem beliebig vagen Ziel-Zustand, verbunden mit einem
teilweise unbekannten Weg dazwischen.* Alle drei Teile sind Arbeitsgegenstand.

| Modul | Name | Informationsmenge |
|-------|------|-------------------|
| **SA** | Situationsanalyse | steigt |
| **PE** | Problemeingrenzung | sinkt |
| **AL** | Alternative Lösungssuche | steigt |
| **LA** | Lösungsauswahl | sinkt |
| **TA** | Tragweitenanalyse | steigt |
| **EU** | Entscheiden / Umsetzen | sinkt |
| **NL** | Nacharbeiten / Lernen | steigt |

Die Spalte rechts ist das Honigwabenmodell und dient als **Selbstkontrolle**: Wenn
ein Modul die Informationsmenge in die falsche Richtung bewegt, wurde es falsch
bearbeitet. Ein PE-Ergebnis, das länger ist als das SA-Ergebnis, hat nicht
eingegrenzt.

---

## IRON RULES (nicht verhandelbar)

| ID | Regel | Wirkung bei Verstoß |
|----|-------|---------------------|
| **IR-1** | Kein Modul ohne vorangehenden Informationscheck. Jeder IC beginnt mit einer Abfrage der internen Wissensbasis; das Ergebnis wird protokolliert — auch „nichts gefunden". | Modul wird nicht gestartet, IC wird nachgeholt |
| **IR-2** | Kein Weiterarbeiten nach PE ohne bestätigten, **prüfbaren** Zielzustand. | Hartes Gate, Pipeline hält an |
| **IR-3** | Keine Bewertung, bevor mindestens **drei echte Alternativen plus die Null-Variante** vorliegen. | LA verweigert Start, zurück zu AL |
| **IR-4** | Bewertungskriterien werden **vor** der Bewertung offengelegt und gewichtet. | Bewertung wird verworfen und neu gerechnet |
| **IR-5** | Keine real wirksame, schwer umkehrbare Umsetzung ohne EU-Gate. | Umsetzung wird nicht begonnen |
| **IR-6** | Module dürfen übersprungen werden — aber nur mit begründetem, protokolliertem IC-Vermerk. | Übersprung wird rückgängig gemacht |
| **IR-7** | Annahmen werden als Annahmen markiert. Kompetenzlücken, die sich nicht simulieren lassen, werden als PLT-Lücke gemeldet, nicht überspielt. | Ergebnis gilt als unvollständig |
| **IR-8** | NL ist nicht optional. Ohne Rückfluss ins Wissen ist der Vorgang nicht abgeschlossen. | Status bleibt `entschieden`, nicht `abgeschlossen` |

---

## Ablage

Der Skill läuft **ohne jede Vorbedingung**. Ein Wissensspeicher macht ihn besser,
ist aber nicht erforderlich. Ablageort zu Beginn des Laufs in dieser Reihenfolge
bestimmen und im Vorgang festhalten:

| # | Bedingung | Modus | Ziel |
|---|-----------|-------|------|
| 1 | `SPALTEN_ABLAGE` gesetzt | **Konfiguriert** | dieser Pfad |
| 2 | `OBSIDIAN_VAULT_PATH` gesetzt und Pfad existiert | **Vault** | Ordner nach Konvention, siehe unten |
| 3 | sonst | **Projekt** | `./spalten/<slug>/` im Arbeitsverzeichnis |

### Projekt-Modus (Standard)

`./spalten/<slug>/` mit je einer Datei: `vorgang.md`, `pcir.md`, `sa.md` … `nl.md`.
Reine Markdown-Dateien, versionierbar, ohne Abhängigkeiten. Einmalig mitteilen,
dass keine dauerhafte Wissensbasis angebunden ist — der IC stützt sich dann auf
das Arbeitsverzeichnis, Nutzerangaben und Recherche.

### Vault-Modus (Obsidian)

**Zuerst nach einer Konventionsdatei im Vault-Wurzelverzeichnis sehen**
(`_CLAUDE.md`, `CLAUDE.md`, `AGENTS.md`). Existiert eine, sind ihre Folder Map,
Naming Conventions und Frontmatter-Regeln **autoritativ** und haben Vorrang vor
allem, was hier steht. Lässt sich ein Ordner nicht auflösen, wird gefragt — nie ein
neuer Ordnername erfunden.

Zielordner: `SPALTEN_VAULT_ORDNER`, falls gesetzt. Sonst `00 Inbox/`, falls
vorhanden. Sonst `SPALTEN/` im Vault-Wurzelverzeichnis. Der Skill verschiebt
Vorgänge nicht selbst; führt der Vault die Inbox als reinen Durchgang, weist NL
einmal darauf hin, dass der abgeschlossene Vorgang einzusortieren ist.

Ablage flach, gruppiert über einen gemeinsamen Namenspräfix:

| Datei | Inhalt |
|-------|--------|
| `SPALTEN - <Titel>.md` | Vorgang (State, IC-Protokoll, Entscheidungslog) |
| `SPALTEN - <Titel> - PCIR.md` | Ideen- und Informationssammlung |
| `SPALTEN - <Titel> - SA.md` … `- NL.md` | Modulergebnisse |

Dateinamen **ASCII**: keine Umlaute (`Waelzlager`, nicht `Wälzlager`), nur der
einfache Bindestrich, nie Gedankenstrich — sonst bricht die Linkauflösung. Im
Fließtext dagegen immer korrekte Umlaute. Frontmatter der Vorgangsnotiz:
`type: project`, `date`, `updated`, `tags: [project, spalten]`, `ai-first: true`,
`status` (`planning` → `active` → `completed`), dazu `related-*`, wo es trägt.

Schreiben und Suchen über die MCP-Tools des Second-Brain-Plugins
(`obsidian_save_note`, `obsidian_update_note`, `obsidian_search`,
`obsidian_read_note`), falls verfügbar. Sonst direkt als Dateien in dieselben Pfade.

### Artefakte (in allen Modi gleich)

- **`vorgang`** — State-Dokument, siehe Schema unten. Macht den Lauf fortsetzbar.
- **`pcir`** — problemorientierte kontinuierliche Ideen- und Informationssammlung.
  Alles, was unterwegs auffällt, aber gerade nicht ins laufende Modul gehört:
  Einfälle, Randbeobachtungen, offene Fragen, Verdachtsmomente. **AL und TA lesen
  die PCIR ausdrücklich wieder aus.** Ohne diese Sammlung geht genau das verloren,
  was ein Mensch beim Nachdenken nebenbei bemerkt.
- **je Modul ein Ergebnisdokument** (`sa`, `pe`, `al`, `la`, `ta`, `eu`, `nl`).

### Schema `vorgang`

```yaml
---
typ: spalten-vorgang
titel: <Kurztitel des Problems>
slug: <kebab-case>
angelegt: YYYY-MM-DD
status: laufend | entschieden | abgeschlossen | abgebrochen
modulstand: SA | PE | AL | LA | TA | EU | NL
ablage: projekt | vault | konfiguriert
zielzustand:
  formulierung: null
  pruefkriterium: null
  bestaetigt: false
alternativen_anzahl: 0
gewaehlte_loesung: null
uebersprungene_module: []
offene_plt_luecken: []
tags: [spalten]
---
```

Darunter im Fließtext: **IC-Protokoll** als Tabelle
(`| nach Modul | Wissensbasis | Informationslage | Nutzen/Aufwand | Ampel | Folge |`)
und **Entscheidungslog** (was wurde wann an welchem Gate entschieden).

---

## Ablauf

### Start

- `/spalten "<Problem>"` → neuer Vorgang.
- `/spalten` ohne Argument → nach Vorgängen mit Status `laufend` oder `entschieden`
  suchen. Genau einer: fortsetzen ab `modulstand`. Mehrere: zur Auswahl stellen.
  Keiner: nach dem Problem fragen.

Beim Anlegen den Vorgang sofort schreiben, bevor Modul SA startet. Ein Lauf, der
abbricht, muss fortsetzbar sein.

### Modulkette

```
[IC/PLT] → SA → [IC/PLT] → PE → ★GATE → [IC/PLT] → AL → [IC/PLT] → LA → ★GATE
→ [IC/PLT] → TA → [IC/PLT] → EU → ★GATE → Umsetzung → [IC/PLT] → NL
```

★ = hartes Gate, immer sichtbar, nie automatisch passiert.

Jedes Modul wird über seine Datei in `agents/` ausgeführt. Die dort benannten
Rollen werden als **eigenständige Subagenten** gestartet (Agent-Tool), nicht als
Perspektivwechsel im eigenen Kontext — sonst kontaminieren sich die Sichtweisen.
Steht kein Agent-Tool zur Verfügung, werden die Rollen nacheinander abgearbeitet;
dann wird im Vorgang vermerkt, dass die Unabhängigkeit der Rollen eingeschränkt war.

### Kurzläufe

Das Original sieht ausdrücklich Modulübersprünge vor. Typische Fälle:

| Lage | Kette |
|------|-------|
| Ursache in PE eindeutig geklärt, Lösung folgt zwingend | SA → PE → EU → NL |
| Lösungsvorschläge liegen schon auf dem Tisch | SA → PE → LA → TA → EU → NL |
| Ereignisfall („Feuer"), keine Zeit für Vorlauf | PE → AL → LA → EU → NL, SA nachgezogen |
| Nur Nachbereitung eines abgeschlossenen Vorgangs | NL |

Jeder Übersprung braucht einen IC-Vermerk mit Begründung (IR-6).

### Rücksprung

Der Ablauf ist iterativ, nicht linear. An jedem Gate ist **„zurück zu Modul X"**
eine reguläre Option und muss als solche angeboten werden. Ein Rücksprung setzt
`modulstand` zurück und wird im Entscheidungslog vermerkt; die alten
Modulergebnisse bleiben stehen und werden als überholt markiert, nicht gelöscht.

---

## Informationscheck und PLT — nach jedem Modul

Ausführung: `agents/ic_check.md`. Läuft **automatisch**, ohne den Nutzer zu fragen,
und erzeugt eine Ampel. Drei Prüfungen:

1. **Interne Wissensbasis befragt?** (IR-1) Reihenfolge immer:
   **Wissensbasis → Nutzer → Web.** Was die Wissensbasis ist, hängt vom Modus ab —
   im Vault-Modus der Vault, sonst das Arbeitsverzeichnis und frühere Vorgänge.
2. **Reicht die Information** für das nächste Modul?
3. **Nutzen/Aufwand angemessen?** Ist die Detailtiefe im Verhältnis zum erreichbaren
   Nutzen sinnvoll? Welches Modul lässt sich überspringen?

Dazu die **PLT-Besetzung** für das nächste Modul: welche Rollen werden gebraucht,
welche davon lassen sich simulieren — und welche nicht.

| Ampel | Bedeutung | Folge |
|-------|-----------|-------|
| 🟢 | Lage tragfähig | weiter ohne Stopp, IC-Zeile ins Protokoll |
| 🟡 | Lücke, die den nächsten Schritt verzerrt | **Stopp** mit einer konkreten Frage |
| 🔴 | Fehlende Grundlage oder nicht simulierbare Kompetenz | **Stopp**, Vorgang pausiert |

---

## Gate-Format

Ein Gate ist eine Entscheidungsvorlage, keine Rückversicherung. Nie „soll ich
weitermachen?" fragen. Immer diese vier Teile:

1. **Stand** — ein Absatz: was ist erarbeitet, worauf beruht es.
2. **Die Entscheidung** — in einem Satz, was jetzt festgelegt wird und was daraus folgt.
3. **Optionen** — als Auswahl (AskUserQuestion), immer inklusive Rücksprung-Option
   und, wo sinnvoll, der Null-Variante.
4. **Unsicherheiten** — was der Agent nicht wissen kann, und welche PLT-Lücke offen ist.

---

## Agentenverzeichnis

| Datei | Modul | Besetzung |
|-------|-------|-----------|
| `agents/ic_check.md` | zwischen allen Modulen | Informationsprüfer |
| `agents/sa_agent.md` | SA | Rechercheur + Systemanalytiker |
| `agents/pe_agent.md` | PE | Ursachenanalytiker + Zieldefinierer |
| `agents/al_agent.md` | AL | zwei unabhängige Ideengeber + Zusammenführer |
| `agents/la_agent.md` | LA | Bewerter + Advocatus Diaboli |
| `agents/ta_agent.md` | TA | Risiko- und Chancenanalytiker |
| `agents/eu_agent.md` | EU | Umsetzungsplaner |
| `agents/nl_agent.md` | NL | Auswerter |

Methoden je Modul: `references/methodenkoffer.md`. Die Werkzeuge sind pragmatisch
einzusetzen, nicht dogmatisch — nur so viel Methode, wie das Problem trägt.
