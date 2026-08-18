# KlarPost MVP

KlarPost ist ein seniorengerechter Orga-Assistent für Papierpost.

## Kernidee

**Post fotografieren → verstehen → wissen, was zu tun ist.**

Die App soll Briefe und Rechnungen erkennen, in einfacher Sprache erklären, konkrete Aufgaben und Fristen ableiten, Erinnerungen verwalten und optional hinterlegte Angehörige oder Betreuer informieren.

## MVP-Scope

- seniorengerechtes Dashboard
- Foto-/Upload-Flow für Dokumente
- simulierte KI-Dokumentanalyse
- Dokumenttyp, Absender, Kurzfassung, Aufgabe und Frist
- Aufgabenstatus: offen / wartet / erledigt / prüfen
- Erinnerungen
- Vertrauenskreis mit Angehörigen
- Demo-Daten ohne produktive Bank-, Versicherungs- oder Behörden-Schnittstellen

## Nicht im MVP

- automatische Zahlungen
- produktive Bankanbindung
- direkte PKV-/Beihilfe-Einreichung
- verbindliche Rechts- oder Medizinberatung
- vollautomatisches Versenden an Dritte

## Start

```bash
npm install
npm run dev
```

Dann http://localhost:3000 öffnen.

## Codex

Vor Änderungen zuerst `AGENTS.md` und `docs/PRD.md` lesen.
