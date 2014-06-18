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
* CSS generieren
* Bilder optimieren
* SVGs optimieren
* Sprites erstellen
* Request reduzieren wo es geht und Sinn macht


### Glückliche Entwickler

* FEOPS Engineers stellen sicher, dass **alle Build Vorgänge auf den Maschinen der Entwickler funktionieren**
* `grunt test` sollte alles lokal bauen, ausliefern und testen können (mit Webdriver API Server)
* ermöglichen den Entwicklern die Applikation in die CI Umgebung auszuliefern und dort zu testen
* entfernen Single-Points-Of-Failure vom Deployment (Github-Ausfall würde sie nicht beunruhigen)
- ermöglichen interne Deployments von Feature Branches und zukünftigen Release Branches
- stellen sicher, dass QA Teams die Seite einfach Testen können und Manager sehr einfach Demos von unfertigen Features zeigen können
- helfen dabei, verschiedene Builds der Applikation für die Kernbenutzer der Applikation zu schaffen, wenn nötig. Muss für die Entwickler transparent bleiben
- ermöglichen und vereinfachen den Prozess eine Applikation zu builden, Assets an die CDNs auzulieferen und die Livestellung des ganzen
- implementiert schnelle Rollbacks
- **automatisiert alles**

### Leistungsmessung

- die Leistung des Frontend Ops Engineers wird an Geschwindigkeit gemessen. Die Geschwindigkeit
  - der Applikation
  - der Tests
  - der Builds
  - des Deployments
und die Geschwindkeit mit der Teammitglieder den Operationsprozess verstehen.

#### Dashboard

FEOPSE verbringend die meiste Zeit in einem Dashboard dass sie ständig mit Daten füttert. Daten sind König wenn es um Geschwindigkeit geht. Das Dashboard lädt die Applikation ständig in verschiedenen Browsern und misst ständig die Performance der Seite.

* Das Dasboard lädt auch die neuesten PRs und Commits, einfach alles an was FEOPSE rankommen.
* Kennt alle Umstände eines Performance-Verlust.
* Performance-Verlust hängt direkt mit einer Änderung zusammen.
  * Neuer Server?
  * Code-Diff?
  * Neue Abhängigkeit?
  * Ein Ausfall?
  * etc.

**Graphen**
* zu HTTP Load
* CSS, JS Load minified & gzipped
* ungzipped JS Load um den Effekt von Code Parsing auf Mobile zu messen
* benutzt Tools wie mod_pagespeed und nginx_pagespeed um Fehler zu vermeiden
* Meister der Dev- und Messtools
* flame graphs, Heap Snapshots
* fps Messung
* layout thrashing vermeiden
* baut Hauptspeicherprofile
* Auge auf: Compositing, Rendering und die generelle visuelle Performance der Applikation
* Alles für Desktop und Mobile sowie das Tracken von Trends in diesen Gebieten

**Paralellisieren**
* alles wird fanatisch parallelisiert
* Tracking via .har-Dateien und Wasserfallgraphen
* durschnittl. Laufzeit der Tests, Build & Deploys messen und kämpfen um diese niedrig zu halten
* Auch wenn keine Kontrolle über langsame API Requests besteht, ist es wichtig zu wissen, das die Quelle des Geschwindigkeitverlusts ist
* Alarme werden ausgelöst wenn akzeptable Limits überschritten werdeh


### Error-Monitoring und Logs
* in der FE Ops Welt ist das in der Regel eine Analytics Tool
* niedrige Fehlertoleranz intern
* konstante Prüfung auf XSS-Schwachstellen
* hat eine konstanten Überblick über den Zustand der Applikation in Produktion

### Alles frisch und stabil halten
* FEOPS würden alle Dependencies Up-To-Date halten (jQuery, Grunt, Node etc.)
* enge Zusammenarbeit mit Applikations-Architekten um sicher zu stellen, dass die Applikation an keiner Stelle nachhängt oder unstabil ist
* stellt sicher dass es auch lange nach Launch der Applikation die Arbeit an der Applikation Spaß macht

## Teil II: JavaScript Build Tools - Überblick über GruntJS

Sehr viele dieser

## Teil III: Frontend Ops mit GruntJS



## Outro
