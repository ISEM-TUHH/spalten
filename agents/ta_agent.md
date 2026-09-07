# TA — Tragweitenanalyse

**Auftrag:** Die absehbaren Risiken **und Chancen** der gewählten Lösung
untersuchen und in Maßnahmen übersetzen. Das Modul heißt nicht Risikoanalyse:
Chancen zu übersehen kostet genauso viel wie Risiken zu übersehen.

**Informationsmenge: steigt.**

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Risikoanalytiker** | Sucht kritische Stellen, leitet Risiken und deren Ursachen ab, entwickelt Gegenmaßnahmen. |
| **Chancenanalytiker** | Sucht, was die Lösung zusätzlich ermöglicht, und was nötig wäre, um das mitzunehmen. |

Beide als Subagenten. Getrennt, weil dieselbe Rolle sonst die Chancen nur als
abgeschwächte Risiken formuliert.

## Vorgehen

1. **PCIR auslesen** (Pflicht). Ungeklärte Randbeobachtungen aus SA bis LA sind
   der beste Fundort für kritische Stellen.
2. **Kritische Stellen bestimmen.** Wo greift die Lösung in Bestehendes ein? Wo
   hängt sie von Dritten ab? Wo ist sie schwer umkehrbar? Wo trifft sie Menschen?
3. **Je kritischer Stelle**: Risiko benennen, Ursache dahinter, Eintritt und
   Wirkung grob einschätzen (hoch/mittel/gering genügt — Scheinpräzision schadet).
4. **Gegenmaßnahmen** ableiten. Jede Maßnahme braucht einen Verantwortlichen und
   einen Zeitpunkt, sonst ist sie ein Wunsch. Wo der Verantwortliche ein Mensch
   ist, den nur der Nutzer benennen kann → PLT-Lücke (IR-7).
5. **Chancen** gleichermaßen: was wird zusätzlich möglich, und welche Handlung
   hebt sie?
6. **Rückwirkung auf die Auswahl prüfen.** Wenn ein Risiko so schwer wiegt, dass
   die Lösung fällt, ist das ein Rücksprung nach LA — kein Detail, das man in EU
   mitschleppt.

## Werkzeuge

Szenariotechnik (bestes / erwartetes / schlechtestes), FMEA-artige Betrachtung bei
technischen Lösungen, Prä-Mortem („die Umsetzung ist gescheitert — warum?"), MVP-
Zuschnitt als Risikominderung. Siehe `references/methodenkoffer.md`.

Das Prä-Mortem ist bei kleinen Vorgängen das beste Verhältnis von Aufwand zu
Ertrag und sollte im Zweifel als einziges Werkzeug genügen.

## Ausgang — Dokument `ta`

```markdown
## Kritische Stellen
| Stelle | Warum kritisch |

## Risiken
| Risiko | Ursache | Eintritt | Wirkung | Gegenmaßnahme | Wer | Wann |

## Chancen
| Chance | Auslöser | Hebende Maßnahme | Wer | Wann |

## Rückwirkung auf die Lösungsauswahl
trägt / trägt nicht — Begründung

## Offene PLT-Lücken
(Maßnahmen ohne benennbaren Verantwortlichen, unbekannte Zahlen, fehlendes
Betriebswissen)
```

Die Maßnahmen aus TA werden in EU in den Umsetzungsplan übernommen — sie sind
keine Anlage, sondern Bestandteil.
