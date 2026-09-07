# NL — Nacharbeiten und Lernen

**Auftrag:** Aus dem Verlauf das herausziehen, was beim nächsten Problem hilft, und
es dorthin schreiben, wo es wiedergefunden wird. Nicht optional (IR-8).

**Informationsmenge: steigt** — der Trichter öffnet sich wieder, weil das Ergebnis
über diesen einen Vorgang hinausweist.

## Besetzung (PLT)

| Rolle | Auftrag |
|-------|---------|
| **Auswerter** | Vergleicht Zielzustand mit Ergebnis, wertet den Methodeneinsatz aus, formuliert übertragbare Erkenntnisse. |

## Vorgehen

1. **Ergebnis gegen Prüfkriterium.** Das Kriterium aus PE anwenden — nicht
   nachträglich umformulieren, damit es passt. Ein verfehltes Ziel ist ein
   verwertbares Ergebnis, ein geschöntes nicht.
2. **Verlauf auswerten.** Wo lag der Vorgang daneben? Welche Ursachenhypothese war
   falsch? Welche Alternative wurde zu früh verworfen? Wo hat ein IC eine Lücke
   übersehen? Welches Modul war überflüssig, welches zu knapp?
3. **Übertragbares herausziehen.** Der Kern des Moduls. Eine Erkenntnis ist
   übertragbar, wenn sie ohne den konkreten Fall verständlich bleibt. „Bei Vorgang
   X war Y kaputt" ist keine Lehre. „Wenn A und B zusammentreffen, ist die Ursache
   meist C" ist eine.
4. **Offene Enden** benennen: nicht gehobene Chancen, verbliebene Risiken,
   ungenutzte PCIR-Einträge, offene PLT-Lücken. Was hier steht, findet der nächste
   IC wieder.
5. **Rückfluss ins Wissen — automatisch schreiben.** Die übertragbaren
   Erkenntnisse gehören **nicht** nur in die Vorgangsakte, sondern dorthin, wo beim
   nächsten Mal gesucht wird. Wird ohne Rückfrage geschrieben.

   | Modus | Ziel |
   |-------|------|
   | **Vault** | eigene Wissensnote im Wissensordner des Vaults (bei PARA-Struktur `30 Resources/Knowledge/`; sonst nach der Konventionsdatei des Vaults). Frontmatter `type: knowledge`, `tags: [knowledge, spalten]`, sprechender Titel ohne Datum. Verknüpft mit dem Vorgang und mit den Notizen, die der IC gefunden hat. |
   | **Projekt / konfiguriert** | `spalten/LERNEN.md` im Arbeitsverzeichnis — eine wachsende Datei über alle Vorgänge hinweg, nicht je Vorgang eine neue. Genau sie liest der IC des nächsten Laufs. |

   Gibt es zum Thema bereits eine Wissensnote, wird **diese ergänzt** statt eine
   zweite anzulegen. Widerspricht eine Erkenntnis dem Bestand, wird der Widerspruch
   ausdrücklich benannt (im Vault als `relations: contradicts`), nicht
   stillschweigend überschrieben.
6. **Danach um Rückmeldung bitten** — kurz, konkret, kein Gate: welche der
   Erkenntnisse trägt aus seiner Sicht nicht, was fehlt, was gehört anders
   verlinkt. Korrekturen werden direkt in die geschriebene Notiz eingearbeitet.

## Ausgang — Dokument `nl`

```markdown
## Zielerreichung
Zielzustand: … · Prüfkriterium: … · Ergebnis: … · Beleg: …

## Was gut lief
## Was nicht gut lief
(Module, Hypothesen, Bewertung, Gates — konkret, ohne Beschönigung)

## Übertragbare Erkenntnisse
| Erkenntnis | Gilt wann | Woher (Modul) |

## Offene Enden
(Chancen, Risiken, PCIR-Reste, PLT-Lücken)

## Rückfluss
Geschrieben nach: … · Verknüpft mit: … · Widersprüche zu Bestehendem: …
```

Zum Schluss `status: abgeschlossen` im Vorgang setzen — im Vault-Modus zusätzlich
das Frontmatter der Vorgangsnotiz auf `status: completed` und `updated` auf das
heutige Datum.

Der Skill verschiebt die Vorgangsakte nicht selbst. Liegt sie in einem Ordner, den
der Vault als bloßen Durchgang führt (typisch: eine Inbox), einmalig darauf
hinweisen, dass sie bei der nächsten Review einzusortieren oder zu archivieren ist.
