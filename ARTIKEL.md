# Frontend Ops & GruntJS, Teil I

Am 1. Juli 2014 hielt ich einen Vortrag an der deutschen Enterprise JavaScript Konferenz [EnterJS](http://enterjs.de) in Köln.

Der Vortrag war an Entwickler gerichtet, für die Frontend Ops ein neuer Begriff ist und die GruntJS oder ein ähnliches Werkzeug gar nicht oder noch nicht an vielen Stellen einsetzen. Das Ziel war es anhand des neu abgesteckten Gebiets der Frontend Operations aufzuzeigen, an welchen Stellen im Frontend-Entwicklungsprozess einer Applikation oder Webseite GruntJS einsetzbar ist um Prozesse zu automatisieren und zu optimieren.

Da der Vortrag nicht aufgezeichnet wurde, stelle ich ihn hiermit als dreiteiligen Artikel zur Verfügung. Dies ist der erste Teil. Die anderen beiden Teile werden hier verlinkt sobald sie verfügbar sind.

## Frontend Ops

In diesem ersten Teil geht es um die Frage was Frontend Ops ist und woher die Bezeichnung kommt.

### Die kurze Geschichte von Frontend Ops

Im Mai 2013 schrieb [Alex Sexton](http://alexsexton.com) einen Artikel über das [Deployment von JavaScript Applikationen](https://alexsexton.com/blog/2013/03/deploying-javascript-applications/). Da er zu der Zeit für Bazaarvoice gearbeitet hat, war sein Bericht sehr geprägt von den Eigenheiten dieses der von Bazaarvoice vertriebenen Applikation. 

Bazaarvoice wird als "Third-Party JavaScript App" auf Shopseiten eingebunden und erlaubt es Kommentare, Reviews und Bewertungen auf Artikeln zu hinterlassen. 

Alex beschreibt die Einbindung einer sogenannten "Scoutfile", die herausfindet in welchem Umfeld (Browser, Platform, mobil oder nicht) sich die Applikation befindet und dann eine für dieses Profil optimierte Version der Applikation nachzuladen.

Das ist ein Ansatz der für eine Third-Party Applikation durchaus wichtig und richtig ist, da man hier besonders darauf Wert legen sollte so wenig zusätzliche Last wie möglich hinzuzufügen. Beispielsweise bekommen moderne Browser Zepto.js anstatt jQuery in der App mitausgeliefert und Sprites können in modernen Browsern im CSS als data-URIs ausgeliefert werden während im IE6 (wenn man denn den unterstützen muss) die Sprites als separate Datei ausgeliefert werden müssen.

Alles in allem ist dieser Artikel sehr interessant und aufschlussreich, trifft aber so nicht auf jede JavaScript Applikation zu, was Alex in seinem Artikel gleich zu Anfang auch klar macht.

#### Der Leserbrief

Ein Leser dieses Artikels drückte in folgendem Kommentar seine Verwunderung über das beschriebene Vorgehen aus:

> With all due respect, **may I ask if you actually enjoy your job?** I am a dev, and I do enjoy using tech to do stuff to a point. If your role is to squeeze every last second of performance out of your app, then yea, all this stuff must be cool. BUT **if you are a coder doing something else and then come back to all of this as well, then wow, I don’t know how you haven’t gone mad already**. I’d be sick to the stomach if I had to do all of this, in addition to my usual work.

Er wunderte sich darüber wie man, wenn man als Entwickler an der Entwicklung einer Applikation arbeiten muss und immer wieder diese Optimierungen durchführen muss, nicht schon längst den Verstand verloren hat.

Alex beantwortete diese Frage mit der Auskunft, dass ihm sein Job Spaß macht, da sein Job eben **nicht** viele dieser Optimierungsaufgaben beinhaltet weil die meisten beschriebenen Tätigkeiten in dem Artikel komplett automatisiert sind.

Daraufhin stellte sich heraus, dass der "Leser" den Artikel gar nicht komplett gelesen hatte und ihm dadurch die Automatisierung entgangen ist.

#### Die Geburt von Frontend Ops

Nichtsdestotrotz brachte ihn diese Leserreaktion aber zum Nachdenken.

In seinem Artikel [Front-End Ops](http://www.smashingmagazine.com/2013/06/11/front-end-ops/), der ein paar Monate später auf Smashing Magazine publiziert wurde erklärt Alex folgendes:

> What I didn’t fully grasp was **how different the role in that article is from the picture that people have of a front-end developer in their head**. Up to this point, a front-end developer had just the few operations duties lumped into their role, and even then, many people chose to skip those steps (that’s why Steve Souders is constantly yelling at you to make your pages faster).

Im bisherigen Bild eines Frontend Developers fallen nur wenige "Operations-Aufgaben" in dessen Aufgabenbereich.

> I think things are about to shift, and I’d (humbly) like to help guide that shift, because I think it’ll be great for the Web.

Alex ist der Meinung, dass sich dies momentan ändert und er bietet mit seinem Artikel eine Möglichkeit diesen neuen wachsenden Aufgabenbereich besser abzustecken und gab ihm den Namen Front End Ops. 

Der Name ist angelehnt an [DevOps](http://en.wikipedia.org/wiki/DevOps), der eine Softwareentwicklungsmethode beschreibt die eine starke Kommunikation, Kollaboration und Integration zwischen Entwicklern und IT Operations erfordert. 

Die Tätigkeiten von DevOps und Frontend Ops ähneln sich, Frontend Ops ist aber natürlich an das Frontend angepasst und dafür erweitert.

Ich stimme in seiner Einschätzung überein und halte seinen Artikel für eine sehr sorgfältig ausgearbeitete und immer noch ziemlich erschöpfende Beschreibung dieses neuen Aufgabenbereiches für Frontend Entwickler.

### Ziele von Frontend Ops

Ich werde hier nicht auf jedes Detail von Frontend Ops eingehen. Wer sich für diese interessiert dem sei Alex' Artikel wärmstens ans Herz gelegt.

Ich möchte aber gerne durch die Beschreibung der Hauptziele von Frontend Ops kurz beschreiben um welche Tätigkeiten es sich hier generell handelt. 

#### Maximale Geschwindigkeit

Eines der zwei wichtigsten Ziele ist das Erreichen der maximalen Geschwindigkeit in allem. Es geht hier also nicht nur um die schnellstmögliche Auslieferung der Applikation oder Webseite an den Benutzer und eine schnelle Reaktionsfähigkeit der interaktiven Elemente. 
Es geht auch um das Erreichen der höchsten Geschwindigkeit in allen Bereichen und Prozessen des kompletten Entwicklungsprozesses.

Somit fallen sowohl Code-Organisation als auch das Aufsetzen von Automatisierungsvorgängen in den Tätigkeitsbereich von Frontend Operations Engineers. 

Sauber modularisierter Code und eine gute Dokumentation führt zu einer möglichst hohen generellen Geschwindigkeit der Entwicklung der Applikation und erlaubt es Neuzugängen möglichst schnell produktiv zu sein. Deshalb sind das Bereiche die für Frontend Operations generell interessant sind. 

Ein größerer Anteil der FeOps Tätigkeit ist das Automatisieren von Dateioperationen, Dateibereitstellungen und Deployments auf verschiedene Server. Hierbei handelt sich um Prozesse die sich ständig wiederholen und von einer Maschine schneller und fehlerfreier ausgeführt werden können als von Menschen. 

In allen Bereichen muss diese optimalste Geschwindigkeit über lange Zeit mindestens beibehalten und im besten Falle weiter verbessert werden. 

Das wichtigste Resultat von hohen Geschwindigkeiten ist gleichzeitig auch ein wichtiges Ziel: 

#### Glückliche Menschen

Es geht hier um alle Personen die in irgend einer Form mit der Webseite oder Applikation in Berührung kommen. Vom Entwickler über den Tester und dem Projektleiter bis hin zum Endbenutzer der Seite.

Entwickler die ohne unnötige Unterbrechungen arbeiten können und sich wirklich hauptsächlich nur auf die Funktionalität konzentrieren können sind glückliche Entwickler. 

Projektleiter und QA-Mitarbeiter sind glücklich wenn Funktionalität oder gar Teilfunktionalität schnell getestet werden kann und Fehler schnell behoben werden. 

Endbenutzer freuen sich über eine Seite die schnell lädt und tut was sie soll, außerdem freuen sie sich auch über das schnelle Beheben von Problemen. 

Alle Tätigkeiten die dieses ermöglichen, sind Frontend Ops Tätigkeiten. 

## Fortsetzung folgt...

Im zweiten Teil dieser Artikelreihe werde ich GruntJS als Werkzeug vorstellen mit dem man viele der angesprochenen Automatisierungen vornehmen kann. 


# Frontend Ops & GruntJS, Teil II

## Roboter

Um Menschen glücklich zu machen braucht man vor allem eins: Roboter. Roboter die uns die langweiligen Tätigkeiten abnehmen können. In unserem Fall hat der Roboter ein Wildschweingesicht.

### GruntJS

GruntJS ist ein JavaScript Task Runner und mittlerweile nicht mehr das einzige Werkzeug seiner Art.

In den letzten Monaten wurde immer wieder nach Vergleichen zwischen GruntJS und GulpJS gefragt. Dazu gibt es nur eine Antwort: Nein!

Die verschiedenen JavaScript Task Runner sind in der Regel alles gute Werkzeuge die bestimmte Probleme lösen. Es gilt also immer zu prüfen welches dieser Werkzeuge mein momentanes Problem am besten löst.

#### Installation

Um GruntJS zu installieren muss erst Node.js installiert werden. Dazu geht man einfach auf die nodejs.org und klickt auf den grünen Installbutton.
