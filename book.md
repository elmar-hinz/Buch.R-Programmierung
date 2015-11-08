---
title: "Einführung in die Programmierung mit R"
author: "Elmar Alexander Hinz"
date: "2015"
output: 
  html_document:
    keep_md: yes
    toc: yes
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

> R is a free software environment for statistical computing and graphics.
> It compiles and runs on a wide variety of UNIX platforms, Windows and MacOS.
>
> https://www.r-project.org

* R ist eine Multiparadigmensprache:
    * dynamisch
    * funktional
    * eingeschränkt objektorientiert
* R ist eine freie Software Sammlung
    * für statisiche Berechnungen und ihre Visualisierung
    * mit Interpreter, Shell, IDE und Bibliotheken
    * die unter Unix, MacOs und Windows benutzt werden kann
* R ist in vielen Bereichen der Wissenschaft der de facto Standard zur
  Erstellung und Veröffentlichung von statistischen Forschungsergebnissen.
* R ist ein Werkzeug, das als Schnittstelle von grossen IT-Firmen in ihre
  Produkte implementiert wird.

### Was macht R besonders?

Zwei der besondere Stärken von R hast Du gerade kennen gerlernt. Erstens die
unkomplizierte Weise, ganze Listen von Daten so einfach zu verarbeiten, als sei
das ein einzelner Wert, zweitens die komfortablen Möglichkeiten, Daten als
Diagramme zu visualisieren. R ist zudem auf allen verbreiteten Betriebssystemen
einsetzbar, nämlich Linux, MacOS und Windows. Das ist vor allem im Vergleich
mit Exel ein Vorteil, nicht zuletzt im Hinblick auf die Reproduzierbarkeit von
Studien.

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

### Ist R eine Programmiersprache oder ein Werkzeug?

> R is a free software environment for statistical computing and graphics.
> It compiles and runs on a wide variety of UNIX platforms, Windows and MacOS.
>
> https://www.r-project.org

> R is more than a programming language. It is an interactive
> environment for doing statistics. I find it more helpful to think of R as
> having a programming language than being a programming language. The R
> language is the scripting language for the R environment, just as VBA is the
> scripting language for Microsoft Excel. Some of the more unusual features of
> the R language begin to make sense when viewed from this perspective."
>
> [John D. Cook](http://www.johndcook.com/blog/r_language_for_programmers/)

Die offizielle Definition lautet, R ist eine Entwicklungsumgebung für
statistische Berechnungen und Graphiken. John D. Cook gibt die sehr
diplomatische Definition, R sei eine Entwicklungsumgebung mit einer
Skriptsprache und damit mehr als eine Programmiersprache.

Tatsächlich stellt sich die Frage, wie weit R auch eine allgemein einsetzbare
Programmiersprache ist im Vergleich zu Java, C oder C++. Sicherlich ist es
heute noch nicht so allgemein einsetzbar, wie weitreichend es aber einsetzbar
ist, darauf fällt die Antwort sehr unterschiedlich aus, je nach Blickwinkel.

Oft lautet auch Frage auch, was im Bereich der Datenwissenschaft die bessere
Sprache ist, Python oder R. R hat in diesem Bereich die umfangreichere
Werkzeugsammlung, die Infrastruktur von Python ist breiter aufgestellt und kann
damit besser Brücken schlagen. In der Bioinformatik bespielsweise, wo
Algorithmen stärker im Vordergrung stehen als Datentabellen, Statistiken und
Diagramme, gibt es eine höhere Affinität zu Python. Beide Sprachen sind so
leicht zu lernen, dass nichts dagegen spricht sie gemeinsam einzusetzten.
Schliesslich werden Konzepte zur Datenberechnung, die sich in R bewährt haben
auch in Python übernommen, so dass die Grenzen zwischen beiden Sprachen
abnehmen.

Die Sprache alleine ist auch nicht das alles Entscheidende. Genauso wichtig
sind die verfügbaren Bibliotheken, Interpreter und Compiler, um das optimale
Einsatzgebiet einer Sprache zu bestimmen. R wurde von Wissenschaftleren für
Wissenschaftler entwickelt und gepflegt. Das hat das Profil der vorhandenen
Werkzeuge geprägt. Datenanalyse wird aber auch in weiten Bereichen der
Wirtschaft, der Politik oder des Journalismus immer wichtiger. Ensprechend
weitet sich aus das Spektrum der Bibliotheken aus.

R ist heute u.a. geeignet, um datenzentierte Artikel und Bücher zu verfassen.
Dieses Buch ist mithilfe solcher Bibliotheken erstellt. Es enstehen
Bibliotheken, die die Veröffentlichung als Webseiten oder als mobile Apps
unterstützen, mit zunehmenden interaktiven Möglichkeiten. IBM, Oracle,
Microsoft, SAP, etc. implementieren Schnittstellen, um R als Werkzeug einbinden
zu können.

Im Vergleich zu Java oder C++ ist R als universelle Programmiersprache heute
noch weniger geeignet. Erstens ist sind seine objektorientieren Möglichkeiten
noch nicht voll entwickelt, zweitens sind seine Bibliotheken sehr spezialisert
und drittens setzt sein Speicherverhalten konzeptionlle Grenzen, die aber
überwindbar sind.

R besetzte eine verwandte Lücke, für die Perl ursprünglich konzeptioniert war,
als "Practical Extraction and Report Language". Perl hat diese Nische
unerwartet verlassen und wurde die erste Sprache der Internet Programmierung.
In der Folge wurde es auf beiden Gebieten abgelöst, u.a wegen seiner Grenzen
bei der Objektorientieren Programmierung und der zu langsamen Erneuerung der
Sprache, aber vielleicht auch wegen dem Verlust seiner Spezialisierung. Wir
finden Parallelen in R, sowohl bei den Chancen als auch bei den Risiken. Die
Unterstützung durch Industrie und Wissenschaft ist aber viel umfassender als in
der Geschichte von Perl.

### Die R-Infrastruktur

### Die Geschichte von R



## Los geht's
### Hardware Anforderungen
### Installation
#### R
#### R Studio
### Programmausführung

R ist eine interpretierte Sprache. Ein Programm muss nicht als Ganzes
kompiliert werden um ausfürbar zu sein. Stattdessen wird eine Instruktion nach
der anderen entgegengenommen und direkt ausgeführt. Diese Instruktionen können
entweder einzeln in der Shell eingegeben oder als Liste in eine Datei
geschrieben werden. Damit erhältst Du dann ein Programmskript.

#### Shell

In der Shell gibtst Du Instruktionen ein, die Du nur einmalig ausführen willst
und nicht speichern. Beispiele sind:

* Aufruf von Programmenskripten.
* Aufruf der Hilfe.
* Austesten von Funktionen, um mehr über R zu lernen.
* Testen von Programmschnipseln, bevor Du sie in Dateien einfügst.
* Exploration von Daten. Nur was brauchbar ist, schreibst Du in Dateien.
* Benutzung der Shell als wissenschaftlicher Taschenrechner.

Es kann also sinnvoll sein, mehrere Shells parallel zu benutzen.

#### Dateien

Alles, was Du wiederholt ausführen oder aufheben willst, schreibst Du in
Dateien.  Das fängt beim Austesten mehrzeiliger Programmschnipsel, die du so
oft ausführst, bis sie funktionieren.

#### Bibliotheken

Bibliotheken sind Dateien, die Funktionen enthalten, die Du aus verschiedenen
Programmen heraus immer wieder benutzen willst. Entweder Du schreibst sie
selbst oder Du lädst Bibliotheken aus öffentlichen und privaten Repositories.

#### IDE RStudio

IDE heisst *integrated development environment*. *RStudio* integriert nicht nur
Shell und Editor für Programmscripte, sondern zeigt zum Beispiel auch direk die
erzeugten Diagramme an. Sie vereint also die verschiedenen Möglichkeiten zur
Programmausführung, mit weiteren nützlichen Werkzeugen.

### Hilfe



## Syntax

### Kommentare

Kommentare werden in R wie in Bash, Python oder Perl mit einer Raute
eingeleitet.


```r
# Dies ist ein Kommentar.

##################################################
# Dies ist ein Kommentar
# über mehrere Zeilen.
##################################################

print("Hallo Welt!") # Der Kommentar kann auch dahinter stehen.
```

```
## [1] "Hallo Welt!"
```

### Variablen

Variablennamen folgen grundsätzlich den Mustern verbreiteter Sprachen.

* Namen bestehen aus Buchstaben, Ziffern, Unterstrichen oder Punkten.
* Namen starten mit einem Buchstaben oder mit einem Punkt.
* Nach einem anführenden Punkt darf keine Ziffer folgen (falsch: .2x).
* Reservierte Worte dürfen nicht verwendet werden.

Reservierte Worte sind kein Ding. Du erkennst das automatisch an der
Fehlermeldung.

Das überraschende ist der Punkt als gültiger Bestandteil von Variablennamen. In
anderen Sprachen werden damit Elemente eines Objektes angesprochen. Das
geschieht in R mittels des Dollarzeichens.


```r
a <- list("alpha" = 1, "beta" = 2) # Variable a befüllt mit einer Liste.
a.punkt <- "Punkt" # Eine ganz andere Variable, die nur aussieht wie a.
print(a) # Die Liste a enthält nicht "Punkt" und wurde auch nicht überschrieben.
```

```
## $alpha
## [1] 1
## 
## $beta
## [1] 2
```

```r
print(a.punkt) # "Punkt" wird unabhängig ausgegeben.
```

```
## [1] "Punkt"
```

```r
print(a$beta) # Mit dem $-Zeichen wird ein Element von a angesprochen.
```

```
## [1] 2
```

```r
print(a$punkt) # Dieses gibt es dagegen nicht.
```

```
## NULL
```

Tip: Wenn Du Verwirrungen mit anderen Sprachen minimieren willst, verwendest Du
den Punkt als Worttrenner nicht. Er ist eher eine historische Erblast als ein
Feature. Die besseren Alternativen sind Unterstrich oder CamelCase.

### Zuweisungen

Kurz gesagt, die Zuweisung zu Variablen erfolgt in R mittels des
Zuweisungsoperators `<-`  während die Zuweisung zu Funktionsparametern und zu
Namen in Listen und Data-Frames mit dem Gleichheitszeichen `=` erfolgt.
Ausserdem gibt es die Zuweisung zu Variablen oberhalb des eigenen
Sichtbarkeitsbereiches mittels `<--`. Das wird im entsprechenden Kapitel näher
erklärt.

Dieses Beispiel zeigt die Anwendung von `<-` und `=`.


```r
##################################################
# Create a dataframe with calculated planet data.
#
# @param names Characters of names.
# @param radii Numbers of radii.
# @return data.frame
##
setupPlanets <- function(names, radii) {
     data.frame(
          Name = names,
          Radius = radii,
          Diameter = 2 * radii,
          Perimeter = 2 * pi * radii,
          Surface = 4 * pi * radii^2,
          Volume =  4/3 * pi * radii^3
    )
 }

input <- list(
    names = c("Merkur", "Venus", "Erde", "Mars"),
    radii = c(2440, 6052, 6371, 3389)
)
planets <- setupPlanets(radii = input$radii, names = input$names)
print(planets)
```

```
##     Name Radius Diameter Perimeter   Surface       Volume
## 1 Merkur   2440     4880  15330.97  74815144 6.084965e+10
## 2  Venus   6052    12104  38025.84 460264737 9.285074e+11
## 3   Erde   6371    12742  40030.17 510064472 1.083207e+12
## 4   Mars   3389     6778  21293.72 144328800 1.630434e+11
```

Hier definiere ich eine Funktion und weise sie der Variablen `setupPlanets`
mittels des `<-`-Operators zu.  Das speichern ganzer Funktionen in Variablen
charakterisiert eine funktionale Programmiersprache. Eine solche Zuweisung
erfolgt auch bei den Variablen `input` und `planets`, denen eine Liste bzw. ein
Data-Frame zugewiesen wird.

Sowohl beim Data-Frame als auch bei der Liste werden die einzelnen benannten
Elemente mittels `=` zugewiesen. Das Gleichheitszeichen wird auch verwendet, um
beim Funktionsaufruf Parameter mit ihrem Namen, statt ihrer Reihenfolge
anzusprechen. Hier habe ich die Reihenfolge vertauscht, um das zu
demonstrieren.

#### Diskussion der Alternativen

Es ist oft, aber eben nicht immer, technisch möglich Variablen mittels `=`
statt mittels `<-` zuzuweisen. Weil das ein Zeichen weniger zu tippen ist und
den Zuweisungen in vielen anderen Programmiersprachen entspricht, wird Dir das
im Code vieler Leute begegnen. Um einen klaren, einheitlichen Programmierstil
zu pflegen, solltest Du aber konsequent `<-` für die Zuweisung von Variablen
benutzen. Das ist einfach R-stylisch.

Die Zuweisung mittels `<--` ist möglich, aber für die Zuweisung an übergeordnete
Sichtbarkeitsbereiche gedacht. Du musst wissen, was du tust. Dazu später.

`->` macht genau dasselbe wie `<-`. Nicht dass Du denkst die Variable käme
dann nach rechts. Es ist also nicht intuitiv verständlich.

Analog ist `-->` dasselbe `<--` und nicht intuitiv verständlich.

Also:

* `=` Ist nicht überall einsetzbar und nicht R-stylisch.
* `->` Ist verwirrend.
* `<--` Du solltest wissen was Du tust.
* `-->` Ist verwirrent und Du solltest wissen, was Du tust.

Darum: Variablenzuweisung mittels `<-` bevorzugen.

### Namensräume

Variablen können bereits Funktionen oder Daten enthalten, auch die aus
den Basis-Paketen und die aus den Bibliotheken, die Du lädst.

Du musst also
aufpassen, dass Du keine Namen von Funktionen oder Daten überschreibst,
jedenfalls nicht solche, die Du später noch verwenden willst.

Tust Du es doch, dann kannst du die Variablen der Pakte aber immer noch über
ihren Full Qualified Name ansprechen. Das kann einerseits lohnenswert sein, um
einen sprechenden Variablennamen wie "data" frei einsetzen zu können,
andererseits  kann es auch eingefleischte R-Benutzer verwirren, wenn der
vertraute Name "zweckentfremdet" wird.


```r
# Die Funktion print ist im Paket base
base::print("Hallo")
```

```
## [1] "Hallo"
```

```r
# Das Paket base ist per default geladen.
# Darum kann base::print() verkürzt angesprochen werden.
print("Hallo")
```

```
## [1] "Hallo"
```

```r
# Die Variable print wird hier mit einer Funktion definiert.
print <- function(...) { "Nope" }
# Was passiert jetzt?
print("Welt")
```

```
## [1] "Nope"
```

```r
# Der Fully Qualified Name funktioniert weiterhin.
base::print("Welt")
```

```
## [1] "Welt"
```

```r
# Definition aufheben.
remove(print)
# Jetzt wird wieder base::print() angesprochen.
print("Welt")
```

```
## [1] "Welt"
```

### Blöcke und Einrückungen

### Coding Guidelines




## Datentypen

### Vektoren

### NA und NAN

### Wahr und falsch

### Text

### Zahlen

### Funktionen


## Operatoren



## Kontrollstrukturen



## Komplexe Datentypen

### Matrix

### Data Frame


## Sichtbarkeitsbereiche (Scopes)

### Lexikalische Sichtbarkeitsbereiche

### Closures

### Klassen und Objekte


## Functionals



## Testen


## Bibliotheken

### dplyr

### ggplot2

### knitr


