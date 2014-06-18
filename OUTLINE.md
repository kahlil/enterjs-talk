# EnterJS Notes

## Aufwärmen
* Aufstehen, Liegestütze, strecken
* Hand geben

## Intro
## Teil I: Frontend Ops - Überblick

### Was ist ein Frontend Ops Engineer?
Wer von euch kann sich unter dem Begriff schon was vorstellen?

* Referenzartikel von Alex Sexton, sicher kann man sich um Details streiten der Artikel ist meines Erachtens aber sehr erschöpfend
* Auf einzelne Aufgaben gehe ich beispielhaft im Detail noch ein aber meiner Meinung nach kann man diese Disziplin schön auf 3 Hauptziele/Hauptmesswerte und zwei Werkzeugklassen reduzieren um die Disziplin zusammen zu fassen

**Ziele:**
* Geschwindigkeit für alle Abläufe
	* Nicht nur die generelle Geschwindigkeit der Webseite oder Applikation, sondern
		* Entwicklungsgeschwindigkeit
		* Geschwindigkeit nach Local, Dev, Stage (, QA?), Prod
		* Geschwindigkeit von Teilfunktionalität nach Dev (, Stage?)
		* Geschwindigkeit von Stage nach Prod
* Glückliche Menschen
	Glückliche Menschen erzeugen langfristig weit besseren Code und somit ein besseres Produkt
	* Glückliche Entwickler durch
		* gute Code-Strukturierung durch Modularisierung und Konventionen
		* gute Einführung und klarer Pfad für Neue Entwickler
		* konsistente Entwicklungsumgeben, leicht einzurichten, keine Zeit für Einrichtung verschwenden
	* Glücklicher Chef/Projektleiter
		* Erhält zeitnah neueste Stände
		* Fixes werden schnell deployed
		* Entwicklung geht zügig voran
	* Glückliche QA
		* kann schnell und bequem neue Features testen
		* schnelle Lieferung von Fixes
	* Glücklicher Kunde
		* neue Features sind möglichst schnell zu sehen und zu testen
		* Teilstände gehen schnell live
		* Komplette Seite geht schnell live
		* Seite performt wie erwartet

**Werkzeugklassen:**
* Automatisierungswerkzeuge
	* AUTOMATE ALL THE THINGS!!!!!!
	* Grunt
	* Gulp
	* Git
	* Travis/Jenkins
	* Shell
* Messwerkzeuge
	* MEASURE ALL THE THINGS!!!!
	* Monitoring
	* Analytics
	* Tracking von Commits und Tickets

Um ein paar Beispiele zu nennen die von diesem Aufgabenbereich abgedeckt werden:
* Mitentwicklung der Konzeption für die Entwicklungsumgebung sowie Code-Modularisierung
* Hat die Hoheit über die externe Performance
* Beäugt HTTP-Requests kritisch
* Hat das Performance Budget im Auge (hat Dateigrößen und Pageload im Blick)
* die Build-Tool-Chain in- und auswändig kennen
* die Test-Instanzen auf denen ihre Applikation läuft auf dem CI Server aufsetzen und dann später auch die Deployment-Instanzen
* Git Post-Commit-Hooks in die Applikation integrieren und die Test laufen lassen (Node.js/Protractor/PhantomJS oder gegen ein Selenium Grid wie Saucelab oder Testling oder BrowserStack) bevor irgendwas nach `master`gemerged wird
* sicherstellen, dass diese Server den rohen Code nehmen können und mit ein paar wenigen Kommandos die Applikation bauen können.
* Einrichten von Grunt Befehlen (AUTOMATISIERUNGSKÜNSTLER)
- die Leistung des Frontend Ops Engineers wird an Geschwindigkeit gemessen. Die Geschwindigkeit
	  - der Applikation
	  - der Tests
	  - der Builds
	  - des Deployments
	* und die Geschwindkeit mit der Teammitglieder den Operationsprozess verstehen.
* Dashboard einrichten für das Monitoring
* Meister über Graphen und Heap Snapshots
* Frontend Perf
* 


## Teil II: JavaScript Build Tools - Überblick über GruntJS
Der Automatisierungsteil von Frontend Ops ist ein riesiger Aufgabenbereich. 

## Teil III: Frontend Ops mit GruntJS



## Outro
