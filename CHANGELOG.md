# Changelog

## 1.1.0 – 2026-10-03

### Datenschutz
- Keine Speicherung auf dem Gerät mehr: `localStorage` (Dunkelmodus, Ton) entfernt. Einstellungen gehen per URL-Parameter (`?dunkel=1`, `?ton=0`).
- Service Worker und Offline-Cache entfernt.
- Schrift und Favicon in `index.html` eingebettet – die Datei lädt keinerlei weitere Ressourcen.
- Dunkelmodus folgt ohne Parameter der Systemeinstellung.

## 1.0.0 – 2026-10-03

Erste Veröffentlichung als GitHub-Projekt, aufbauend auf der Einzeldatei `Unterrichtstimer.html`.

### Neu
- Arbeitsauftrag direkt über dem Timer eintippen (Klick oder Taste `A`); bleibt während der Laufzeit sichtbar.
- Eigene Zeit eingeben (`Eigene…` oder Taste `E`): `7`, `2,5` oder `1:30`. Klick auf `0:00` öffnet das Feld ebenfalls.
- Anzeige der Endzeit („Ende um 10:45 Uhr“) sowie „pausiert“ / „Zeit ist um“.
- Knöpfe für Ton, Dunkelmodus und Vollbild – alles auch ohne Tastatur am Smartboard bedienbar.
- `−1`-Knopf und Taste `-` zum Verkürzen.
- URL-Parameter `min`, `auftrag`, `start`, `presets`, `dunkel` – Timer lassen sich als Link aus Folien heraus öffnen.
- Offline-Fähigkeit (Service Worker) und Installation als App (PWA).
- Dunkelmodus folgt beim ersten Aufruf der Systemeinstellung.

### Geändert
- Schrift wird lokal ausgeliefert statt über Google Fonts (keine Übertragung der IP-Adresse an Google).
- `Esc` setzt einen laufenden Timer nicht mehr zurück (Schutz vor versehentlichem Reset, z. B. beim Verlassen des Vollbilds).
- Orange Warnfarbe erscheint nur noch bei Timern über 75 Sekunden – passend zum Hinweiston.
- Bedienleiste blendet sich nach dem Start zuverlässig nach 3 Sekunden aus.

### Behoben
- Bildschirmleser bekamen jede Sekunde eine Ansage; jetzt nur noch „Noch eine Minute“ und „Zeit ist um“.
- Tastenkürzel greifen nicht mehr, während in ein Eingabefeld getippt wird.
- `+` im Ruhezustand veränderte die Anzeige, ohne einen Timer vorzubereiten.
- Mehrfache Wake-Lock-Anfragen werden vermieden.
