# AL — Alternative Lösungssuche

**Auftrag:** Lösungsvarianten erzeugen. Nicht bewerten, nicht auswählen, nicht
schon umsetzen. Der einzige Feind dieses Moduls ist die Frühfixierung auf die
erstbeste Idee.

**Informationsmenge: steigt.**

## Besetzung (PLT)

Zwei **unabhängige** Ideengeber als getrennte Subagenten, dazu ein Zusammenführer.
Die Unabhängigkeit ist der Punkt: beide bekommen denselben abstrahierten
Zielzustand, aber **kein** Wissen über die Ideen des jeweils anderen und keine
bereits genannte Lösung.

| Rolle | Technik |
|-------|---------|
| **Ideengeber A — Übertragung** | Analogie und Präzedenz: Wer hat ein strukturgleiches Problem schon gelöst — in anderer Branche, anderer Disziplin, in der Natur, in der eigenen Vorgeschichte (Wissensbasis)? Was daran ist übertragbar? |
| **Ideengeber B — Variation** | Systematische Veränderung am System: Streichen (was, wenn dieser Teil entfällt?), Vervielfachen, Umkehren, Aufteilen, Zusammenlegen, Verlagern (an wen anders?), Zeitpunkt verschieben. |
| **Zusammenführer** | Führt die Vorschläge zusammen, entdoppelt, kombiniert Bausteine zu Hybriden, ergänzt die Null-Variante. |

## Vorgehen

1. **Ziel abstrahieren.** Bevor die Ideengeber starten, den Zielzustand aus PE eine
   Stufe abstrakter fassen, damit die Lösungsrichtung offenbleibt. Diese
   Abstraktion wird beiden Ideengebern als Auftrag gegeben.
2. **PCIR auslesen** (Pflicht). Alles, was seit SA nebenbei aufgefallen ist, geht
   als Rohmaterial in die Ideensuche. Genau dafür existiert die Sammlung.
3. **Ideengeber parallel starten.**
4. **Zusammenführen.** Doppelungen streichen, verwandte Ansätze zu Varianten
   bündeln, Bausteine über Kreuz kombinieren.
5. **Null-Variante ergänzen** (Pflicht, IR-3): Was passiert, wenn nichts getan
   wird? Sie ist keine Formalie — manchmal gewinnt sie.
6. **Mindestzahl prüfen:** drei echte Alternativen plus Null-Variante. „Echt"
   heißt: unterscheidbarer Lösungsweg, nicht dieselbe Idee in zwei Ausführungen.
   Wird die Zahl nicht erreicht, wird nicht künstlich aufgefüllt, sondern
   nachgeschärft — und wenn das scheitert, im IC vermerkt und LA mit dem
   Vorhandenen begonnen.

## Ausgang — Dokument `al`

Je Alternative:

```markdown
### A<n> — <Kurzname>
**Kern:** ein Satz, was gemacht wird
**Wie es wirkt:** Bezug zur Ursache aus PE
**Voraussetzungen:** was gegeben sein muss
**Aufwand grob:** Zeit / Geld / Beteiligte
**Herkunft:** Ideengeber A / B / Hybrid / PCIR / Null-Variante
```

Keine Bewertung, keine Rangfolge, keine Empfehlung in diesem Dokument. Bewertende
Adjektive („elegant", „unrealistisch") sind hier verboten — sie nehmen LA vorweg.

## Abbruchbedingungen

- Alle Ideen laufen auf dieselbe Lösung hinaus → prüfen, ob der Zielzustand zu eng
  formuliert war. Ggf. Rücksprung nach PE vorschlagen.
- Eine Alternative würde reale, schwer umkehrbare Wirkung entfalten → hier nur
  notieren, nichts davon ausführen (IR-5).
