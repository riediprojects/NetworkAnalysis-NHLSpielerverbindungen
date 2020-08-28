# Netzwerk Analyse für NHL Spieler

## Kurz
### Ziel
Aus verschiedenen Datenquellen verarbeiten wir ca. 456'750 Datensätze aus der NHL-API. Diese Datensätze enthalten Infomrationen zu Spielern, Teams und Seasons. 
Diese Daten sollen mittels einer Netzwerkanalyse so analysiert werden, dass beispielsweise Spieler, die ihrem Verein über längere Zeit true blieben, indentifiziert werden können. Als weiteres Beispiel soll auch untersucht werden, ob sich bestimmte Cliquen unter den Spielern gebildet haben.  

### Projekt-Team
•	Riedi Manuel </br>
•	Hürzeler Janick </br>
•	Winter Joël

### Tools
•	Gephi </br>
•	Python </br>
•	Json </br>
•	KNIME

### Bedeutung Knoten und Kanten
Die Knoten im Netzwerk bilden die einzelnen Spieler. Die Kanten haben die Bedeutung «hat zusammen gespielt mit» und können mit verschiedenen Werten, wie z.B. Anzahl Spiele, Anzahl Saisons oder Anzahl verschiedene gemeinsame Teams gewichtet werden. Es handelt sich somit um ein One-Mode-Netzwerk.

## Vorgang
### 1 Datenbeschafung
Daten werden von der NHL über ihre Stats-API (https://statsapi.web.nhl.com/api/v1, abgerufen </br>
In einem ersten Schritt wurde ein API-Fetcher in Python programmiert, der in Form eines Jupyter Notebooks die benötigten API-Calls pro Jahr durchführt. Die geladenen Daten einer Anfrage werden dabei als JSON-Datei (UTF8-Encoding) gespeichert, damit diese zu einem späteren Zeitpunkt nicht erneut geladen werden müssen. 

Detailiertere Informationen zur Datenbeschafung (S.1-2): [Dokumentation Datenbeschaffung](./Dokumentation/DokumentationDatenbeschaffung.pdf) </br>

### 2 Datenaufbereitung
Mit KNIME werden die gesammelten Daten aus den JSON-Files zu einem Node- und einem Edge-Table transformiert, sodass sie später in Gephi optimal eingesetzt werden können.
[KNIME Workflow](./Source/Knime/SNA_Projekt.knwf)

![KNIME Workflow](./KNIME.jpg)

Detailiertere Informationen zur Datenaufbereitung (S.2-7): [Dokumentation Datenbeschaffung](./Dokumentation/DokumentationDatenbeschaffung.pdf) </br>

### 3 Datenanalyse
#### Analyse: Vertrauten Mitspieler
Bei dieser Untersuchung sollen die Spieler identifiziert werden, welche auf eine grosse bzw. kleine Anzahl vertrauter Mitspieler setzen können. Um eine Aussage diesbezüglich machen zu können, werden zwei folgende Überlegungen über die Spieler-Knoten gemacht:
• Spieler mit hoher “Degree Centrality” und verhältnismässig niedriger “WeightedDegree Centrality”, wechseln oft das Team und sollten daher eher weniger vertraute Spieler aufweisen.
• Spieler mit niedriger “Degree Centrality” und verhältnismässig hoher “WeightedDegree Centrality”, bleiben ihrem Team eher treu und sollten daher auch eher eine
hohe Anzahl vertrauter Spieler aufweisen.

![VertrauteMitspieler](./TrustedPlayer.jpg)

#### Analye: Gegenüberstellung von «guten» und «schlechten» Teams
Bei dieser Analyse sollen eher bessere und eher schlechtere Teams aus einem gewissen Zeitraum gegenübergestellt werden. Dabei wurde anhand von Zentralitätswerten untersucht, ob treue Spieler einen Einfluss auf den Erfolg eines Teams haben. Ob eher gleich bleibende Kader ohne viele Spielerwechsel zum Erfolg beitragen können, wurde über die Dichte des Netzwerks versucht herauszufinden.

![GuteUndSchlechteTeams](./GoodBadTeams.jpg)

Detailiertere Informationen zur Analyse: [Dokumentation Soziale Netzwerkanalyse](./Dokumentation/DokumentationSozialeNetzwerkanalyse.pdf) </br>

#### Analyse: Cliquen
Bei dieser Analyse wurde untersucht, ob sich verschiedene Cliquen gebildet haben. Für den k-Core wurde die Grenzwerte für k ermittelt. In den gefundenen Cliquen wurde die Betweenness-Centrality für eher treue und untreue Spieler im Detail analysiert.


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







