# Was hier passiert ist — und warum dieser Ordner gelöscht werden kann

## Das Problem

Auf GitHub gab es beim Klick auf „Fragebogen starten" eine 404-Fehlermeldung.

## Die Ursache (in drei Schritten erklärt)

1. **Falscher Ordner aktiv:** GitHub Pages hat nicht diese `index.html` hier geladen,
   sondern die `index.html` die direkt im Root des Repos liegt (eine Ebene höher).
   Dieser `50.3 Landing_Page`-Ordner ist damit überflüssig.

2. **Falscher Pfad im Button-Link:** In der Root-`index.html` zeigte der Button auf
   `../50.4 Fragebogen/fragebogen.html` — zwei Fehler auf einmal:
   - `../` geht eine Ebene über das Repo hinaus → existiert nicht
   - `50.4 Fragebogen` mit Leerzeichen → Webserver mag das nicht

3. **Falscher Ordnername auf GitHub:** Der Fragebogen-Ordner hieß `50.4 Fragebogen`
   (mit Leerzeichen), was auf Webservern zu Problemen führt.

## Was korrigiert wurde

- Ordner `50.4 Fragebogen` → umbenannt zu `50.4_Fragebogen` (Unterstrich statt Leerzeichen)
- Button-Links in der Root-`index.html` korrigiert:
  - Vorher: `../50.4 Fragebogen/fragebogen.html`
  - Nachher: `50.4_Fragebogen/fragebogen.html`

## Warum dieser Ordner gelöscht werden kann

Die Live-Webseite läuft über die Root-`index.html`, nicht über diese Datei hier.
`50.3 Landing_Page/` ist ein Überbleibsel aus der Entwicklungsphase und hat
auf GitHub keine Funktion mehr. Löschen ist sicher.

## Funktionierende Struktur danach

```
Webseite-NB/          ← GitHub-Repo Root
├── index.html        ← Live-Landing-Page (diese wird von GitHub Pages geladen)
├── 50.4_Fragebogen/
│   └── fragebogen.html   ← Fragebogen (Button zeigt hierher)
└── 50.4 Handout/
    └── ...
```
