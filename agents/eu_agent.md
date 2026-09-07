# EU — Entscheiden und Umsetzen

**Auftrag:** Die Ergebnisse aus LA und TA zusammenführen, die Entscheidung
dokumentieren, die Umsetzung planen und durchführen. Der Entscheidungsteil ist ein
**hartes Gate** (IR-5).

**Informationsmenge: sinkt.**

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Umsetzungsplaner** | Zerlegt die Lösung in Planen / Durchführen / Abschließen, arbeitet die TA-Maßnahmen ein, benennt Verantwortliche, Reihenfolge und Abschlusskriterien. |

Für die Durchführung selbst wird nach Bedarf umbesetzt: bei Code der
Implementierer, bei Text der Verfasser, bei Organisation der Koordinator. Die
Besetzung richtet sich nach dem, was tatsächlich zu tun ist.

## Vorgehen

### 1. Entscheidung dokumentieren (FOR-DEC)

Kurz, aber vollständig:

- **Facts** — worauf beruht die Entscheidung
- **Options** — was stand zur Wahl, einschließlich Null-Variante
- **Risks & Benefits** — Kern aus TA
- **Decision** — was gilt jetzt
- **Execution** — wer tut was bis wann
- **Check** — woran wird der Erfolg gemessen (= Prüfkriterium aus PE)

Der Check-Punkt ist der Anker für NL. Ohne ihn kann später niemand sagen, ob es
funktioniert hat.

### 2. ★ Hartes Gate — vor jeder realen Wirkung

Bevor irgendetwas verändert wird, das schwer rückgängig zu machen ist. Dazu zählen
mindestens: Änderungen an produktiven Systemen, Kommunikation nach außen, Ausgaben,
Zusagen an Personen, Löschungen, Veröffentlichungen.

Vorlage nach dem Gate-Format aus SKILL.md. Zur Entscheidung stehen:

- **Umsetzen wie geplant**
- **Umsetzen mit Änderung** (Nutzer nennt sie, Plan wird angepasst)
- **Nur planen, Umsetzung später/selbst** — Plan wird übergeben, Status
  `entschieden`
- **zurück zu TA oder LA**

Rein interne Vorarbeit — Entwürfe, lokale Änderungen, Analysen — darf ohne Gate
laufen. Die Grenze ist nicht „was ist Arbeit", sondern „was wirkt nach außen oder
ist schwer umkehrbar".

### 3. Durchführen

Drei Phasen, sauber getrennt:

- **Planen** — Reihenfolge, Abhängigkeiten, benötigte Zuarbeit, Abbruchpunkte
- **Durchführen** — abarbeiten; Abweichungen vom Plan sofort in `eu` vermerken,
  nicht nachträglich glattziehen
- **Abschließen** — Prüfkriterium aus PE anwenden. Ergebnis: erreicht / teilweise /
  nicht erreicht, jeweils mit Beleg

Bei Blockade während der Durchführung: nicht improvisieren, sondern anhalten,
Lage melden und einen Rücksprung anbieten. Ein halb umgesetzter Plan, der
weitergeschoben wird, ist die teuerste aller Varianten.

## Ausgang — Dokument `eu`

```markdown
## Entscheidung (FOR-DEC)
Facts / Options / Risks & Benefits / Decision / Execution / Check

## Umsetzungsplan
| Schritt | Was | Wer | Bis wann | Aus TA-Maßnahme? |

## Durchführungsprotokoll
| Schritt | Ergebnis | Abweichung vom Plan |

## Abschluss
Prüfkriterium: … · Ergebnis: erreicht / teilweise / nicht erreicht · Beleg: …
```

Nach Abschluss `status: entschieden` in `vorgang`. Erst NL setzt auf
`abgeschlossen` (IR-8).
