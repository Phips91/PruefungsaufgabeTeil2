#Projektname: PruefungsaufgabeTeil2

Datensatz: MNIST-Projekt

Anleitung zum Betrieb des Codes:
-  MyBinder über den BinderBatch öffnen [diese Version läuft aufgrund der max. Memory Kapazität von myBinder (2GB) über die Verknüpfung der myBinder Version von https://notebooks.gesis.org/binder/ welches eine Kooperation mit mybinder hat und 4GB RAM bereitstellt, Gesis Notebooks ist Teil der myBinder Federation und nutzt ebenso wie myBinder original die gesamte Mybinder Architektur, lediglich dass 4GB Memory statt 2GB zur Verfügung stehen]
-  Nach dem öffnen über MyBinder, ist das Notebook auf der Linken Seite der Webpage zu finden, durch Doppelklick kann es geöffnet werden.
-  Über den PlayButton kann das Notebook Schritt für Schritt durchgeführt werden, über das >> Symbol kann das System fast komplett durchlaufen, lediglich in der Mitte des Skriptes muss eine Prozentzahl für die Datenverarbeitung eingegeben werden.

[![Binder](https://mybinder.org/badge_logo.svg)](https://notebooks.gesis.org/services/binder/v2/gh/Phips91/PruefungsaufgabeTeil2/HEAD)

Hier ist eine kurze Dokumentation zum gegebenen Code:

Der gegebene Code implementiert eine Anwendung zur Verarbeitung von MNIST-Daten und zur Erstellung eines maschinellen Lernmodells. Hier ist eine Zusammenfassung der wichtigsten Funktionen und Teile des Codes:

1. Datenverarbeitung:
   - Zusammenbauen der Train-Data File des MNIST-Daten und Konvertieren der Labels in Ganzzahlen. Der MNIST Datensatz wurde mit dem letzten Stand der Daten (31.10.2023) heruntergeladen und in das GitHub Repositorie geladen. Lediglich die Train-images Datei wurde zuvor in drei ZIP Files aufgeteilt um diese auf GitHub Hochladen zukönnen. Dies musste gemacht werden, da der Train-images Datensatz 45MB groß ist und GitHub nur eine maximale Upload Größe von 25MB zu lässt. Der Traings-images Datensatz wird direkt zum Anfang wieder zusammengebaut, so dass er komplett nutzbar ist.
   - Normalisieren der Daten und Aufteilen in Trainings- und Testdatensätze.

2. Neuronales Netzwerk:
   - Definition eines mehrschichtigen neuronalen Netzwerks mit Platzhaltern für die Eingabe und Gewichts- und Bias-Variablen.
   - Festlegen der Kostenfunktion und des Optimierungsalgorithmus.
   - Für die Festlegung der Kostenfunktion und des Optimierungsalgoritmus wurde eine Prozenteingabe implementiert. Dieser erwartet einen prozentualen Wert zwischen 0 - 100%.
     (Für den hier vorliegenden Testfall wurde aus zeittechnisch Gründen mit 1% der Daten gearbeitet)

3. Training und Vorhersage:
   - Die "TheAlgorithm"-Klasse enthält Methoden zur Modellierung und Evaluation.
   - Die "fit"-Methode trainiert ein Logistisches Regressionsmodell auf den Trainingsdaten und berechnet die Trainingsgenauigkeit.
   - Die "predict"-Methode verwendet das trainierte Modell, um Vorhersagen auf den Testdaten zu treffen und berechnet die Testgenauigkeit.

4. Zusätzliche Funktionen:
   - Der Code enthält Dekoratoren "my_logger" und "my_timer" zur Protokollierung und Messung der Funktionen.
   - Es werden Unittest-Testfälle erstellt, um die Modellfunktionen und die Laufzeit zu überprüfen.

5. Laufzeitmessung:
   - Der Code enthält Tests zur Laufzeitmessung, um sicherzustellen, dass die Modellierungsfunktionen innerhalb eines akzeptablen Zeitrahmens ausgeführt werden.

Insgesamt ist der Code eine umfassende Implementierung zur Verarbeitung von MNIST-Daten und zur Erstellung eines Modells zur Ziffernerkennung. Er enthält Tests und Metriken zur Überwachung der Leistung des Modells.

Ergebnisse:
"if __name__" - Funktion
Zunächst wird die Startzeit gemessen.
1. Die MNIST-Daten werden heruntergeladen und die Größe der Daten wird angezeigt (70000 Beispiele mit jeweils 784 Merkmalen).
2. Die Daten werden in Trainings- und Testdatensätze aufgeteilt.
3. Das Modell "TheAlgorithm" wird initialisiert, trainiert und auf den Trainings- und Testdaten getestet.
4. Die Trainingsgenauigkeit beträgt etwa 72,86%, und die dazugehörige Verwirrungsmatrix wird angezeigt.
5. Die Testgenauigkeit beträgt etwa 57,65%, und die dazugehörige Verwirrungsmatrix wird ebenfalls angezeigt.
6. Es wird ein Klassifikationsbericht für den Testdatensatz erstellt, der die Genauigkeit und Leistung des Modells für jede Klasse zeigt.
7. Die gesamte Ausführungszeit des Codes wird berechnet und angezeigt (ungefähr 50,51 Sekunden).

"class TestInput" - Funktion (Laufzeit 0.01%)
1. Die Methode test_fit testet, ob die Genauigkeit der fit-Funktion des Modells den erwarteten Trainingsgenauigkeitswert erreicht. Der Test wurde erfolgreich bestanden.
2. Die Methode test_predict testet, ob die Genauigkeit der predict-Funktion des Modells den erwarteten Testgenauigkeitswert erreicht. Der Test wurde ebenfalls erfolgreich bestanden.
3. Die Methode test_runtime_fit prüft, ob die Laufzeit der fit-Funktion innerhalb eines akzeptablen Bereichs liegt. Der Test schlägt jedoch fehl, da die gemessene Laufzeit von 18,396 Sekunden den Grenzwert von 0,0018 Sekunden (120% der repräsentativen Laufzeit) überschreitet.

"class TestInput" - Funktion (Laufzeit 120%)
1. Die Methode test_fit testet, ob die Genauigkeit der fit-Funktion des Modells den erwarteten Trainingsgenauigkeitswert erreicht. Der Test wurde erfolgreich bestanden.
2. Die Methode test_predict testet, ob die Genauigkeit der predict-Funktion des Modells den erwarteten Testgenauigkeitswert erreicht. Der Test wurde ebenfalls erfolgreich bestanden.
3. Die Methode test_runtime_fit überprüft, ob die Laufzeit der fit-Funktion innerhalb des akzeptablen Bereichs liegt. Im Gegensatz zur vorherigen Ausführung, hat dieser Test jetzt erfolgreich bestanden, da die gemessene Laufzeit von 18,039 Sekunden innerhalb des zulässigen Bereichs von 1,2-mal der repräsentativen Laufzeit liegt.
