# Netzwerk Analyse für NHL Spieler

## Ziel
Aus verschiedenen Datenquellen verarbeiten wir ca. 456'750 Datensätze aus der NHL-API. Diese Datensätze enthalten Infomrationen zu Spielern, Teams und Seasons. 
Diese Daten sollen mittels einer Netzwerkanalyse so analysiert werden, dass beispielsweise Spieler, die ihrem Verein über längere Zeit true blieben, indentifiziert werden können. 

## Projekt-Team
•	Riedi Manuel </br>
•	Hürzeler Janick </br>
•	Winter Joël

### Tools
•	Gephi </br>
•	Python </br>
•	Json </br>
•	KNIME

### Detailierte Informationen
Detailiertere Informationen zum Projekt können von folgenden Dokumenten entnommen werden.
Projektinformationen: [Dokumentation Datenbeschaffung](./Dokumentation/DokumentationDatenbeschaffung.pdf) </br>
Datenbeschaffung: [my directory](./Dokumentation/DokumentationDatenbeschaffung.pdf)  </br>
Datenanalyse (Endergebnisse): [my directory](./Dokumentation/DokumentationDatenbeschaffung.pdf) 

### Datenquellen
Die Daten werden direkt von der NHL über ihre Stats-API (https://statsapi.web.nhl.com/api/v1, abgerufen </br>
Beispiel-Abfrage: https://statsapi.web.nhl.com/api/v1/teams/1). </br>
Datenzugriff mittels API. 

## Bedeutung der Knoten und Kanten
Die Knoten im Netzwerk bilden die einzelnen Spieler. Die Kanten haben die Bedeutung «hat zusammen gespielt mit» und können mit verschiedenen Werten, wie z.B. Anzahl Spiele, Anzahl Saisons oder Anzahl verschiedene gemeinsame Teams gewichtet werden. Es handelt sich somit um ein One-Mode-Netzwerk.

## Durchgeführte Analysen
### Analyse 1: Vertraute Spieler
#### Frage: 
Welche Spieler können auf eine grosse Anzahl an vertrauter Mitspieler setzen und welche haben in ihrer Karriere eher viel verschiedene Mitspieler gehabt. 
#### Analyse:	
Die Degree Centrality wird eine wichtige Rolle spielen. Ein tiefer Wert an Anzahl Verbindungen (mit tiefer Gewichtung) sagt aus, dass ein Spieler weniger oft den Klub gewechselt hat. Eine eher weniger hohe Anzahl (dafür mit hoher Gewichtung), deutet auf einen «treuen» Spieler hin. 
#### Erwartung:	
Spieler, welche lange beim selben Klub sind, werden tiefere (ungewichtete) Degree Centrality Werte haben, jedoch sind die einzelnen Kantengewichte deutlich höher. Als Beispiel wäre hier Joe Thornton zu nennen, der seit der Saison 05/06 für denselben Klub spielt und zuvor nur bei einem weiteren war.

### Analyse 2: Cliquen und besonders treue Spieler
#### These / Frage:	
Gibt es Cliquen und besonders treue Spieler, die evtl. eine Ära in einem Verein geprägt haben?
#### Analyse:	
Mit K-Core soll ermittelt werden, ob sich bestimmte Cliquen gebildet haben. Innerhalb der Cliquen kann ein hoher Betweenness-Centrality Wert auf eine wichtige Rolle hinweisen.
#### Erwartung:	
Spieler, die in der ersten Analyse als «treue Spieler» analysiert wurden, werden eine gewichtige Rolle in allfälligen Cliquen spielen.







