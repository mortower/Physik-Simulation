# Physik-Simulation

Eine browserbasierte Physik-Simulation als Alternative zu Möbius für den Physik-Leistungskurs.

## Starten

Öffne `index.html` direkt im Browser oder starte im Projektordner einen lokalen Webserver:

```bash
python3 -m http.server 8000
```

Rufe anschließend `http://localhost:8000` auf. Die Anwendung benötigt keine Installation.

## Simulationscode und Startwerte

Der Simulationscode besteht aus einer Zuweisung pro Zeile. Jede Wiederholung führt die Zeilen der Reihe nach aus; ein späterer Wert kann daher in derselben Wiederholung bereits berechnete Größen verwenden. Zeilen können mit `#` kommentiert werden. Zum Beispiel:

```text
a = F/m
ds = v*dt
dv = a*dt
v = v+dv
s = s+ds
t = t+dt
```

Bedingte Zuweisungen haben die Form `if t < 5 then a = 0,3`. Unterstützt sind die Vergleiche `<`, `<=`, `>`, `>=`, `=`/`==` und `!=`. Zahlen dürfen ein Dezimalkomma oder einen Dezimalpunkt haben; auch Exponentialschreibweise ist möglich.

Benötigte Startwerte werden aus dem Code ermittelt und als Eingabefelder angezeigt. Einen Startwert braucht eine Größe nur, wenn sie gelesen wird, bevor sie im aktuellen Schleifendurchlauf zugewiesen wurde. Im obigen Beispiel sind das `F`, `m`, `dt`, `v`, `s` und `t`. Die Anzahl der Wiederholungen ist von 1 bis 10.000 einstellbar. Fehler im Code, in Startwerten oder in Berechnungen werden in der Anwendung angezeigt.

Erlaubt sind Zahlen, Variablen, Klammern sowie `+`, `-`, `*`, `/` und `^`. Multiplikation kann auch ohne `*` geschrieben werden, zum Beispiel `a/2 dt^2`. Außerdem gibt es `sin()`, `cos()`, `tan()`, `sqrt()` sowie die Konstanten `pi` und `e`. Trigonometrische Funktionen erwarten Winkel im Bogenmaß. Der Code wird als eingeschränkte Formelsprache ausgewertet, nicht als JavaScript. Mit „Formelansicht“ lässt sich gültiger Code zusätzlich in mathematischer Schreibweise mit Hoch- und Tiefstellungen anzeigen.

## Diagramm und Auswertung

Nach einer erfolgreichen Simulation:

- Wähle eine gemeinsame Größe für die x-Achse und bis zu 12 Größen für die y-Achse. Für jeden Graphen lassen sich Farbe und y-Größe separat einstellen.
- Die Achsen können automatisch oder manuell skaliert werden. Bei manueller Skalierung lassen sich Minimum und Maximum festlegen. Ist nur eine Achse manuell eingestellt, wird die automatische Skalierung der anderen Achse anhand der im gewählten Bereich sichtbaren Messpunkte berechnet.
- Für beide Achsen sind der Abstand der Hauptstriche und die Anzahl der Unterteilungen pro Abschnitt einstellbar. Ohne eigenen Hauptstrich-Abstand wird ein passender Wert gewählt. Die automatische Skalierung schließt den Ursprung ein; liegt null im Achsenbereich, werden die Achsen auch bei null gezeichnet.
- Zoome mit dem Mausrad um die Zeigerposition. Der Zoom-out führt zurück zur eingestellten Achsenskalierung. Verschiebe einen gezoomten Ausschnitt mit gedrückter Maustaste.
- Bewege den Zeiger im Diagramm nahe an einen Messpunkt, um die zugehörigen x- und y-Werte anzuzeigen.
- Öffne „Tabelle“ für eine seitenweise Tabelle aller berechneten Größen. Die Tabelle zeigt bis zu 50 Messpunkte pro Seite.
- Aktiviere optional die Referenzkurve, um denselben Programmcode mit kleineren `dt`-Schritten erneut auszuführen. Sie kann für die ausgewählten Graphen angezeigt werden und erscheint gestrichelt in einer Kontrastfarbe. Pro Simulationsschritt wird `dt` bis zu 10.000-mal geteilt; die Gesamtzahl interner Teilschritte ist auf 1.000.000 und die Referenzkurve auf 10.000 Punkte begrenzt.

## Programme speichern und drucken

- „Programm exportieren“ speichert Code, Startwerte, Wiederholungen sowie Graphen-, Referenzkurven- und Achseneinstellungen als JSON-Datei. „Programm importieren“ lädt eine solche Datei und führt die Simulation mit den gespeicherten Einstellungen aus.
- „Simulation herunterladen“ erzeugt eine eigenständige HTML-Datei. Sie enthält die Anwendung, startet aber mit einem leeren Programm und Standardeinstellungen und kann separat im Browser geöffnet werden.
- „Drucken“ und „Diagramm drucken“ öffnen die Druckansicht mit Diagramm, Feldern für Name, Kurs und Thema, aktuellem Datum und Uhrzeit sowie Simulationscode, Startwerten und Wiederholungszahl. Die Druckansicht ist ansonsten schwarz-weiß; Graphen behalten ihre Farben.

## Darstellung und Datenschutz

Die Seite startet im Darkmode. Über den Regler oben lässt sich unabhängig von den Systemeinstellungen zum hellen Normalmodus wechseln. Die Seite speichert keine personenbezogenen Daten; laut Datenschutzhinweis protokolliert der Hosting-Provider technische Zugriffsdaten.
