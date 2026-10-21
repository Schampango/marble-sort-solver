# Marble Sort Levelatlas

Lösungswege für die Level von **Marble Sort! – Color Puzzle** (Version 1.22.02).
Für jedes Level zeigt der Atlas das Spielfeld, die Becher am Band und eine Zugfolge,
bei der das Band möglichst wenig belegt ist.

> Inoffizielles Fanprojekt. Es steht in keiner Verbindung zum Hersteller des Spiels.

## Funktionen

- Lösungsweg Zug für Zug mit Spalte und Reihe
- Varianten: Je nach Spielverlauf stellt das Spiel die Becher anders zusammen, die passende Variante lässt sich auswählen
- Raketen zu Beginn: Getroffene Boxen markieren, dann rechnet ein Python-Löser direkt im Browser (über Pyodide von cdn.jsdelivr.net) einen neuen Weg
- Vereiste Becher werden markiert

## Hosting

Den Inhalt dieses Repos in ein Verzeichnis eines Webservers kopieren. Die Seite muss über HTTP(S) geöffnet werden, nicht per Doppelklick als Datei.

- `index.html`: die Seite
- `d/*.dat`: Leveldaten in Blöcken zu 50 Leveln, gzip-komprimiert, mit Prüfwert im Dateinamen
- `r-*/`: Leveldaten für die Raketen-Neuberechnung, werden nur bei Bedarf geladen
- `.htaccess`: Einstellungen für Apache (Cache ein Jahr für die Datendateien, `index.html` immer frisch)

Für Apache werden `mod_headers` und `AllowOverride FileInfo Options` empfohlen.
Ein typischer Besuch lädt etwa 70 bis 100 KB.

### Datenschutz

Die Seite lädt keine externen Schriften. Nur bei „Weg neu berechnen“ wird die Python-Laufzeit
(etwa 13 MB) von cdn.jsdelivr.net geladen, dabei geht die IP-Adresse des Besuchers an jsDelivr.
