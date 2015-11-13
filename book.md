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

Ich schreibe dieses Buch nicht aus der Perspektive eines Experten in R, sondern
aus der Perspektive eines erfahren Programmierers, der mit großer Neugierde
selbst die Welt von R erkundet. Auf diese Reise will ich Dich mitnehmen. Wir
werden Parallelen zu anderen Programmiersprachen ziehen. Wir werden seltener
die trockene Dokumentation heran ziehen, als R immer wieder aktiv aus sein
Verhalten testen, basierend auf meiner Erfahrung, was in der Programmierung
wichtig ist. Learning-By-Doing und Testing sind zwei Prinzipien, die ich beim
Lernen einer Programmiersprache für sehr wichtig halte.

Damit dieses Buch ein durchgängiges Anspruchsniveau erhält, muss ich mir
Gedanken über seine Leser machen, über Dich, darüber, was ich an Wissen und
Erfahrung voraussetzen kann. Es macht natürlich einen großen Unterschied, ob
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

Erstens solltest Du Begriffe, die Dir fremd sind nachschlagen, zum Beispiel in
der Wikipedia. Zweitens brauchst Du eine spielerische, aktive Herangehensweise.
Du musst viel ausprobieren, auch wenn Dich das Buch nicht direkt dazu
auffordert, also aus eigenem Antrieb, bis Du fühlst, die Idee verstanden zu
haben. Drittens brauchst Du den Mut Kapitel, die du nicht sofort verstehst, zu
überspringen und das vor zu ziehen, was Dir zugänglicher erscheint.

Wenn diese selbständig, aktive Herangehensweise nicht Deinem Naturell
entspricht, empfehle ich, die Grundlagen des Programmierens auf andere Weise zu
lernen, insbesondere in einem Kursus unter Anleitung. Solche Kurse als Einstieg
in die Programmierung findest Du häufiger für andere Sprachen, wie Python, Java
oder JavaScript. Die Denkmuster und Arbeitstechniken sind übertragbar. Die
modernen Programmiersprachen sind sich ähnlicher als Du denkst.

Als Nachschlagewerk ist dieses Buch nicht gedacht. R hat eine sehr gute
interaktive Hilfe zum Nachschlagen der Funktionen. Rezepte für konkrete
Problemstellungen findest Du schneller mit Hilfe einer Suchmaschine als mit
einem Buch.

## Einführung

### Hallo Welt in R


```r
print("Hallo Welt!")
```

```
## [1] "Hallo Welt!"
```

Bist Du enttäuscht? Nichts Neues im Vergleich zu anderen Sprachen?  R ist eben
leicht zu lernen.

Charakteristisches für R zeigt dieses kleine Programm. Wir berechnen die
Oberflächen mehrerer Planeten anhand ihres Radius, ohne dass eine Schleife
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

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 

**Aufgabe:** Wie viel Zeilen Code wäre in anderen Programmiersprache, die Du
kennst, nötig, um Listen von Daten zu berechnen und in einem Diagramm zu
visualisieren?

### Die Funktion print()

Die Ausgabe von Variablen ist in einem Lehrbuch so wichtig, dass ich die
Funktion `print()` gleich hier anspreche.


```r
print("Hallo!") # Direkte Ausgabe des Strings
```

```
## [1] "Hallo!"
```

```r
hallo <- "Hallo!"
print(hallo) # Ausgabe der Variablen hallo
```

```
## [1] "Hallo!"
```

Was bedeuten die Zeichen vor der Ausgabe?

Die beiden Rauten `##` vor der Ausgabe sind Kommentarzeichen. Sie bewirken,
dass die Zeile nicht ausgeführt wird, wenn Du die Ausgabe mit "Copy and Paste"
übernimmst. Bei einer gedruckten Ausgabe des Buches, geht das nicht. Sie dienen
auch dazu, die Ausgabe als Ausgabe zu kennzeichnen.

Jetzt zähle ich von 1 bis 50


```r
print(1:50)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46
## [47] 47 48 49 50
```

Du siehst, dass die Zahl in eckigen Klammern dem Index der ersten Zahl in
jeder Reihe entspricht.

**Aufgabe:** Fängt die Aufzählung mit null oder eins an?

Bei Zahlen von 1 bis 50 bringt Dir das keinen besonderen Nutzen. Schütteln wir
die Zahlen also einmal ordentlich durch.


```r
print(sample(1:50))
```

```
##  [1] 40 19  5 46 50 26 44 48 29 20 25 24 18 12 32 45 10 15 35  6 49 11 27
## [24]  7 30  8 17 38 14 42  9 37 41 31 22 47 16  3  1 43 21 13  2 34 39 36
## [47]  4 28 23 33
```

**Aufgabe:** Welche Zahl hat den Index 30?

Meist wird die Funktion `print()` aber im Verborgenen ausgeführt. Werte werden
automatisch ausgedruckt, wenn Du sie nicht in eine Variable schreibst oder
anders weiter verwendest. Von diesem Feature mache ich in fast allen Beispielen
dieses Buches Gebrauch.


```r
hallo <- "hallo" # wird nicht ausgedruckt
"HALLO" # wird ausgedruckt
```

```
## [1] "HALLO"
```

Ausnahme: Werte werden nicht automatisch ausgedruckt, wenn sie in Schleifen
stehen.


```r
for(counter in 1:2) {
    print("Hallo")
    "Welt"
}
```

```
## [1] "Hallo"
## [1] "Hallo"
```

**Aufgabe:** Gib die obigen Beispiele ohne `print()` aus, sobald Du R
installierst hast.

* `"Hallo"`
* `hallo <- "Hallo!"; hallo`
* `1:50`
* `sample(1:50)`

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
    * für statistische Berechnungen und ihre Visualisierung
    * mit Interpreter, Shell, IDE und Bibliotheken
    * die unter Unix, Mac OS und Windows benutzt werden kann
* R ist in vielen Bereichen der Wissenschaft der de facto Standard zur
  Erstellung und Veröffentlichung von statistischen Forschungsergebnissen.
* R ist ein Werkzeug, das als Schnittstelle von großen IT-Firmen in ihre
  Produkte implementiert wird.

### Was macht R besonders?

Zwei der besondere Stärken von R hast Du gerade kennen gelernt. Erstens die
unkomplizierte Weise, ganze Listen von Daten so einfach zu verarbeiten, als sei
das ein einzelner Wert, zweitens die komfortablen Möglichkeiten, Daten als
Diagramme zu visualisieren. R ist zudem auf allen verbreiteten Betriebssystemen
einsetzbar, nämlich Linux, Mac OS und Windows. Das ist vor allem im Vergleich
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
um Daten aufzuarbeiten, zu analysieren und zu visualisieren. Auch wie
das getan wird, ist wissenschaftlich fundiert. Die Schritte folgen
definierten Grammatiken.

Natürlich verarbeiten alle Programmiersprachen Daten. Entscheidend ist also,
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
flexibel auch mit großen Datenmengen jonglieren kannst, Stichwort Exploration.
Für Twitter oder ein Betriebssystem wäre diese Herangehensweise gar nicht
möglich, weil die Daten kontinuierlich strömen. Mit diesem Feature setzt sich R
also zugleich auch eine wichtige Grenze. Für die Verarbeitung von Datenströmen
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
damit besser Brücken schlagen. In der Bioinformatik beispielsweise, wo
Algorithmen stärker im Vordergrund stehen als Datentabellen, Statistiken und
Diagramme, gibt es eine höhere Affinität zu Python. Beide Sprachen sind so
leicht zu lernen, dass nichts dagegen spricht sie gemeinsam einzusetzen.
Schließlich werden Konzepte, die sich in R bewährt haben auch in Python
übernommen, so dass die Grenzen zwischen beiden Sprachen abnehmen.

Die Sprache alleine ist auch nicht das alles Entscheidende. Genauso wichtig
sind die verfügbaren Bibliotheken, Interpreter und Compiler, um das optimale
Einsatzgebiet einer Sprache zu bestimmen. R wurde von Wissenschaftlern für
Wissenschaftler entwickelt und gepflegt. Das hat das Profil der vorhandenen
Werkzeuge geprägt. Datenanalyse wird aber auch in weiten Bereichen der
Wirtschaft, der Politik oder des Journalismus immer wichtiger. Entsprechend
weitet sich aus das Spektrum der Bibliotheken aus.

R ist heute unter anderem geeignet, um datenzentierte Artikel und Bücher zu verfassen.
Dieses Buch ist mithilfe solcher Bibliotheken erstellt. Es enstehen
Bibliotheken, die die Veröffentlichung als Webseiten oder als mobile Apps
unterstützen, mit zunehmenden interaktiven Möglichkeiten. IBM, Oracle,
Microsoft, SAP, et cetera implementieren Schnittstellen, um R als Werkzeug einbinden
zu können.

Im Vergleich zu Java oder C++ ist R als universelle Programmiersprache heute
noch weniger geeignet. Erstens ist sind seine objektorientierten Möglichkeiten
noch nicht voll entwickelt, zweitens sind seine Bibliotheken sehr spezialisiert
und drittens setzt sein Speicherverhalten konzeptionelle Grenzen, die aber
überwindbar sind.

R besetzte eine verwandte Lücke, für die Perl ursprünglich entworfen wurde, als
"Practical Extraction and Report Language". Perl hat diese Nische unerwartet
verlassen und wurde die erste Sprache der Internet Programmierung.  In der
Folge wurde es auf beiden Gebieten abgelöst, unter anderem wegen seiner Grenzen
bei der objektorientierten Programmierung und der zu langsamen Erneuerung der
Sprache, aber vielleicht auch wegen des Verlustes seiner Spezialisierung. Wir
finden Parallelen in R, sowohl bei den Chancen als auch bei den Risiken. Die
Unterstützung durch Industrie und Wissenschaft ist aber viel umfassender als in
der Geschichte von Perl.

### Die R-Infrastruktur

### Die Geschichte von R



## Los geht's

### Hardware Anforderungen

Ich setze in diesem Buch voraus, dass Du über einen zeitgemäßen Rechner
verfügst, PC oder Mac. Damit meine ich dass er nicht unbedingt älter als 5
Jahre ist. Grenzfälle lassen sich im Rahmen einer Einführung leider schlecht
behandeln.

Die Programme **R** und **RStudio** selbst nehmen nur wenige hundert Megabyte
ein. Allenfalls bis 2 GB Arbeitsspeicher werden sie spürbar, wenn Du
gleichzeitig noch viele andere Programme geöffnet hast.

Der entscheidende Faktor ist die Menge der Daten, welche Du in den
Arbeitsspeicher lädst. Für die Übungen in diesem Buch wirst Du da nicht an
Grenzen stoßen. Sobald Du aber mit realen Daten arbeitest, sind der Datenmenge
nach oben keine Grenzen gesetzt, Deinem Arbeitsspeicher dagegen schon.

Ohne besondere Maßnahmen lädt R die Gesamtmenge der Daten in den
Arbeitsspeicher bevor es damit arbeiten kann. Man sagt daher als Faustregel,
dass der Arbeitsspeicher mindestens doppelt so groß seine sollte, wie die
zu verarbeitende Datenmenge.

Dabei liegt die Betonung auf mindestens, denn dann musst Du immer noch
intelligent programmieren. Stell Dir vor, die Daten füllen Deinen halben
Arbeitsspeicher aus. Könntest Du dann eine Kopie der Daten in eine zweite
Variable speichern? In der zweiten Hälfte Deines Arbeitsspeichers liegen ja
auch Betriebssystem und Programme. Der Rechner würde wahrscheinlich heftig
anfangen zu swappen.

Swappen heißt, der Rechner schreibt unbenutzte Arbeitsspeicherbereiche auf die
Festplatte und lädt sie, sobald sie wieder gebraucht werden. Das bremst bis zur
Unbenutzbarkeit.

### Installation
#### R
#### R Studio
### Programmausführung

R ist eine interpretierte Sprache. Ein Programm muss nicht als Ganzes
kompiliert werden um ausführbar zu sein. Stattdessen wird eine Instruktion nach
der anderen entgegengenommen und direkt ausgeführt. Diese Instruktionen können
entweder einzeln in der Shell eingegeben oder als Liste in eine Datei
geschrieben werden. Damit erhältst Du dann ein Programmskript.

#### Shell

In der Shell gibst Du Instruktionen ein, die Du nur einmalig ausführen willst
und nicht speichern. Beispiele sind:

* Aufruf von Programmskripten.
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

IDE heißt *integrated development environment*. *RStudio* integriert nicht nur
Shell und Editor für Programmskripte, sondern zeigt zum Beispiel auch direkt die
erzeugten Diagramme an. Sie vereint also die verschiedenen Möglichkeiten zur
Programmausführung, mit weiteren nützlichen Werkzeugen.

### Hilfe



## Syntax

### Kommentare

Kommentare werden in R wie in Bash, Python oder Perl mit einer Raute
eingeleitet. Kommentare dienen der Dokumentation. Die Zeilen werden
nicht ausgeführt.


```r
# Dies ist ein Kommentar.

################################################################################
# Dies ist ein Kommentar über mehrere Zeilen. Die Rahmenbalken sind 80 Zeichen
# lang. Sie werden auch mit einer Raute eingeleitet und sind daher einfach
# ein Kommentar.
################################################################################

# Ein mehrzeiliger Kommentar muss natürlich nicht immer solche Rahmenbalken
# haben. Ein solcher Rahmen eignet sich gut für das Copyright im Seitenkopf
# einer Datei oder als Kopf über einer Funktionsdefinition. Auch um wichtige
# Hinweise zu betonen, ist ein Rahmen geeignet.

print("Hallo Welt!") # Der Kommentar kann auch hinter einer Instruktion stehen.
```

```
## [1] "Hallo Welt!"
```

Eine Raute innerhalb eines Strings ist kein Kommentar.


```r
print("Das Zeichen # ist hier Bestandteil des Strings.")
```

```
## [1] "Das Zeichen # ist hier Bestandteil des Strings."
```

Schreibt die Raute dagegen vor eine Instruktion, so wird die Instruktion selbst
zum Kommentar und damit nicht mehr ausgeführt. Das ist ein gängiges Mittel, um
Bereiche im Programmcode vorübergehend auszuschalten. Man nennt es
Auskommentieren.


```r
# print("Dies wird nicht ausgegeben.")
```

### Instruktionen

Instruktionen werden wie in C mittels Semikolon getrennt.


```r
x <- "Hallo Welt!"; print(x);
```

```
## [1] "Hallo Welt!"
```

Am Zeilenende können diese ausgelassen werden. Das ist die Regel.


```r
x <- "Hallo Welt!"
print(x)
```

```
## [1] "Hallo Welt!"
```

### Blöcke und Einrückungen

Programmcode wird in Bereiche eingeteilt, die gezielt ausführbar sind. Ein
solcher Bereich wird Block genannt und besteht aus mehreren Zeilen von
Instruktionen. Beispiele solcher Blöcke sind Funktionen, Schleifen oder die
unterschiedlichen Zweige von If-Else-Bedingungen. Daraus ergibt sich, dass die
Blöcke verschachtelt auftreten, wenn zum Beispiel eine Funktion eine Schleife
enthält.


```r
# Ein Funktionsblock, der einen Schleifenblock enthält.
show <- function() {
    for(i in 1:3) {
        print(i);
    }
}
show()
```

```
## [1] 1
## [1] 2
## [1] 3
```

Wie werden solche Blöcke nun definiert?

Drei Techniken sind bei Programmiersprachen verbreitet, erstens Schlüsselworte
(Keywords), zweitens Einrückungen (Indentation, Off-Side-Rule), drittens
geschweifte Klammern. Keywords wurden bereits in den 1950er von ALGOL benutzt.
Heute findest Du sie zum Beispiel in Ruby und Bash. Off-Side-Rule wird u.a.
verwendet von Python, YAML und CoffeScript und lässt sich bis ins Jahr 1966
zurück verfolgen. Die geschweiften Klammern wurden 1972 mit C eingeführt und
haben heute eine weite Verbreitung so in C++, Java, C#, JavaScript, Perl oder
Go.

R verwendet geschweifte Klammern wie C. Gerade mit einer deutschen Tastatur
sind diese Klammern lästig zu tippen und einrücken muss man den Code für die
Lesbarkeit genau so wie bei der Off-Side-Rule. Es ist vor allem mehr Arbeit. Im
Vergleich zur Off-Side-Rule sieht ein solcher Text viel technischer und damit
schlechter lesbar aus.



```r
# Nicht hübsch, aber lauffähig.
# Die geschweiften Klammern begrenzen die Code-Blöcke.
# Einrückungen dienen in R allein der besseren Lesbarkeit.
show <- function() { for(i in 1:3) { print(i); } }; show();
```

```
## [1] 1
## [1] 2
## [1] 3
```

Warum verwendet R geschweifte Klammern und warum sind
sie so weit verbreitet?

Sicherlich hat C einen großen normativen Einfluss ausgeübt, gerade in der Zeit
als die Sprache entworfen wurde. Geschweifte Klammern sind im Vergleich zum
Whitespace von Einrückungen leichter zu parsen. Fehler sind seltener. Gerade
in großen Projekten sind Fehler, die durch Einrückungsfehler entstehen,
schwierig zu finden. Werden Sprachen gemischt wird es mit Einrückungen
besonders schwierig.

Fazit: Unterm Strich ist es etwas bedauerlich, dass R nicht wie Python Off-Side-Rule verwendet. Zu lang sind die Skripte eigentlich nicht.

#### Blöcke sind Instruktionen

### Variablen

Variablennamen folgen grundsätzlich den Mustern verbreiteter Sprachen.

* Namen bestehen aus Buchstaben, Ziffern, Unterstrichen oder Punkten.
* Namen starten mit einem Buchstaben oder mit einem Punkt.
* Nach einem anführenden Punkt darf keine Ziffer folgen (falsch: .2x).
* Reservierte Worte dürfen nicht verwendet werden.

Reservierte Worte sind kein Thema. Du erkennst Konflikte automatisch an der
Fehlermeldung.

Das Überraschende ist der Punkt als gültiger Bestandteil von Variablennamen. In
anderen Sprachen werden damit Elemente eines Objektes angesprochen. Das
geschieht in R dagegen ziemlich eigentümlich mittels des Dollarzeichens.


```r
# Variable greek befüllt mit einer Liste.
greek <- list("alpha" = 1, "beta" = 2)
# Eine unabhängige Variable, die nur aussieht wie Teil von greek.
greek.dot <- "Punkt"
# Die Liste greek enthält nicht "Punkt" und wurde auch nicht überschrieben.
print(greek)
```

```
## $alpha
## [1] 1
## 
## $beta
## [1] 2
```

```r
# "Punkt" wird unabhängig ausgegeben.
print(greek.dot)
```

```
## [1] "Punkt"
```

```r
# Mit dem $-Zeichen wird ein Element von greek angesprochen.
print(greek$beta)
```

```
## [1] 2
```

```r
# Dieses gibt es dagegen nicht.
print(greek$dot)
```

```
## NULL
```

**Tip**: Wenn Du Verwirrungen mit anderen Sprachen minimieren willst,
verwendest Du den Punkt als Worttrenner nicht. Er ist eher eine Erblast als ein
Feature. Die besseren Alternativen sind *unter_strich* oder *CamelCase*.

Der Punkt als Namensbestandteil wird Dir aber gerade in den fundamentalen und
daher besonders alten Funktionen und Parametern begegnen, das heißt häufig.
Häufiges Sehen verleitet dazu, es zu kopieren. Ich betrachte es dagegen als
Chance meine Funktionen von den internen zu unterscheiden.

### Zuweisungen

Kurz gesagt, die Zuweisung zu Variablen erfolgt in R mittels des
Zuweisungsoperators `<-`  während die Zuweisung zu Funktionsparametern und zu
Namen in Listen und Data-Frames mit dem Gleichheitszeichen `=` erfolgt.

**Tip:** Die Zeichenfolge **"<- "** kannst Du in RStudio unter Mac OS mittels
**[Alt][-]** abkürzen. Mit anderen Betriebssystemen mag das variieren.

Dieses Beispiel zeigt die Anwendung von `<-` und `=`.


```r
################################################################################
# Create a dataframe with calculated planet data.
#
# @param names Characters of names.
# @param radii Numbers of radii in km.
# @return data.frame
##
setupPlanets <- function(names, radii, star = "Sonne") {
     data.frame(
        Name = names,
        Star = star,
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
##     Name  Star Radius Diameter Perimeter   Surface       Volume
## 1 Merkur Sonne   2440     4880  15330.97  74815144 6.084965e+10
## 2  Venus Sonne   6052    12104  38025.84 460264737 9.285074e+11
## 3   Erde Sonne   6371    12742  40030.17 510064472 1.083207e+12
## 4   Mars Sonne   3389     6778  21293.72 144328800 1.630434e+11
```

Hier definiere ich eine Funktion und weise sie der Variablen `setupPlanets`
mittels des `<-`-Operators zu.  Das speichern ganzer Funktionen in Variablen
charakterisiert eine funktionale Programmiersprache. Eine solche Zuweisung
erfolgt auch bei den Variablen `input` und `planets`, denen eine Liste
beziehungsweise einen Data-Frame zugewiesen wird.

Sowohl beim Data-Frame als auch bei der Liste werden die einzelnen benannten
Elemente mittels `=` zugewiesen.

Das Gleichheitszeichen verwende ich auch, um den Parameter `star` bei der
Funktionsdefinition mit einem Defaultwert vorzubelegen, hier `"Sonne"`.
Beim Funktionsaufruf dient mir das Gleichheitszeichen schließlich dazu, die
Parameter mit ihrem Namen statt mit ihrer Reihenfolge an zu sprechen.  Hier
habe ich die Reihenfolge vertauscht, um das zu demonstrieren.

#### Diskussion der Alternativen

Es ist oft, aber eben nicht immer, technisch möglich Variablen mittels `=`
statt mittels `<-` zuzuweisen. Weil das ein Zeichen weniger zu tippen ist und
den Zuweisungen in vielen anderen Programmiersprachen entspricht, wird Dir das
im Code vieler Leute begegnen. Um einen klaren, einheitlichen Programmierstil
zu pflegen, solltest Du aber konsequent `<-` für die Zuweisung von Variablen
benutzen. Das ist einfach R-stylish.

Die Zuweisung mittels `<--` ist möglich, aber für die Zuweisung an
übergeordnete Sichtbarkeitsbereiche gedacht. Du musst wissen, was du hiermit
tust. Dazu mehr im Kapitel über die Sichtbarkeitsbereiche.

`->` macht genau dasselbe wie `<-`. Nicht dass Du denkst die Variable käme dann
nach rechts. Es ist also nicht intuitiv verständlich.

Analog ist `-->` dasselbe `<--` und nicht intuitiv verständlich.

Also:

* `=` Ist nicht überall einsetzbar und nicht R-stylish.
* `->` Ist verwirrend.
* `<--` Du solltest wissen, was Du tust.
* `-->` Ist verwirrend und Du solltest wissen, was Du tust.

**Tip:** Zuweisung mittels `<-` bevorzugen.

### Namensräume

Variablen können bereits Funktionen oder Daten enthalten, auch die aus
den Basis-Paketen und die aus den Bibliotheken, die Du lädst.

Du musst also
aufpassen, dass Du keine Namen von Funktionen oder Daten überschreibst,
jedenfalls nicht solche, die Du später noch verwenden willst.

Tust Du es doch, dann kannst du die Variablen der Pakte aber immer noch über
ihren Fully-Qualified-Name ansprechen. Das kann einerseits lohnenswert sein, um
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
# Der Fully-Qualified-Name funktioniert weiterhin.
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

### Coding-Guidelines

Es gibt keine verbindlichen Coding-Guidelines für R, was sicherlich auch mit
dem freien Geist der Wissenschaft zusammenhängt. Gerade im Hinblick auf die
wachsenden Ansprüche an die Reproduzierbarkeit von Studien, werden Standards
aber auch hier wichtiger. Darum möchte ich ein paar Empfehlungen aussprechen,
die sich aus anderen Bereichen herleiten lassen.

Klarheit, Einheitlichkeit und Dokumentation sind Elemente, die Du in Deinem
Programmcode anstreben solltest. Klarheit und Einheitlichkeit helfen Dir und
anderen, sich schnell und einfach in Deinem Code zu orientieren. Dokumentation
hilft, die Gedanken nachzuvollziehen, die zu Deinen Programmlösungen führen.
Alles das hilft auch Bugs zu vermeiden, zu finden und zu fixen.

Unter Dokumentation verstehe ich zuerst die Wahl sprechender Namen für Deine
Variablen, zu allererst die der Funktionsnamen. Je mehr Dein Programmcode der
gesprochenen Sprache nahe kommt, desto weniger musst Du in zusätzlichen
Kommentaren erklären. Kryptischer Programmcode ist kein Zeichen einer
überlegenen Intelligenz, wie in den Kinofilmen gezeigt, sondern von
suboptimalen Bezeichnern. Desto einfacher andere Deinen Code nachvollziehen
können, desto besser ist Deine Arbeit und desto weniger Fehler wird er
enthalten.

Es ist eine gute Idee, einheitlich englische Bezeichner zu verwenden. Erstens
hast Du dann niemals Probleme mit Umlauten, zweitens sind englische Bezeichner
fast immer kürzer als deutsche und drittens arbeitest Du heute zunehmend in
internationalen Teams. Wenn Du aber deutsche Bezeichner benutzen willst, dann
solltest Du auch darin möglichst konsequent sein.

Auch wenn Dozenten Variablen wie `x`, `y`, `z` benutzen, sollte so etwas nicht
in Deinem Code vorkommen, sondern nur ganze Worte als Variablennamen. Wichtig
ist, dass Du die Auto-Vervollständigung Deines Editors kennen lernst, damit Du
nicht jedes Zeichen einzeln tippen musst. Das spart Zeit und Tippfehler.

Sprechende Bezeichner bestehen oft aus zwei oder noch mehr Wortteilen. Darum ist
es wichtig, wie Du Diese zusammenfügst. Für eine gute Lesbarkeit haben sich
CamelCase oder die Benutzung des Unterstriches bewährt. Bei drei Wortteilen
spart CamelCase im Vergleich zwei Unterstriche an Zeilenlänge. Da Deine Zeilen
80 Zeichen im Regelfall nicht überschreiten sollten, halte ich CamelCase für
vorteilhafter.


```r
################################################################################
# Diese Kommentarbalken sind 80 Zeichen lang.
################################################################################

speakingWordExample = "kürzer" # CamelCase, sehr gut.
speaking_word_example = "länger" # Unterstrich, auch gut.
speakingwordexample = "schwer lesbar" # mangelhaft
nswe = "Aküfi" # So sprichst Du hoffentlich nicht den ganzen Tag.
s = "wie in Mathe" # Jetzt versteht Dich nur noch der Prozessor.
```

80 Zeichen sind ein allgemeiner Richtwert, wie lang Programmzeilen sein
sollten. Damit kannst Du auf einem normalen Monitor gut zwei Dateien
nebeneinander öffnen inklusive Zeilennummern. Wenn Du professionell arbeitest,
ist ein solcher Split-View eher die Regel als die Ausnahme, besonders dann,
wenn Du Code und Tests side-by-side erstellst. Diese Breite ist auch im
Hinblick auf eine einfache Fokussierbarkeit des Textes wichtig. Bei längeren
Zeilen wird es anstrengend, beim Lesen in der richtigen Zeile zu bleiben.

Den Programmcode solltest Du entsprechend seiner Blocktiefe einrücken. Ob du
das mittels Leerzeichen oder Tabs tust, ist Geschmacksache. Beides hat vor und
Nachteile. Wichtig ist, dass Dein Team und Du hier eine einheitliche Richtlinie
festlegen, weil beides durcheinander schlecht funktioniert.

Der verbreitetste Standard bei den Einrückungen sind 8 Zeichen. Bei vier Ebenen
sind dann aber schon 32 von 80 Zeichen damit verbraucht. Wenn Du zusammengesetzte
Worte als Bezeichner verwendest, bist schnell am Ende der Zeile. Was tun?

1. Gute Bezeichner sind wichtiger als tiefe Einrückungen. Ich halte darum vier
   Zeichen bei den Einrückungen für sinnvoller.
2. Verschachtelungen von 4 Tiefen sind in der Regel ein Zeichen von zu langen
   und komplexen Funktionen. Meist kannst Du dann ganze Code-Blöcke in eigene
   Funktionen auslagern und erhälst damit ein besseres Ergebnis. Funktionen
   sollten selten länger als zwanzig Zeilen sein.
3. Wenn der Platz nicht ausreicht, dann brich die Zeile um und rücke die zweite
   Zeile noch einmal eine Ebene ein. Du kannst in R aber nicht an beliebigen
   Stellen umbrechen, weil das Zeilenende als Semikolon fehlinterpretiert
   werden kann. So lange Du innerhalb einer geöffneten Klammer umbrichst, zum
   Beispiel innerhalb der Funktionsparameter, erkennt R, dass hier kein
   Instruktionsende sein kann. Probiere einfach etwas herum, bis Du das
   routiniert meisterst.

Auch wenn Du konsequent ganze Worte als Variablennamen verwendest, solltest Du
immer noch Kommentare schreiben. Kommentare innerhalb von Funktionen sollten
dann aber so gut wie überflüssig werden. Oberhalb von Funktionen sollte ein
einheitlich formatierter Kommentar stehen, der in der Regel 4 Angaben macht:

1. Titel der Funktion
2. Beschreibung, was die Funktion tut (kann bei Banalitäten fehlen).
3. Beschreibung jedes einzelnen Parameters.
4. Rückgabewert der Funktion.


```r
################################################################################
# Do nothing
#
# This function does nothing. It just exists,
# that you have something to call.
#
# @param Integer Defaults to 43.
# @param ...     Eats up any additional parameters that you feed into.
# @return NULL
##
doNothing <- function(dummy = 43, ...) {
    NULL
}
```

Dein Code sieht aufgeräumt aus, wenn du wie in diesem Beispiel einen
einheitlichen Rahmen um den Funktionskommentar zeichnest. Ich wähle auch hier
eine Länge von 80 Zeichen, um dem Leser eine Fokussionshilfe zu geben.

In R sind Funktionen, die in Variablen gespeichert sind, zwar auch Objekte, In
dem Moment, in dem die sie aufrufst, werden sie aber aktiv. Sie sind die
Verben deines Programmcodes. Darum solltest Du sie auch immer mit Verben
benennen. Der Standard ist, dazu den Imperativ zu verwenden, so wie im
vorstehenden Beispiel `doNothing()`. Andere Beispiele wären `getName()`,
`setName()`, `createTable()`, `translateToSomeThing()`, `format()`,
`showResult()`.

Eine Ausnahme sind Funktionen, die `TRUE` oder `FALSE` zurück geben. Sie
werden am besten wie Fragen formuliert, so dass sie in `if`-Verzweigungen oder
`while`-Schleifen sprachlich Sinn ergeben.


```r
if(isChild(person)) {
    print("Kein Zugang")
}

while(hasMoreElements(iterator)) {
    print(getNextElement(iterator))
}
```

Das Beispiel `doNothing()` zeigt auch, dass der erste Buchstabe immer klein
sein sollte, auch bei CamelCase. Das gilt sowohl für Werte als auch für
Funktionen. Eine sinnvolle Ausnahme sind Funktionen, die wie Klassen in
anderen Sprachen verwendet werden. Dazu später.



## Datentypen

### Vektoren

Vektoren, wie klingt das für Dich? Spannend, abschreckend, kompliziert,
wissenschaftlich oder nach gymnasialer Oberstufe? Wie auch immer, es ist das
Feature in R, welches Du ziemlich bald in anderen Programmiersprachen vermissen
wirst, falls Du mit anderen Sprachen arbeitest.

Warum? So wissenschaftlich der Begriff auch klingen mag, der Vektor entspricht
ziemlich genau dem, wie wir natürlicherweise über Dinge denken und wie wir über
den Umgang mit Dingen denken. Fast möchte ich sagen, er sei quasi neuronal.

Nehmen wir an, Du willst eine Party feiern, und hast eine Liste mit Leuten im
Kopf, die Du einladen willst. Da sagst dann, "**Jeder** bekommt eine Einladung.
Für **jeden** muss ich etwa 3 Flaschen Bier besorgen oder besser vier, usw.".
In Deiner Sprache und Deinen Gedanken kommen dabei keine Schleifen vor, wie Du
das organisiert. Du stellst Dir vor, wie Du das für eine Person tust und sagst
einfach **jeder**.

Genauso vereinfachen Vektoren die Programmierung. Du beschreibst die Lösung wie
für ein einzelnes Element, aber reichst gleich die ganze Liste hin, **jedes**
Element auf der Liste. Der Vektor ist also eine Auflistung gleichartiger
Elemente, die alle gleich verarbeitet werden, ohne dass Du zuerst eine Schleife
programmierst, um das einzelne Element verarbeiten zu können, wie in anderen
Sprachen.

Du sparst damit in R eine Menge Schleifenprogrammierung ein, ich schätze im
Vergleich bis 60%, je nachdem, was der Code tut. Der Code sieht damit viel
weniger technisch aus, sondern viel mehr wie gesprochene Sprache. Reden wir gar
nicht von der Zeit und der Suche nach Schleifenfehlern.

Wie ist das möglich? Erinnere Dich an die Oberstufe. Der Vektor packt eine
kleine Liste von Elementen zusammen, die alle gemeinsam verarbeitet werden
und zwar jedes in der gleichen Weise.

Der Vektor ist die kleinste Recheneinheit in R. Er hat eins oder mehrere
Elemente, aber Du kannst sie nicht aus dem Vektor nehmen. Wenn Du ein Element
aus dem Vektor nimmst, dann erhältst Du nämlich wieder einen Vektor und zwar
einen mit der Länge eins.


```r
lengthThreeVector <- c(1, 3, 5)
lengthThreeVector
```

```
## [1] 1 3 5
```

```r
# Das Einzelelement aus Position 2 genommen ist auch wieder ein Vektor.
positionTwoVector <- lengthThreeVector[2]
is.vector(positionTwoVector) # Notiz: Der Punkt im Namen ist eher historisch als vorbildlich.
```

```
## [1] TRUE
```

```r
# Sogar dieses Ergebnis TRUE ist ein Vektor der Länge eins.

positionTwoVector
```

```
## [1] 3
```

Wenn Du einen Vektor mit sieben multiplizierst, dann wird jedes Element im
Vektor mit sieben multipliziert und das Ergebnis ist ein neuer Vektor. Wenn Du
jedes Element mit einem eigenen Wert multiplizieren willst, dann nimmst Du
einen zweiten Vektor, der diese Werte enthält. Du multiplizierst beide Vektoren
und brauchst immer noch keine Schleife.


```r
c(2, 3) * 7
```

```
## [1] 14 21
```

```r
c(2, 3) * c(3, 4)
```

```
## [1]  6 12
```

So praktisch dieser Ansatz auch ist, er funktioniert in R nur, aber immerhin,
sinnvoll für elementare, einheitliche Datentypen. Jedenfalls ist er nur dafür
implementiert. In der Datenwissenschaft verarbeiten wir typischerweise
Tabellen, in denen jede Spalte genau so eine einheitliche Liste elementarer
Typen darstellt. Deswegen ist dieser Ansatz in der Datenwissenschaft ungeheuer
produktiv. Es wäre interessant zu überlegen, wie weit er sich auch auf
komplexere Objekte ausdehnen ließe. Könnten wir dann weitgehend auf Schleifen
verzichten?

Ein verwandtes Verfahren Schleifen für komplexere Objekte zu vermeiden,
beinhaltet die Familie der Map-Funktionen, wenn auch nicht ganz so einfach
in der Anwendung wie Vektoren. Dazu ein eigenes Kapitel.

Hast Du schon einmal mit SQL gearbeitet? Dann werden Dir Parallelen auffallen.
Auch in SQL formulierst Du eine Instruktion so, als hättest Du es mit einem
einzelnen Datensatz zu tun. Dann wird die Instruktion auf alle Datensätze
angewendet. Dabei entspricht jede Spalte der Datenbank einem Vektor.

> One observation I would make is that with vectorisation and
> subsetting, a lot of operations in R are more like SQL operations on
> databases than linear programming. If people can wrap their heads around
> that concept it often helps them he a good feel for why things are done
> in the way that they are.
>
> [David Hood on Coursera](https://class.coursera.org/repdata-034/forum/thread?thread_id=26)

### Atomare Vektortypen

Atomare Vektoren erfüllen die Funktionen von skalaren Typen in anderen
Sprachen, aber mit den Features eines Vektors angereichert. R kennt diese
atomaren Vektortypen:

* logical
* integer
* double (Synonym "numeric")
* complex
* character
* raw

Literale Schreibweisen skalarer Typen erzeugen einen Vektor der Länge eins.


```r
length(FALSE)
```

```
## [1] 1
```

```r
is.vector(FALSE) # logical
```

```
## [1] TRUE
```

```r
is.vector(7L) # integer
```

```
## [1] TRUE
```

```r
is.vector(7.1) # double
```

```
## [1] TRUE
```

```r
is.vector(7) # double !!!
```

```
## [1] TRUE
```

```r
is.vector(3i) # complex
```

```
## [1] TRUE
```

```r
is.vector("Hallo") # character
```

```
## [1] TRUE
```

```r
is.vector(as.raw(15)) # raw, keine literale Schreibweise
```

```
## [1] TRUE
```

Bei den literalen Schreibweisen musst Du also besonders beachten, dass auch die
einfache Schreibweise eines Integers `7` einen Vektor vom Typ *double* erzeugt.
Um einen Integer-Vektor zu erzwingen, stellst Du ein großes **L** dahinter
`7L`.

**Aufgabe:** Schreibe für jeden der atomaren Vektortypen einen eigenen Wert und
teste ihn auf seinen Typ mit der Funktion `typeof()`, ob Du es richtig gemacht
hast.

Der Vektortyp *raw* enthält binäre Daten und wird nicht literal eingegeben. Du
wirst ihn wohl eher selten verwenden. Angezeigt wird er als hexadezimaler Wert.


```r
as.raw(15)
```

```
## [1] 0f
```

Die verwandte hexadezimale literale Eingabe erzeugt dagegen keinen Vektor vom
Typ *raw*, sondern einen Vektor vom Typ *double*.


```r
typeof(0x0f)
```

```
## [1] "double"
```

### Die Funktion Combine `c()`

Soweit haben wir uns jetzt  mit atomaren Vektoren der Länge eins beschäftigt
und bis hierher sehen sie einfach aus wie skalare Typen. Nützlich wird die
Natur des Vektors erst, wenn er länger als eins wird, wie in dieser Addition,
die jedes Element um eins erhöht.


```r
c(1, 2, 3) + 1
```

```
## [1] 2 3 4
```

Wir wissen bereits, dass hier jeder Parameter ein atomarer Vektor der Länge
eins ist und auch die Kombination ist wieder ein Vektor.


```r
is.vector(c(1, 2, 3))
```

```
## [1] TRUE
```

Offensichtlich fügt die Funktion `c()` die Parameter zu einem längeren Vektor
zusammen. Prüfen wir das doch einmal.


```r
length(c(3, 2, 1))
```

```
## [1] 3
```

Wenn `c()` Vektoren der Länge eins zusammenfügt, kann es dann auch längere
Vektoren zusammen fügen? Natürlich! Es lässt sich beliebig verschachteln.


```r
c(c(1, 2), c(1, 2, c(3)), 4)
```

```
## [1] 1 2 1 2 3 4
```

```r
identical(c(1, 2, 1, 2, 3, 4), c(c(1, 2), c(1, 2, c(3)), 4))
```

```
## [1] TRUE
```

Dabei wird die Reihenfolge nicht verändert. Wir sehen hier auch, dass
derselbe skalare Wert mehrfach in einem Vektor enthalten sein kann.

Was aber passiert, wenn wir unterschiedliche Typen zusammenfügen wollen?


```r
c("eins", 2)
```

```
## [1] "eins" "2"
```

Hättest Du eine Fehlermeldung erwartet? Die Funktion formt die übergebenen
Parameter sozusagen auf den kleinsten gemeinsamen Nenner um. Dieser ist hier
*character*. Diese automatische Typumwandlung nennt sich mit dem englischen
Fachbegriff **Type Conversion**.

Jeder Wert lässt ich im Zweifel in *character* umformen. Der Typ *character*
ist also die unterste Stufe dieser Hierarchie. Ganz oben steht *raw*. Der
niedrigste Datentyp in der folgenden Liste, der in den Parametern von `c()`
vertreten ist, wird als Kombinationstyp gewählt.

* raw
* logical
* integer
* double (Synonym "numeric")
* complex
* character

**Aufgabe:** Was erwartest Du als Ergebnis von `c(TRUE, 3i)`, `c(as.raw(15), TRUE)`
und `c(as.raw(0), "Hallo")`? Teste es.

**Dokumentation**: `?c`

### Der Doppelpunkt Operator (Colon Operator)

Der **Colon Operator** ist eine Kurzschreibweise für die Funktion `seq(from,
to)`. Er ist ein sehr gängiges Verfahren, um eine Sequenz von Integer-Zahlen zu
erzeugen. In dieser Funktion wird er hier kurz angeschnitten. Er wird
regelmäßig in `for`-Schleifen eingesetzt.


```r
for(counter in 1:3) print(counter)
```

```
## [1] 1
## [1] 2
## [1] 3
```

Betrachte jetzt den Vektor selbst.


```r
1:10
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

Du schreibst ihn in der Regel nicht mit Integern `1L:10L`, sondern mit Doubles.
Das ist kürzer zu schreiben. Was denkst Du welcher Typ von Vektor erzeugt wird?


```r
typeof(1:10)
```

```
## [1] "integer"
```

Ist das nicht überraschend? Rufe diese beiden Hilfeseiten auf und finde heraus,
warum das so ist:

* `?":"`
* `?seq`

Kurz gesagt, wenn sich die erste Zahl auf einen Integer reduzieren lässt, dann
ist der Rückgabewert ein Integer, andernfalls nicht.


```r
1.1:5
```

```
## [1] 1.1 2.1 3.1 4.1
```

```r
typeof(1.1:5)
```

```
## [1] "double"
```

Hier sehen wir auch, dass die zweite Zahl eine Obergrenze ist, aber nicht immer
im Ergebnis selbst enthalten ist.

Die Sequenz muss auch nicht immer mit `1` beginnen und kann auch abwärts zählen.
Du kannst mit negativen Zahlen arbeiten.


```r
3:-3
```

```
## [1]  3  2  1  0 -1 -2 -3
```

**Aufgabe:** Probiere folgende Varianten aus:

* `2:4`
* `1L:10L`
* `10:1`
* `10:-10`
* `pi:10`

### Vektorelemente lesen, bearbeiten und löschen

Du hast jetzt gelernt, wie Du atomare Vektoren erzeugst. Wenn Du Daten
verarbeitest sind Vektoren Teil des Inputs. Um sie zu verarbeiten, ist es jetzt
wichtig zu lernen, wie Du sie veränderst und Teilmengen daraus heraus ziehst.

Fangen wir damit an, ein einzelnes Element zu lesen. Wir sprechen es mit seinem
Index an.


```r
input <- c("eins", "zwei", "drei", "vier")
input[3]
```

```
## [1] "drei"
```

Was passiert, wenn Du mit einem negativen Index arbeitest? Wird dann von hinten
gezählt? Probiere es!


```r
input[-3]
```

```
## [1] "eins" "zwei" "vier"
```

Was ist denn das? Du erhältst einen Negativabdruck des Vorstehenden. Statt des
indizierten Elementes aus dem Vektor, erhältst Du den Vektor ohne das negativ
indizierte Element.

Jetzt verändern wir ein einzelnes Element im Vektor.


```r
input[3] <- "DREI"
input
```

```
## [1] "eins" "zwei" "DREI" "vier"
```

Genau wie bei *Colon Operator* schreibst Du hier wieder *doubles*, weil sich
das kürzer schreibt, obwohl der Index eine klassische Integer-Sequenz ist.
Beweisen wir also, dass ein echter Integer-Vektor auch als Selektor
funktioniert.


```r
input[3L] <- "drei"
input
```

```
## [1] "eins" "zwei" "drei" "vier"
```

**Aufgabe:** Nimm die Zahl `pi` als Selektor. Welches Ergebnis erwartest Du?

Bis hierher haben wir einen Vektor der Länge eins als Selektor genommen. Wenn
Du die Idee der Vektoren verstanden hast, fragst Du dich sicher schon, was
passiert, wenn Du einen längeren Vektor verwendest, z.B. `c(1, 4)`. Probiere
es aus!


```r
input[c(1,4)]
```

```
## [1] "eins" "vier"
```

Das ist doch mal logisch! Du kannst jetzt verallgemeinern und sagen, dass Du in
den eckigen Klammern von *input* einen Vektor übergibst, der die Elemente
indiziert, die Du als Teilmenge von *input* erhalten willst.

Wie das für die Negativauswahl funktioniert, kannst Du jetzt auch ableiten.


```r
input[-c(1,4)]
```

```
## [1] "zwei" "drei"
```

Ganz im Geiste von Vektoren kannst Du jetzt auch mehrere Elemente in einer
einzigen Instruktion ersetzen. Cool!


```r
input[c(2,3,4)] <- c("ZWEI", "DREI", "VIER")
input
```

```
## [1] "eins" "ZWEI" "DREI" "VIER"
```

Erinnere Dich, dass Du den Vektor `c(2L, 3L, 4L)` auch mit dem *Colon Operator*
erzeugen kannst, als `2:4`! In den eckigen Klammern entfaltet das seine volle
Magie.


```r
input[2:4] <- c("zwei", "drei", "vier")
input
```

```
## [1] "eins" "zwei" "drei" "vier"
```

Zeigen wir, dass wir in den Eckigen Klammern nicht nur die Elemente
selektieren, sondern auch ihre Reihenfolge festlegen können. Jetzt zählen
wir rückwärts.


```r
input[4:2]
```

```
## [1] "vier" "drei" "zwei"
```

Um Elemente vor oder hinter dem Vektor einzufügen eignet sich die Funktion
`c()`. Die Vereinigungsmenge wird in die originale Variable zurück geschrieben.
Diese Operationen sind in anderen Sprachen als `unshift` und `push` bekannt.


```r
input <- c("null", input) # unshift
input <- c(input, "fünf")
input
```

```
## [1] "null" "eins" "zwei" "drei" "vier" "fünf"
```

Du löscht Elemente, indem Du die verbleibende Teilmenge in die originale
Variable zurückschreibst. Gerade hierfür eignet sich die Negativauswahl
besonders gut, weil Du dabei einfach die zu löschenden Elemente indizierst.


```r
input <- input[-(2:3)]
input
```

```
## [1] "null" "drei" "vier" "fünf"
```

**Zusammenfassung**: Datenverarbeitung ist vollständig, wenn der CRUD-Zyklus
vollständig ist, nämlich *create*, *read*, *update* und *delete*.


```r
# create:
words <- c("eins", "zwei", "drei", "vier")

# update:
words[1:2] <- c("EINS", "ZWEI")

# delete:
words <- words[-(2:3)]

# read:
words[2:1]
```

```
## [1] "vier" "EINS"
```

**Aufgabe:** Spiele den CRUD-Zyklus für einen Zahlenvektor durch. Beachte
dabei, dass sich beim Löschen der Index verkürzt.

**Dokumentation**: `?"["`

### Vektorelemente mit logischen Vektoren selektieren

Du hast Vektorelemente im vorigen Abschnitt über ihren Index selektiert, als
Positivauswahl oder als Negativauswahl. Eine Alternative dazu ist die Auswahl
mittels logischer Vektoren. Vergleiche die beiden folgenden Methoden.


```r
planets <- c("Merkur", "Venus", "Erde", "Mars")
planets[c(2, 4)]
```

```
## [1] "Venus" "Mars"
```

```r
planets[c(FALSE, TRUE, FALSE, TRUE)]
```

```
## [1] "Venus" "Mars"
```

In beiden Fällen ist die Auswahl dieselbe. Während Du im ersten Fall nur die
positiven Elemente über ihren Index aufzählst, musst Du im zweiten Fall für
jedes einzelne Element angeben, ob es berücksichtigt werden soll oder nicht.

Warum solltest Du das tun? Es so zu schreiben macht wenig Sinn. Eine logische
Abfrage gegen einen Vektor gibt aber einen logischen Vektor zurück, mit dem Du
dann so etwas tun kannst.

Hier benutzen wir den Modulo-Operator, um ungrade Zahlen zu finden und
speichern den logischen Vektor in die Variable `odd`.  Den logischen Vektor
`odd` verwenden wir dann als Selektor der Zahlen.


```r
numbers <- 10:20
odd <- numbers %% 2 > 0
odd
```

```
##  [1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE
```

```r
numbers[odd]
```

```
## [1] 11 13 15 17 19
```

Das geht natürlich auch ohne die Zwischenspeicherung in die Variable `odd`.


```r
numbers[numbers %% 2 > 0]
```

```
## [1] 11 13 15 17 19
```

Vielleicht nimmst Du daran Anstoß, dass Du hier `numbers` zwei mal schreiben
musst. Damit hast Du im Sinne einer natürlichen Lesbarkeit vollkommen
recht. Wendet man R so an wie hier, dann wird es ziemlich kryptisch.

Bei diesem Gebrauch können die eckigen Klammern nicht wissen, dass der logische
Vektor aus derselben Menge berechnet wurde, wie der Zahlenvektor selbst. Daher
musst Du `numbers` zwei mal schreiben.

Es ähnelt einer mathematischen Formel, in der dieselbe Variable mehrfach
vorkommt, und aus der Mathematik stammen die eckigen Klammern ja auch. Wie in
anderen Programmiersprachen auch, gehören sie aber so sehr zu den Grundlagen,
dass sie bald zur zweiten Natur werden.

Hier will ich auch noch einmal auf die Verwandschaft zwischen Vektoren und
Tabellenspalten in SQL hinweisen.

```
SELECT numbers FROM table WHERE numbers %% 2 > 0
```

**Aufgabe:** Mische die Zahlen von 1 bis 100 `numbers <- sample(100)`. Benutze
einen logischen Vektor, um alle Zahlen zu selektieren, die grösser als 50
sind, wobei die Zufallsreihenfolge erhalten bleiben soll.

### Listen

#### Was sind Listen?


```r
is.vector(list())
```

```
## [1] TRUE
```

```r
typeof(list())
```

```
## [1] "list"
```

Listen sind Vektoren, aber keine atomaren Vektoren. Sie vereinigen Objekte
unterschiedlicher Typen. Damit sind auch keine gemeinsamen Operationen mit
diesen Objekten möglich, wie sie für die atomaren Vektoren charakteristisch
sind. Mit den atomaren Vektoren teilen Listen jedoch die Operationen, mit
Teilmengen zu arbeiten.

#### Doppelte eckige Klammern

Die Syntax der Listen ist dennoch gewöhnungsbedürftig, nicht nur weil sie eine
Verschachtelung darstellen. Während die atomaren Vektoren skalare Daten
verpacken, verpacken Listen unterschiedliche Objekte, wie atomare Vektoren,
Funktionen oder anderen Listen. Verpackt eine Liste z.B. atomare Vektoren,
erhalten wir damit eine zweidimensionale Datenstruktur. Verpacken wir Listen in
verschachtelter Form, dann erhalten wir eine mehrdimensionale Struktur oder
einen Datenbaum.


```r
# Eine Liste mit zwei atomaren Vektoren und einer Funktion
mixed <- list(5:7, "Hallo", print)
mixed
```

```
## [[1]]
## [1] 5 6 7
## 
## [[2]]
## [1] "Hallo"
## 
## [[3]]
## function (x, ...) 
## UseMethod("print")
## <bytecode: 0x7f9b597acd10>
## <environment: namespace:base>
```

Betrachte die Ausgabe `mixed` des vorstehenden Beispiels. Du siehst doppelte
eckige Klammern, die den Index der Liste darstellen `[[1]], [[2]], [[3]]`. Bei
den beiden atomaren Vektoren findest Du einfache eckige Klammern, die Du
bereits für atomare Vektoren kennst. Bei der Funktion `function(x, ...)`
findest Du keine eckigen Klammern, denn Funktionen sind keine Vektoren, sondern
Einzelelemente.

Dieses Beispiel soll veranschaulichen, dass sich die doppelten eckigen Klammern
nicht etwa auf eine Mehrdimensionalität beziehen, denn sie treten auch bei
der Funktion auf. Sie beziehen sich also allein auf die Indizierung der Liste.

Um das zweite Element des ersten Vektors anzusprechen, wird folgende
Schreibweise nötig.


```r
mixed[[1]][2]
```

```
## [1] 6
```

Warum nicht einfach `mixed[1][2]`? Das wäre doch intuitiver und einfacher!
(Oder gleich `mixed.1.2`? Das wäre so elegant zu tippen!)

In diesem Fall müsste `mixed[1]` den Integer-Vektor zurückgeben, damit das
zweite Klammerpaar das zweite Element daraus wählen kann. Listen sind aber auch
Vektoren. Bei Vektoren haben wir die Regel, dass die Teilmenge vom selben Typ
ist. Darum muss `mixed[1]` wiederum eine Liste zurückgeben. Also wird eine
alternative Schreibweise notwendig, um das eigentliche Element in dieser
Teilmenge anzusprechen:


```r
typeof(mixed[1]) # die Teilmenge ist eine Liste
```

```
## [1] "list"
```

```r
typeof(mixed[[1]]) # das Element in der Teilmenge ist der Integer-Vektor
```

```
## [1] "integer"
```

**Aufgabe:** Teste,  was bei `mixed[1][2]` heraus kommt! Kannst Du das Ergebnis
erklären?

#### Verschachtelte Listen

Erzeugen wir eine verschachtelte Liste.


```r
nested <- list(
    list(
        list(1:3, 4:6, 7:9),
        list(10:12),
        list(13:15)
    ),
    list(16:18)
)
nested
```

```
## [[1]]
## [[1]][[1]]
## [[1]][[1]][[1]]
## [1] 1 2 3
## 
## [[1]][[1]][[2]]
## [1] 4 5 6
## 
## [[1]][[1]][[3]]
## [1] 7 8 9
## 
## 
## [[1]][[2]]
## [[1]][[2]][[1]]
## [1] 10 11 12
## 
## 
## [[1]][[3]]
## [[1]][[3]][[1]]
## [1] 13 14 15
## 
## 
## 
## [[2]]
## [[2]][[1]]
## [1] 16 17 18
```

Die Liste `nested` enthält zwei Listen. Die erste Liste enthält wiederum 3
Listen. Diese enthält drei Integer-Vektoren.

Der Index `[[1]][[1]][[1]]` adressiert den Integer-Vektor `1:3` auf der dritten
Verschachtelungsebene.

**Aufgabe:** Druck die Zahl 14 aus der Liste `nested` aus, indem Du sie richtig
adressierst.

**Aufgabe:** Teste `c(nested, recursive = TRUE)`. Schlage in der Dokumentation
nach, was *recursive* genau bewirkt.

Jetzt wollen wir den Baum etwas editieren. Die verschachtelten Listen nenne ich
Äste, die Nicht-Listen-Elemente, d.h. die Integer-Vektoren, nenne ich Zweige.
Den einzelnen Integer-Werte entsprechen damit einem Blatt.

##### Blätter verändern

Ziel: Setze das Blatt 18 auf 180.

Überlege:

* Wie wird das Blatt adressiert?
* Wie wird das Blatt ersetzt?


```r
# Das Blatt adressieren
nested[[2]][[1]][3]
```

```
## [1] 18
```

```r
# Das Blatt verändern
nested[[2]][[1]][3] <- 180

# Teilbaum anzeigen
nested[[2]]
```

```
## [[1]]
## [1]  16  17 180
```

Bei den atomaren Vektoren, hatten wir bereits gesehen, wie Teile einer
Variablen mit Hilfe der eckigen Klammern verändert werden. Die ganze Variable
zu ersetzen, kann man als Maximalform davon betrachten. Hier ersetzen wir einen
Teil, den wir über einen Pfad in der Variable `nested` adressieren.

##### Mehrere Blätter verändern

Ziel: Setze das Blatt 16 und 17 auf 160 und 170.


```r
nested[[2]][[1]][1:2] <- c(160, 170)
nested[[2]]
```

```
## [[1]]
## [1] 160 170 180
```

##### Blätter löschen

Ziel: Lösche das Blatt 160.

Überlege:

* Wie unterscheidet sich das Löschen vom Bearbeiten?
* Was musst Du in diesem Falle adressieren?

Rekapitulation: Zum Löschen eines Elementes in einem atomaren Vektor muss die
Variable mit der Teilmenge neu beschrieben werden.

Genauer formuliert, es geht nicht immer um die ganze Variable, sondern um den
Speicherbereich des Vektors. Die ganze Variable `nested` muss nämlich nicht neu
geschrieben werden, sondern nur der Zweig, in dem das Blatt gelöscht wird.


```r
# Pfad des Vektors
nested[[2]][[1]]
```

```
## [1] 160 170 180
```

```r
# Beschreiben mit der Teilmenge
nested[[2]][[1]] <- nested[[2]][[1]][-1]

# Teilbaum anzeigen
nested[[2]]
```

```
## [[1]]
## [1] 170 180
```

Ist es nicht verwirrend, dass drei Ebenen äquivalent zu zwei Ebenen sein
sollen?

Die Verschachtelung ist eine Natur der Listen, aber nicht die Natur des
Vektors. Der Vektor kennt Mengen und Teilmengen. Hier operieren wir auf der
Ebene des Vektors, der einfachen eckigen Klammer, nicht der doppelten. Die
doppelte schachtelt (bei Listen) das Element darunter.


```r
numbers <- 11:15
# Mit oder ohne eckige Klammer, hier wird die Gesamtmenge es Vektors
# aufgerufen.
identical(numbers, numbers[1:5])
```

```
## [1] TRUE
```

##### Einen Zweig verändern

Technisch betrachtet, gehört der Punkt "Blätter löschen" schon zum
Kapitel "Zweige verändern", weil der gesamte Vektor ersetzt wird.
Die Technik wendest Du jetzt an um um den Vektor als ganze zu verändern.

Ziel: Stelle den letzten Vektor wieder her als `16:18`.


```r
# Neu beschreiben
nested[[2]][[1]] <- 16:18

# Teilbaum anzeigen
nested[[2]]
```

```
## [[1]]
## [1] 16 17 18
```

##### Einen Zweig im Typ verändern

Ziel: Ersetze den Zweig mit einem analogen Character-Vektor.


```r
# Neu beschreiben
nested[[2]][[1]] <- c("sechzehn", "siebzehn", "achtzehn")

# Teilbaum anzeigen
nested[[2]]
```

```
## [[1]]
## [1] "sechzehn" "siebzehn" "achtzehn"
```

##### Einen Zweig auf NULL setzen

Ziel: Setze den Zweig auf NULL und teste, was passiert.


```r
# Teilbaum vorher
nested[[2]]
```

```
## [[1]]
## [1] "sechzehn" "siebzehn" "achtzehn"
```

```r
# Mit NULL beschreiben
nested[[2]][[1]] <- NULL

# Teilbaum nachher
nested[[2]]
```

```
## list()
```

Zurück bleibt eine leere Liste. Indem der Vektor `nested[[2]][[1]]` auf *NULL*
gesetzt wurde, wurde auch sein Listenindex `nested[[2]][1]` entfernt.

Indem man die Prozedur für andere Positionen wiederholt könnte man auch mehrere
Zweige entfernen. Im Geiste der Vektor-Operationen ist eine solche Wiederholung
aber nicht. Wir wollen mehrere Zweige löschen, indem wir einen Vektor mit den
zu löschenden Indizes übergeben. Dies hier ist also eher eine Sackgasse oder
ein Workaround.

Stelle den Vektor mit der folgenden Zeile darum wieder her.


```r
nested[[2]] <- list(16:18)
nested[[2]]
```

```
## [[1]]
## [1] 16 17 18
```

Ziel: Vergleiche was passiert, wenn Du dasselbe mit nur einer eckigen Klammer
machst. Also indem du den Listenvektor statt des zugehörigen atomaren Vektors
ansprichst.


```r
nested[[2]][1] <- NULL
nested[[2]]
```

```
## list()
```

Das Ergebnis bleibt sich gleich.

##### Mehrere Zweige zugleich löschen

Wie uns bei den Blättern das Löschen eine Ebene höher führte, so wird es das
sicherlich auch bei den Zweigen tun, von den Zweigen auf die Ebene des Astes,
vom atomaren Vektor auf die Ebene der Liste.




Überlege:

* Was genau ist dieser Ast?
* Wie wird der Ast gelöscht?
* Wie wird `nested` anschließend aussehen?

Hast Du deine Hypothesen aufgestellt? Los geht's!

Was enthält der Ast?


```r
typeof(nested[[1]][[1]][2])
```

```
## [1] "list"
```

```r
nested[[1]][[1]][2]
```

```
## [[1]]
## [1] 4 5 6
```

Der Ast enthält eine Liste, denn das letzte Klammerpaar ist einfach.
Andernfalls würde es den Integer-Vektor adressieren.

Wie wird der Ast gelöscht?

Wir haben bereits gesehen, dass Vektoren gelöscht werden, indem man die
verbleibende Teilmenge in die original Variable zurück schreibt. Das
gilt grundsätzlich auch für Listen-Vektoren.

Bei verschachtelten Listen müssen wir das allerdings auf der Ebene eines Astes
praktizieren, und zwar auf der Ebene oberhalb des zu löschenden Asts. Um im
Bild zu bleiben, sägen wir von diesem übergeordneten Ast den zu entfernenden
Ast ab.

Der übergeordnete Ast adressiert den Vektor seiner Unteräste. Das ist die
Menge mit der wir arbeiten. Genau dahin schreiben wir den Satz der
verbleibenden Unteräste.


```r
# Der übergeordnete Ast adressiert den Vektor seiner Unteräste
nested[[1]][[1]]
```

```
## [[1]]
## [1] 1 2 3
## 
## [[2]]
## [1] 4 5 6
## 
## [[3]]
## [1] 7 8 9
```

```r
# Die Teilmenge entsteht durch Entfernung des Zielastes
nested[[1]][[1]][-2]
```

```
## [[1]]
## [1] 1 2 3
## 
## [[2]]
## [1] 7 8 9
```

```r
# Zurückschreiben der Teilmenge
nested[[1]][[1]] <- nested[[1]][[1]][-2]
# Ergebnis
nested
```

```
## [[1]]
## [[1]][[1]]
## [[1]][[1]][[1]]
## [1] 1 2 3
## 
## [[1]][[1]][[2]]
## [1] 7 8 9
## 
## 
## [[1]][[2]]
## [[1]][[2]][[1]]
## [1] 10 11 12
## 
## 
## [[1]][[3]]
## [[1]][[3]][[1]]
## [1] 13 14 15
## 
## 
## 
## [[2]]
## list()
```

#### Die Funktion Combine c() mit Listen

Prüfe jetzt, wie sich die Funktion Combine `c()` für Listen verhält. Was
erwartest Du als kleinsten gemeinsamen Nenner? Bei den atomaren Vektoren war
der Charakter-Vektor der kleinste gemeinsame Nenner. Kombiniere eine Liste mit
einem Charakter-Vektor und einem Integer-Vektor:


```r
combined <- c(c("Hallo", "Welt"), list(list("Liste1"), list("Liste2")), 1:2)
typeof(combined)
```

```
## [1] "list"
```

`combined` ist eine Liste. Offenbar ist die *list* der kleinste gemeinsame
Nenner noch unterhalb von *charakter*. Schaue Dir `comined` selbst an!


```r
combined
```

```
## [[1]]
## [1] "Hallo"
## 
## [[2]]
## [1] "Welt"
## 
## [[3]]
## [[3]][[1]]
## [1] "Liste1"
## 
## 
## [[4]]
## [[4]][[1]]
## [1] "Liste2"
## 
## 
## [[5]]
## [1] 1
## 
## [[6]]
## [1] 2
```

#### CRUD - Create, Read, Update, Delete mit Listen

Kommen wir zum CRUD-Zyklus einer Liste:


```r
# Create
names <- c("Merkur", "Venus", "Welt", "Mars")
radii <- c(2440, 6052, 6371, 3389)
planets <- list(names, radii)

# Update

# Read
planets
```

```
## [[1]]
## [1] "Merkur" "Venus"  "Welt"   "Mars"  
## 
## [[2]]
## [1] 2440 6052 6371 3389
```


### NA und NaN

### Wahr und falsch

### Text

### Zahlen

Das **L** steht hier vermutlich für *long* im Vergleich zu *double*. Würdest Du
Dir die Wortpaare *integer* und *float* wünschen? Das ist aber leider nicht die
Terminologie von R. Prüfen wir, wie beide offiziell heißen:


```r
typeof(7L)
```

```
## [1] "integer"
```

```r
typeof(7)
```

```
## [1] "double"
```

```r
class(7L)
```

```
## [1] "integer"
```

```r
class(7)
```

```
## [1] "numeric"
```
Das ist nicht gerade konsistent, nicht wahr, und sicherlich ein Hinweis auf die
Entwicklungsgeschichte von R. Welche Wortpaarung ist sprachlich sinnvoller und
damit vermutlich jünger?

**Aufgabe:** Teste `7` und `7L` jeweils mit den Funktionen `is.integer()`,
`is.double()` und `is.numeric()`. Stimmt das Ergebnis mit Deinen Erwartungen
überein?

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


