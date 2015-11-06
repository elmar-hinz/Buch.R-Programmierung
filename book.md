---
title: "Einführung in die Programmierung mit R"
author: "Elmar Alexander Hinz"
output: 
  html_document:
    toc: true
---


## Ist das Dein Buch?

Du willst also R lernen? Cool! Dafür kann es manche Gründe geben, aber sehr
wahrscheinlich willst Du R in Zukunft benutzen, um Daten zu analysieren und zu
visualisieren. Wenn Du dieses Buch liest, hast Du Dich bereits grundlegend über
R informiert.

Damit dieses Buch ein durchgängiges Anspruchsniveau erhält, muss ich mir
Gedanken über seine Leser machen, über Dich, darüber, was ich an Wissen und
Erfahrung voraussetzen kann. Es macht natürlich einen grossen Unterschied, ob
Du bereits mit anderen Sprachen gearbeitet hast oder mit R ganz neu in die Welt
Programmierung einsteigst. Beide Szenarios schätze ich als häufig ein. Ist das
also Dein Buch?

Das Buch ist primär dazu gedacht, R zu lernen, sekundär als möglicher Einstieg
in die Programmierung. Wenn Du bereits Erfahrung mit anderen Sprachen gesammelt
hast, macht das die Dinge einfacher, weil Du die Denkmuster und die
Terminologie bereits kennst.

Ich versuche die Beispiele einfach genug zu halten, dass Du auch ohne vorherige
Programmiererfahrung dem Buch folgen kannst. Das setzt aber eine sehr aktive
Herangehensweise von Deiner Seite voraus, denn das Programmieren lernst Du nur
indem Du es tust.

Erstens solltest Du Begriffe, die Dir fremd sind nachschlagen, z.B. mittels
Wikipedia. Zweitens brauchst Du eine spielerische, aktive Herangehensweisea.
Du musst viel ausprobieren, auch wenn Dich das Buch nicht direkt dazu
auffordert, also aus eigenem Antrieb, bis Du fühlst, die Idee verstanden zu
haben. Drittens brauchst Du den Mut Kapitel, die du nicht sofort verstehst, zu
überspringen und das vor zu ziehen, was Dir zugänglicher erscheint.

Wenn diese aktive Herangehensweise nicht Deinem Naturell entspricht, empfehle
ich, die Grundlagen des Programmierens auf andere Weise zu lernen, insbesondere
in einem Kursus unter Anleitung. Solche Kurse als Einstieg in die
Programmierung findest Du häufiger für andere Sprachen, wie Python, Java oder
JavaScript. Die Denkmuster und Arbeitstechniken sind übertragbar. Die modernen
Programmiersprachen sind sich ähnlicher als Du denkst.

Als Nachschlagewerk ist dieses Buch nicht gedacht. R hat eine gut
Online-Hilfe zum Nachschlagen der Funktionen. Rezepte für Problemstellungen
findest Du sowieso am besten mit Hilfe einer Suchmaschine.

## Einführung

### Hallo Welt in R


```r
print("Hallo Welt!")
```

```
## [1] "Hallo Welt!"
```

Bist Du enttäuscht? Nichts Neues im Vergleich zu anderen Sprachen?
R ist einfach zu lernen. Das ist gut so.

Charakteristisches für R zeigt dieses kleine Programm. Wir berechen die
Oberflächen meherer Planeten anhand ihres Radius, ohne dass eine Schleife
nötig wird.


```r
names <- c("Merkur", "Venus", "Erde", "Mars")
radii <- c(2440, 6052, 6371, 3389)
surfaces <- round(4 * pi * radii^2 / 1000) * 1000
paste(names, ":", radii, "km, ", surfaces, "km^2")
```

```
## [1] "Merkur : 2440 km,  74815000 km^2" "Venus : 6052 km,  460265000 km^2"
## [3] "Erde : 6371 km,  510064000 km^2"  "Mars : 3389 km,  144329000 km^2"
```

Davon machen wir noch - quick and dirty - einen explorativen Plot, um zu sehen,
wie die Fläche im Quadrat ansteigt.


```r
plot(radii, surfaces)
```

![plot of chunk planetsPlot](figure/planetsPlot-1.png) 

Wie viel Zeilen Code wäre in anderen Sprachen nötig, um Listen von Daten zu
berechnen und in einem Diagramm zu visualieren?

### Was ist R?

* R ist eine Multiparadigmensprache:
    * dynamisch
    * funktional
    * eingeschränkt objektorientiert
* R ist eine freie Software Suite
    * für statisiche Berechnungen und ihre Visualisierung
    * mit Interpreter, Shell, IDE und Bibliotheken
    * die auf Unix, MacOs und Windows installiert werden kann
* R ist in vielen Bereichen der Wissenschaft der de facto Standard zur
  Erstellung und Veröffentlichung von statistischen Forschungsergebnissen.
* R ist ein Werkzeug, das als Schnittstelle von grossen IT-Firmen in ihre
  Produkte implementiert wird.

### Was macht R besonders?

Zwei der Besonderheiten von R hast Du gerade kennen gerlernt. Erstens die
unkomplizierte Weise, ganze Listen von Daten zu verarbeiten, zweitens die
komfortablen Möglichkeiten, Daten als Diagramme zu visualisieren.

R versucht dem möglichst nahe zu kommen, wie der Wissenschaftler denkt.
Einerseits sind das nicht unbedingt Schleifen, wie beim Programmierer.
Andererseits sind das zum Beispiel die Zuweisungsoperatoren "<-", wie sie
in der wissenschaftlichen Schreibweise gebräuchlich sind.

Wie bei anderen Sprachen auch, ist vieles gewachsen und begründet sich dann
als "historisch bedingt". Zur Geschichte gibt es noch ein eigenes Kapitel.

Das Alleinstellungsmerkmal von R sind aber sicherlich die umfangreichen
frei verfügbaren Bibliotheken, die dem Wissenschaftler zur Verfügung stehen,
um Daten aufzuarbeiten, zu analysiern und zu visualisieren. Auch wie
das getan wird, ist wissenschaftlich fundiert. Die Schritte folgen
definierten Grammatiken.

Natürlich verabeiten alle Programmiersprachen Daten. Entscheidend ist also,
wie die Daten betrachtet und genutzt werden. In der Wissenschaft steht der
Erkenntnisgewinn im Vordergrund. Charakteristisch sind die Umformung der
Daten, die Analyse und die Visualisierung.

Vergleicht man das mit Twitter, steht dort der Transport und die Vervielfältigung
von Textnachrichten im Vordergrund, was zu anderen Anforderungen an die Software
führt. Vergleicht man das mit einem Betriebssystem, steht dort die Anbindung
der Hardware im Vordergrund, sowie die Aufteilung der Rechenzeit, was wiederum
ganz andere Anforderungen an die Software stellt.

Im Regelfall lädt R die Daten komplett in den Arbeitsspeicher, bevor es mit der
weiteren Verarbeitung beginnt. Das hat den Vorteil, dass Du sehr schnell und
flexibel auch mit grossen Datenmengen jonglieren kannst, Stichwort Exploration.
Für Twitter oder ein Betriebssystem wäre diese Herangehensweise gar nicht
möglich, weil die Daten kontinuierlich strömen. Mit diesem Feature setzt sich R
also zugleich auch eine wichtige Grenze. Für die Verabeitung von Datenstömen
ist R nicht optimiert.

### Ist R eine vollwertige Programmiersprache oder eher ein Werkzeug?

Die kurze Antwort ist, dass beides richtig ist. R ist durchaus eine
Programmiersprache, mit der man theoretisch alles programmieren kann.
Aber wie bereits angedeutet, ist jede Programmiersprache für bestimmte
Anwendungsbereiche optimiert.

Die Sprache alleine ist auch nicht das alles Entscheidende. Genauso wichtig
sind die verfügbaren Bibliotheken, Interpreter und Compiler, um das optimale
Einsatzgebiet einer Sprache zu bestimmen. R wurde von Wissenschaftleren für
Wissenschaftler entwickelt und gepflegt. Das hat das Profil der vorhandenen
Werkzeuge geprägt.

Datenanalyse wird aber auch in weiten Bereichen der Wirtschaft, der Politik
oder des Journalismus immer wichtiger. Ensprechend weitet sich aus das Spektrum
der Bibliotheken aus.

R ist heute u.a. geeignet, um datenzentierte Artikel und Bücher zu verfassen.
Dieses Buch ist mithilfe solcher Bibliotheken erstellt. Es enstehen
Bibliotheken, die die Veröffentlichung als Webseiten oder als mobile Apps
unterstützen, mit zunehmenden interaktiven Möglichkeiten. IBM, Oracle,
Microsoft, SAP, etc. implementieren Schnittstellen, um R als Werkzeug einbinden
zu können.

Die Entscheidung für die Sprache R wird also stark von den Bibliotheken
bestimmt, die für unterschiedliche Bereiche zur Verfügung stehen. Man kann R
als eine Sprache mit Bibilotheken betrachten. Die umgekehrte Perspektive ist
für viele Anwendungsfälle genauso wichtig, R als ein Werkzeug zu betrachten,
das über eine eigene Programmiersprache verfügt, so wie eine Datanbank über SQL
als Sprache verfügt.

Ich finde, dass R im Vergleich zu andern Sprachen noch zu viele Grenzen
hat, um es uneigeschränkt als Programmiersprache für generelle Bereiche zu
empfeheln, wie zum Beispiel Java oder C++. Neben seinem Speicherverhalten
erreicht es schnell Grenzen bei den Möglichkeiten der Objektorientieren
Programmierung. Geht es um Datenanalyse, ist es aber herausragend und baut
seinen Versprung eher noch aus.

R besetzte eine verwandte Lücke, für die Perl ursprünglich konzeptioniert war,
als "Practical Extraction and Report Language". Perl hat diese Nische
unerwartet verlassen und wurde die erste Sprache der Internet Programmierung.
In der Folge wurde es auf beiden Gebieten abgelöst, u.a wegen seiner Grenzen
bei der Objektorientieren Programmierung und der zu langsamen Erneuerung der
Sprache, aber vielleicht auch wegen dem Verlust seiner Spezialisierung. Wir
finden Parallelen in R, sowohl bei den Chancen als auch bei den Risiken. Die
Unterstützung durch Industrie und Wissenschaft ist aber viel massiver als in
der Geschichte von Perl.

In der Data Science ist derzeit Python der einzige ernst zu nehmende Konkurrent.
Für komplexe Anforderungen wird man R im Verbund mit anderer Software
einsetzen, möglicherweise gerade mit Python, oder auch mit völlig fachfremden
Sprachen. Dabei stellt sich im konkreten Fall die Frage, wo man die Daten
übergibt und in welcher Form. Im Verbund mit Python ist R der Daten-Spezialist
und Python eher der Generalist, der es mit der Welt verbindet.

### Die R-Infrastruktur

### Die Geschichte von R




## Los geht's

