# Changelog

Alle nennenswerten Änderungen an diesem Skill. Format nach
[Keep a Changelog](https://keepachangelog.com/de/1.1.0/),
Versionierung nach [Semantic Versioning](https://semver.org/lang/de/).

Für einen Skill aus Prosa gelesen: **Major** = eine IRON RULE oder der Ablauf
ändert sich, **Minor** = ein Modul, eine Rolle oder ein Werkzeug kommt hinzu,
**Patch** = Formulierung, Korrektur, Dokumentation.

## [1.0.0] — 2026-09-07

Erste Fassung. Der Skill wurde selbst nach SPALTEN gebaut; die Entscheidungen
stehen mitsamt dem Verworfenen in [`DESIGN.md`](DESIGN.md).

### Hinzugefügt

- Sieben Module (SA, PE, AL, LA, TA, EU, NL) als je eigene Rollenanweisung.
- Automatischer Informationscheck zwischen je zwei Modulen, mit Ampel und
  Protokollzeile. Sichtbarer Stopp nur bei Gelb oder Rot.
- Bindende Quellenreihenfolge Wissensbasis → Nutzer → Web; das Suchergebnis wird
  immer protokolliert, auch wenn es leer ist.
- Modulweise wechselndes Problemlösungsteam als getrennte Subagenten: zwei
  abgeschottete Ideengeber in AL, Advocatus Diaboli in LA.
- Meldung nicht simulierbarer Kompetenzen als PLT-Lücke, statt sie durch Annahmen
  zu ersetzen.
- Drei harte Gates: Zielzustand (nach PE), Lösungswahl (nach LA), Umsetzung (EU).
- Acht IRON RULES.
- Fortsetzbarer Vorgang mit State-Dokument; `/spalten` ohne Argument nimmt einen
  offenen Vorgang wieder auf.
- PCIR als mitlaufende Ideen- und Informationssammlung, verpflichtend ausgelesen
  in AL und TA.
- Drei Ablagemodi: konfiguriert, Vault, Projektverzeichnis (Standard). Der Skill
  läuft ohne Vorbedingungen.
- Honigwabenmodell als Selbstkontrolle über die Informationsmenge je Modul.
- Methodenkoffer mit „nimm, wenn"-Auswahlspalte je Werkzeug.
- Kurzläufe und Rücksprungregel: der Ablauf ist iterativ, nicht linear.

[1.0.0]: https://github.com/FeFoe/spalten/releases/tag/v1.0.0
