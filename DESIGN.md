# Designentscheidungen

Der Skill wurde selbst nach SPALTEN gebaut. Dieses Dokument ist das Ergebnis von
SA/PE/AL/LA und hält fest, **was entschieden wurde, warum, und was dafür verworfen
wurde** — damit spätere Änderungen nicht Wege wiederholen, die schon einmal
begangen und verlassen wurden.

## Quellen

- **Albers, A.; Burkardt, N.; Meboldt, M.; Saak, M.:** *SPALTEN Problem Solving
  Methodology in the Product Development.* International Conference on Engineering
  Design (ICED 05), Melbourne 2005.
  Übernommen: Problemdefinition (Ist/Ziel/Weg), sieben Module, Honigwabenmodell,
  Informationscheck, modulweise Besetzung des Problemlösungsteams, PCIR,
  ausdrückliche Erlaubnis zum Modulübersprung, iterativer statt linearer Ablauf.
- **consulting-life.de, *SPALTEN-Methode*:** pragmatische Werkzeugzuordnung je
  Schritt → Grundlage von `references/methodenkoffer.md`.
- **Human-in-the-Loop-Praxis 2026** (u. a. Human Gate Designer, HITL Governance,
  pattern-stack/claudecode-patterns, Towards Data Science): designte Gates statt
  Tool-Prompts, Gates nur an Entscheidungspunkten, keine Fragen mit offensichtlicher
  Antwort, Selbst-Eskalation bei steigender Unsicherheit, resume-fähiger Checkpoint.

Der Befund aus der Gegenüberstellung ist der eigentliche Grund für diesen Skill:
Der IC/PLT-Rhythmus von 2005 ist praktisch deckungsgleich mit dem, was die
HITL-Literatur 2026 als gutes Gate-Design beschreibt. Der einzige Unterschied liegt
in der Gate-Dichte — daher der adaptive Informationscheck.

## Entscheidungen

| # | Entscheidung | Begründung | Verworfen |
|---|--------------|------------|-----------|
| 1 | **Löser mit Gates**, nicht Moderator | Der Skill soll Denkarbeit leisten, nicht abfragen | Moderator, reiner Dokumentierer, Modus-Schalter |
| 2 | **Universell** einsetzbar | Wie im Original: jede Domäne, jede Komplexität | Zuschnitt auf Produktentwicklung, Organisation oder Software |
| 3 | **Adaptiver IC**, drei harte Gates (PE, LA, EU) | Der IC nach jedem Modul erhält das Alleinstellungsmerkmal der Methodik; ein sichtbarer Stopp nur bei Gelb/Rot vermeidet Gate-Müdigkeit und Blind-Bestätigung | 7 sichtbare Gates, nur 3 Gates, wählbare Eingriffstiefe |
| 4 | **PLT als getrennte Subagenten**, zusätzlich Meldung nicht simulierbarer Kompetenz | Echte Perspektivenvielfalt; Denkbrillen im selben Kontext kontaminieren sich gegenseitig | Perspektivwechsel im eigenen Kontext, reine Personenempfehlung |
| 5 | **Wissensspeicher optional**, Projektverzeichnis als Standard | Der IC soll zuerst fragen, was schon bekannt ist. Wo ein Vault existiert, ist er die beste Quelle; ohne ihn treten Arbeitsverzeichnis, `git log` und frühere Läufe an seine Stelle. Der Skill läuft ohne jede Vorbedingung. | Vault als Pflicht, reine Konversation ohne Persistenz |
| 6 | **Ein Command `/spalten`** | Modulübersprünge entscheidet der IC ohnehin selbst; das Fortsetzen läuft über den State | Modul-Einstiege, ein Command je Modul, gar kein Command |
| 7 | **Zwei Ideengeber in AL** statt drei | Aufwand; zwei unabhängige Techniken (Übertragung, Variation) decken die Bandbreite ausreichend ab | Drei oder mehr Ideengeber |
| 8 | **NL schreibt automatisch** und bittet danach um Rückmeldung | Der Rückfluss ins Wissen darf nicht an einer Bestätigung scheitern. Eine Korrektur ist billiger als das Vergessen. | Vorlegen und erst nach Freigabe speichern |

## Bewusst nicht gebaut (YAGNI)

Zweiter Betriebsmodus, Slash-Commands je Modul, Domänenspezialisierung,
Anbindung an Projekt- oder Kanban-Werkzeuge in EU, Zeitlimits auf Gates.
Alles nachrüstbar, sobald ein realer Lauf zeigt, dass es fehlt.

## Offene Prüfpunkte für die Nachbereitung

- Feuert der adaptive IC in der Praxis zu selten (dann rutschen Fehler durch) oder
  zu oft (dann ist er nur ein verkleidetes Pflicht-Gate)?
- Liefern zwei Ideengeber genug echte Varianz, oder ähneln sich ihre Vorschläge?
- Wird die PCIR tatsächlich in AL und TA ausgewertet, oder verkommt sie zur Ablage?
- Sind die Erkenntnisse aus NL beim nächsten Vorgang im IC wiederauffindbar?
- Reicht der Wissensbasis-Ersatz im Projekt-Modus (`git log`, `docs/`, frühere
  Läufe) an den Nutzen eines gepflegten Vaults heran — und wenn nicht, woran liegt es?
