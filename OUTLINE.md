# EnterJS Notes

## Aufwärmen
* Aufstehen, Liegestütze, strecken
* Hand geben

## Intro
## Teil I: Frontend Ops - Überblick



### Was ist ein Frontend Ops Engineer?
Wer von euch kann sich unter dem Begriff schon was vorstellen?

#### Geschichte
* 26.03.2013: Artikel von Alex Sexton: "[Deploying JavaScript Applications](https://alexsexton.com/blog/2013/03/deploying-javascript-applications)"
* 30.03.2013: Kommentar auf den oben genannten Artikel

> With all due respect, may I ask if you actually enjoy your job? I am dev, and I do enjoy using tech to do stuff - to a point. If your role is to squeeze every last second of performance out of your app, then yea, all this stuff must be cool. BUT if you are a coder doing something else and *then* come back to all of *this* as well, then wow, I don't know how you haven't gone mad already.
>
> I'd be sick to the stomach if I had to do all of this, in addition to my usual work."

* Führte zu einem Artikel am 11.06.2013: "[Front End Ops](http://www.smashingmagazine.com/2013/06/11/front-end-ops/)" auf Smashingmagazine

Alex Sexton:
> What I didn’t fully grasp was how different the role in that article is from the picture that people have of a front-end developer in their head. Up to this point, a front-end developer had just the few operations duties lumped into their role, and even then, many people chose to skip those steps (that’s why Steve Souders is constantly yelling at you to make your pages faster).
>
> I think things are about to shift, and I’d (humbly) like to help guide that shift, because I think it’ll be great for the Web.
 
Man kann sich um Details streiten der Artikel ist meines Erachtens aber sehr gut, ausführlich und erschöpfend


#### 3 Wesentliche Punkte

Auf einzelne Aufgaben gehe ich beispielhaft im Detail noch ein aber meiner Meinung nach kann man diese Disziplin in drei Hauptpunkte zusammenfassen.


* **Geschwindigkeit für alle Abläufe**
	* Nicht nur die generelle Geschwindigkeit der Webseite oder Applikation, sondern
		* Entwicklungsgeschwindigkeit
		* Geschwindigkeit nach Local, Dev, Stage (, QA?), Prod
		* Geschwindigkeit von Teilfunktionalität nach Dev (, Stage?)
		* Geschwindigkeit von Stage nach Prod
* **Glückliche Menschen**
	Glückliche Menschen kommunizieren besser, erzeugen kurz- und langfristig weit besseren Code und somit ein besseres Produkt mit weniger Fehlern oder zumindest leichter behebbare Fehler.
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
* **Messen, messen, messen**
	* Performance der App in versch. Szenarios
	* Performance der Build Prozesse
	* Performance der Deploymentprozesse
	* Monitoring, Alarme

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
Der Automatisierungsteil von Frontend Ops ist ein riesiger Aufgabenbereich und mittlerweile gibt es dafür einige JavaScript Tools, auf Node basierend, die uns bei der Automatisierung helfen können.

* Gulp
	Ein Streaming build System das auf Code statt Konfiguration setzt
* Broccoli (Browser Compliation Library)
	Ein low-level Build System für Projekte mit einer großen Anzahl von Dateien
* Fez
	Yet Another Build System
* Grunt
    Der JavaScript Task Runner. Benutzung basiert auf Konfiguration statt Code.

Wer die unnütze Grabenkriege im Internet verfolgt, weiß bestimmt dass Gulp und Grunt eine Weile stark in Konkurrenz zueinander standen. Es ist auch weiterhin unumstritten, das aufgrund seiner Architektur Gulp in bestimmten fällen schneller ist als Grunt. Gulp verwendet Streams und aggressive Parallelisierung der Tasks. Grunt's Architektur wird in der Zukunft jedoch genau die gleiche Architektur haben und somit wird der Unterschied lediglich CODE VS. CONFIG sein. Auf der anderen Seite, sprach der Gulp-Hauptentwickler schon öfters davon eine Abstraktion schaffen zu wollen die die Verwendung von Gulp durch Konfiguration ermöglicht. 

Die Waffe meiner Wahl für Frontend Ops ist und bleibt erstmal Grunt. Konfiguration über Code macht es zu einem Tool, dass nicht nur von JavaScript-Entwicklern verstanden und verwendet werden kann und der Umstand dass es ein Task Runner ist und nicht ein Werkzeug  dass speziell auf Build-Vorgänge oder anderes spezialisiert ist, macht es unheimlich vielseitig in der Anwendung.

Kurzüberblick über die Anwendung:
* Node und npm installieren
* npm install -g grunt-cli
* Projektordner erstellen
* Boilerplate Code einfügen (evtl. grunt-init verwenden)
	* package.json
	* Gruntfile.js
* Gewüschte Plugins installieren, z.B. grunt-contrib-concat
	* npm i --save-dev grunt-contrib-concat
* Auf die Pluginseite gehen und "Usage Example" suchen und nach dem Muster konfigurieren.

## Teil III: Frontend Ops mit GruntJS
Warum erzähl ich euch das alles? 

FeOps ist ein riesiger Bereich und auch wenn es das jetzt als neue Disziplin gibt, wird die Firma bei der ihr jetzt arbeitet wahrscheinlich nicht hergehen und eine Person anstellen die das Vollzeit macht. Trotzdem sind diese Punkte aber für fast jedes mittelgroße bis große Webprojekt essentiell um das bestmögliche Ergebnis möglichst effizient zu erreichen. 

Also müsst ihr herhalten und das könnt ihr und zwar sofort. 
Ich bin mir sicher, dass ihr in eurem Team verargumentieren könnt, dass eine Person einmal die Woche oder in einem anderen Rhytmus einen Tag lang FeOps-Tätigkeiten übernehmen kann.

Diese Person nimmt sich GruntJS zu Hand und kann sich damit in kurzer Zeit daran machen die grössten Engpässe in Entwicklung/Deployment/Code-Qualität usw. zu entfernen.

Ihr könnt prinzipiell sofort damit anfangen euer Leben und das eurer Mitarbeiter und Kunden zu verbessern. 

Ich gebe euch hier nun einen Rundumschlag über die vielen Möglichkeiten die ihr allein mit Grunt habt.

**Code**
	**Classics**
* grunt-contrib-concat
* grunt-contrib-uglify
* grunt-contrib-sass
	**Code-Quali**
* grunt-contrib-jshint
* grunt-jscs-checker
	**Präprozess**
* grunt-contrib-handlebars
* grunt-preprocess
* grunt-cdn
	**Modules**
* grunt-require
* grunt-browserify
	**Testing**
* grunt-karma
* grunt-protractor-runner
* grunt-githooks
* grunt-istanbul
* grunt-phantomjs
	**Messen**
* grunt-phantomas
* grunt-photobox
	**Deployment**
* grunt-ssh
* grunt-ftp
* grunt-sftp
* grunt-gh-pages
* grunt-shell
* grunt-jenkins
	**Produktivität**
* grunt-contrib-connect
* grunt-contrib-livereload
* grunt-devtools
* grunt-jira
* grunt-casper
* grunt-bump
* grunt-git

### Stories
* Deployment per Webinterface mit CasperJS & PhantomJS
* Shell-Befehle hintereinander ausführen: Build, Git push, copy, Git push, Jenkins build

### Tipps
* Yeoman
* Web Starter Kit
* Alex' Artikel
* 1. FEOC Videos auf Youtube

## Outro
