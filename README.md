# Unterrichtstimer

Ein schlanker Countdown-Timer für den Unterricht – gemacht für Beamer, Smartboard und Tablet.

**Datenschutzfreundlich by design:** eine einzige, in sich geschlossene HTML-Datei. Keine Cookies, keine Speicherung auf dem Gerät, keine externen Quellen, kein Tracking.

![Unterrichtstimer während einer Arbeitsphase](docs/screenshot.png)

**Live-Version:** `https://<dein-github-name>.github.io/unterrichtstimer/` (nach der Einrichtung von GitHub Pages, siehe unten)

## Funktionen

- Große, aus der letzten Reihe lesbare Ziffern mit Fortschrittsbalken
- Arbeitsauftrag über dem Timer, der während der Arbeitsphase sichtbar bleibt
- Schnellwahl (3, 5, 10, 15, 20, 45 Minuten) und eigene Zeiten wie `7`, `2,5` oder `1:30`
- Endzeit („Ende um 10:45 Uhr“), damit die Lerngruppe sich selbst orientieren kann
- Letzte Minute in Orange mit leisem Hinweiston, Ablauf in Rot mit Gong
- Zeit während der Laufzeit verlängern oder verkürzen (`+1`, `+5`, `−1`)
- Bedienleiste und Mauszeiger verschwinden während der Arbeitsphase
- Dunkelmodus, Vollbild, Ton aus – per Knopf oder Tastenkürzel
- Bildschirm bleibt während der Laufzeit an (Wake Lock, sofern der Browser es unterstützt)
- Läuft ohne Internet: `index.html` herunterladen, auf USB-Stick oder Schulrechner legen, per Doppelklick öffnen

## Bedienung

| Taste | Wirkung |
|---|---|
| `1` – `6` | Schnellwahl starten (3, 5, 10, 15, 20, 45 Min.) |
| `E` | Eigene Zeit eingeben |
| `Leertaste` | Start / Pause / Weiter |
| `+` / `-` | Eine Minute mehr / weniger |
| `A` | Arbeitsauftrag bearbeiten (`Enter` zum Übernehmen) |
| `F` | Vollbild |
| `D` | Dunkelmodus |
| `M` | Ton an / aus |
| `Esc` | Zurücksetzen (nur wenn der Timer pausiert oder abgelaufen ist) |

Ein Klick auf die Ziffern pausiert bzw. setzt fort; nach Ablauf setzt er den Timer zurück.

## Timer als Link (z. B. aus Folien)

Über URL-Parameter lässt sich ein Timer vorbereiten – praktisch als Link auf einer Folie oder in einem reveal.js-Vortrag.

| Parameter | Beispiel | Wirkung |
|---|---|---|
| `min` | `min=12` oder `min=1:30` | Zeit voreinstellen |
| `start` | `start=1` | sofort starten (sonst wartet der Timer auf „Start“) |
| `auftrag` | `auftrag=Partnerarbeit%20Fall%202` | Arbeitsauftrag anzeigen |
| `presets` | `presets=2,5,8,12` | eigene Schnellwahl (bis zu 9 Werte) |
| `dunkel` | `dunkel=1` / `dunkel=0` | hell oder dunkel öffnen (ohne Angabe: Systemeinstellung) |
| `ton` | `ton=0` | stumm starten |

Beispiel:

```
https://<dein-github-name>.github.io/unterrichtstimer/?min=15&auftrag=Pflegeprobleme%20formulieren
```

Hinweis: Browser spielen Töne erst nach einer ersten Berührung oder einem Klick auf der Seite ab. Bei `start=1` daher einmal kurz auf den Bildschirm tippen.

## Auf GitHub veröffentlichen

1. Auf github.com ein neues, öffentliches Repository `unterrichtstimer` anlegen.
2. Den Inhalt dieses Ordners hochladen – entweder über „Add file → Upload files“ im Browser oder per Git:
   ```bash
   git init
   git add .
   git commit -m "Unterrichtstimer 1.0.0"
   git branch -M main
   git remote add origin https://github.com/<dein-github-name>/unterrichtstimer.git
   git push -u origin main
   ```
3. Im Repository unter **Settings → Pages** bei „Source“ *Deploy from a branch*, Branch `main`, Ordner `/ (root)` wählen und speichern.
4. Nach ein bis zwei Minuten ist der Timer unter `https://<dein-github-name>.github.io/unterrichtstimer/` erreichbar.

## Lokal nutzen

`index.html` per Doppelklick öffnen – fertig. Schrift und Icon sind in der Datei eingebettet, es wird nichts nachgeladen. Damit ist die lokale Nutzung die datensparsamste Variante.

## Datenschutz

Der Timer selbst verarbeitet keine personenbezogenen Daten:

- keine Cookies
- keine Speicherung auf dem Gerät (kein `localStorage`, kein `sessionStorage`, keine IndexedDB, kein Service Worker, kein Cache)
- keine externen Quellen (keine Google Fonts, kein CDN, keine Analyse- oder Tracking-Dienste)
- der Arbeitsauftrag existiert nur im Browserfenster und ist nach dem Schließen weg

Weil nichts gespeichert wird, merkt sich der Timer Dunkelmodus und Ton nicht. Wer eine feste Einstellung möchte, legt sich ein Lesezeichen an, z. B. `index.html?dunkel=1&ton=0`.

Geprüft wurde das automatisiert im Browser: Beim Aufruf und bei der Bedienung wird ausschließlich `index.html` selbst angefragt, Cookies und Browserspeicher bleiben leer.

**Zum Hosting:** Wird der Timer über GitHub Pages bereitgestellt, verarbeitet GitHub als Hoster technisch bedingt die IP-Adresse der Aufrufenden (Server-Logs). Das betrifft den Hoster, nicht den Timer. Für die strengste Variante gibt es zwei Möglichkeiten: Entweder wird die Datei lokal genutzt oder auf dem Webserver bzw. im LMS der Schule (z. B. Moodle, IServ) abgelegt. Ob für ein öffentliches Angebot ein Impressum und eine Datenschutzerklärung nötig sind, klärt am besten der oder die Datenschutzbeauftragte der Schule.

## Projektstruktur

```
├── index.html             Timer – vollständig eigenständig (HTML, CSS, JS, Schrift, Icon)
├── manifest.webmanifest   optional: Name und Icon beim Anheften auf dem Startbildschirm
├── icons/                 App-Icons für das Manifest
├── fonts/OFL.txt          Lizenz der eingebetteten Schrift Plus Jakarta Sans
└── docs/screenshot.png
```

## Ideen für spätere Versionen

- Nachlaufzeit nach Ablauf anzeigen (`+0:42`)
- Mehrere Phasen hintereinander (z. B. 10 Min. Einzelarbeit → 15 Min. Gruppenarbeit → 5 Min. Plenum)
- Lautstärkeregler und Auswahl verschiedener Signaltöne

## Lizenz

Code: [MIT](LICENSE) · Schrift: SIL Open Font License 1.1 ([fonts/OFL.txt](fonts/OFL.txt))
