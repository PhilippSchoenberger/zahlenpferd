# Zahlenpferd

Ein Einmaleins-Trainer für den täglichen Gebrauch: fünf Minuten, Zahlenraum bis 20×20,
Spaced Repetition, Ponystall. Läuft komplett im Browser, ohne Server und ohne Konto.

## Wie es aufgesetzt wird

Die Dateien im Hauptverzeichnis sind die fertige Website. Bei GitHub Pages:
**Settings → Pages → Source: „Deploy from a branch“ → Branch `main`, Ordner `/ (root)`.**

Danach ist die App unter `https://<benutzername>.github.io/zahlenpferd/` erreichbar.

## Wichtig für das iPad

Die Seite einmal in Safari öffnen und über **Teilen → Zum Home-Bildschirm** ablegen.

Das ist nicht bloß Bequemlichkeit: iOS löscht die gespeicherten Daten normaler
Webseiten, die eine Woche lang nicht benutzt werden. Apps auf dem Home-Bildschirm sind
davon ausgenommen. Wird die App immer über dieses Symbol gestartet, bleibt der
Fortschritt erhalten.

Nicht funktionieren wird der Weg über eine eingebettete Vorschau (etwa eine
Artefakt-Ansicht): dort läuft die Seite in einem abgeschotteten Rahmen ohne
Speicherrecht. Die App erkennt das und zeigt oben ein rotes Warnband.

## Wo der Fortschritt liegt

Im Browser des jeweiligen Geräts (`localStorage`), nicht auf einem Server. Daraus folgt:

- Jedes Gerät hat seinen eigenen Stand.
- Unter **Mehr → Fortschritt sichern** gibt es „Als Datei sichern“ und „Aus Datei laden“.
  Die Datei enthält den kompletten Stand samt Fotoalbum und eignet sich als Sicherung
  und für den Umzug auf ein anderes Gerät.
- Die Fotos im Album kommen aus der Fotomediathek des Geräts und werden nirgendwohin
  hochgeladen.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | die gesamte App — Oberfläche, Lernlogik, Grafiken |
| `manifest.webmanifest` | macht sie zur installierbaren Web-App |
| `icon.svg`, `icon-180.png`, `icon-192.png`, `icon-512.png` | App-Symbol |
| `intern/artifact.html` | Fassung ohne Dokumentrahmen, nur für die Artefakt-Veröffentlichung |

`index.html` ist bewusst eine einzige Datei ohne Abhängigkeiten. Sie lässt sich auch
per Doppelklick vom Rechner öffnen — dann allerdings ohne App-Symbol.

## Wie das Training denkt

Jede Aufgabe wandert durch acht Fächer mit Abständen von 1, 2, 4, 8, 16, 32 und 60 Tagen.
Richtig und flott heißt ein Fach weiter, blitzschnell zwei, falsch zwei zurück und noch
in derselben Runde erneut. Neue Aufgaben werden ohne Vorsagen gefragt; wer sie auf Anhieb
kann, überspringt mehrere Fächer, damit die Zeit den kniffligen gehört. `7 × 8` und `8 × 7`
zählen als eine Aufgabe, werden aber in beiden Richtungen gefragt — daher 210 statt 400.
