# Informationscheck (IC) + Problemlösungsteam (PLT)

Läuft **zwischen je zwei Modulen**, automatisch, ohne Rückfrage. Erzeugt eine
Ampel und eine Protokollzeile. Nur bei 🟡/🔴 wird der Nutzer angehalten.

Dieser Check ist das Herz von SPALTEN. Er verhindert zwei Fehler: mit zu dünner
Grundlage weiterzurennen, und mit zu viel Aufwand an einem Problem zu arbeiten,
dessen Nutzen den Aufwand nicht trägt.

---

## Prüfung 1 — Interne Wissensbasis (IR-1, Pflicht)

**Reihenfolge ist bindend: Wissensbasis → Nutzer → Web.** Erst wenn die
Wissensbasis ausgeschöpft ist, wird der Nutzer gefragt; erst danach wird recherchiert.
Nie eine Frage stellen, deren Antwort auffindbar gewesen wäre.

Gesucht wird immer nach dreierlei:

- **Sachwissen** zum Problemfeld (was ist über System, Beteiligte, Zahlen bekannt?)
- **Vorgeschichte** (gab es diesen Vorgang oder einen ähnlichen schon einmal?
  Wurde etwas versucht, das gescheitert ist?)
- **Lessons Learned** aus früheren SPALTEN-Vorgängen

Wo die Wissensbasis liegt, hängt vom Ablagemodus ab:

| Modus | Wissensbasis | Vorgehen |
|-------|--------------|----------|
| **Vault** | der Obsidian-Vault | `obsidian_search` mit den Kernbegriffen von Problem und nächstem Modul; ohne MCP-Tools per Grep/Glob über den Vault-Pfad. Frühere Vorgänge über `tags: [spalten]`. |
| **Projekt / konfiguriert** | das Arbeitsverzeichnis | `README`, `docs/`, `CHANGELOG`, Architektur- und Entscheidungsnotizen, `git log`/`git blame` zur Vorgeschichte, sowie frühere Läufe unter `spalten/*/`. Bei Code-Problemen zusätzlich Tests, Issues und Logs. |

Gefundenes wird **gelesen und in das Modulergebnis eingearbeitet**, nicht nur
verlinkt. Das Ergebnis wird **immer** protokolliert, auch wenn es leer ist. Ein
„nichts gefunden" ist ein Befund, keine Auslassung — es sagt dem nächsten IC, dass
hier nicht noch einmal gesucht werden muss.

## Prüfung 2 — Informationslage

Reicht das Vorhandene für das nächste Modul?

| Nächstes Modul | Braucht mindestens |
|----------------|--------------------|
| SA | Problemnennung und wer betroffen ist |
| PE | Ist-Zustand, Beteiligte, Randbedingungen |
| AL | bestätigter Zielzustand mit Prüfkriterium |
| LA | ≥3 Alternativen + Null-Variante (IR-3) |
| TA | gewählte Lösung |
| EU | Risiken mit Gegenmaßnahmen |
| NL | dokumentierter Verlauf und Ergebnis |

Fehlt etwas davon → 🟡 oder 🔴.

## Prüfung 3 — Nutzen/Aufwand

Zwei Fragen:

- Steht die Detailtiefe im Verhältnis zum erreichbaren Nutzen? Ein Problem, dessen
  Schaden bei einer Stunde Arbeit liegt, rechtfertigt keinen dreistündigen Vorgang.
- **Lässt sich ein Modul überspringen?** Wenn ja: welches, und warum (IR-6). Die
  Begründung gehört ins Protokoll, nicht in eine Nutzerfrage.

## Prüfung 4 — PLT-Besetzung

Welche Rollen braucht das nächste Modul? Die Regelbesetzung steht in der jeweiligen
Agentendatei; sie ist ein Vorschlag, kein Zwang. Wenn das konkrete Problem eine
andere Kompetenz verlangt, wird umbesetzt.

Entscheidend ist die zweite Frage: **welche gebrauchte Kompetenz lässt sich nicht
simulieren?** Dazu gehören

- Betriebswissen („wie läuft das bei uns wirklich")
- Rechts-, Vertrags-, Personalfragen mit realen Folgen
- alles, was nur eine bestimmte Person weiß oder entscheiden darf
- Zahlen, Messwerte, Systemzustände, die niemand erhoben hat

Solche Lücken werden in `offene_plt_luecken` eingetragen und am nächsten Gate
ausdrücklich benannt (IR-7). Sie werden **nicht** durch plausible Annahmen
ersetzt. Eine Annahme darf getroffen werden, muss aber als solche markiert sein.

---

## Ampel

| Ampel | Kriterium | Folge |
|-------|-----------|-------|
| 🟢 | Alle vier Prüfungen tragen | weiter ohne Stopp |
| 🟡 | Eine Lücke, die das nächste Modul verzerrt, aber vom Nutzer schnell zu schließen ist | **Stopp** mit *einer* konkreten Frage |
| 🔴 | Grundlage fehlt, oder eine nicht simulierbare Kompetenz blockiert | **Stopp**, Vorgang auf `laufend` pausieren, Weg zur Klärung benennen |

Bei 🟡/🔴 gilt dieselbe Regel wie am Gate: nie „soll ich weitermachen?", sondern
die fehlende Information konkret erfragen. Ist die Frage beantwortet, IC
wiederholen.

## Protokollzeile

In `vorgang` anhängen:

```
| nach SA | Vault: 3 Treffer (Projektnotiz X, Person Y) | vollständig | angemessen | 🟢 | weiter zu PE |
| nach PE | Repo: README + 2 ADR, git log seit 04/26 | Zielkriterium fehlt | angemessen | 🟡 | Rückfrage Prüfkriterium |
```
