# SA — Situationsanalyse

**Auftrag:** Die Lage erfassen und aufschließen. Daten sammeln, ordnen,
dokumentieren. Am Ende steht ein belastbares Bild des Ist-Zustands — noch keine
Ursache, noch kein Ziel, noch keine Lösung.

**Informationsmenge: steigt.** Dieses Modul darf breit sein.

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Rechercheur** | Trägt zusammen, was schon bekannt ist: Wissensbasis, vorhandene Dokumente, Repos, Daten, Nutzerangaben. Fragt nicht nach dem, was er selbst finden kann. |
| **Systemanalytiker** | Ordnet den Rohbestand: Systemgrenze, Beteiligte, Wirkzusammenhänge, Randbedingungen, Ressourcen. |

Beide als Subagenten starten, parallel. Der Rechercheur liefert Material, der
Systemanalytiker strukturiert es.

## Vorgehen

1. **Systemgrenze ziehen.** Was gehört zum Problem, was ausdrücklich nicht?
   Die Nicht-Zugehörigkeit explizit notieren — sie wird in PE gebraucht.
2. **Fakten sammeln**, getrennt nach Herkunft: gemessen / dokumentiert / berichtet /
   vermutet. Diese Kennzeichnung nie weglassen (IR-7).
3. **Beteiligte und Betroffene** benennen: wer verursacht, wer leidet, wer
   entscheidet, wer muss mitziehen.
4. **Randbedingungen und Ressourcen**: Zeit, Geld, Personen, Technik, Regeln,
   Verträge. Auch: wie viel Aufwand rechtfertigt dieses Problem überhaupt?
5. **Erste Einschätzung der Problemart**: einmaliges Ereignis oder wiederkehrendes
   Muster? Geplant angegangen oder Feuerwehr? Das bestimmt den weiteren Lauf
   (siehe Kurzläufe in SKILL.md).

## Werkzeuge

Desk Research, Interviewfragen an den Nutzer, Gap-Analyse (Ist ↔ grobe Erwartung),
SWOT wenn strategisch, Systemskizze wenn technisch. Siehe
`references/methodenkoffer.md`.

## Ausgang — Dokument `sa`

```markdown
## Systemgrenze
Dazu gehört: … | Ausdrücklich nicht: …

## Ist-Zustand
(Fakten, je mit Herkunft: gemessen / dokumentiert / berichtet / vermutet)

## Beteiligte und Betroffene
| Wer | Rolle | Interesse |

## Randbedingungen und Ressourcen

## Problemart
Ereignis / Muster · Geplant / Feuerwehr · vertretbarer Aufwand: …

## Auffälligkeiten
(alles, was noch nicht eingeordnet ist → zusätzlich in die PCIR)
```

## Abbruchbedingungen

- Das „Problem" ist in Wahrheit eine Aufgabe mit bekanntem Weg → dem Nutzer sagen,
  Vorgang mit Status `abgebrochen` schließen, Begründung notieren. SPALTEN kostet
  mehr, als es hier einbrächte.
- Der Ist-Zustand lässt sich mit vertretbarem Aufwand nicht ermitteln → 🔴 im IC,
  benennen, welche Erhebung fehlt.
