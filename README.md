# Netzwerk Analyse für NHL Spieler

## Projekt-Team
•	Riedi Manuel </br>
•	Hürzeler Janick </br>
•	Winter Joël

### Detailierte Informationen
Detailiertere Informationen zum Projekt können von folgenden Dokumenten entnommen werden.
Projektinformationen: [my directory](./Dokumentation/DokumentationDatenbeschaffung.pdf) </br>
Datenbeschaffung: [my directory](./Dokumentation/DokumentationDatenbeschaffung.pdf)  </br>
Datenanalyse (Endergebnisse): [my directory](./Dokumentation/DokumentationDatenbeschaffung.pdf) 

### Tools
Gephi
Python 
KNIME

### Datenquellen
Die Daten werden direkt von der NHL über ihre Stats-API (https://statsapi.web.nhl.com/api/v1, abgerufen </br>
Beispiel-Abfrage: https://statsapi.web.nhl.com/api/v1/teams/1). </br>
Datenzugriff mittels API. 

## Durchgeführte Analysen
### Analyse 1
#### These / Frage: 
Welche Spieler können auf eine grosse Anzahl an vertrauter Mitspieler setzen und welche haben in ihrer Karriere eher viel verschiedene Mitspieler gehabt.
#### Filterung:	
Die Operationen werden auf dem kompletten Netzwerk ausgeführt 
#### Analyse:	
Die Degree Centrality wird eine wichtige Rolle spielen. Ein tiefer Wert an Anzahl Verbindungen (mit tiefer Gewichtung) sagt aus, dass ein Spieler weniger oft den Klub gewechselt hat. Eine eher weniger hohe Anzahl (dafür mit hoher Gewichtung), deutet auf einen «treuen» Spieler hin. 
#### Erwartung:	
Spieler, welche lange beim selben Klub sind, werden tiefere (ungewichtete) Degree Centrality Werte haben, jedoch sind die einzelnen Kantengewichte deutlich höher. Als Beispiel wäre hier Joe Thornton zu nennen, der seit der Saison 05/06 für denselben Klub spielt und zuvor nur bei einem weiteren war.

### Analyse 2
#### These / Frage:	
Gibt es Cliquen um besonders treue Spieler, die evtl. eine Ära in einem Verein geprägt haben?
#### Filterung:	
Die Operationen werden auf dem kompletten Netzwerk ausgeführt
#### Analyse:	
Mit K-Core soll ermittelt werden, ob sich bestimmte Cliquen gebildet haben. Für k ist ein sinnvoller Wert währende der Analyse noch zu definieren. Innerhalb der Cliquen kann ein hoher Betweenness-Centrality Wert auf eine wichtige Rolle hinweisen.
#### Erwartung:	
Spieler, die in der ersten Analyse als «treue Spieler» analysiert wurden, werden eine gewichtige Rolle in allfälligen Cliquen spielen.







