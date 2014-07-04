# Frontend Ops & GruntJS

Am 1. Juli 2014 hielt ich diesen Vortrag an der deutschen Enterprise JavaScript Konferenz
EnterJS in Köln.

Der Talk war an Entwickler gerichtet, für die Frontend Ops ein neuer Begriff ist und die GruntJS oder ein ähnliches Werkzeug gar nicht oder noch nicht an vielen Stellen
einsetzen. Mit dem Ziel aufzuzeigen an welchen Stellen im Frontend-Entwicklunsprozess einer Applikation oder Webseite GruntJS einsetzbar ist um Prozesse zu automatisieren und zu optimieren.

Dieser Artikel ist dieser Talk in Blogartikelform.

Als erstes werde ich kurz auf die Geschichte von Fronend Ops eingehen, da diese neue Disziplin sehr gut und ausführlich
absteckt an welchen Stellen man automatisieren kann und sollte und mit welchen Zielen. Im zweiten Teil führe ich GruntJS
kurz ein um dann im dritten Teil mit einer beispielhaften Beschreibung eines optimierten Entwicklungsflusses abzuschliessen.

[Hier](#grunt-einführung) geht es direkt zur Grunt-Einführung und [hier](#feops-mit-grunt) zur Beschreibung des optimierten
Entwicklungsflusses.

## Die kurze Geschichte von Frontend Ops

Im Mai 2013 schrieb Alex Sexton einen Artikel über das [Deployment von JavaScript Applikationen](https://alexsexton.com/blog/2013/03/deploying-javascript-applications/). Da er zu der Zeit für Bazaarvoice, einer Third-Party Applikation, gearbeitet hat, war sein Bericht sehr geprägt von den Eigenheiten dieses Projektes. Beispielsweise beschrieb er die Einbindung einer sogenannten "Scoutfile", die
herausfindet in welchem Umfeld (Browser, Platform, mobil oder nicht) sich die Applikation befindet und dann eine für dieses Profil optimierte Version der Applikation nachlädt.

Das ist ein Ansatz der für eine Third-Party Applikation durchaus wichtig und richtig ist, da man hier besonders darauf Wert legen sollte so wenig zusätzliche Last wie möglich hinzuzufügen. 

Beispielsweise bekommen moderne Browser Zepto.js anstatt jQuery in der App mitausgeliefert und Sprites können in modernen Browsern im CSS als data-URIs ausgeliefert werden während im IE6 (wenn man denn den unterstützen muss) die ein Icon-Sprite als separate Datei ausgeliefert werden muss.

### Der Leserbrief

Ein Leser dieses Artikels drückte in folgendem Kommentar seine Verwunderung über dieses Vorgehen aus:

> With all due respect, **may I ask if you actually enjoy your job?** I am a dev, and I do enjoy using tech to do stuff to a point. If your role is to squeeze every last second of performance out of your app, then yea, all this stuff must be cool. BUT **if you are a coder doing something else and then come back to all of this as well, then wow, I don’t know how you haven’t gone mad already**. I’d be sick to the stomach if I had to do all of this, in addition to my usual work.

Er wunderte sich darüber wie man, wenn man als Entwickler an der Entwicklung einer Applikation arbeiten muss und immer wieder diese Optimierungen durchführen muss, nicht schon längst den Verstand verloren hat. 

Alex beantwortete diese Frage mit der Auskunft, dass ihm sein Job Spaß macht, da sein Job eben **nicht** viele dieser Optimierungsaufgaben beinhaltet weil die meisten beschriebenen Tätigkeiten in dem Artikel komplett automatisiert sind.

Daraufhin stellte sich heraus, dass der "Leser" den Artikel gar nicht komplett gelesen hatte und ihm dadurch die Automatisierung entgangen ist. 

### Die Geburt von Frontend Ops

Nichtsdestotrotz brachte ihn diese Leserreaktion aber zum Nachdenken. 
 
In seinem Artikel "Front-End Ops", der auf Smashing Magazine publiziert wurde erklärt er folgendes: 

> What I didn’t fully grasp was how different the role in that article is from the picture that people have of a front-end developer in their head. Up to this point, a front-end developer had just the few operations duties lumped into their role, and even then, many people chose to skip those steps (that’s why Steve Souders is constantly yelling at you to make your pages faster).

Im bisherigen Bild eines Frontend Developers fallen nur wenige "Operations-Aufgaben" in dessen Aufgabenbereich. 

> I think things are about to shift, and I’d (humbly) like to help guide that shift, because I think it’ll be great for the Web.

Alex ist der Meinung, dass sich dies momentan ändert und er bietet mit seinem Artikel "Front-End Ops" eine Möglichkeit diesen neuen wachsenden Aufgabenbereich besser abzustecken.

Ich stimme in seiner Einschätzung überein und halte seinen Artikel für eine sehr sorgfältig ausgearbeitete und immer noch ziemlich erschöpfende Beschreibung dieses neuen Aufgabenbereiches für Frontend Entwickler.

## Ziele von Frontend Ops

Ich werde hier nicht auf jedes Detail von Frontend Ops eingehen. Wer sich für diese interessiert dem sei Alex' Artikel wärmstens ans Herz gelegt. 

Ich möchte aber versuchen diese neue Disziplin über ihre beiden Hauptziele zu beschreiben.

Eines dieser beiden Ziele ist wahrscheinlich jetzt schon allen klar. 

### Maximale Geschwindigkeit

Es geht um das Erreichen der maximalen Geschwindigkeit. Und zwar geht es hier nicht nur um die schnellstmögliche Auslieferung der Applikation oder Webseite an den Benutzer und eine schnelle Reaktionsfähigkeit. Es geht auch um das Erreichen der höchsten Geschwindigkeit in allen Bereichen und Prozessen des kompletten Entwicklungsprozesses.

#### Maximale Entwicklungsgeschwindigkeit

Einmal muss die generelle Geschwindigkeit der Entwicklung durch eine klare Frontend Architektur und Modularisierung gesichert werden. Eine gute Dokumentation der Architektur ermöglicht es Neuzugängen möglichst schnell produktiv zu sein. 

Im Entwicklungsprozess sollte möglichst alles was nicht mit der Programmierung der Funktionalität der Webseite oder Applikation zu tun hat, automatisiert sein. Z.B. die Optimierung von Assets oder das Bereitstellen von Asset-Änderungen im lokalen Entwicklungsserver oder das Triggern von Tests und das Deployment auf andere Server. Gleichzeitig können über Automatisierung Störer eingerichtet werden die die Assetkompilierung oder Deploymentvorgänge stoppt wenn Tests nicht durchlaufen oder Best Practices oder Code Style nicht eingehalten werden. Das verlangsamt zwar kurzfristig die Entwicklungsgeschwindigkeit, langfristig jedoch wird die Entwicklungsgeschwindigkeit optimiert weil man damit vermeiden kann, dass sich sehr schwer zu findende Fehler einschleichen. 

Je nach Anforderung des Projektes kann hier mehr oder weniger optimiert werden. 

### Glückliche Menschen

Das zweite Hauptziel, dass auch direkt mit dem ersten zusammenhängt sind glückliche Menschen. Hier geht es auch wiederum nicht nur um die Benutzer der Seite sondern auch um alle die in irgend einer Form am Entwicklungsprozess beteiligt sind. 

Entwickler, die zügig arbeiten können und ihre Arbeit zügig überall dorthin deployen können wo es nötig ist, sind glücklich und produzieren langfristig guten Code und ein stabile Applikation. Projektleiter die frühzeitig in der Entwicklung Teilfunktionalitäten testen oder dem Kunden zeigen können sind glücklich. Angestellte in der Qualitätssicherung, die zügig testen können und gefundene Bugs schnell gefixt bekommen sind glücklich und sorgen auch wiederum langfristig für eine konsistent hohe Qualität. 

## Roboter

Um Menschen glücklich zu machen braucht man vor allem eins: Roboter. Roboter die uns die langweiligen Tätigkeiten abnehmen können. In unserem Fall hat der Roboter ein Wildschweingesicht.

### GruntJS

GruntJS ist ein JavaScript Task Runner und mittlerweile nicht mehr das einzige Werkzeug seiner Art. 

In den letzten Monaten wurde immer wieder nach Vergleichen zwischen GruntJS und GulpJS gefragt. Dazu gibt es nur eine Antwort: Nein!

Die verschiedenen JavaScript Task Runner sind in der Regel alles gute Werkzeuge die bestimmte Probleme lösen. Es gilt also immer zu prüfen welches dieser Werkzeuge mein momentanes Problem am besten löst.

#### Installation 

Um GruntJS zu installieren muss erst Node.js installiert werden. Dazu geht man einfach auf die nodejs.org und klickt auf den grünen Installbutton.




 






 



