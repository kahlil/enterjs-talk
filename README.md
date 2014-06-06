# EnterJS Notes

## Intro

## Teil I: Frontend Operations: eine neue Disziplin

* Mehr Applikationslogik wandert in den Client

### Frontend Operations Engineer

**tldr;** Sicherstellung von hoher Performance der Webseite um Zufriedenheit der Benutzer zu erhöhen, Sicherstellung flüssiger Entwicklungsprozesse und Deployments um die nachhaltige Gesundheit und positive Weiterentwicklung der Applikation oder Webseite zu gewährleisten.

* Experte im Hosten und ausliefern von Resourcen
* Grunt Pro
* Hat starke Meinungen zu Code-Modularisierung
* ermittelt den besten Weg um die einzelnen Komponenten einer Webapplikation zusammenzuführen
* Experte in Versionierung, Caching & Deployment
* Hat die Hoheit über die externe Performance
* Beäugt HTTP-Requests kritisch
* Hat das Performance Budget im Auge (hat Dateigrößen und Pageload im Blick)
* Hoheit über alles NACH der Funktionalität
* Hält exzellente Beziehungen zur QS-Abteilung (stellt sicher, dass Performance Tests auf grün sind)
* Ist die Brücke zwischen Intention und Realität einer Applikation/Webseite

### Warum?

* Arbeit kann nicht von einem einzelnen verrichtet werden
* Wenn es beim Feature-Entwickeln heiß her geht, dann werden i.d.R. Performance Tasks nach unten priorisiert
* Nicht jede Firma kann sich eine Person leisten die sich Vollzeit um FE Ops kümmert, aber selbst wenn ein Tag in der Woche für für FE Ops reserviert ist, gewinnt der Benutzer letztendlich
* **Es ist schlussendlich völlig egal wie viele Features die Webseite hat oder wie "sexy" die Features sind, wenn sie nicht schnell und mit Leichtigkeit beim Benutzer ankommen und die Performance danach nicht weiter unter Beobachtung bleibt.**
* Frontend Operations Engineers **ermöglichen nachhaltig eine positive Weiterentwicklung**

### Builds & Deployment

Klassische Aufgaben von Build bzw. Operations Engineers beinhalten:

* RPM Files generieren,
* EC2 Instanzen hoch fahren,
* CI Tools einsetzen
* Load Balancer auf neue Maschinen umswitchen

Für den Frontend Engineer werden einige dieser Aufgaben erhalten bleiben und aber auch neue dazu kommen.

Frontend Ops Engineer müssen

* die Build-Tool-Chain in- und auswändig kennen
* die Test-Instanzen auf denen ihre Applikation läuft auf dem CI Server aufsetzen und dann später auch die Deployment-Instanzen
* Git Post-Commit-Hooks in die Applikation integrieren und die Test laufen lassen (Node.js/Protractor/PhantomJS oder gegen ein Selenium Grid wie Saucelab oder Testling oder BrowserStack) bevor irgendwas nach `master`gemerged wird
* sicherstellen, dass diese Server den rohen Code nehmen können und mit ein paar wenigen Kommandos die Applikation bauen können.

Für viele Aufgaben die für den Frontend Operations Engineer anfallen wird oft GruntJS verwendet. Mit einem `grunt build` kann ein korrekt eingerichteter Server eine gebaute Version der Applikation bereitstellen um dann die Teste dagegen zu fahren.

FEOPS Engineers müssen sich um das Einrichten von Grunt Befehlen kümmern.

* JavaScript Module bauen (Require.js / Browserify)
* minifizieren
* konkatinieren
* 

## Teil II: JavaScript Build Tools - Überblick über GruntJS

## Teil III: Frontend Ops mit GruntJS



## Outro
