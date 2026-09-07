# LA — Lösungsauswahl

**Auftrag:** Die Alternativen analysieren, bewerten und die aussichtsreichste
auswählen. Ergebnis ist ein **hartes Gate**.

**Informationsmenge: sinkt.**

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Bewerter** | Legt Kriterien fest, gewichtet sie, bewertet jede Alternative, rechnet den Nutzwert. |
| **Advocatus Diaboli** | Greift das Ergebnis an, **nachdem** es steht: Welche Annahme trägt nicht? Welches Kriterium fehlt oder ist falsch gewichtet? Warum könnte der Zweitplatzierte in Wahrheit besser sein? Wo hat sich der Bewerter in die Lösung verliebt? |

Beide als getrennte Subagenten. Der Advocatus Diaboli bekommt die Bewertung, aber
nicht die Begründung des Bewerters — sonst übernimmt er dessen Rahmen.

## Vorgehen

### 1. Kriterien zuerst (IR-4)

Kriterien werden **vor** der Bewertung festgelegt, aus dem Zielzustand und den
Randbedingungen abgeleitet, und offengelegt. Üblich sind vier Gruppen:

- **fachlich/technisch** — löst es die Ursache, ist es machbar?
- **wirtschaftlich** — Aufwand, laufende Kosten, Bindung von Ressourcen
- **zeitlich** — wann wirkt es?
- **rechtlich/organisatorisch** — zulässig, durchsetzbar, akzeptiert?

Dazu Ausschlusskriterien: Bedingungen, an denen eine Alternative sofort scheitert,
unabhängig vom Punktwert. Sie werden zuerst geprüft.

Gewichtung: Summe 100 %. Wer gewichtet, entscheidet — deshalb wird die Gewichtung
am Gate sichtbar gemacht und ist dort änderbar.

### 2. Bewerten

Nutzwertanalyse: je Kriterium 0–10, mal Gewicht, Summe. Bei wenigen Alternativen
oder unklarer Skala stattdessen paarweiser Vergleich. Jede Punktvergabe braucht
einen halben Satz Begründung — eine Zahl ohne Begründung ist geraten.

Unsicherheiten in den Eingangsdaten explizit markieren. Wo eine Bewertung auf einer
Annahme beruht, wird die Annahme genannt (IR-7).

### 3. Angriff

Der Advocatus Diaboli liefert eine schriftliche Gegenrede. Ihre Punkte werden
**nicht** stillschweigend eingearbeitet, sondern im Dokument sichtbar
beantwortet — angenommen oder begründet zurückgewiesen.

### 4. Robustheitsprobe

Liegen Erst- und Zweitplatzierter nahe beieinander (< 10 % Abstand), oder kippt die
Reihenfolge bei kleiner Änderung der Gewichte? Dann ist die Auswahl nicht robust.
Das wird am Gate ausdrücklich gesagt, statt eine Scheinsicherheit zu erzeugen.

## Ausgang — Dokument `la`

```markdown
## Ausschlusskriterien
| Kriterium | A1 | A2 | A3 | Null |

## Bewertungskriterien und Gewichte
| Kriterium | Gewicht | Begründung der Gewichtung |

## Nutzwertmatrix
| Kriterium | Gewicht | A1 | A2 | A3 | Null |
… Summe …

## Gegenrede (Advocatus Diaboli)
| Einwand | Antwort: angenommen / zurückgewiesen (Grund) |

## Robustheit
Abstand Platz 1 zu 2: … · kippt bei: …

## Empfehlung
… (ein Absatz, mit dem Grund, nicht nur der Zahl)
```

## ★ Hartes Gate

Vorlage nach dem Gate-Format aus SKILL.md. Zur Entscheidung stehen:

- **Empfohlene Alternative wählen**
- **Andere Alternative wählen** (Nutzer überstimmt die Rechnung — legitim, wird
  im Entscheidungslog mit Begründung festgehalten)
- **Gewichtung ändern** und neu rechnen
- **zurück zu AL** — keine der Alternativen überzeugt
- **Null-Variante** — nichts tun, Vorgang beenden

Nach der Wahl `gewaehlte_loesung` in `vorgang` setzen.
