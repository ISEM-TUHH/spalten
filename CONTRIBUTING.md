# Mitwirken

Dieser Skill besteht ausschließlich aus Prosa. Es gibt nichts zu kompilieren und
keine Tests, die grün werden könnten — die einzige Prüfung ist ein echter Lauf.
Das macht Beiträge leicht und Sorgfalt umso wichtiger.

## Die eine Regel

**Wer eine Regel ändert, sollte sagen können, welcher reale Fehllauf sie nötig
gemacht hat.** Eine Anweisung, die niemand je gebraucht hat, macht den Skill nicht
besser, sondern nur länger — und ein längerer Skill wird schlechter befolgt. Im
Zweifel gilt YAGNI.

## Was hilfreich ist

- **Fehllaufberichte.** Der wertvollste Beitrag: eine Beschreibung, an welcher
  Stelle der Skill etwas Falsches getan hat, was er stattdessen hätte tun sollen,
  und woran man das im Ablauf hätte erkennen können.
- **Werkzeuge für den Methodenkoffer**, mit ausgefüllter „nimm, wenn"-Spalte. Die
  Spalte ist wichtiger als das Werkzeug: eine Methode ohne Auswahlkriterium wird
  entweder immer oder nie benutzt.
- **Übersetzungen.** Der Skill ist deutsch. Eine englische Fassung wäre eine eigene
  Datei, keine Ersetzung.
- **Schärfere Formulierungen.** Kürzer und eindeutiger ist fast immer besser.

## Was nicht hineingehört

- Neue Module. Die sieben stehen fest; sie kommen aus der zitierten Methodik.
- Weitere Slash-Commands. Der IC entscheidet Modulübersprünge selbst
  (siehe [`DESIGN.md`](DESIGN.md), Entscheidung 6).
- Domänenspezifische Anweisungen. Der Skill ist bewusst universell
  (Entscheidung 2).
- Harte Abhängigkeiten von einem bestimmten Werkzeug oder Wissensspeicher. Der
  Skill muss ohne Vorbedingungen laufen (Entscheidung 5).

Wer trotzdem einen dieser Punkte für richtig hält: gern, aber bitte mit dem
Argument, das in `DESIGN.md` noch nicht abgewogen wurde. Die Tabelle dort führt
absichtlich mit, was verworfen wurde.

## Ablauf

1. Issue eröffnen und die Änderung kurz begründen — besonders bei allem, was die
   IRON RULES oder den Ablauf berührt.
2. Fork, Branch, Änderung.
3. **Den geänderten Skill mindestens einmal an einem echten Problem laufen lassen.**
   Was dabei aufgefallen ist, gehört in die Pull-Request-Beschreibung.
4. Pull Request stellen.

## Stil

- Deutsch, vollständige Rechtschreibung samt Umlauten im Fließtext.
- Dateinamen ohne Umlaute und ohne Gedankenstriche — sie brechen die Linkauflösung
  über Windows- und POSIX-Werkzeuge hinweg.
- Zeilen im Fließtext bei etwa 88 Zeichen umbrechen (siehe `.editorconfig`).
- Anweisungen im Imperativ oder als Regel, nicht als Beschreibung. „Kriterien
  werden vor der Bewertung offengelegt" ist eine Regel; „der Skill legt meistens
  Kriterien offen" ist keine.
- Tabellen, wo eine Auswahl getroffen wird; Fließtext, wo begründet wird.
