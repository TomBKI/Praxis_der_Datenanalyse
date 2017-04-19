--- 
title: "Praxis der Datenanalyse"
author: "Sebastian Sauer"
date: '2017-04-12'
colorlinks: yes
cover-image: cover.jpg
bibliography:
- Praxis_der_Datenanalyse.bib
- libs.bib
description: Eine Einführung in moderne Statistik für Praktiker
documentclass: book
fontsize: 12pt
github-repo: sebastiansauer/Praxis_der_Datenanalyse
link-citations: yes
lof: yes
lot: yes
nocite: |
  @*
site: bookdown::bookdown_site
biblio-style: apalike
---





# Vorwort

<img src="images/farb1.jpg" width="100%" />


Statistik heute; was ist das? Sicherlich haben sich die Schwerpunkte von gestern zu heute verschoben. Wenig überraschend spielt der Computer eine immer größere Rolle und die Daten werden vielseitiger und massiger. Entsprechend sind neue Verfahren nötig - und vorhanden, in Teilen - um auf diese neue Situation einzugehen. Einige Verfahren werden daher weniger wichtig, z.B. der p-Wert und der t-Test. Allerdings wird vielfach, zumeist, noch die Verfahren gelehrt und verwendet, die für die erste Hälfte des 20. Jahrhunderts entwickelt wurden. Eine Zeit, in der kleine Daten, ohne Hilfe von Computern und basierend auf einer kleinen Theoriefamilie im Rampenlicht standen [@cobb2007introductory]. Die Zeiten haben sich geändert!

<img src="images/Forschung_frueher_heute.jpg" width="4108" />

Zu Themen, die heute zu den dynamischten Gebieten der Datenanalyse gehören, die aber früher keine große Rolle spielten, gehören [@hardin2015data]: 

- Nutzung von Datenbanken und anderen Data Warehouses
- Daten aus dem Internet automatisch einlesen ("scraping")
- Genanalysen mit Tausenden von Variablen
- Gesichtserkennung




Es gibt bisher noch relativ wenig *deutschsprachige* Bücher für moderne Datenanalyse; es ist zu erwarten, dass sich dies bald ändert. Dieses Buch soll beitragen, diese Lücke zu füllen. Sie werden einige praktische Aspekte der modernen Datenanalyse lernen. Es ist ein Grundlagenkurs; dieses Buch ist nicht für Experten geschrieben und durch das Lesen wird man auch kein Experte. Aber man erwirbt Grundkenntnisse. Das didaktische Konzept beruht auf einem induktiven, intuitiven Lehr-Lern-Ansatz. Auf Formeln und mathematische Hintergründe wurde weitestgehend verzichtet. 

Im Gegensatz zu anderen Statistik-Büchern steht hier die Umsetzung mit R deutlich stärker im Vordergrund. Dies hat pragmatische Gründe: Möchte man Daten einer statistischen Analyse unterziehen, so muss man sie zumeist erst aufbereiten; oft mühselig aufbereiten. Selten kann man den Luxus genießen, einfach "nur", nach Herzenslust sozusagen, ein Feuerwerk an multivariater Statistik abzubrennen. Zuvor gilt es, die Daten aufzubereiten, umzuformen, zu prüfen und zusammenzufassen. Diesem Teil ist hier recht ausführlich Rechnung getragen. 

Dieses Buch versteht sich als "Kursbuch", weniger als "Lehrbuch". Es soll neben Inhalt auch Übungen bieten, um den Inhalt zu erarbeiten (Arbeitsbuch wäre auch treffend).

"Statistical thinking" sollte, so eine verbreitete Idee, im Zentrum oder als Ziel einer Statistik-Ausbildung stehen [@wild1999statistical]. Es ist die Hoffnung der Autoren dieses Buches, dass das praktische Arbeiten (im Gegensatz zu einer theoretischen Fokus) zur Entwicklung einer Kompetenz im statistischen Denken beiträgt.‹

Außerdem spielt die Visualisierung von Daten eine große Rolle. Zum einen könnte der Grund einfach sein, dass Diagramme ansprechen und gefallen (einigen Menschen). Zum anderen bieten Diagramme bei umfangreichen Daten Einsichten, die sonst leicht wortwörtlich überersehen würden.

*R-Pseudo-Syntax*: R ist (momentan) die führende Umgebung für Datenanalyse. Entsprechend zentral ist R in diesem Kurs. Zugebenermaßen braucht es etwas Zeit, bis man ein paar Brocken "Errisch" spricht. Um den Einstieg zu erleichern, ist Errisch auf Deutsch übersetzt an einigen Stellen, wo mir dies besonders hilfreich erschien. Diese Stellen sind mit diesem Symbol ![](images/pseudocode.png){ width=5% } gekennzeichnet (für R-Pseudo-Syntax).

*Achtung, Falle*: Schwierige oder fehlerträchtige Stellen sind mit diesem Symbol ![](images/caution.png){ width=5% } markiert.

*Übungsaufgaben*: Das Skript beinhaltet in jedem Kapitel Übungsaufgaben oder/und Testfragen. Auf diese wird mit diesem Icon ![](images/exercises.png){ width=5% } verwiesen oder die Übungen sind in einem Abschnitt mit einsichtigem Titel zu finden.

Ansonsten: Wenn Ihnen R diesen Smiley präsentiert, dann sind Sie am Ziel Ihrer Träume: ![](images/love.png){ width=5% }. 


Dieses Skript wurde mit dem Paket `bookdown` [@xie2015] erstellt, welches wiederum stark auf den Paketen `knitr` [@xie2015] und `rmarkdown` [@rmarkdown] beruht. Diese Pakete stellen verblüffende Funktionalität zur Verfügung als freie Software (frei wie in Bier und frei wie in Freiheit).

Aus Gründen des Lesbarkeit wird das männliche Generikum verwendet, welches Frauen und Männer in gleichen Maßen ansprechen soll.


Die Bildnachweise sind in folgenden Muster aufgebaut:
Nummer (Verweis) des Bildes, Names des Autors, Titel, Quelle (URL), Lizenz, Abrufdatum.


- \@ref(fig:modellieren_plot), Sebastian Unrau, ohne Titel, https://unsplash.com/photos/CoD2Q92UaEg, CC0, 2017-02-12
 

Alle verwendeten Datensätze und R-Pakete finden sich im Literaturverzeichnis; im Text werden Pakete nicht zitiert.


<!--chapter:end:index.Rmd-->



\pagenumbering{arabic}

# I EXPLORIEREN {-}



# Rahmen

\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Einen Überblick über die fünf wesentliche Schritte der Datenanalyse gewinnen.
- R und RStudio installieren können.
- Einige häufige technische Probleme zu lösen wissen.
- R-Pakete installieren können.
- Einige grundlegende R-Funktionalitäten verstehen.
- Auf die Frage "Was ist Statistik?" eine Antwort geben können.

</div>\EndKnitrBlock{rmdcaution}


In diesem Skript geht es um die Praxis der Datenanalyse. Mit Rahmen ist das 
"Drumherum" oder der Kontext der eigentlichen Datenanalyse gemeint. Dazu gehören
einige praktische Vorbereitungen und ein paar Überlegungen. Zum Beispiel 
brauchen wir einen Überblick über das Thema. Voilà (Abb. \@ref(fig:fig-prozess)):

<div class="figure" style="text-align: center">
<img src="images/Prozess_Datenanalyse.pdf" alt="Der Prozess der Datenanalyse" width="70%" />
<p class="caption">(\#fig:fig-prozess)Der Prozess der Datenanalyse</p>
</div>


Datenanalyse, praktisch betrachtet, kann man in fünf Schritte einteilen [@r4ds].
Zuerst muss man die Daten *einlesen*, die Daten also in R (oder einer anderen 
Software) verfügbar machen (laden). Fügen wir hinzu: In *schöner Form* verfügbar
machen; man nennt dies auch *tidy data*[hört sich cooler an]. Sobald die Daten in geeigneter 
Form in R geladen sind, folgt das *Aufbereiten*. Das beinhaltet Zusammenfassen, 
Umformen oder Anreichern je nach Bedarf. Ein nächster wesentlicher Schritt ist 
das *Visualisieren* der Daten. Ein Bild sagt bekanntlich mehr als viele Worte. 
Schließlich folgt das *Modellieren* oder das Hypothesen prüfen: Man überlegt 
sich, wie sich die Daten erklären lassen könnten. Zu beachten ist, dass diese 
drei Schritte - Aufbereiten, Visualisieren, Modellieren - keine starre Abfolge 
sind, sondern eher ein munteres Hin-und-Her-Springen, ein aufbauendes 
Abwechseln. Der letzte Schritt ist das *Kommunizieren* der Ergebnisse der 
Analyse - nicht der Daten. Niemand ist an Zahlenwüsten interessiert; es gilt, 
spannende Einblicke zu vermitteln.

Der Prozess der Datenanalyse vollzieht sich nicht im luftleeren Raum, sondern 
ist in einem *Rahmen* eingebettet. Dieser beinhaltet praktische Aspekte - wie 
Software, Datensätze - und grundsätzliche Überlegungen - wie Ziele und 
Grundannahmen.




## Software installieren


Als Haupt-Analysewerkzeug nutzen wir R; daneben wird uns die sog. 
"Entwicklungsumgebung" RStudio einiges an komfortabler Funktionalität bescheren.
Eine Reihe von R-Paketen ("Packages"; d.h. Erweiterungen) werden wir auch 
nutzen. R ist eine recht alte Sprache; viele Neuerungen finden in Paketen 
Niederschlag, da der "harte Kern" von R lieber nicht so stark geändert wird. 
Stellen Sie sich vor: Seit 29 Jahren nutzen Sie eine Befehl, der Ihnen einen 
Mittelwert ausrechnet, sagen wir die mittlere Anzahl von Tassen Kaffee am Tag. 
Und auf einmal wird der Mittelwert anders berechnet?! Eine Welt stürzt ein! 
Naja, vielleicht nicht ganz so tragisch in dem Beispiel, aber grundsätzlich sind
Änderungen in viel benutzen Befehlen potenziell problematisch. Das ist wohl ein 
Grund, warum sich am "R-Kern" nicht so viel ändert. Die Innovationen in R 
passieren in den Paketen. Und es gibt viele davon; als ich diese Zeilen 
schreibe, sind es fast schon 10.000! Genauer: 9937 nach dieser Quelle: 
<https://cran.r-project.org/web/packages/>.


### R und RStudio installieren


Setzt natürlich voraus, dass R installiert ist. Sie können R unter 
<https://cran.r-project.org> herunterladen und installieren (für Windows, Mac 
oder Linux). RStudio finden Sie auf der gleichnamigen Homepage: 
<https://www.rstudio.com>; laden Sie die "Desktop-Version" für Ihr 
Betriebssystem herunter.

Die Oberfläche von R, die "Console", sieht so aus:

<!-- ![](images/R-small.jpg) ![](images/R-Mac-small.png) -->




Die Oberfläche von RStudio sieht (unter allen Betriebssystemen etwa gleich) so 
aus:

<img src="images/RStudio-Screenshot.png" width="70%" style="display: block; margin: auto;" />


Das *Skript-Fenster*\index{Skript-Fenster} ähnelt einem normalem Text-Editor; 
praktischerweise finden Sie aber einen Button "run", der 
die aktuelle Zeile oder die Auswahl "abschickt", d.h. in die 
Konsole gibt, wo die Syntax ausgeführt wird. Wenn Sie ein Skript-Fenster
öffnen möchten, so können Sie das Icon ![new_script](images/new_script.png) 
klicken^[Alternativ: Cntrl-Shift-N oder File > New File > R Script].

Aus dem Fenster der *Konsole*\index{Konsole} spricht R zu uns bzw. 
wir mit ihm (ihr?). Wird ein Befehl hier eingegeben, so führt R ihn aus. 
Es ist aber viel praktischer, Befehle in das Skript-Fenster einzugeben, als in
die Konsole. Behalten Sie dieses Fenster im Blick, wenn Sie Antwort von R erwarten.

Im Fenster *Umgebung*\index{Umgebung} (engl. "environment") zeigt R, 
welche Variablen (Objekte) vorhanden sind. Stellen Sie sich die Umgebung wie einen
Karpfenteich vor, in dem die Datensätze und andere Objekte herumschwimmen. Was nicht
in der Umgebung angezeigt wird, existiert nicht für R.

Im Fenster rechts unten werden mehrere Informationen bereit gestellt, z.B. 
werden Diagramme (Plots) dort ausgegeben. Klicken Sie mal die anderen Reiter im Fenster
rechts unten durch.


Wer Shortcuts mag, wird in RStudio überschwänglich beschenkt; der Shortcut für die Shortcuts ist `Shift-Alt-K`.


### Hilfe! R tut nicht so wie ich das will

>    Manntje, Manntje, Timpe Te,   
    Buttje, Buttje inne See,    
    myne Fru de Ilsebill    
    will nich so, as ik wol will. 


*Gebrüder Grimm, Märchen vom Fischer und seiner Frau^[<https://de.wikipedia.org/wiki/Vom_Fischer_und_seiner_Frau>]*




Ihr R startet nicht oder nicht richtig? Die drei wichtigsten Heilmittel sind:

1. Schließen Sie die Augen für eine Minute. Denken Sie an etwas Schönes und was 
Rs Problem sein könnte. 
2. Schalten Sie den Rechner aus und probieren Sie es 
morgen noch einmal. 
3. Googeln.

Sorry für die schnoddrigen Tipps. Aber: Es passiert allzu leicht, dass man 
Fehler wie diese macht:

- `install.packages(dplyr)` 
- `install.packages("dliar")`
- `install.packages("derpyler")` 
- `install.packages("dplyr")  # dependencies vergessen` 
- Keine Internet-Verbindung 
- `library(dplyr)  # ohne vorher zu installieren`


Wenn R oder RStudio dann immer noch nicht starten oder nicht richtig laufen, 
probieren Sie dieses:


- Sehen Sie eine Fehlermeldung, die von einem fehlenden Paket spricht (z.B. 
"Package 'Rcpp' not available") oder davon spricht, dass ein Paket nicht 
installiert werden konnte (z.B. "Package 'Rcpp' could not be installed" oder "es
gibt kein Paket namens ‘Rcpp’" oder "unable to move temporary installation XXX 
to YYY"), dann tun Sie folgendes:

- Schließen Sie R und starten Sie es neu. 
- Installieren Sie das oder die angesprochenen Pakete mit `install.packages("name_des_pakets", dependencies = TRUE)` oder mit dem entsprechenden Klick in RStudio. 
- Starten Sie das entsprechende Paket mit `library(paket_name)`.


- Gerade bei Windows 10 scheinen die Schreibrechte für R (und damit RStudio oder
RCommander) eingeschränkt zu sein. Ohne Schreibrechte kann R aber nicht die 
Pakete ("packages") installieren, die Sie für bestimmte R-Funktionen benötigen. 
Daher schließen Sie R bzw. RStudio und suchen Sie das Icon von R oder wenn Sie 
RStudio verwenden von RStudio. Rechtsklicken Sie das Icon und wählen Sie "als 
Administrator ausführen". Damit geben Sie dem Programm Schreibrechte. Jetzt 
können Sie etwaige fehlende Pakete installieren.

- Ein weiterer Grund, warum R bzw. RStudio die Schreibrechte verwehrt werden 
könnten (und damit die Installation von Paketen), ist ein Virenscanner. Der 
Virenscanner sagt, nicht ganz zu Unrecht: "Moment, einfach hier Software zu 
installieren, das geht nicht, zu gefährlich". Grundsätzlich gut, in diesem Fall 
unnötig. Schließen Sie R/RStudio und schalten Sie dann den Virenscanner 
*komplett* (!) aus. Öffnen Sie dann R/RStudio wieder und versuchen Sie fehlende 
Pakete zu installieren.



### Hier werden Sie geholfen

Es ist keine Schande, nicht alle Befehle der ca. 10,000 R-Pakete auswendig zu 
wissen. Schlauer ist, zu wissen, wo man Antworten findet. Hier eine Auswahl:

- Zu diesen Paketen gibt es gute "Spickzettel" (cheatsheets): ggplot2, 
RMarkdown, dplyr, tidyr. Klicken Sie dazu in RStudio auf *Help > Cheatsheets > 
...* oder gehen Sie auf <https://www.rstudio.com/resources/cheatsheets/>.

- In RStudio gibt es eine Reihe (viele) von Tastaturkürzeln (Shortcuts), die Sie
hier finden: *Tools > Keyboard Shortcuts Help*.

- Für jeden Befehl (d.i. Funktion) können Sie mit `?` Hilfe erhalten; probieren 
Sie z.B. `?mean`.

- Im Internet finden sich zuhauf Tutorials.

- Die bekannteste Seite, um Fragen rund um R zu diskutieren ist 
http://stackoverflow.com.





### Die Denk- und Gefühlswelt von R

- Wenn Sie RStudio starten, startet R automatisch auch. Starten Sie daher, wenn 
Sie RStudio gestartet haben, *nicht* noch extra R. Damit hätten Sie sonst zwei 
Instanzen von R laufen, was zu Verwirrungen (bei R und beim Nutzer) führen kann.

#### R-Skript-Dateien

- Ein neues *R-Skript*\index{R-Skript} im RStudio können Sie z.B. öffnen mit `File-New File-R Script`. Schreiben Sie dort Ihre R-Befehle; Sie können die Skriptdatei speichern, öffnen, ausdrucken, übers Bett hängen...

- R-Skripte können Sie speichern (`File-Save`) und öffnen.

- R-Skripte sind einfache Textdateien, die jeder Texteditor verarbeiten kann. 
Nur statt der Endung `.txt`, sind R-Skripte stolzer Träger der Endung `.R`. Es 
bleibt aber eine schnöde Textdatei. Geben Sie Ihren R-Skript-Dateien die Endung ".R",
damit erkennt RStudio, dass es sich um ein R-Skript handelt und bietet ein paar 
praktische Funktionen wie den "Run-Button".


#### Stolpersteine beim Errisch lernen

>    I Errr, therefore I am...


Verwenden Sie möglichst die neueste Version von R, RStudio und Ihres 
Betriebssystems. Ältere Versionen führen u.U. zu Problemen; je älter, desto 
Problem... Updaten Sie Ihre Packages regelmäßig z.B. mit `update.packages()` 
oder dem Button "Update" bei RStudio (Reiter `Packages`).

R zu lernen kann hart sein. Ich weiß, wovon ich spreche. Wahrscheinlich eine 
spirituelle Prüfung in Geduld und Hartnäckigkeit... Tolle Gelegenheit, sich in 
diesen Tugenden zu trainieren :-)





### Pakete installieren

Ein R-Paket, welches für die praktische Datenanalyse praktisch ist, heißt 
`dplyr`. Wir werden viel mit diesem Paket arbeiten. Bitte installieren Sie es 
schon einmal, sofern noch nicht geschehen:


```r
install.packages("dplyr", dependencies = TRUE) 
```




\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Beim Installieren von 
R-Paketen könnten Sie gefragt werden, welchen "Mirror" Sie verwenden möchten. 
Das hat folgenden Hintergrund: R-Pakete sind in einer Art "App-Store", mit Namen
CRAN (Comprehense R Archive Network) gespeichert. Damit nicht ein armer, kleiner
Server überlastet wird, wenn alle Studis dieser Welt just gerade beschließen, 
ein Paket herunterzuladen, gibt es viele Kopien dieses Servers - die "Mirrors", 
Spiegelbilder. Suchen Sie sich einfach einen aus, der in der Nähe ist.
</div>\EndKnitrBlock{rmdcaution}


Bei der Installation von Paketen mit `install.packages("name_des_pakets")` 
sollte stets der Parameter `dependencies = TRUE` angefügt werden. Also 
`install.packages("name_des_pakets", dependencies = TRUE)`. Hintergrund ist: 
Falls das zu installierende Paket seinerseits Pakete benötigt, die noch nicht 
installiert sind (gut möglich), dann werden diese sog. "dependencies" gleich 
mitinstalliert (wenn Sie  `dependencies = TRUE` setzen).


Sie müssen online sein, um Packages zu installieren.

Nicht vergessen: Installieren muss man eine Software *nur einmal*; *starten* 
(laden) muss man sie jedes Mal, wenn man sie vorher geschlossen hat und wieder 
nutzen möchte:


```r
library(dplyr) 
```

Der Befehl bedeutet sinngemäß: "Hey R, geh in die Bücherei (library) und hole 
das Buch (package) dplyr!".


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Wann benutzt man bei R Anführungszeichen? Das ist etwas verwirrend im Detail, aber die Grundegel 
lautet: wenn man Text anspricht. Im Beispiel oben "library(dplyr)" ist "dplyr" 
hier erst mal für R nichts Bekanntes, weil noch nicht geladen. Demnach müssten 
*eigentlich* Anführungsstriche stehen. Allerdings meinte ein Programmierer, dass
es doch so bequemer ist. Hat er Recht. Aber bedenken Sie, dass es sich um die 
Ausnahme einer Regel handelt. Sie können also auch schreiben: library("dplyr") 
oder library('dplyr'); geht beides.
</div>\EndKnitrBlock{rmdcaution}



Das Installieren und Starten anderer Pakete läuft genauso ab. Am besten 
installieren Sie alle Pakete, die wir in diesem Buch benötigen auf einmal, dann 
haben Sie Ruhe.



### R-Pakete für dieses Buch 

In diesem Buch verwenden wir die folgenden 
R-Pakete; diese müssen installiert^[Ggf. benötigen Sie Administrator-Rechte, um Pakete zu installieren. Virenscanner müssen evtl. ausgestaltet sein.] sein und geladen:





```r
Pakete 
#>  [1] "tidyverse"     "readr"         "knitr"         "stringr"      
#>  [5] "car"           "nycflights13"  "ISLR"          "pdftools"     
#>  [9] "downloader"    "ggdendro"      "gridExtra"     "tm"           
#> [13] "tidytext"      "lsa"           "SnowballC"     "wordcloud"    
#> [17] "RColorBrewer"  "okcupiddata"   "reshape2"      "wesanderson"  
#> [21] "GGally"        "titanic"       "compute.es"    "corrr"        
#> [25] "rpart"         "rpart.plot"    "MASS"          "titanic"      
#> [29] "arules"        "arulesViz"     "SDMTools"      "corrplot"     
#> [33] "gplots"        "corrplot"      "scatterplot3d" "BaylorEdPsych"
#> [37] "nFactors"      "rmarkdown"     "methods"
```


<!-- ### Vertiefung: Mehrere Pakete auf einmal installieren/starten -->
<!-- Anstelle alle einzeln zu laden (`library` verdaut nur ein Paket auf einmal),  -->
<!-- können wir mit etwas R-Judo alle auf einen Haps laden: -->

<!-- ```{r eval = FALSE}  -->
<!-- lapply(Pakete, require, character.only = TRUE)  -->
<!-- ``` -->


<!-- ```{r load_packages, include = FALSE}  -->
<!-- lapply(Pakete, require, character.only = TRUE)  -->
<!-- ``` -->


<!-- ``` {r include = FALSE, echo = FALSE, eval = FALSE}  -->
<!-- knitr::write_bib(Pakete, file = "libs.bib")  -->
<!-- ``` -->

<!-- Der Befehl heißt auf Deutsch: "Wende auf jedes Element von `Pakete` den Befehl  -->
<!-- `library` an"^[http://stackoverflow.com/questions/8175912/load-multiple-packages-at-once]. -->

<!-- Hin und wieder ist es sinnvoll, die Pakete auf den neuesten Stand zu bringen;  -->
<!-- das geht mit `update.packages()` . -->





### Datensätze


- Datensatz `profiles` aus dem R-Paket {okcupiddata} [@kim2015okcupid]; es handelt sich um Daten von einer Online-Singlebörse 
- Datensatz `Wage` aus dem R-Paket {ISLR} [@introstatlearning]; es handelt sich um Gehaltsdaten von US-amerikanischen Männern 
- Datensatz `inf_test_short`, hier herunterzuladen: <osf.io/sjhu> [@Sauer_2017]; es handelt sich um Ergebnisse einer Statistikklausur 
- Datensatz `flights` aus dem R-Paket {nycflights13} [@nycflights13]; es handelt sich um Abflüge von den New Yorker Flughäfen 
- Datensatz 'wo_men`, hier herunterzuladen: <osf.io/ja9dw> [@Sauer_2017a]; es handelt sich um Körper- und Schuhgröße von Studierenden
- Datensatz `tips` aus dem R-Paket {reshape2} [@bryant1995practical]; es handelt sich um Trinkgelder in einem Restaurant 
- Datensatz `extra`, hier herunterzuladen: <osf.io/4kgzh> [@Sauer_2016]; es handelt sich die Ergebnisse einer Umfrage zu Extraversion


Wir verwenden zwei Methoden, um Datensätze in R zu laden.

- Zum einen laden wir Datensätze aus R-Paketen, z.B. aus dem Paket 
`okcupiddata`. Dazu muss das entsprechende Paket installiert und geladen sein. 
Mit dem Befehl `data(name_des_datensatzes, package = "name_des_paketes")`, kann 
man dann die Daten laden. Das Laden eines Pakets lädt noch *nicht* die Daten des
Paketes; dafür ist der Befehl `data` zuständig.


```r
library(okcupiddata) data(profiles, package = "okcupiddata")
```


- Alternativ kann man die Daten als CSV- oder als XLS(X)-Datei importieren. Die 
Datei darf dabei sowohl auf einer Webseite als auch lokal (Festplatte, Stick...) 
liegen.


```r
Daten <- read.csv("https://sebastiansauer.github.io/data/tips.csv") 
```

Wir werden mit beiden Methoden arbeiten und "on the job" Details besprechen.






### Übungen

1. Öffnen Sie das Cheatsheet für RStudio und machen Sie sich mit dem Cheatsheet vertraut.

2. Sichten Sie kurz die übrigen Cheatsheets; später werden die Ihnen vielleicht von Nutzen sein.






## ERRRstkontakt

<!-- Es fehlen noch: -->
<!-- - Hinweise zu R-Datentypen -->


### Hinweise


Unser erster Kontakt mit R! Ein paar Anmerkungen vorweg:

- R unterscheidet zwischen Groß- und Kleinbuchstaben, d.h. `Oma` und `oma` sind 
zwei verschiedene Dinge für R!
- R verwendet den Punkt `.` als 
Dezimaltrennzeichen.
- Fehlende Werte werden in R durch `NA` kodiert.
- Kommentare werden mit dem Rautezeichen `#` eingeleitet; der Rest der Zeile von von R dann ignoriert. 
- Hilfe zu einem Befehl erhält man über ein vorgestelltes Fragezeichen `?`.
- Zusätzliche Funktionalität kann über Zusatzpakete hinzugeladen werden. Diese 
müssen ggf. zunächst installiert werden.
- *Variablennamen*\index{Variablen} (synonym: *Objekte*\index{Objekte}) in R müssen mit Buchstaben beginnen; ansonsten dürfen nur Zahlen, Unterstriche `-` und Minuszeichen `-` enthalten sein. Leerzeichen sind nicht erlaubt.
- Variablen einen Namen zu geben, ist nicht leicht, aber wichtig. Namen sollten knapp, aber aussagekräftig sein.

```
# so nicht:
var
x
dummy
objekt
dieser_name_ist_etwas_lang_vielleicht

# gut:
tips_mw
lm1
```

Um den Inhalt einer Variablen auszulesen, geben wir einfach den Namen des Objekts ein (und schicken den Befehl ab).

### R als Taschenrechner

Auch wenn Statistik nicht Mathe ist, so kann man mit R 
auch rechnen. Geben Sie zum Üben die Befehle in der R Konsole hinter der 
Eingabeaufforderung `>` ein und beenden Sie die Eingabe mit `Return` bzw. 
`Enter`. 


```r
4+2 
#> [1] 6
```
Das Ergebnis wird direkt angezeigt. Bei 

```r
x <- 4+2 
```

erscheint zunächst kein Ergebnis. Über `<-` wird der Variable `x` der Wert 
`4+2` zugewiesen. Wenn Sie jetzt 

```r
x 
```

eingeben, wird das 
Ergebnis 

```
#> [1] 6
```

angezeigt. Sie können jetzt auch mit `x` 
weiterrechnen, z.B.: 


```r
x/4 
#> [1] 1.5
```

Vielleicht fragen Sie sich was die `[1]` vor dem 
Ergebnis bedeutet. R arbeitet vektororientiert, und die `[1]` zeigt an, dass es 
sich um das erste (und hier auch letzte) Element des Vektors handelt.


### Text und Variablen zuweisen

Man kann einer Variablen auch Text zuweisen (im Gegensatz zu Zahlen):


```r
y <- "Hallo R!"
```


Man kann auch einer Variablen eine andere zuweisen:


```r
y <- x
```

Wird jetzt y mit dem Inhalt von x überschrieben oder umgekehrt? Der Zuweisungspfeil `<-` macht die Richtung der Zuweisung ganz klar. Zwar ist in R das Gleichheitszeichen synonym zum Zuweisungspfeil erlaubt, aber der Zuweisungspfeil macht die Sache glasklar und sollte daher bevorzugt werden.


Man kann auch einer Variablen *mehr als* einen Wert zuweisen:


```r
x <- c(1, 2, 3)
```

Dieser Befehl erzeugt eine "Spalte" (einen Vektor). Will man einer Variablen *mehr als* einen Wert zuweisen, muss man die Werte erst in einen Vektor "zusammen binden"; das geht mit dem Befehl `c` (wie *c*ombine).


### Funktionen aufrufen


Um einen "Befehl" (präziser: eine Funktion) aufzurufen, geben wir ihren Namen an
und definieren sog. "Parameter" in einer runden Klammer, z.B. so:


```r
wo_men <- read.csv("data/wo_men.csv")
```

Allgemein gesprochen:

```
funktionsname(parametername1 = wert1, parametername2 = wert2, ...)
```

Die drei Punkte `...` sollen andeuten, dass evtl. weitere Parameter zu übergeben wären. 
Die Reihenfolge der Parameter ist egal - wenn man die Parameternamen anführt. 
Ansonsten muss man sich an die Standard-Reihenfolge, die eine Funktion vorgibt halten:


```r
#ok:
wo_men <- read.csv(file = "data/wo_men.csv", header = TRUE, sep = ",")
wo_men <- read.csv("data/wo_men.csv", TRUE, ",")
wo_men <- read.csv(header = TRUE, sep = ",", file = "data/wo_men.csv")


# ohno:
wo_men <- read.csv(TRUE, "data/wo_men.csv", ",")
```


### Übungen 

3. Führen Sie diese Syntax aus:


```r
meine_coole_variable <- 10
meine_coole_var1able 
```

Woher rührt der Fehler?

4. Korrigieren Sie die Syntax:


```r
install.packages(dplyer)
```


`y <- Hallo R!`


`Hallo R <- 1`



```r
Hallo_R < - 1
```


## Was ist Statistik? Wozu ist sie gut?

Zwei Fragen bieten sich sich am Anfang der Beschäftigung mit jedem Thema an: Was
ist die Essenz des Themas? Warum ist das Thema (oder die Beschäftigung damit) 
wichtig?

Was ist Statistik? *Eine* Antwort dazu ist, dass Statistik die Wissenschaft von
Sammlung, Analyse, Interpretation und Kommunikation von Daten ist mithilfe 
mathematischer Verfahren ist und zur Entscheidungshilfe beitragen solle 
[@oxford; @sep-statistics]. Damit hätten wir auch den Unterschied zur schnöden 
Datenanalyse (ein Teil der Statistik) herausgemeißelt. Statistik wird häufig in 
die zwei Gebiete *deskriptive* und *inferierende* Statistik eingeteilt. Erstere 
fasst viele Zahlen zusammen, so dass wir den Wald statt vieler Bäume sehen. 
Letztere verallgemeinert von den vorliegenden (sog. "Stichproben-")Daten auf 
eine zugrunde liegende Grundmenge (Population). Dabei spielt die 
Wahrscheinlichkeitsrechnung (Stochastik) eine große 
Rolle.


Aufgabe der deskriptiven Statistik ist es primär, Daten prägnant 
zusammenzufassen. Aufgabe der Inferenzstatistik ist es, zu prüfen, ob Daten 
einer Stichprobe auf eine Grundgesamtheit verallgemeinert werden können.


Dabei lässt sich der Begriff "Statistik" als Überbegriff von "Datenanalyse" 
verstehen, wenn diese Sicht auch nicht von allen geteilt wird 
[@grolemund2014cognitive]. In diesem Buch steht die Aufbereitung, Analyse, 
Interpretation und Kommunikation von Daten im Vordergrund. Liegt der Schwerpunkt
dieser Aktivitäten bei computerintensiven Methoden, so wird auch von *Data 
Science* gesprochen, wobei der Begriff nicht einheitlich verwendet wird [@r4ds;
@hardin2015data]

*Daten* kann man definieren als *Informationen, die in einem Kontext stehen*
[@moore1990uncertainty], wobei eine numerische Konnotation mitschwingt.

*Modellieren* kann man als *zentrale Aufgabe von Statistik* begreifen 
[@cobb2007introductory; @grolemund2014cognitive]. Einfach gesprochen, bedeutet 
Modellieren in diesem Sinne, ein mathematisches Narrativ ("Geschichte") zu 
finden, welches als Erklärung für gewisse Muster in den Daten fungiert; vgl. 
Kap. \@ref{mod1}.

Statistisches Modellieren läuft gewöhnlich nach folgendem Muster ab [@grolemund2014cognitive]:


```
Prämisse 1: Wenn Modell M wahr ist, dann sollten die Daten das Muster D aufweisen.
Prämisse 2: Die Daten weisen das Muster D auf.

---

Konklusion: Daher muss das Modell M wahr sein.
```

Die Konklusion ist *nicht* zwangsläufig richtig. Es ist falsch zu sagen, dass dieses Argumentationsmuster - Abduktion [@peirce1955abduction] genannt - wahre, sichere Schlüsse (Konklusionen) liefert. Die Konklusion *kann, muss aber nicht*, zutreffen.

Ein Beispiel: Auf dem Nachhauseweg eines langen Arbeitstags wartet, in einer dunklen Ecke, ein Mann, der sich als Statistik-Professor vorstellt und Sie zu einem Glücksspiel einlädt. Sofort sagen Sie zu. Der Statistiker will 10 Mal eine Münze werfen, er setzt auf Zahl (versteht sich). Wenn er gewinnt, bekommt er 10€ von Ihnen; gewinnen Sie, bekommen Sie 11€ von ihm. Hört sich gut an, oder? Nun wirft er die Münze zehn Mal. Was passiert? Er gewinnt 10 Mal, natürlich (so will es die Geschichte). Sollten wir glauben, dass er ein Betrüger ist?

Ein Modell, welches wir hier verwenden könnten, lautet: Wenn die Münze gezinkt ist (Modell M zutrifft), dann wäre diese Datenlage D (10 von 10 Treffern) wahrscheinlich - Prämisse 1. Datenlage D ist tatsächlich der Fall; der Statistiker hat 10 von 10 Treffer erzielt - Prämisse 2. Die Daten D "passen" also zum Modell M; man entscheidet sich, dass der Professor ein Falschspieler ist. 

Wichtig zu erkennen ist, dass Abduktion mit dem Wörtchen *wenn* beginnt. Also davon *ausgeht*, dass ein Modell M der Fall ist (der Professor also tatsächlich ein Betrüger ist). Dass, worüber wir entscheiden wollen, wird also bereits vorausgesetzt. Gilt also M, wie gut passen dann die Daten dazu? 

>    Wie gut passen die Daten D zum Modell M?

Das ist die Frage, die hier tatsächlich gestellt bzw. beantwortet wird.

Natürlich ist es keineswegs sicher, *dass* das Modell gilt. Darüber macht die Abduktion auch keine Aussage. Es könnte also sein, dass ein anderes Modell zutrifft: Der Professor könnte ein Heiliger sein, der uns auf etwas merkwürdige Art versucht, Geld zuzuschanzen... Oder er hat einfach Glück gehabt.

>   Statistische Modelle beantworten i.d.R. nicht, wie wahrsheinlich es ist, dass ein Modell gilt. Statistische Modelle beurteilen, wie gut Daten zu einem Modell passen.

Häufig trifft ein Modell eine Reihe von Annahmen, die nicht immer explizit gemacht werden, aber die klar sein sollten. Z.B. sind die Münzwürfe unabhängig voneinander? Oder kann es sein, dass sich die Münze "einschießt" auf eine Seite? Dann wären die Münzwürfe nicht unabhängig voneinander. In diesem Fall klingt das reichlich unplausibel; in anderen Fällen kann dies eher der Fall sein[^447]. Auch wenn die Münzwürfe unabhängig voneinander sind, ist die Wahrscheinlichkeit für Zahl jedes Mal gleich? Hier ist es wiederum unwahrscheinlich, dass sich die Münze verändert, ihre Masse verlagert, so dass eine Seite Unwucht bekommt. In anderen Situationen können sich Untersuchungsobjekte verändern (Menschen lernen manchmal etwas, sagt man), so dass die Wahrscheinlichkeiten für ein Ereignis unterschiedlich sein können, man dies aber nicht berücksichtigt. 


## Befehlsübersicht


Funktion             Beschreibung
-----------------    -------------
install.packages     installiert ein Paket
library              lädt ein Paket
<-                   Weist einer Variablen einen Wert zu
c                    erstellt eine Spalte/ einen Vektor

Diese Befehle "wohnen" alle im Standard-R; es ist für diese Befehle nicht nötig, zusätzliche Pakete zu installieren/ laden.


## Verweise

- Chester Ismay erläutert einige Grundlagen von R und RStudio, die für 
Datenanalyse hilfreich sind: https://bookdown.org/chesterismay/rbasics/.

- Roger Peng und Kollegen bieten hier einen Einstieg in Data Science mit R: 
https://bookdown.org/rdpeng/artofdatascience/

- Wickam und Grolemund [-@r4ds] geben einen hervorragenden Überblick in das 
Thema dieses Buches; ihr Buch ist sehr zu empfehlen.

- Wer einen stärker an der Statistik orientierten Zugang sucht, aber 
"mathematisch sanft" behandelt werden möchte, wird bei James et al. 
[-@introstatlearning] glücklich oder zumindest fündig werden.





[^447]: Sind z.B. die Prüfungsergebnisse von Schülern unabhängig voneinander? Möglicherweise haben sie von einem "Superschüler" abgeschrieben. Wenn der Superschüler viel weiß, dann zeigen die Abschreiber auch gute Leistung.

<!--chapter:end:020_Rahmen_1.Rmd-->





# Daten einlesen


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Wissen, was eine CSV-Datei ist.
- Wissen, was UTF-8 bedeutet.
- Erläutern können, was R unter dem "working directory" versteht.
- Erkennen können, ob eine Tabelle in Normalform vorliegt.
- Daten aus R hinauskriegen (exportieren).

</div>\EndKnitrBlock{rmdcaution}

Dieses Kapitel beantwortet eine Frage: "Wie kriege ich Daten in vernünftiger Form in R hinein?".

<div class="figure" style="text-align: center">
<img src="images/Einlesen.pdf" alt="Daten sauber einlesen" width="70%" />
<p class="caption">(\#fig:step-Einlesen)Daten sauber einlesen</p>
</div>


## Daten in R importieren
In R kann man ohne Weiteres verschiedene, gebräuchliche (Excel oder CSV) oder weniger
gebräuchliche (Feather^[<https://cran.r-project.org/web/packages/feather/index.html>]) Datenformate einlesen. In RStudio lässt sich dies
z.B. durch einen schnellen Klick auf `Import Dataset` im Reiter `Environment`
erledigen^[Um CSV-Dateien zu laden wird durch den Klick im Hintergrund das Paket `readr` verwendet [@readr];
die entsprechende Syntax wird in der Konsole ausgegeben, so dass man sie sich
anschauen und weiterverwenden kann].


### Excel-Dateien importieren

Am einfachsten ist es, eine Excel-Datei (.xls oder .xlsx) über die RStudio-Oberfläche zu importieren; das ist mit ein paar Klicks geschehen^[im Hintergrund wird das Paket `readxl` verwendet]:

<div class="figure" style="text-align: center">
<img src="images/import_RStudio.png" alt="Daten einlesen (importieren) mit RStudio" width="50%" />
<p class="caption">(\#fig:data-import-RStudio)Daten einlesen (importieren) mit RStudio</p>
</div>



Es ist für bestimmte Zwecke sinnvoll, nicht zu klicken, sondern die Syntax einzutippen. Zum Beispiel: Wenn Sie die komplette Analyse als Syntax in einer Datei haben (eine sog. "Skriptdatei"), dann brauchen Sie (in RStudio) nur alles auszuwählen und auf `Run` zu klicken, und die komplette Analyse läuft durch! Die Erfahrung zeigt, dass das ein praktisches Vorgehen ist.


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">
Daten (CSV, Excel,...)  können Sie *nicht* öffnen über `File > Open File ...`. Dieser Weg ist Skript-Dateien vorbehalten. 
</div>\EndKnitrBlock{rmdcaution}


### CSV-Dateien importieren

Die gebräuchlichste Form von Daten für statistische Analysen ist wahrscheinlich das CSV-Format. Das ist ein einfaches Format, basierend auf einer Textdatei. Schauen Sie sich mal diesen Auszug aus einer CSV-Datei an.

```
"ID","time","sex","height","shoe_size"
"1","04.10.2016 17:58:51",NA,160.1,40
"2","04.10.2016 17:58:59","woman",171.2,39
"3","04.10.2016 18:00:15","woman",174.2,39
"4","04.10.2016 18:01:17","woman",176.4,40
"5","04.10.2016 18:01:22","man",195.2,46
```

Erkennen Sie das Muster? Die erste Zeile gibt die "Spaltenköpfe" wieder, also die Namen der Variablen. Hier sind es 5 Spalten; die vierte heißt "shoe_size". Die Spalten sind offenbar durch Komma `,` voneinander getrennt. Dezimalstellen sind in amerikanischer Manier mit einem Punkt `.` dargestellt. Die Daten sind "rechteckig"; alle Spalten haben gleich viele Zeilen und umgekehrt alle Spalten gleich viele Zeilen. Man kann sich diese Tabelle gut als Excel-Tabelle mit Zellen vorstellen, in denen z.B. "ID" (Zelle oben links) oder "46" (Zelle unten rechts) steht.

An einer Stelle steht `NA`. Das ist Errisch für "fehlender Wert". Häufig wird die Zelle auch leer gelassen, um auszudrücken, dass ein Wert hier fehlt (hört sich nicht ganz doof an). Aber man findet alle möglichen Ideen, um fehlende Werte darzustellen. Ich rate von allen anderen ab; führt nur zu Verwirrung.

Lesen wir diese Daten jetzt ein:



```r
daten <- read.csv("data/wo_men.csv")
```



Der Befehl `read.csv` liest also eine CSV-Datei, was uns jetzt nicht übermäßig überrascht. Aber Achtung: Wenn Sie aus einem Excel mit deutscher Einstellung eine CSV-Datei exportieren, wird diese CSV-Datei als Trennzeichen `;` (Strichpunkt) und als Dezimaltrennzeichen `,` verwenden. Da der Befehl `read.csv` als Standard mit Komma und Punkt arbeitet, müssen wir die deutschen Sonderlocken explizit angeben, z.B. so:


```r
# nicht ausführen:
daten_deutsch <- read.csv("daten_deutsch.csv", sep = ";", dec = ".")
```

Dabei steht `sep` (separator) für das Trennzeichen zwischen den Spalten und `dec` für das Dezimaltrennzeichen. R bietet eine Kurzfassung für `read.csv` mit diesen Parametern: `read.csv2("daten_deutsch.csv")`.

### Vertiefung: Einlesen mit Prüfung


```
#>   X                time   sex height shoe_size
#> 1 1 04.10.2016 17:58:51 woman    160        40
#> 2 2 04.10.2016 17:58:59 woman    171        39
#> 3 3 04.10.2016 18:00:15 woman    174        39
#> 4 4 04.10.2016 18:01:17 woman    176        40
#> 5 5 04.10.2016 18:01:22   man    195        46
#> 6 6 04.10.2016 18:01:53 woman    157        37
```

Wir haben zuerst geprüft, ob die Datei (`wo_men.csv`) im entsprechenden Ordner existiert oder nicht (das `!`-Zeichen heißt auf Errisch "nicht"). Falls die Datei nicht im Ordner existiert, laden wir sie mit `read.csv` herunter und direkt ins R hinein. Andernfalls (`else`) lesen wir sie direkt ins R hinein.



### Das Arbeitsverzeichnis

\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">
Übrigens: Wenn Sie keinen Pfad angeben, so geht R davon aus, dass die Daten im aktuellen Verzeichnis (dem *working directory*) liegen. 
</div>\EndKnitrBlock{rmdcaution}

Das aktuelle Verzeichnis (Arbeitsverzeichnis; "working directory") kann man mit `getwd()` erfragen und mit `setwd()` einstellen. Komfortabler ist es aber, das aktuelle Verzeichnis per Menü zu ändern. In RStudio: `Session > Set Working Directory > Choose Directory ...` (oder per Shortcut, der dort angezeigt wird).

Es ist praktisch, das Arbeitsverzeichnis festzulegen, denn dann kann man z.B. eine Datendatei einlesen, ohne den Pfad eingeben zu müssen:


```r
# nicht ausführen:
daten_deutsch <- read.csv("daten_deutsch.csv", sep = ";", dec = ".")
```

R geht dann davon aus, dass sich die Datei `daten_deutsch.csv` im Arbeitsverzeichnis befindet.

## Normalform einer Tabelle
Tabellen in R werden als `data frames` ("Dataframe" auf Denglisch; moderner: als `tibble`, Tibble kurz für "Table-df") bezeichnet. Tabellen sollten in "Normalform" vorliegen ("tidy"), bevor wir weitere Analysen starten. Unter Normalform verstehen sich folgende Punkte:

- Es handelt sich um einen Dataframe, also um eine Tabelle mit Spalten mit Namen und gleicher Länge; eine Datentabelle in rechteckiger Form und die Spalten haben einen Namen.
- In jeder Zeile steht eine Beobachtung, in jeder Spalte eine Variable.
- Fehlende Werte sollten sich in *leeren* Zellen niederschlagen.
- Daten sollten nicht mit Farbmarkierungen o.ä. kodiert werden.
- Es gibt keine Leerzeilen und keine Leerspalten.
- In jeder Zelle steht ein Wert.
- Am besten verwendet man keine Sonderzeichen verwenden und keine Leerzeichen in Variablennamen und -werten, sondern nur Ziffern und Buchstaben und Unterstriche.
- Variablennamen dürfen nicht mit einer Zahl beginnen.

Abbildung \@ref{fig:tidy1} visualisiert die Bestimmungsstücke eines Dataframes [@r4ds]: 

<div class="figure" style="text-align: center">
<img src="images/tidy-1.png" alt="Schematische Darstellung eines Dataframes in Normalform" width="70%" />
<p class="caption">(\#fig:tidy1)Schematische Darstellung eines Dataframes in Normalform</p>
</div>



Der Punkt "Jede Zeile eine Beobachtung, jede Spalte eine Variable" verdient besondere Beachtung. Betrachten Sie dieses Beispiel:

<div class="figure" style="text-align: center">
<img src="images/breit_lang.pdf" alt="Dieselben Daten - einmal breit, einmal lang" width="70%" />
<p class="caption">(\#fig:lang-breit)Dieselben Daten - einmal breit, einmal lang</p>
</div>


In der rechten Tabelle sind die Variablen `Quartal` und `Umsatz` klar getrennt; jede hat ihre eigene Spalte. In der linken Tabelle hingegen sind die beiden Variablen vermischt. Sie haben nicht mehr ihre eigene Spalte, sondern sind über vier Spalten verteilt. Die rechte Tabelle ist ein Beispiel für eine Tabelle in Normalform, die linke nicht.


<div class="figure" style="text-align: center">
<img src="images/Normalform.pdf" alt="Illustration eines Datensatzes in Normalform" width="70%" />
<p class="caption">(\#fig:fig-Normalform)Illustration eines Datensatzes in Normalform</p>
</div>

## Vertiefung

### Tabelle in Normalform bringen

Eine der ersten Aktionen einer Datenanalyse sollte also die "Normalisierung" Ihrer Tabelle sein. In R bietet sich dazu das Paket `tidyr` an, mit dem die Tabelle von Breit- auf Langformat (und wieder zurück) geschoben werden kann.

Ein Beispiel dazu:


```r
meindf <- read.csv("http://stanford.edu/~ejdemyr/r-tutorials/data/unicef-u5mr.csv")

df_lang <- gather(meindf, year, u5mr, U5MR.1950:U5MR.2015)

df_lang <- separate(df_lang, year, into = c("U5MR", "year"), sep = ".")
```

- Die erste Zeile liest die Daten aus einer CSV-Datei ein; praktischerweise direkt von einer Webseite.   
- Die zweite Zeile `gather` formt die Daten *von breit nach lang* um. Die neuen Spalten, nach der Umformung heißen dann `year` und `u5mr` (Sterblichkeit bei Kindern unter fünf Jahren). In die Umformung werden die Spalten `U5MR 1950` bis `U5MR 2015` einbezogen.
- Die dritte Zeile `separate` *entzerrt* die Werte der Spalte `year`; hier stehen die ehemaligen Spaltenköpfe. Man nennt sie auch `key` Spalte daher. Steht in einer Zelle von `year` bspw. `U5MR 1950`, so wird `U5MR` in eine Spalte mit Namen `U5MR` und `1950` in eine Spalte mit Namen `year` geschrieben.


### Textkodierung

Öffnet man eine Textdatei mit einem Texteditor seiner Wahl, so sieht man... Text und sonst nichts, also keine Formatierung etc. Eine Textdatei besteht aus Text und sonst nichts (daher der Name...). Auch eine R-Skript-Datei (`Coole_Syntax.R`) ist eine Textdatei.
Technisch gesprochen werden nur die Textzeichen gespeichert, sonst nichts; im Gegensatz dazu speichert eine Word-Datei noch mehr, z.B. Formatierung. Ein bestimmtes Zeichen wie "A" bekommt einen bestimmten Code wie "41". Mit etwas Glück weiß der Computer jetzt, dass er das Zeichen "41" auf den Bildschirm ausgeben soll. Es stellt sich jetzt die Frage, welche Code-Tabelle der Computer nutzt? Welchem Code wird "A" (bzw. ein beliebiges Zeichen) zugeordnet? Mehrere solcher Kodierungstafeln existieren. Die gebräuchlichste im Internet heißt *UTF-8*^[https://de.wikipedia.org/wiki/UTF-8]. Leider benutzen unterschiedliche Betriebssysteme unterschiedliche Kodierungstafeln, was zu Verwirrung führt. Ich empfehle, ihre Textdateien als UTF-8 zu kodieren. RStudio fragt sie, wie eine Textdatei kodiert werden soll. Sie können auch unter `File > Save with Encoding...` die Kodierung einer Textdatei festlegen.

>    Speichern Sie R-Textdateien wie Skripte stets mit UTF-8-Kodierung ab.


### Daten exportieren

Wie bekommt man seine Daten wieder aus R raus ("ich will zu Excel zurück!")?

Eine Möglichkeit bietet die Funktion `write.csv`; sie schreibt eine CSV-Datei:

```
write.csv(name_der_tabelle, "Dateiname.csv")
```

Mit `help(write.csv)` bekommt man mehr Hinweise dazu. Beachten Sie, dass immer in das aktuelle Arbeitsverzeichnis geschrieben wird.



## Befehlsübersicht

Paket::Funktion      Beschreibung
-----------------    -------------
read.csv             Liest eine CSV-Datei ein.
write.csv            Schreibt einen Dateframe in eine CSV-Datei.
readr::gather        Macht aus einem "breiten" Dataframe einen "langen".
readr::separate      "Zieht" Spalten auseinander.  




## Übungen^[F, R, F, R, R, R, F, F]

\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. In CSV-Dateien dürfen Spalten *nie* durch Komma getrennt sein.
2. RStudio bietet die Möglichkeit, CSV-Dateien per Klick zu importieren.
2. RStudio bietet *nicht* die Möglichkeit, CSV-Dateien per Klick zu importieren.
2. "Deutsche" CSV-Dateien verwenden als Spalten-Trennzeichen einen Strichpunkt.
2. In einer Tabelle in Normalform stehen in jeder Zeile eine Beobachtung.
2. In einer Tabelle in Normalform stehen in jeder Spalte eine Variable.
2. R stellt fehlende Werte mit einem Fragezeichen `?` dar.
2. Um Excel-Dateien zu importieren, kann man den Befehl `read.csv` verwenden.


</div>\EndKnitrBlock{rmdexercises}




## Verweise

- *R for Data Science* bietet umfangreiche Unterstützung zu diesem Thema [@r4ds].



<!--chapter:end:030_Tidy_Data.Rmd-->





# Datenjudo

\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Typische Probleme der Datenanalyse schildern können.
- Zentrale `dplyr`-Befehle anwenden können.
- `dplyr`-Befehle kombinieren können.
- Die Pfeife anwenden können.
- Werte umkodieren und "binnen" können.

</div>\EndKnitrBlock{rmdcaution}


<div class="figure" style="text-align: center">
<img src="images/Datenjudo/Aufbereiten.pdf" alt="Daten aufbereiten" width="70%" />
<p class="caption">(\#fig:fig-datenjudo)Daten aufbereiten</p>
</div>

In diesem Kapitel benötigte Pakete: 

```r
library(tidyverse)  # Datenjudo
library(stringr)   # Texte bearbeiten
library(car)  # für 'recode'
```

Das Paket `tidyverse` lädt `dplyr`, `ggplot2` und weitere Pakete^[für eine Liste s. `tidyverse_packages(include_self = TRUE)`]. Daher ist es komfortabler, `tidyverse` zu laden, damit spart man sich Tipparbeit. Die eigentliche Funktionalität, die wir in diesem Kapitel nutzen, kommt aus dem Paket `dplyr`.


Mit *Datenjudo*\index{Datenjudo} ist gemeint, die Daten für die eigentliche Analyse "aufzubereiten". Unter *Aufbereiten*\index{Datenjudo} ist hier das Umformen, Prüfen, Bereinigen, Gruppieren und Zusammenfassen von Daten gemeint. Die deskriptive Statistik fällt unter die Rubrik Aufbereiten. Kurz gesagt: Alles, wan tut, nachdem die Daten "da" sind und bevor man mit anspruchsvoller(er) Modellierung beginnt.

Ist das Aufbereiten von Daten auch nicht statistisch anspruchsvoll, so ist es trotzdem von großer Bedeutung und häufig recht zeitintensiv. Eine Anekdote zur Relevanz der Datenaufbereitung, die (so will es die Geschichte) mir an einer Bar nach einer einschlägigen Konferenz erzählt wurde (daher keine Quellenangebe, Sie verstehen...). Eine Computerwissenschaftlerin aus den USA (deutschen Ursprungs) hatte einen beeindruckenden "Track Record" an Siegen in Wettkämpfen der Datenanalyse. Tatsächlich hatte sie keine besonderen, raffinierten Modellierungstechniken eingesetzt; klassische Regression war ihre Methode der Wahl. Bei einem Wettkampf, bei dem es darum ging, Krebsfälle aus Krankendaten vorherzusagen (z.B. von Röntgenbildern) fand sie nach langem Datenjudo heraus, dass in die "ID-Variablen" Information gesickert war, die dort nicht hingehörte und die sie nutzen konnte für überraschend (aus Sicht der Mitstreiter) gute Vorhersagen zu Krebsfällen. Wie war das möglich? Die Daten stammten aus mehreren Kliniken, jede Klinik verwendete ein anderes System, um IDs für Patienten zu erstellen. Überall waren die IDs stark genug, um die Anonymität der Patienten sicherzustellen, aber gleich wohl konnte man (nach einigem Judo) unterscheiden, welche ID von welcher Klinik stammte. Was das bringt? Einige Kliniken waren reine Screening-Zentren, die die Normalbevölkerung versorgte. Dort sind wenig Krebsfälle zu erwarten. Andere Kliniken jedoch waren Onkologie-Zentren für bereits bekannte Patienten oder für Patienten mit besonderer Risikolage. Wenig überraschen, dass man dann höhere Krebsraten vorhersagen kann. Eigentlich ganz einfach; besondere Mathe steht hier (zumindest in dieser Geschichte) nicht dahinter. Und, wenn man den Trick kennt, ganz einfach. Aber wie so oft ist es nicht leicht, den Trick zu finden. Sorgfältiges Datenjudo hat hier den Schlüssel zum Erfolg gebracht.


## Typische Probleme
Bevor man seine Statistik-Trickkiste so richtig schön aufmachen kann, muss man die Daten häufig erst noch in Form bringen. Das ist nicht schwierig in dem Sinne, dass es um komplizierte Mathe ginge. Allerdings braucht es mitunter recht viel Zeit und ein paar (oder viele) handwerkliche Tricks sind hilfreich. Hier soll das folgende Kapitel helfen.

<!-- Mit "Datenjudo" (ein Fachbegriff aus der östlichen Zahlentheorie) ist gemeint, die Daten so "umzuformen", "aufzubereiten", oder "reinigen" , dass sie passend für statistische Analysen sind.  -->

Typische Probleme, die immer wieder auftreten, sind:

- *Fehlende Werte*: Irgend jemand hat auf eine meiner schönen Fragen in der Umfrage nicht geantwortet!
- *Unerwartete Daten*: Auf die Frage, wie viele Facebook-Freunde er oder sie habe, schrieb die Person "I like you a lot". Was tun???
- *Daten müssen umgeformt werden*: Für jede der beiden Gruppen seiner Studie hat Joachim einen Google-Forms-Fragebogen aufgesetzt. Jetzt hat er zwei Tabellen, die er "verheiraten" möchte. Geht das?
- *Neue Variablen (Spalten) berechnen*: Ein Student fragt nach der Anzahl der richtigen Aufgaben in der Statistik-Probeklausur. Wir wollen helfen und im entsprechenden Datensatz eine Spalte erzeugen, in der pro Person die Anzahl der richtig beantworteten Fragen steht.


## Daten aufbereiten mit `dplyr`

Es gibt viele Möglichkeiten, Daten mit R aufzubereiten; `dplyr`^[https://cran.r-project.org/web/packages/dplyr/index.html] ist ein populäres Paket dafür. Eine zentrale Idee von `dplyr` ist, dass es nur ein paar wenige Grundbausteine geben sollte, die sich gut kombinieren lassen. Sprich: Wenige grundlegende Funktionen mit eng umgrenzter Funktionalität. Der Autor, Hadley Wickham, sprach einmal in einem Forum (citation needed), dass diese Befehle wenig können, das Wenige aber gut. Ein Nachteil dieser Konzeption kann sein, dass man recht viele dieser Bausteine kombinieren muss, um zum gewünschten Ergebnis zu kommen. Außerdem muss man die Logik des Baukastens gut verstanden habe - die Lernkurve ist also erstmal steiler. Dafür ist man dann nicht darauf angewiesen, dass es irgendwo "Mrs Right" gibt, die genau das kann, was ich will. Außerdem braucht man sich auch nicht viele Funktionen merken. Es reicht einen kleinen Satz an Funktionen zu kennen (die praktischerweise konsistent in Syntax und Methodik sind). 


Willkommen in der Welt von `dyplr`! `dplyr` hat seinen Namen, weil es sich ausschließlich um *D*ataframes bemüht; es erwartet einen Dataframe als Eingabe und gibt einen Dataframe zurück (zumindest bei den meisten Befehlen).


Diese Bausteine sind typische Tätigkeiten im Umgang mit Daten; nichts Überraschendes. Schauen wir uns diese Bausteine näher an.


### Zeilen filtern mit `filter`

Häufig will man bestimmte Zeilen aus einer Tabelle filtern; `filter`\index{dplyr::filter}. Zum Beispiel man arbeitet für die Zigarettenindustrie und ist nur an den Rauchern interessiert (die im Übrigen unser Gesundheitssystem retten [@kraemer2011wir]), nicht an Nicht-Rauchern; es sollen die nur Umsatzzahlen des letzten Quartals untersucht werden, nicht die vorherigen Quartale; es sollen nur die Daten aus Labor X (nicht Labor Y) ausgewertet werden etc.

Ein Sinnbild:

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/filter.pdf" alt="Zeilen filtern" width="70%" />
<p class="caption">(\#fig:fig-filter)Zeilen filtern</p>
</div>

Merke:

>    Die Funktion `filter` filtert Zeilen aus einem Dataframe.

Schauen wir uns einige Beispiel an; zuerst die Daten laden nicht vergessen. Achtung: "Wohnen" die Daten in einem Paket, muss dieses Paket installiert sein, damit man auf die Daten zugreifen kann.


```r
data(profiles, package = "okcupiddata")  # Das Paket muss installiert sein
```



```r
df_frauen <- filter(profiles, sex == "f")  # nur die Frauen
df_alt <- filter(profiles, age > 70)  # nur die alten
df_alte_frauen <- filter(profiles, age > 70, sex == "f")  # nur die alten Frauen, d.h. UND-Verknüpfung
df_nosmoke_nodrinks <- filter(profiles, smokes == "no" | drinks == "not at all") 
# liefert alle Personen, die Nicht-Raucher *oder* Nicht-Trinker sind
```

Gar nicht so schwer, oder? Allgemeiner gesprochen werden diejenigen Zeilen gefiltert (also behalten bzw. zurückgeliefert), für die das Filterkriterium `TRUE` ist. 



\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Manche Befehle wie `filter` haben einen Allerweltsnamen; gut möglich, dass ein Befehl mit gleichem Namen in einem anderen (geladenen) Paket existiert. Das kann dann zu Verwirrungen führen - und kryptischen Fehlern. Im Zweifel den Namen des richtigen Pakets ergänzen, und zwar zum Beispiel so: `dplyr::filter(...)`.
</div>\EndKnitrBlock{rmdcaution}

#### Aufgaben^[F, R, F, F, R]

\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. `filter` filtert Spalten.
1. `filter` ist eine Funktion aus dem Paket `dplyr`.
1. `filter` erwartet als ersten Parameter das Filterkriterium.
1. `filter` lässt nur ein Filterkriterium zu.
1. Möchte man aus dem Datensatz `profiles` (`okcupiddata`) die Frauen filtern, so ist folgende Syntax korrekt: `filter(profiles, sex == "f")´.


</div>\EndKnitrBlock{rmdexercises}


#### Vertiefung: Fortgeschrittene Beispiele für `filter`

Einige fortgeschrittene Beispiele für `filter`:

Man kann alle Elemente (Zeilen) filtern, die zu einer Menge gehören und zwar mit diesem Operator: `%in%`:


```r
filter(profiles, body_type %in% c("a little extra", "average"))
```

Besonders Textdaten laden zu einigen Extra-Überlegungen ein; sagen wir, wir wollen alle Personen filtern, die Katzen bei den Haustieren erwähnen. Es soll reichen, wenn `cat` ein Teil des Textes ist; also `likes dogs and likes cats` wäre OK (soll gefiltert werden). Dazu nutzen wir ein Paket zur Bearbeitung von Strings (Textdaten):


```r

filter(profiles, str_detect(pets, "cats"))
```


Ein häufiger Fall ist, Zeilen *ohne* fehlende Werte (`NA`s) zu filtern. Das geht einfach:


```r
profiles_keine_nas <- na.omit(profiles)

```

Aber was ist, wenn wir nur bei bestimmten Spalten wegen fehlender Werte besorgt sind? Sagen wir bei `income` und bei `sex`:


```r
filter(profiles, !is.na(income) | !is.na(sex))
```

### Spalten wählen mit `select`

Das Gegenstück zu `filter` ist `select`\index{dplyr::select}; dieser Befehl liefert die gewählten Spalten zurück. Das ist häufig praktisch, wenn der Datensatz sehr "breit" ist, also viele Spalten enthält. Dann kann es übersichtlicher sein, sich nur die relevanten auszuwählen. Das Sinnbild für diesen Befehl:

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/select.pdf" alt="Spalten auswählen" width="70%" />
<p class="caption">(\#fig:fig-select)Spalten auswählen</p>
</div>


Merke:

>    Die Funktion select wählt Spalten aus einem Dataframe aus.

Laden wir als ersten einen Datensatz.


```r
stats_test <- read.csv("data/test_inf_short.csv")
```

Dieser Datensatz beinhaltet Daten zu einer Statistikklausur.

Beachten Sie, dass diese Syntax davon ausgeht, dass sich die Daten in einem Unterordner mit dem Namen `data` befinden, welcher sich im Arbeitsverzeichnis befindet^[der angegebene Pfad ist also *relativ*  zum aktuellen Verzeichnis.].




<!-- Hier haben wir erst geprüft, ob die Datei `test_inf_short.csv` existiert; falls nein, laden wir sie herunter. Andernfalls lesen wir sie aus dem lokalen Verzeichnis. -->


```r
select(stats_test, score)  # Spalte `score` auswählen
select(stats_test, score, study_time)  # Splaten `score` und `study_time` auswählen
select(stats_test, score:study_time) # dito
select(stats_test, 5:6) Spalten 5 bis 6 auswählen
```

Tatsächlich ist der Befehl `select` sehr flexibel; es gibt viele Möglichkeiten, Spalten auszuwählen. Im `dplyr`-Cheatsheet findet sich ein guter Überblick dazu.


#### Aufgaben^[F, F, R, R, F]

\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. `select` wählt *Zeilen* aus.
1. `select` ist eine Funktion aus dem Paket `knitr`.
1. Möchte man zwei Spalten auswählen, so ist folgende Syntax prinzipiell korrekt: `select(df, spalte1, spalte2)`.
1. Möchte man Spalten 1 bis 10 auswählen, so ist folgende Syntax prinzipiell korrekt: `select(df, spalte1:spalte10)
1. Mit `select` können Spalten nur bei ihrem Namen, aber nicht bei ihrer Nummer aufgerufen werden.

</div>\EndKnitrBlock{rmdexercises}


### Zeilen sortieren mit `arrange`

Man kann zwei Arten des Umgangs mit R unterscheiden: Zum einen der "interaktive Gebrauch" und zum anderen "richtiges Programmieren". Im interaktiven Gebrauch geht es uns darum, die Fragen zum aktuell vorliegenden Datensatz (schnell) zu beantworten. Es geht nicht darum, eine allgemeine Lösung zu entwickeln, die wir in die Welt verschicken können und die dort ein bestimmtes Problem löst, ohne dass der Entwickler (wir) dabei Hilfestellung geben muss. "Richtige" Software, wie ein R-Paket oder Microsoft Powerpoint, muss diese Erwartung erfüllen; "richtiges Programmieren" ist dazu vonnöten. Natürlich sind in diesem Fall die Ansprüche an die Syntax (der "Code", hört sich cooler an) viel höher. In dem Fall muss man alle Eventualitäten voraussehen und sicherstellen, dass das Programm auch beim merkwürdigsten Nutzer brav seinen Dienst tut. Wir haben hier, beim interaktiven Gebrauch, niedrigere Ansprüche bzw. andere Ziele. 

Beim interaktiven Gebrauch von R (oder beliebigen Analyseprogrammen) ist das Sortieren von Zeilen eine recht häufige Tätigkeit. Typisches Beispiel wäre der Lehrer, der eine Tabelle mit Noten hat und wissen will, welche Schüler die schlechtesten oder die besten sind in einem bestimmten Fach. Oder bei der Prüfung der Umsätze nach Filialen möchten wir die umsatzstärksten sowie -schwächsten Niederlassungen kennen. 

Ein R-Befehl hierzu ist `arrange`\index{dplyr::arrange}; einige Beispiele zeigen die Funktionsweise am besten:


```r

arrange(stats_test, score) # liefert die *schlechtesten* Noten zuerst zurück
arrange(stats_test, -score) # liefert die *besten* Noten zuerst zurück
arrange(stats_test, interest, score)
```



```
#>     X                 V_1 study_time self_eval interest score
#> 1 234 23.01.2017 18:13:15          3         1        1    17
#> 2   4 06.01.2017 09:58:05          2         3        2    18
#> 3 131 19.01.2017 18:03:45          2         3        4    18
#> 4 142 19.01.2017 19:02:12          3         4        1    18
#> 5  35 12.01.2017 19:04:43          1         2        3    19
#> 6  71 15.01.2017 15:03:29          3         3        3    20
#>    X                 V_1 study_time self_eval interest score
#> 1  3 05.01.2017 23:33:47          5        10        6    40
#> 2  7 06.01.2017 14:25:49         NA        NA       NA    40
#> 3 29 12.01.2017 09:48:16          4        10        3    40
#> 4 41 13.01.2017 12:07:29          4        10        3    40
#> 5 58 14.01.2017 15:43:01          3         8        2    40
#> 6 83 16.01.2017 10:16:52         NA        NA       NA    40
#>     X                 V_1 study_time self_eval interest score
#> 1 234 23.01.2017 18:13:15          3         1        1    17
#> 2 142 19.01.2017 19:02:12          3         4        1    18
#> 3 221 23.01.2017 11:40:30          1         1        1    23
#> 4 230 23.01.2017 16:27:49          1         1        1    23
#> 5  92 17.01.2017 17:18:55          1         1        1    24
#> 6 107 18.01.2017 16:01:36          3         2        1    24
```

Einige Anmerkungen. Die generelle Syntax lautet `arrange(df, Spalte1, ...)`, wobei `df` den Dataframe bezeichnet und `Spalte1` die erste zu sortierende Spalte; die Punkte `...` geben an, dass man weitere Parameter übergeben kann. Man kann sowohl numerische Spalten als auch Textspalten sortieren. Am wichtigsten ist hier, dass man weitere Spalten übergeben kann. Dazu gleich mehr.

Standardmäßig sortiert `arrange` *aufsteigend*  (weil kleine Zahlen im Zahlenstrahl vor den großen Zahlen kommen). Möchte man diese Reihenfolge umdrehen (große Werte zuert, d.h. *absteigend*), so kann man ein Minuszeichen vor den Namen der Spalte setzen.

Gibt man *zwei oder mehr* Spalten an, so werden pro Wert von `Spalte1` die Werte von `Spalte2` sortiert etc; man betrachte den Output des Beispiels oben dazu.

<!-- Aber was heißt dieses komisch Symbol:  `%>%`? Diese sogenannte "Pfeife" lässt sich mit "und dann" ins Deutsce übersetzen. Also: -->

<!-- ``` -->
<!-- sortiere(diese_Tabelle, nach_dieser_Spalte) UND DANN zeig_die_ersten_Zeilen -->
<!-- ``` -->

<!-- Der Befehl `head` zeigt dier ersten paar Zeilen eines Dataframes [^5]. -->


Merke:

>    Die Funktion arrange sortiert die Zeilen eines Datafames.

Ein Sinnbild zur Verdeutlichung:

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/arrange.pdf" alt="Spalten sortieren" width="70%" />
<p class="caption">(\#fig:fig-arrange)Spalten sortieren</p>
</div>



Ein ähnliches Ergebnis erhält mit man `top_n()`, welches die `n` *größten Ränge* widergibt:


```r

top_n(stats_test, 3)
#>      X                 V_1 study_time self_eval interest score
#> 1    3 05.01.2017 23:33:47          5        10        6    40
#> 2    7 06.01.2017 14:25:49         NA        NA       NA    40
#> 3   29 12.01.2017 09:48:16          4        10        3    40
#> 4   41 13.01.2017 12:07:29          4        10        3    40
#> 5   58 14.01.2017 15:43:01          3         8        2    40
#> 6   83 16.01.2017 10:16:52         NA        NA       NA    40
#> 7  116 18.01.2017 23:07:32          4         8        5    40
#> 8  119 19.01.2017 09:05:01         NA        NA       NA    40
#> 9  132 19.01.2017 18:22:32         NA        NA       NA    40
#> 10 175 20.01.2017 23:03:36          5        10        5    40
#> 11 179 21.01.2017 07:40:05          5         9        1    40
#> 12 185 21.01.2017 15:01:26          4        10        5    40
#> 13 196 22.01.2017 13:38:56          4        10        5    40
#> 14 197 22.01.2017 14:55:17          4        10        5    40
#> 15 248 24.01.2017 16:29:45          2        10        2    40
#> 16 249 24.01.2017 17:19:54         NA        NA       NA    40
#> 17 257 25.01.2017 10:44:34          2         9        3    40
#> 18 306 27.01.2017 11:29:48          4         9        3    40
top_n(stats_test, 3, interest)
#>     X                 V_1 study_time self_eval interest score
#> 1   3 05.01.2017 23:33:47          5        10        6    40
#> 2   5 06.01.2017 14:13:08          4         8        6    34
#> 3  43 13.01.2017 14:14:16          4         8        6    36
#> 4  65 15.01.2017 12:41:27          3         6        6    22
#> 5 110 18.01.2017 18:53:02          5         8        6    37
#> 6 136 19.01.2017 18:22:57          3         1        6    39
#> 7 172 20.01.2017 20:42:46          5        10        6    34
#> 8 214 22.01.2017 21:57:36          2         6        6    31
#> 9 301 27.01.2017 08:17:59          4         8        6    33
```

Gibt man *keine* Spalte an, so bezieht sich `top_n` auf die letzte Spalte im Datensatz.

Da sich hier mehrere Personen den größten Rang (Wert 40) teilen, bekommen wir *nicht* 3 Zeilen zurückgeliefert, sondern entsprechend mehr.

#### Aufgaben^[F, F, F, F, R]

\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. `arrange` arrangiert Spalten.
1. `arrange` sortiert im Standard absteigend.
1. `arrange` lässt nur ein Sortierkriterium zu.
1. `arrange` kann numerische Werte, aber nicht Zeichenketten sortieren.
1. `top_n(5)` liefert die fünf kleinsten Ränge.</div>\EndKnitrBlock{rmdexercises}

### Datensatz gruppieren mit `group_by`

Einen Datensatz zu gruppieren ist ebenfalls eine häufige Angelegenheit: Was ist der mittlere Umsatz in Region X im Vergleich zu Region Y? Ist die Reaktionszeit in der Experimentalgruppe kleiner als in der Kontrollgruppe? Können Männer schneller ausparken als Frauen? Man sieht, dass das Gruppieren v.a. in Verbindung mit Mittelwerten oder anderen Zusammenfassungen sinnvol ist; dazu im nächsten Abschnitt mehr.

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/group_by.pdf" alt="Datensätze nach Subgruppen aufteilen" width="70%" />
<p class="caption">(\#fig:fig-groupby)Datensätze nach Subgruppen aufteilen</p>
</div>

In der Abbildung wurde der Datensatz anhand der Spalte `Fach` in mehrere Gruppen geteilt. Wir könnten uns als nächstes z.B. Mittelwerte pro Fach - d.h. pro Gruppe (pro Ausprägung von `Fach`) - ausgeben lassen; in diesem Fall vier Gruppen (Fach A bis D).


```r
test_gruppiert <- group_by(stats_test, interest)
test_gruppiert
#> Source: local data frame [306 x 6]
#> Groups: interest [7]
#> 
#>        X                 V_1 study_time self_eval interest score
#>    <int>              <fctr>      <int>     <int>    <int> <int>
#> 1      1 05.01.2017 13:57:01          5         8        5    29
#> 2      2 05.01.2017 21:07:56          3         7        3    29
#> 3      3 05.01.2017 23:33:47          5        10        6    40
#> 4      4 06.01.2017 09:58:05          2         3        2    18
#> 5      5 06.01.2017 14:13:08          4         8        6    34
#> 6      6 06.01.2017 14:21:18         NA        NA       NA    39
#> 7      7 06.01.2017 14:25:49         NA        NA       NA    40
#> 8      8 06.01.2017 17:24:53          2         5        3    24
#> 9      9 07.01.2017 10:11:17          2         3        5    25
#> 10    10 07.01.2017 18:10:05          4         5        5    33
#> # ... with 296 more rows
```

Schaut man sich nun den Datensatz an, sieht man erstmal wenig Effekt der Gruppierung. R teilt uns lediglich mit `Groups: interest [7]`, dass es die Gruppen gibt, aber es gibt keine extra Spalte oder sonstige Anzeichen der Gruppierung. Aber keine Sorge, wenn wir gleich einen Mittelwert ausrechnen, bekommen wir den Mittelwert pro Gruppe!

Ein paar Hinweise: `Source: local data frame [306 x 6]` will sagen, dass die Ausgabe sich auf einen `tibble` bezieht^[http://stackoverflow.com/questions/29084380/what-is-the-meaning-of-the-local-data-frame-message-from-dplyrprint-tbl-df], also eine bestimmte Art von Dataframe. `Groups: interest [7]` zeigt, dass der Tibble in 7 Gruppen - entsprechend der Werte von `interest` aufgeteilt ist.

`group_by` an sich ist nicht wirklich nützlich. Nützlich wird es erst, wenn man weitere Funktionen auf den gruppierten Datensatz anwendet - z.B. Mittelwerte ausrechnet (z.B mit `summarise`, s. unten). Die nachfolgenden Funktionen (wenn sie aus `dplyr` kommen), berücksichtigen nämlich die Gruppierung. So kann man einfach Mittelwerte pro Gruppe ausrechnen.


#### Aufgaben^[R, F, R, R]

\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. Mit `group_by` gruppiert man einen Datensatz.
1. `group_by` lässt nur ein Gruppierungskriterium zu.
1. Die Gruppierung durch `group_by` wird nur von Funktionen aus `dplyr` erkannt.
1. `group_by` ist sinnvoll mit `summarise` zu kombinieren.

</div>\EndKnitrBlock{rmdexercises}


Merke:

>    Mit group_by teilt man einen Datensatz in Gruppen ein, entsprechend der Werte einer mehrerer Spalten.



### Eine Spalte zusammenfassen mit `summarise`

Vielleicht die wichtigste oder häufigte Tätigkeit in der Analyse von Daten ist es, eine Spalte zu *einem* Wert zusammenzufassen; `summarise`\index{dplyr::summarise} leistet dies. Anders gesagt: Einen Mittelwert berechnen, den größten (kleinsten) Wert heraussuchen, die Korrelation berechnen oder eine beliebige andere Statistik ausgeben lassen. Die Gemeinsamkeit dieser Operaitonen ist, dass sie eine Spalte zu einem Wert zusammenfassen, "aus Spalte mach Zahl", sozusagen. Daher ist der Name des Befehls `summarise` ganz passend. Genauer gesagt fasst dieser Befehl eine Spalte zu einer Zahl zusammen *anhand* einer Funktion wie `mean` oder `max`. Hierbei ist jede Funktion erlaubt, die eine Spalte als Input verlangt und eine Zahl zurückgibt; andere Funktionen sind bei `summarise` nicht erlaubt. 

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/summarise.pdf" alt="Spalten zu einer Zahl zusammenfassen" width="70%" />
<p class="caption">(\#fig:fig-summarise)Spalten zu einer Zahl zusammenfassen</p>
</div>



```r
summarise(stats_test, mean(score))
#>   mean(score)
#> 1        31.1
```

Man könnte diesen Befehl so ins Deutsche übersetzen: `Fasse aus Tabelle stats_test die Spalte score anhand des Mittelwerts zusammen`. Nicht vergessen, wenn die Spalte `score` fehlende Werte hat, wird der Befehl `mean` standardmäßig dies mit `NA` quittieren. Ergänzt man den Parameter `nr.rm = TRUE`, so ignoriert R fehlende Werte und der Befehl `mean` liefert ein Ergebnis zurück.

Jetzt können wir auch die Gruppierung nutzen:

```r
test_gruppiert <- group_by(stats_test, interest)
summarise(test_gruppiert, mean(score, na.rm = TRUE))
#> # A tibble: 7 × 2
#>   interest `mean(score, na.rm = TRUE)`
#>      <int>                       <dbl>
#> 1        1                        28.3
#> 2        2                        29.7
#> 3        3                        30.8
#> 4        4                        29.9
#> 5        5                        32.5
#> 6        6                        34.0
#> 7       NA                        33.1
```

Der Befehl `summarise` erkennt also, wenn eine (mit `group_by`) gruppierte Tabelle vorliegt. Jegliche Zusammenfassung, die wir anfordern, wird anhand der Gruppierungsinformation aufgeteilt werden. In dem Beispiel bekommen wir einen Mittelwert für jeden Wert von `interest`. Interessanterweise sehen wir, dass der Mittelwert tendenziell größer wird, je größer `interest` wird.

Alle diese `dplyr`-Befehle geben einen Dataframe zurück, was praktisch ist für weitere Verarbeitung. In diesem Fall heißen die Spalten `interst` und `mean(score)`. Zweiter Name ist nicht so schön, daher ändern wir den wie folgt:

Jetzt können wir auch die Gruppierung nutzen:

```r
test_gruppiert <- group_by(stats_test, interest)
summarise(test_gruppiert, mw_pro_gruppe = mean(score, na.rm = TRUE))
#> # A tibble: 7 × 2
#>   interest mw_pro_gruppe
#>      <int>         <dbl>
#> 1        1          28.3
#> 2        2          29.7
#> 3        3          30.8
#> 4        4          29.9
#> 5        5          32.5
#> 6        6          34.0
#> 7       NA          33.1
```

Nun heißt die zweite Spalte `mw_pro_Gruppe`. `na.rm = TRUE` veranlasst, bei fehlenden Werten trotzdem einen Mittelwert zurückzuliefern (die Zeilen mit fehlenden Werten werden in dem Fall ignoriert).

Grundsätzlich ist die Philosophie der `dplyr`-Befehle: "Mach nur eine Sache, aber die dafür gut". Entsprechend kann `summarise` nur *Spalten* zusammenfassen, aber keine *Zeilen*.

Merke:

>    Mit summarise kann man eine Spalte eines Dataframes zu einem Wert zusammenfassen.


#### Deskriptive Statistik mit `summarise`


>    Die deskriptive Statistik hat zwei Haupt-Bereiche: Lagemaße und Streuungsmaße.

*Lagemaße* geben den "typischen", "mittleren" oder "repräsentativen" Vertreter der Verteilung an. Bei den Lagemaßen\index{Lagemaße} denkt man sofort an das *arithmetische Mittel* (synonym: Mittelwert; häufig als $\bar{X}$ abgekürzt; `mean`). Ein Nachteil von Mittelwerten ist, dass sie nicht robust gegenüber Extremwerte sind: Schon ein vergleichsweise großer Einzelwert kann den Mittelwert deutlich verändern und damit die Repräsentativität des Mittelwerts für die Gesamtmenge der Daten in Frage stellen. Eine robuste Variante ist der *Median* (Md; `median`). Ist die Anzahl der (unterschiedlichen) Ausprägungen nicht zu groß im Verhältnis zur Fallzahl, so ist der *Modus* eine sinnvolle Statistik; er gibt die häufigste Ausprägung an^[Der *Modus* ist im Standard-R nicht mit einem eigenen Befehl vertreten. Man kann ihn aber leicht von Hand bestimmen; s.u. Es gibt auch einige Pakete, die diese Funktion anbieten: z.B. https://cran.r-project.org/web/packages/modes/index.html].

*Streuungsmaße*\index{Streuungsmaße} geben die Unterschiedlichkeit in den Daten wieder; mit anderen Worten: sind die Daten sich ähnlich oder unterscheiden sich die Werte deutlich? Zentrale Statistiken sind der *mittlere Absolutabstand* (MAA; MAD) ^[Der *MAD* ist im Standard-R nicht mit einem eigenen Befehl vertreten. Es gibt einige Pakete, die diese Funktion anbieten: z.B. https://artax.karlin.mff.cuni.cz/r-help/library/lsr/html/aad.html], die *Standardabweichung* (sd; `sd`), die *Varianz* (Var; `var`) und der *Interquartilsabstand* (IQR; `IQR`). Da nur der IQR *nicht* auf dem Mittelwert basiert, ist er am robustesten. Beliebige Quantile bekommt man mit dem R-Befehl `quantile`.

Der Befehl `summarise` eignet sich, um deskriptive Statistiken auszurechnen.


```r
summarise(stats_test, mean(score))
#>   mean(score)
#> 1        31.1
summarise(stats_test, sd(score))
#>   sd(score)
#> 1      5.74
```

Natürlich könnte man auch einfacher schreiben:


```r
mean(stats_test$score)
#> [1] 31.1
median(stats_test$score)
#> [1] 31
```


`summarise` liefert aber im Unterschied zu `mean` etc. immer einen Dataframe zurück. Da der Dataframe die typische Datenstruktur ist, ist es häufig praktisch, wenn man einen Dataframe zurückbekommt, mit dem man weiterarbeiten kann. Außerdem lassen `mean` etc. keine Gruppierungsoperationen zu; über `group_by` kann man dies aber bei `dplyr` erreichen.




#### Aufgaben^[R, R, R, R, R]



\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. Möchte man aus der Tabelle `stats_test` den Mittelwert für die Spalte `score` berechnen, so ist folgende Syntax korrekt: `summarise(stats_test, mean(score))`.
1. `summarise` liefert eine Tabelle, genauer: einen Tibble, zurück.
1. Die Tabelle, die diese Funktion zurückliefert: `summarise(stats_test, mean(score))`, hat eine Spalte mit dem Namen `mean(score)`.
1. `summarise` lässt zu, dass die zu berechnende Spalte einen Namen vom Nutzer zugewiesen bekommt.
1. `summarise` darf nur verwendet werden, wenn eine Spalte zu einem Wert zusammengefasst werden soll.




1. (Fortgeschritten) Bauen Sie einen eigenen Weg, um den mittleren Absolutabstand auszurechnen! Gehen Sie der Einfachheit halber (zuerst) von einem Vektor mit den Werten (1,2,3) aus!


Lösung:
</div>\EndKnitrBlock{rmdexercises}

```r
x <- c(1, 2, 3)
x_mw <- mean(x)
x_delta <- x - x_mw
x_delta <- abs(x_delta)
mad <- mean(x_delta)
mad
#> [1] 0.667
```

```

### Zeilen zählen mit `n` und `count`
Ebenfalls nützlich ist es, Zeilen zu zählen. Im Gegensatz zum Standardbefehl^[Standardbefehl meint, dass die Funktion zum Standardrepertoire von R gehört, also nicht über ein Paket extra geladen werden muss] `nrow` versteht der `dyplr`-Befehl `n`\index{dplyr::n} auch Gruppierungen. `n` darf nur innerhalb von `summarise` oder ähnlichen `dplyr`-Befehlen verwendet werden.


```r
summarise(stats_test, n())
#>   n()
#> 1 306
summarise(test_gruppiert, n())
#> # A tibble: 7 × 2
#>   interest `n()`
#>      <int> <int>
#> 1        1    30
#> 2        2    47
#> 3        3    66
#> 4        4    41
#> 5        5    45
#> 6        6     9
#> 7       NA    68
nrow(stats_test)
#> [1] 306
```

Außerhalb von gruppierten Datensätzen ist `nrow` meist praktischer.


Praktischer ist der Befehl `count`\index{dplyr::count}, der nichts anderes ist als die Hintereinanderschaltung von `group_by` und `n`. Mit `count` zählen wir die Häufigkeiten nach Gruppen; Gruppen sind hier zumeist die Werte einer auszuzählenden Variablen (oder mehrerer auszuzählender Variablen). Das macht `count` zu einem wichtigen Helfer bei der Analyse von Häufigkeitsdaten.


```r
dplyr::count(stats_test, interest)
#> # A tibble: 7 × 2
#>   interest     n
#>      <int> <int>
#> 1        1    30
#> 2        2    47
#> 3        3    66
#> 4        4    41
#> 5        5    45
#> 6        6     9
#> 7       NA    68
dplyr::count(stats_test, study_time)
#> # A tibble: 6 × 2
#>   study_time     n
#>        <int> <int>
#> 1          1    31
#> 2          2    49
#> 3          3    85
#> 4          4    56
#> 5          5    17
#> 6         NA    68
dplyr::count(stats_test, interest, study_time)
#> Source: local data frame [29 x 3]
#> Groups: interest [?]
#> 
#>    interest study_time     n
#>       <int>      <int> <int>
#> 1         1          1    12
#> 2         1          2     7
#> 3         1          3     8
#> 4         1          4     2
#> 5         1          5     1
#> 6         2          1     9
#> 7         2          2    15
#> 8         2          3    16
#> 9         2          4     6
#> 10        2          5     1
#> # ... with 19 more rows
```

Allgemeiner formuliert lautet die Syntax: `count(df, Spalte1, ...)`, wobei `df` der Dataframe ist und `Spalte1` die erste (es können mehrere sein) auszuzählende Spalte. Gibt man z.B. zwei Spalten an, so wird pro Wert der 1. Spalte die Häufigkeiten der 2. Spalte ausgegeben.

Merke:

>    n und count zählen die Anzahl der Zeilen, d.h. die Anzahl der Fälle. 



#### Aufgaben^[R, R, F, F]



\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. Mit `count` kann man Zeilen zählen.
1. `count` ist ähnlich (oder identisch) zu einer Kombination von `group_by` und `n()`. 
1. Mit `count` kann man nur nur eine Gruppe beim Zählen berücksichtigen.
1. `count` darf nicht bei nominalskalierten Variablen verwendet werden.
</div>\EndKnitrBlock{rmdexercises}


1. Bauen Sie sich einen Weg, um den Modus mithilfe von `count` und `arrange` zu bekommen!


```r
stats_count <- count(stats_test, score)
stats_count_sortiert <- arrange(stats_count, -n)
head(stats_count_sortiert,1)
#> # A tibble: 1 × 2
#>   score     n
#>   <int> <int>
#> 1    34    22
```

Ah! Der Score `34` ist der häufigste!



## Die Pfeife
Die zweite Idee kann man salopp als "Durchpfeifen"\index{Pfeife} oder die "Idee der Pfeife\index{Pfeife} bezeichnen; ikonographisch mit einem Pfeifen ähnlichen Symbol dargestellt ` %>% `. Der Begriff "Durchpfeifen" ist frei vom Englischen "to pipe" übernommen. Das berühmte Bild von René Magritte stand dabei Pate.

<div class="figure" style="text-align: center">
<img src="images/Datenjudo/ma-150089-WEB.jpg" alt="La trahison des images [Ceci n'est pas une pipe], René Magritte, 1929, © C. Herscovici, Brussels / Artists Rights Society (ARS), New York, http://collections.lacma.org/node/239578" width="70%" />
<p class="caption">(\#fig:cecie-une-pipe)La trahison des images [Ceci n'est pas une pipe], René Magritte, 1929, © C. Herscovici, Brussels / Artists Rights Society (ARS), New York, http://collections.lacma.org/node/239578</p>
</div>


 Hierbei ist gemeint, einen Datensatz sozusagen auf ein Fließband zu legen und an jedem Arbeitsplatz einen Arbeitsschritt auszuführen. Der springende Punkt ist, dass ein Dataframe als "Rohstoff" eingegeben wird und jeder Arbeitsschritt seinerseits wieder einen Datafram ausgiebt. Damit kann man sehr schön, einen "Flow" an Verarbeitung erreichen, außerdem spart man sich Tipparbeit und die Syntax wird lesbarer. Damit das Durchpfeifen funktioniert, benötigt man Befehle, die als Eingabe einen Dataframe erwarten und wieder einen Dataframe zurückliefern. Das Schaubild verdeutlich beispielhaft eine Abfolge des Durchpfeifens.


<div class="figure" style="text-align: center">
<img src="images/Datenjudo/durchpfeifen.pdf" alt="Das 'Durchpeifen'" width="80%" />
<p class="caption">(\#fig:fig-durchpreifen)Das 'Durchpeifen'</p>
</div>

Die sog. "Pfeife" (pipe\index{Pfeife}: ` %>% `) in Anspielung an das berühmte Bild von René Magritte, verkettet Befehle hintereinander. Das ist praktisch, da es die Syntax vereinfacht. Vergleichen Sie mal diese Syntax


```r
filter(summarise(group_by(filter(stats_test, !is.na(score)), interest), mw = mean(score)), mw > 30)
```

mit dieser


```r
stats_test %>% 
  filter(!is.na(score)) %>% 
  group_by(interest) %>% 
  summarise(mw = mean(score)) %>% 
  filter(mw > 30)
#> # A tibble: 4 × 2
#>   interest    mw
#>      <int> <dbl>
#> 1        3  30.8
#> 2        5  32.5
#> 3        6  34.0
#> 4       NA  33.1
```

Es ist hilfreich, diese "Pfeifen-Syntax" in deutschen Pseudo-Code zu übersetzen.



\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Nimm die Tabelle "stats_test" UND DANN  
filtere alle nicht-fehlenden Werte UND DANN  
gruppiere die verbleibenden Werte nach "interest" UND DANN  
bilde den Mittelwert (pro Gruppe) für "score" UND DANN  
liefere nur die Werte größer als 30 zurück.  
</div>\EndKnitrBlock{rmdpseudocode}


Die zweite Syntax, in "Pfeifenform" ist viel einfacher zu verstehen als die erste! Die erste Syntax ist verschachelt, man muss sie von innen nach außen lesen. Das ist kompliziert. Die Pfeife in der 2. Syntax macht es viel einfacher, die Snytax zu verstehen, da die Befehle "hintereinander" gestellt (sequenziell organisiert) sind.



Die Pfeife zerlegt die "russische Puppe", also ineinander verschachelteten Code, in sequenzielle Schritte und zwar in der richtigen Reihenfolge (entsprechend der Abarbeitung). Wir müssen den Code nicht mehr von innen nach außen lesen (wie das bei einer mathematischen Formel der Fall ist), sondern können wie bei einem Kochrezept "erstens ..., zweitens .., drittens ..." lesen. Die Pfeife macht die Syntax einfacher. Natürlich hätten wir die verschachtelte Syntax in viele einzelne Befehle zerlegen können und jeweils eine Zwischenergebnis speichern mit dem Zuweisungspfeil `<-` und das Zwischenergebnis dann explizit an den nächsten Befehl weitergeben. Eigentlich macht die Pfeife genau das - nur mit weniger Tipparbeit. Und auch einfacher zu lesen. Flow!


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

Wenn Sie Befehle verketten mit der Pfeife, sind nur Befehle erlaubt, die einen Datensatz als Eingabe verlangen und einen Datensatz ausgeben. Das ist bei den hier vorgestellten Funktionen der Fall. Viele andere Funktionen erfüllen dieses Kriterium aber nicht; in dem Fall liefert `dplyr` eine Fehlermeldung.
</div>\EndKnitrBlock{rmdcaution}


### Spalten berechnen mit `mutate`

Wenn man die Pfeife benutzt, ist der Befehl `mutate`\index{dplyr::mutate} ganz praktisch: Er berechnet eine Spalte. Normalerweise kann man einfach eine Spalte berechnen mit dem Zuweisungsoperator:

Zum Beispiel so:

```
df$neue_spalte <- df$spalte1 + df$spalte2
```

Innerhalb einer Pfeifen-Syntax geht das aber nicht (so gut). Da ist man mit der Funtion `mutate` besser beraten; `mutate` leistest just dasselbe wie die Pseudo-Syntax oben:

```
df %>% 
  mutate(neue_spalte = spalte1 + spalte2)
```

In Worten:


\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Nimm die Tabelle "df" UND DANN  
bilde eine neue Spalte mit dem Namen `neue_spalte`,
die sich berechnet als Summe von `spalte1` und `spalte2`.  
</div>\EndKnitrBlock{rmdpseudocode}


Ein konkretes Beispiel:


```r
stats_test %>% 
  mutate(bestanden = score > 25) %>% 
  head()
#>   X                 V_1 study_time self_eval interest score bestanden
#> 1 1 05.01.2017 13:57:01          5         8        5    29      TRUE
#> 2 2 05.01.2017 21:07:56          3         7        3    29      TRUE
#> 3 3 05.01.2017 23:33:47          5        10        6    40      TRUE
#> 4 4 06.01.2017 09:58:05          2         3        2    18     FALSE
#> 5 5 06.01.2017 14:13:08          4         8        6    34      TRUE
#> 6 6 06.01.2017 14:21:18         NA        NA       NA    39      TRUE
```

Diese Syntax erzeugt eine neue Spalte innerhalb von `stats_test`; diese Spalte prüft pro Persion, ob `score` > 25 ist. Falls ja (TRUE), dann ist `bestanden` TRUE, ansonsten ist `bestanden` FALSE (Pech). `head` zeigt die ersten 6 Zeilen des resultierenden Dataframes an.


Ein Sinnbild für `mutate`:

<img src="images/mutate.png" width="70%" style="display: block; margin: auto;" />



### Aufgaben

1. Entschlüsseln Sie dieses Ungetüm! Übersetzen Sie diese Syntax auf Deutsch:


```r

library(nycflights13)
data(flights)

verspaetung <-
  filter(
    summarise(
    group_by(filter(flights, !is.na(dep_delay), month)), delay = mean(dep_delay), n = n()), n > 10)
 
```


2. Entschlüsseln Sie jetzt diese Syntax bzw. übersetzen Sie sie ins Deutsche:


```r
verspaetung <- flights %>% filter(!is.na(dep_delay)) %>%
group_by(month) %>%
summarise(delay = mean(dep_delay), n = n()) %>% filter(n > 10)
```


3. (schwierig) Die Pfeife bei `arr_delay`

- Übersetzen Sie die folgende Pseudo-Syntax ins ERRRische!

\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Nehme den Datensatz `flights` UND DANN...  
Wähle daraus die Spalte `arr_delay` UND DANN...  
Berechne den Mittelwert der Spalte UND DANN...  
ziehe vom Mittelwert die Spalte ab UND DANN...
quadriere die einzelnen Differenzen UND DANN...
bilde davon den Mittelwert.  
</div>\EndKnitrBlock{rmdpseudocode}

Lösung:


```r
flights %>% 
  select(arr_delay) %>% 
  mutate(arr_delay_delta = arr_delay - mean(flights$arr_delay, na.rm = TRUE)) %>% 
  mutate(arr_delay_delta_quadrat = arr_delay_delta^2) %>% 
  summarise(arr_delay_var = mean(arr_delay_delta_quadrat, na.rm = TRUE)) %>% 
  summarise(sqrt(arr_delay_var))
#> # A tibble: 1 × 1
#>   `sqrt(arr_delay_var)`
#>                   <dbl>
#> 1                  44.6
```


- Berechnen Sie die sd von `arr_delay` in `flights`! Vergleichen Sie sie mit dem Ergebnis der vorherigen Aufgabe!^[`sd(flights$arr_delay, na.rm = TRUE)`]


- Was hat die Pfeifen-Syntax oben berechnet?^[die sd von `arr_delay`]


## Befehlsübersicht


Paket::Funktion     Beschreibung
----------------    -------------
dplyr::arrange      Sortiert Spalten
dplyr::filter       Filtert Zeilen
dplyr::select       Wählt Spalten
dplyr::group_by     gruppiert einen Dataframe
dplyr::n            zählt Zeilen
dplyr::count        zählt Zeilen nach Untergruppen
%>% (dplyr)         verkettet Befehle
dplyr::mutate       erzeugt/berechnet Spalten


## Verweise

- Die offizielle Dokumentation von `dplyr` findet sich hier^[https://cran.r-project.org/web/packages/dplyr/dplyr.pdf]. 

- Eine schöne Demonstration der Mächtigkeit von `dplyr` findet sich hier^[<http://bit.ly/2kX9lvC>].

- Die GUI "exploratory" ist ein "klickbare" Umsetzung von `dplyr`, mächtig, modern und sieht cool aus: https://exploratory.io.

- *R for Data Science* bietet umfangreiche Unterstützung zu diesem Thema [@r4ds].  






<!--chapter:end:040_Datenjudo.Rmd-->





# Fallstudie `nycflights13` 

\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Grundlegende Funktionen von `dplyr` andwenden können.
- Das Konzept der Pfeife in einem echten Datensatz anwenden können.
- Auch mit relativ großen Daten sicher hantieren können.
</div>\EndKnitrBlock{rmdcaution}


Schauen wir uns einige Beispiele der Datenaufbereitung mittels `dplyr` anhand einer Fallstudie an. Wir verwenden hier den Datensatz `flights`aus dem Package `nycflights13`. Der Datensatz ist recht groß (~300.000 Zeilen und 19 Spalten); wenn man ihn als Excel importiert, kann eine alte Möhre von Computer schon in die Knie gehen. Beim Import als CSV habe ich noch nie von Problemen gehört; beim Import via Package ebenfalls nicht. Werfen wir einen ersten Blick in die Daten:

Laden wir zuerst `dplyr` and friends. Das geht mit dem Paket `tidyverse`:


```r
library(tidyverse)
library(nycflights13)  # für die Daten
library(knitr)  # für HTML-Tabellen
```


Dann laden wir die Daten aus dem Paket `nycflights13` und werfen eine Blick hinein ("to glimpse"). `glimpse` zeigt uns einen Überblick über den Dataframe.


```r
data(flights)
glimpse(flights)
#> Observations: 336,776
#> Variables: 19
#> $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013,...
#> $ month          <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,...
#> $ day            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,...
#> $ dep_time       <int> 517, 533, 542, 544, 554, 554, 555, 557, 557, 55...
#> $ sched_dep_time <int> 515, 529, 540, 545, 600, 558, 600, 600, 600, 60...
#> $ dep_delay      <dbl> 2, 4, 2, -1, -6, -4, -5, -3, -3, -2, -2, -2, -2...
#> $ arr_time       <int> 830, 850, 923, 1004, 812, 740, 913, 709, 838, 7...
#> $ sched_arr_time <int> 819, 830, 850, 1022, 837, 728, 854, 723, 846, 7...
#> $ arr_delay      <dbl> 11, 20, 33, -18, -25, 12, 19, -14, -8, 8, -2, -...
#> $ carrier        <chr> "UA", "UA", "AA", "B6", "DL", "UA", "B6", "EV",...
#> $ flight         <int> 1545, 1714, 1141, 725, 461, 1696, 507, 5708, 79...
#> $ tailnum        <chr> "N14228", "N24211", "N619AA", "N804JB", "N668DN...
#> $ origin         <chr> "EWR", "LGA", "JFK", "JFK", "LGA", "EWR", "EWR"...
#> $ dest           <chr> "IAH", "IAH", "MIA", "BQN", "ATL", "ORD", "FLL"...
#> $ air_time       <dbl> 227, 227, 160, 183, 116, 150, 158, 53, 140, 138...
#> $ distance       <dbl> 1400, 1416, 1089, 1576, 762, 719, 1065, 229, 94...
#> $ hour           <dbl> 5, 5, 5, 5, 6, 5, 6, 6, 6, 6, 6, 6, 6, 6, 6, 5,...
#> $ minute         <dbl> 15, 29, 40, 45, 0, 58, 0, 0, 0, 0, 0, 0, 0, 0, ...
#> $ time_hour      <dttm> 2013-01-01 05:00:00, 2013-01-01 05:00:00, 2013...
```

Der Befehl `data` lädt Daten aus einem zuvor gestarteten Paket. 

Achtung, Fallstudie. Sie sind der/die Assistent_in des Chefs der New Yorker Flughäfen. Ihr Chef kommt gut gelaunt ins Büro und sagt, dass er diesen Schnarchnasen einheizen wolle und sagt, sie sollen ihm mal schnell die Flüge mit der größten Verspätung raussuchen. Nix schickes, aber zacki-zacki...


```r
flights %>% 
  arrange(arr_delay)
#> # A tibble: 336,776 × 19
#>     year month   day dep_time sched_dep_time dep_delay arr_time
#>    <int> <int> <int>    <int>          <int>     <dbl>    <int>
#> 1   2013     5     7     1715           1729       -14     1944
#> 2   2013     5    20      719            735       -16      951
#> 3   2013     5     2     1947           1949        -2     2209
#> 4   2013     5     6     1826           1830        -4     2045
#> 5   2013     5     4     1816           1820        -4     2017
#> 6   2013     5     2     1926           1929        -3     2157
#> 7   2013     5     6     1753           1755        -2     2004
#> 8   2013     5     7     2054           2055        -1     2317
#> 9   2013     5    13      657            700        -3      908
#> 10  2013     1     4     1026           1030        -4     1305
#> # ... with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
#> #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
#> #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
#> #   minute <dbl>, time_hour <dttm>
```

Hm, übersichtlicher wäre es wahrscheinllich, wenn wir weniger Spalten anschauen müssten. Am besten neben der Verspätung nur die Information, die wir zur Identifizierung der Schuldigen... will sagen der gesuchten Flüge benötigen


```r
flights %>% 
  arrange(arr_delay) %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest)
#> # A tibble: 336,776 × 8
#>    arr_delay carrier month   day dep_time tailnum flight  dest
#>        <dbl>   <chr> <int> <int>    <int>   <chr>  <int> <chr>
#> 1        -86      VX     5     7     1715  N843VA    193   SFO
#> 2        -79      VX     5    20      719  N840VA     11   SFO
#> 3        -75      UA     5     2     1947  N851UA    612   LAX
#> 4        -75      AA     5     6     1826  N3KCAA    269   SEA
#> 5        -74      AS     5     4     1816  N551AS      7   SEA
#> 6        -73      UA     5     2     1926  N24212   1628   SFO
#> 7        -71      DL     5     6     1753  N3760C   1394   PDX
#> 8        -71      UA     5     7     2054  N806UA    622   SFO
#> 9        -71      B6     5    13      657  N805JB    671   LAX
#> 10       -70      VX     1     4     1026  N855VA     23   SFO
#> # ... with 336,766 more rows
```

Da Zahlen in ihrer natürlichen Form von klein nach groß sortiert sind, sortiert `arrange` in ebendieser Richtung. Wir können das umdrehen mit einem Minuszeichen vor der zu sortierenden Spalte:


```r
flights %>% 
  arrange(-arr_delay) %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest)
#> # A tibble: 336,776 × 8
#>    arr_delay carrier month   day dep_time tailnum flight  dest
#>        <dbl>   <chr> <int> <int>    <int>   <chr>  <int> <chr>
#> 1       1272      HA     1     9      641  N384HA     51   HNL
#> 2       1127      MQ     6    15     1432  N504MQ   3535   CMH
#> 3       1109      MQ     1    10     1121  N517MQ   3695   ORD
#> 4       1007      AA     9    20     1139  N338AA    177   SFO
#> 5        989      MQ     7    22      845  N665MQ   3075   CVG
#> 6        931      DL     4    10     1100  N959DL   2391   TPA
#> 7        915      DL     3    17     2321  N927DA   2119   MSP
#> 8        895      DL     7    22     2257  N6716C   2047   ATL
#> 9        878      AA    12     5      756  N5DMAA    172   MIA
#> 10       875      MQ     5     3     1133  N523MQ   3744   ORD
#> # ... with 336,766 more rows
```

Eine kleine Zugabe: Mit dem Befehl `knitr::kable` kann man einen Dateframe automatisch in eine (einigermaßen) schöne Tabelle ausgeben lassen. Oh halt, wir wollen keine Tabelle mit 300.000 Zeilen (der Chef ist kein Freund von Details). Also begrenzen wir die Ausgabe auf die ersten 10 Plätze.


```r
flights %>% 
  arrange(-arr_delay) %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest) %>% 
  filter(row_number() < 11) %>% 
  kable()
```



 arr_delay  carrier    month   day   dep_time  tailnum    flight  dest 
----------  --------  ------  ----  ---------  --------  -------  -----
      1272  HA             1     9        641  N384HA         51  HNL  
      1127  MQ             6    15       1432  N504MQ       3535  CMH  
      1109  MQ             1    10       1121  N517MQ       3695  ORD  
      1007  AA             9    20       1139  N338AA        177  SFO  
       989  MQ             7    22        845  N665MQ       3075  CVG  
       931  DL             4    10       1100  N959DL       2391  TPA  
       915  DL             3    17       2321  N927DA       2119  MSP  
       895  DL             7    22       2257  N6716C       2047  ATL  
       878  AA            12     5        756  N5DMAA        172  MIA  
       875  MQ             5     3       1133  N523MQ       3744  ORD  

"Geht doch", war die Antwort des Chefs, als sie die Tabelle rübergeben (er mag auch keine Emails). "Ach ja", raunt der Chef, als Sie das Zimmer verlassen wollen, "hatte ich erwähnt, dass ich die gleiche Auswertung für jeden Carrier brauche? Reicht bis in einer halben Stunde".

Wir gruppieren also den Datensatz nach der Fluggesellschaft (`carrier`) und filtern dann  die ersten 3 Zeilen (damit die Tabelle für den Chef nicht zu groß wird). Wie jeder `dplyr`-Befehl wird die vorherige Gruppierung berücksichtigt und daher die Top-3-Zeilen *pro Gruppe*, d.h. pro Fluggesellschaft, ausgegeben.


```r
flights %>% 
  arrange(-arr_delay) %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest) %>% 
  group_by(carrier) %>% 
  filter(row_number() < 4) 
#> Source: local data frame [48 x 8]
#> Groups: carrier [16]
#> 
#>    arr_delay carrier month   day dep_time tailnum flight  dest
#>        <dbl>   <chr> <int> <int>    <int>   <chr>  <int> <chr>
#> 1       1272      HA     1     9      641  N384HA     51   HNL
#> 2       1127      MQ     6    15     1432  N504MQ   3535   CMH
#> 3       1109      MQ     1    10     1121  N517MQ   3695   ORD
#> 4       1007      AA     9    20     1139  N338AA    177   SFO
#> 5        989      MQ     7    22      845  N665MQ   3075   CVG
#> 6        931      DL     4    10     1100  N959DL   2391   TPA
#> 7        915      DL     3    17     2321  N927DA   2119   MSP
#> 8        895      DL     7    22     2257  N6716C   2047   ATL
#> 9        878      AA    12     5      756  N5DMAA    172   MIA
#> 10       852      AA     5    19      713  N3HEAA    257   LAS
#> # ... with 38 more rows
```

Vielleicht gefällt dem Chef diese Darstellung (sortiert nach `carrier`) besser:


```r
flights %>% 
  arrange(-arr_delay) %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest) %>% 
  group_by(carrier) %>% 
  filter(row_number() < 4) %>% 
  arrange(carrier)
#> Source: local data frame [48 x 8]
#> Groups: carrier [16]
#> 
#>    arr_delay carrier month   day dep_time tailnum flight  dest
#>        <dbl>   <chr> <int> <int>    <int>   <chr>  <int> <chr>
#> 1        744      9E     2    16      757  N8940E   3798   CLT
#> 2        458      9E     7    24     1525  N927XJ   3538   MSP
#> 3        421      9E     7    10     2054  N937XJ   3325   DFW
#> 4       1007      AA     9    20     1139  N338AA    177   SFO
#> 5        878      AA    12     5      756  N5DMAA    172   MIA
#> 6        852      AA     5    19      713  N3HEAA    257   LAS
#> 7        198      AS     3     8     1012  N587AS     11   SEA
#> 8        196      AS     1    20     2157  N305AS      7   SEA
#> 9        188      AS     5    23     2205  N516AS      7   SEA
#> 10       497      B6     1    16     1622  N661JB    517   MCO
#> # ... with 38 more rows
```

Da Sie den Chef gut kennen, berechnen Sie gleich noch die durchschnittliche Verspätung pro Fluggesellschaft.


```r
flights %>% 
  select(arr_delay, carrier, month, day, dep_time, tailnum, flight, dest) %>% 
  group_by(carrier) %>% 
  summarise(delay_mean = mean(arr_delay, na.rm = TRUE)) %>% 
  arrange(-delay_mean) %>% 
  kable()
```



carrier    delay_mean
--------  -----------
F9             21.921
FL             20.116
EV             15.796
YV             15.557
OO             11.931
MQ             10.775
WN              9.649
B6              9.458
9E              7.380
UA              3.558
US              2.130
VX              1.764
DL              1.644
AA              0.364
HA             -6.915
AS             -9.931

Der Chef ist zufrieden. Sie können sich wieder wichtigeren Aufgaben zuwenden...



## Befehlsübersicht


Funktion             Beschreibung
-----------------    -------------
data                 Lädt Daten aus einem Paket.
dplyr::glimpse       Zeigt einen Überblick über einen Datensatz.
knitr::kable         Erzeugt den HTML-Code für eine Tabelle
dplyr::row_number    Gibt die Zeilennummern zurück.



## Verweise

- Eine ausführlichere Version einer "YACSDA"^[yet another case study on data analysis] findet sich hier^[https://sebastiansauer.github.io/Fallstudie_Flights/] oder hier^[https://cran.rstudio.com/web/packages/dplyr/vignettes/introduction.html].

- Es finden sich online viele ähnliche Datenanalysen zu `dplyr`, z.B. hier^[http://stat545.com/block009_dplyr-intro.html] oder hier^[http://genomicsclass.github.io/book/pages/dplyr_tutorial.html].


<!--chapter:end:041_Fallstudie_dplyr.Rmd-->





# Fallstudie zur Visualisierung


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Diagramme für nominale Variablen erstellen können.
- Balkendiagramme mit Prozentpunkten auf der Y-Achse erstellen können.
- Balkendiagramme drehen können.
- Text-Labels an Balkendiagramme anfügen können.
- Farbschemata von Balkendiagrammen ändern können.

</div>\EndKnitrBlock{rmdcaution}


Benötigte Pakete:

```r
library(tidyverse)
library(corrr)
library(GGally)
```



Eine recht häufige Art von Daten in der Wirtschaft kommen von Umfragen in der Belegschaft. Diese Daten gilt es dann aufzubereiten und graphisch wiederzugeben. Das ist der Gegenstand dieser Fallstudie.


## Daten einlesen
Hier laden wir einen Datensatz von einer Online-Umfrage:


```r
data <- read.csv("https://osf.io/meyhp/?action=download")
```

Der DOI für diesen Datensatz ist 10.17605/OSF.IO/4KGZH.

Der Datensatz besteht aus 10 Extraversions-Items (B5T nach Satow^[https://www.zpid.de/pub/tests/PT_9006357_B5T_Forschungsbericht.pdf]) sowie einigen Verhaltenskorrelaten (zumindest angenommenen). Uns interessieren also hier nur die 10 Extraversions-Items, die zusammen Extraversion als Persönlichkeitseigenschaft messen (sollen). Wir werden die Antworte der Befragten darstelle, aber uns hier keine Gedanken über Messqualität u.a. machen.


Die Umfrage kann hier^[https://docs.google.com/forms/d/e/1FAIpQLSfD4wQuhDV_edx1WBfN3Qos7XqoVbe41VpiKLRKtGLeuUD09Q/viewform] eingesehen werden. Schauen wir uns die Daten mal an:

```r
glimpse(data)
#> Observations: 501
#> Variables: 28
#> $ X                  <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, ...
#> $ timestamp          <fctr> 11.03.2015 19:17:48, 11.03.2015 19:18:05, ...
#> $ code               <fctr> HSC, ERB, ADP, KHB, PTG, ABL, ber, hph, IH...
#> $ i01                <int> 3, 2, 3, 3, 4, 3, 4, 3, 4, 4, 3, 3, 4, 4, 3...
#> $ i02r               <int> 3, 2, 4, 3, 3, 2, 4, 3, 4, 4, 3, 4, 3, 3, 3...
#> $ i03                <int> 3, 1, 1, 2, 1, 1, 1, 2, 1, 2, 1, 1, 1, 4, 1...
#> $ i04                <int> 3, 2, 4, 4, 4, 4, 3, 3, 4, 4, 3, 3, 2, 4, 3...
#> $ i05                <int> 4, 3, 4, 3, 4, 2, 3, 2, 3, 3, 3, 2, 3, 3, 3...
#> $ i06r               <int> 4, 2, 1, 3, 3, 3, 3, 2, 4, 3, 3, 3, 3, 3, 3...
#> $ i07                <int> 3, 2, 3, 3, 4, 4, 2, 3, 3, 3, 2, 4, 2, 3, 3...
#> $ i08                <int> 2, 3, 2, 3, 2, 3, 3, 2, 3, 3, 3, 2, 3, 3, 4...
#> $ i09                <int> 3, 3, 3, 3, 3, 3, 3, 4, 4, 3, 4, 2, 4, 4, 4...
#> $ i10                <int> 1, 1, 1, 2, 4, 3, 2, 1, 2, 3, 1, 3, 2, 3, 2...
#> $ n_facebook_friends <int> 250, 106, 215, 200, 100, 376, 180, 432, 200...
#> $ n_hangover         <int> 1, 0, 0, 15, 0, 1, 1, 2, 5, 0, 1, 2, 20, 2,...
#> $ age                <int> 24, 35, 25, 39, 29, 33, 24, 28, 29, 38, 25,...
#> $ sex                <fctr> Frau, Frau, Frau, Frau, Frau, Mann, Frau, ...
#> $ extra_single_item  <int> 4, 3, 4, 3, 4, 4, 3, 3, 4, 4, 4, 4, 4, 4, 4...
#> $ time_conversation  <dbl> 10, 15, 15, 5, 5, 20, 2, 15, 10, 10, 1, 5, ...
#> $ presentation       <fctr> nein, nein, nein, nein, nein, ja, ja, ja, ...
#> $ n_party            <int> 20, 5, 3, 25, 4, 4, 3, 6, 12, 5, 10, 5, 10,...
#> $ clients            <fctr> , , , , , , , , , , , , , , , , , , , , , ...
#> $ extra_vignette     <fctr> , , , , , , , , , , , , , , , , , , , , , ...
#> $ extra_description  <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
#> $ prop_na_per_row    <dbl> 0.0435, 0.0435, 0.0435, 0.0435, 0.0435, 0.0...
#> $ extra_mean         <dbl> 2.9, 2.1, 2.6, 2.9, 3.2, 2.8, 2.8, 2.5, 3.2...
#> $ extra_median       <dbl> 3.0, 2.0, 3.0, 3.0, 3.5, 3.0, 3.0, 2.5, 3.5...
#> $ client_freq        <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
```




## Daten umstellen
Wir haben ein Diagramm vor Augen (s.u.), bei dem auf der X-Achse die Items stehen (1,2,...,n) und auf der Y-Achse die Anzahl der Kreuze nach Kategorien.

Viele Grafik-Funktionen sind nun so aufgebaut, dass auf der X-Achsen nur *eine* Variable steht. `ggplot2`, das wir hier verwenden, ist da keine Ausnahme. Wir müssen also die "breite" Tabelle (10 Spalten, pro Item eine) in eine "lange Spalte" umbauen: Eine Spalte heißt dann "Itemnummer" und die zweite "Wert des Items" oder so ähnlich.


Also, los geht's: Zuerst wählen wir aus der Fülle der Daten, die Spalten, die uns interessieren: Die 10 Extraversions-Items, in diesem Fall.


```r
data_items <- select(data, i01:i10)
```

Dann stellen wir die Daten von "breit" nach "lang" um, so dass die Items eine Variable bilden und damit für `ggplot2` gut zu verarbeiten sind.


```r
data_long <- gather(data_items, key = items, value = Antwort)

data_long$Antwort <- factor(data_long$Antwort)
```

Den Befehl mit `factor` brauchen wir für zum Diagramm erstellen im Folgenden. Dieser Befehl macht aus den Zahlen bei der Variable `Antwort` eine nominale Variable (in R: `factor`) mit Text-Werten "1", "2" und so weiter. Wozu brauchen wir das? Der Digrammbefehl unten kann nur mit nominalen Variablen Gruppierungen durchführen. Wir werden in dem Diagramm die Anzahl der Antworten darstellen - die Anzahl der Antworten nach Antwort-Gruppe (Gruppe mit Antwort "1" etc.).

Keine Sorge, wenn sich das reichlich ungewöhnlich anhört. Sie müssen es an dieser Stelle nicht erfinden :-)

Man gewöhnt sich daran einerseits; und andererseits ist es vielleicht auch so, dass diese Funktionen nicht perfekt sind, oder nicht aus unserer Sicht oder nur aus Sicht des Menschen, der die Funktion geschrieben hat. Jedenfalls brauchen wir hier eine `factor` Variable zur Gruppierung...


Damit haben wir es schon! Jetzt wird gemalt.

## Diagramme für Anteile

Wir nutzen `ggplot2`, wie gesagt, und davon die Funktion `qplot` (q wie quick, nehme ich an.).


```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") 
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-7-1.png" width="70%" style="display: block; margin: auto;" />

Was macht dieser `ggplot` Befehl? Schauen wir es uns in Einzelnen an:

- `ggplot(data = ...)`: Wir sagen "Ich möchte gern die Funktion ggplot nutzen, um den Datensatz ... zu plotten". 
- `aes(...)`: Hier definieren wir die "aesthetics" des Diagramms, d.h. alles "Sichtbare". Wir ordnen in diesem Fall der X-Achse die Variable `items` zu. Per Standardeinstellung geht `ggplot` davon aus, dass sie die Häufigkeiten der X-Werte auf der Y-Achse haben wollen, wenn Sie nichts über die Y-Achse sagen. Jetzt haben wir ein Koordinatensystem definiert (das noch leer ist).
- `geom_bar()`: "Hey R oder ggplot, jetzt male mal einen barplot in den ansonsten noch leeren plot".
- `aes(fill = Antwort)`: Genauer gesagt nutzen wir `aes` um einen sichtbaren Aspekte des Diagramms (wie die X-Achse) eine Variable des Datensatzes zuzuordnen. Jetzt sagen wir, dass die Füllung (im Balkendiagramm) durch die Werte von `Antwort` definiert sein sollen (also "1", "2" etc.).
- `position = "fill"` sagt, dass die Gesamt-Höhe des Balken aufgeteilt werden soll mit den "Teil-Höhen" der Gruppen (Antwort-Kategorien 1 bis 4); wir hätten die Teil-Höhen auch nebeneinander stellen können.

Vielleicht ist es schöner, die NAs erst zu entfernen.


```r
data_long <- na.omit(data_long)
```

Und dann noch mal plotten:



```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") 
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-9-1.png" width="70%" style="display: block; margin: auto;" />



## Um 90° drehen

Dazu nehmen wir `+ coord_flip()`, also "flippe das Koordinatensystem".

```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") +
  coord_flip()
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-10-1.png" width="70%" style="display: block; margin: auto;" />


## Text-Labels für die Items

Wir definieren die Texte ("Labels") für die Items:

```r
item_labels <- c("Ich bin das erste Item",
                 "Das zweite Item",
                 "Item 3 sdjfkladsjk",
                 "Ich bin ein krasser Couch-Potato UMKODIERT",
"i5 asf", "i6 sdf", "adfjks", "sfjlkd", "sdfkjl", "sdfjkl")
```

Jetzt hängen wir die Labels an die Items im Diagramm:


```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") +
  coord_flip() +
  scale_x_discrete(labels = item_labels)
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-12-1.png" width="70%" style="display: block; margin: auto;" />


Man kann auch einen Zeilenumbruch in den Item-Labels erzwingen... wobei das führt uns schon recht weit, aber gut, zum Abschluss :-)


```r
item_labels <- c("Ich bin das erste Item",
                 "Das zweite Item",
                 "Item 3 sdjfkladsjk",
                 "Ich bin ein krasser \nCouch-Potato***mit Zeilenumbruch***",
"i5 asf", "i6 sdf", "adfjks", "sfjlkd", "sdfkjl", "sdfjkl")
```


Und wieder plotten:



```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") +
  coord_flip() +
  scale_x_discrete(labels = item_labels, name = "Extraversionsitems") +
  scale_y_continuous(name = "Anteile")
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-14-1.png" width="70%" style="display: block; margin: auto;" />


## Diagramm mit Häufigkeiten
Ach so, schön wäre noch die echten Zahlen an der Y-Achse, nicht Anteile. Dafür müssen wir unseren Diagrammtyp ändern, bzw. die Art der Anordnung ändern. Mit `position = "fill"` wird der Anteil (also mit einer Summe von 100%) dargestellt. Wir können auch einfach die Zahlen/Häufigkeiten anzeigen, in dem wir die Kategorien "aufeinander stapeln"



```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "stack") +
  coord_flip() +
  scale_x_discrete(labels = item_labels) 
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-15-1.png" width="70%" style="display: block; margin: auto;" />

## Farbschema
Ja, die Wünsche hören nicht auf... Also, noch ein anderes Farbschema:


```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "stack") +
  coord_flip() +
  scale_x_discrete(labels = item_labels) +
  scale_fill_brewer(palette = 17)
```

<img src="056_Fallstudie_Visualisierung_files/figure-html/unnamed-chunk-16-1.png" width="70%" style="display: block; margin: auto;" />


<!--chapter:end:056_Fallstudie_Visualisierung.Rmd-->





# II MODELLIEREN {-}

# Grundlagen des Modellierens {#mod1}



\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Erläutern können, was man unter einem Modell versteht.
- Die Ziele des Modellieren aufzählen und erläutern können.
- Die Vor- und Nachteile von einfachen vs. komplexen Modellen vergleichen können.
- Wissen, was man unter "Bias-Varianz-Abwägung" versteht.
- Um die Notwendigkeit von Trainings- und Test-Stichproben wissen.
- Wissen, was man unter Modellgüte versteht.
- Um die Schwierigkeiten der Prädiktorenauswahl wissen.

</div>\EndKnitrBlock{rmdcaution}


In diesem Kapitel benötigen wir diese Pakete:

```r
library(tidyverse)
require(gridExtra)
```

<img src="images/Modellieren.pdf" width="70%" style="display: block; margin: auto;" />




## Was ist ein Modell? Was ist Modellieren? {#Modellieren}

Das Leben ist schwer... oder sagen wir: komplex. Um einen Ausschnitt der Wirklichkeit[^41] zu verstehen, erscheint es sinnvoll, sich einige als wesentlich erachteten Aspekte "herauszugreifen" bzw. auszusuchen und sich nur noch deren Zusammenspiel näher anzuschauen.

Manche Aspekte der Wirklichkeit sind wirklicher als andere. Interessiert man sich für den Zusammenhang von Temperatur und Grundwasserspiegel, so sind diese Dinge direkt beobachtbar. Interessiert man sich hingegen für Lebensqualität und Zufriedenheit, so muss man diese Untersuchungsgegenstände erst konstruieren. Sprechen wir daher von Wirklichkeit lieber vorsichtiger vom *Gegenstandsbereich*, also den *konstruierten Auszug der Wirklichkeit* für den sich die forschende Person interessiert. Bestenfalls (er)findet man eine *Annäherung* an die Wirklichkeit, schlechterenfalls eine *verzerrte*, gar *grob falsche* Darstellung[^42], vgl. Abb. \@(fig:modellieren-plot).


<div class="figure" style="text-align: center">
<img src="images/Modell.pdf" alt="Modellieren" width="70%" />
<p class="caption">(\#fig:modellieren-plot)Modellieren</p>
</div>


Damit verstehen wir Modellieren als eine typische Aktivität von Menschen [@9783497008957], genauer eines Menschen mit einem bestimmten Ziel. Wir können gar nicht anders, als nur ein Modell unserer Umwelt zu machen. Vielfältige Medien kommen dazu in Frage: Bilder, Geschichten, Logik, Gleichungen. Wir werden uns hier auf *numerische* Modelle konzentrieren, weil es dort am einfachsten ist, die Informationen herauszuziehen.



Schauen wir uns ein Beispiel aus der Datenanalyse an; laden Sie dazu zuerst den Datensatz `wo_men`.




<div class="figure" style="text-align: center">
<img src="060_Modellieren_files/figure-html/plot-women-1.png" alt="Ein Beispiel für Modellieren" width="90%" />
<p class="caption">(\#fig:plot-women)Ein Beispiel für Modellieren</p>
</div>


Im ersten Plot von Abb. \@ref(fig:plot-women) sehen wir - schon übersetzt in eine Datenvisualisierung - den Gegenstandsbereich. Dort sind einige Objekte zusammen mit ihren Relationen abgebildet (Gewicht vs. Körpergröße). Der rechte Plot spezifiziert nun diesen Einfluss: Es wird ein linearer Einfluss (eine Gerade) zwischen Größe und Schuhgröße unterstellt. 

Im nächsten Plot (Abb. \@ref(fig:mod-beispiel)) sehen wir ein (graphisches) Modell dazu, ein sog. *Pfadmodell*. Noch ist das Modell recht unspezifisch; es wird nur postuliert, dass Körpergröße auf Schuhgröße einen Einfluss habe. 


<div class="figure" style="text-align: center">
<img src="images/Modellieren_Bsp1.png" alt="Ein Beispiel für ein Pfadmodell" width="70%" />
<p class="caption">(\#fig:mod-beispiel)Ein Beispiel für ein Pfadmodell</p>
</div>


>   Bei einem linearen Modell ist der Zuwachs der Ausgabevariablen konstant. Steigt eine Eingabevariable X um k, so steigt die Ausgabevariable ebenfalls um einen b*k, unabhängig vom Wert von X.



Ein etwas aufwändigeres Modell könnte so aussehen (Abb. \@ref(plot-modell-bsp2):

<div class="figure" style="text-align: center">
<img src="images/Modellieren_Bsp2.pdf" alt="Ein etwas aufwändigeres Modell" width="70%" />
<p class="caption">(\#fig:plot-modell-bsp2)Ein etwas aufwändigeres Modell</p>
</div>


Allgemeiner formuliert, haben wir einen oder mehrere *Eingabegrößen*\index{Einflussgrößen} bzw. *Prädiktoren*\index{Prädiktoren}, von denen wir annehmen, dass sie einen Einfluss haben auf genau eine *Zielgröße* (*Ausgabegröße*) bzw. *Kriterium*\index{Kriterium}. Modelle, wie wir sie betrachten werden, postulieren eine quantifizierbaren Zusammenhang zwischen diesen beiden Arten von Größen. Wir gehen dabei nicht davon aus, dass unsere Modelle perfekt sind, sondern dass Fehler passieren. Damit lassen sich unsere Modelle in drei Aspekte gliedern.

<div class="figure" style="text-align: center">
<img src="images/Modell_Blackbox.pdf" alt="Modelle mit schwarzer Kiste" width="70%" />
<p class="caption">(\#fig:fig-blackbox)Modelle mit schwarzer Kiste</p>
</div>


Die Einflussgrößen werden in einer "schwarzen Kiste", die wir hier noch nicht näher benennen, irgendwie verwurstet, will sagen, verrechnet, so dass ein *geschätzter* Wert für das Kriterium, eine *Vorhersage* "hinten bei rauskommt"^[das ist schließlich entscheidend - frei nach Helmut Kohl.]. Mathematischer ausgedrückt:

$$Y = f(X) + \epsilon$$

Hier stehen $Y$ für das Kriterium, $X$ für den oder die Prädiktoren, $f$ für die "schwarze Kiste" und $\epsilon$ für den Fehler, den wir bei unserer Vorhersage begehen. Durch den Fehlerterm in der Gleichung ist das Modell *nicht* mehr *deterministisch*\indes{deterministisch}, sondern beinhaltet einen funktionalen Term ($Y=f(x)$) und einen *stochastischen* Term ($\epsilon$). Die schwarze Kiste könnte man auch als eine "datengenerierende Maschine" bezeichnen.

Übrigens: Auf das Skalenniveau der Eingabe- bzw. Ausgabegrößen (qualitativ vs. quantitativ) kommt es hier nicht grundsätzlich an; es gibt Modelle für verschiedene Skalenniveaus bzw. Modelle, die recht anspruchslos sind hinsichtlich des Skalenniveaus (sowohl für Eingabe- als auch Ausgabegrößen). Was die Ausgabegröße (das Kriterium) betrifft, so "fühlen" qualitative Variablen von quantitativen Variablen anders an. Ein Beispiel zur Verdeutlichung: "Gehört Herr Bussi-Ness zur Gruppe der Verweigerer oder der Wichtigmacher?" (qualitatives Kriterium); "Wie hoch ist der Wichtigmacher-Score von Herrn Bussi-Ness?" (quantitatives Kriterium). Ein Modell mit qualitativem Kriterium bezeichnet man auch als *Klassifikation*\index{Klassifikation}; ein Modell mit quantitativem Kriterium bezeichnet man auch als *Regression*\index{Klassifikation}. Bei letzterem Begriff ist zu beachten, dass er *doppelt* verwendet wird. Neben der gerade genannten Bedeutung steht er auch für ein häufig verwendetes Modell - eigentlich das prototypische Modell - für quantitative Kriterien.


## Ziele des Modellierens { #ziele }
Man kann drei Arten von Zielen abgrenzen: Vorhersagen, Erklären und Reduzieren.

- *Vorhersagen*\index{Vorhersagen} hat das Ziel, eine geschickte Black Box zu wählen (oder eine Black Box geschickt zu wählen), so dass der Vohersagefehler möglichst klein ist. Sicherlich wird der Vorhersagefehler nie Null sein. Das Innenleben der "schwarzen Kiste" interessiert uns hier nicht.

- *Erklären*\index{Erklären} bedeutet, zu verstehen, *wie* oder *warum* sich der Kriteriumswert so verändert, wie er es tut. Auf *welche Art* werden die Prädiktoren verrechnet, so dass eine bestimmter Kriteriumswert resultiert? Welche Prädikatoren sind dabei (besonders) wichtig?  Ist die Art der Verrechnung abhängig von den Werten der Prädiktoren? Hierbei interessiert uns vor allem die Beschaffenheit der schwarzen Kiste.

- *Reduzieren*\index{Reduzieren} meint, dass man die Fülle des Materials verringert, in dem man ähnliche Dinge zusammenfasst. Dabei kann man sowohl Observationen zusammen fassen ("Britta", "Carla" und "Dina" zu "Frau" und "Joachim", "Alois" und "Casper" zu "Mann") oder auch Variablen zusammen fassen ("Frage 1", "Frage 2" und "Frage 3" zu "Markentreue" etc.).


Vorhersagen und Erklären haben gemein, dass Eingabegrößen genutzt werden, um Aussagen über einen Ausgabegröße zu treffen. Hat man einen Datensatz, so kann man prüfen, *wie gut* das Modell funktioniert, also wie genau man die Ausgabewerte vorhergesagt hat. Das ist also eine Art "Lernen mit Anleitung" oder *angeleitetes Lernen* oder *geleitetes Modellieren* (engl. *supervised learning*). Abbildung \@ref(fig:fig-blackbox) gibt diesen Fall wieder. Soll dem gegenüber das Ziel aber sein, die Daten zu reduzieren, also z.B. Kunden nach Persönlichkeit zu gruppieren, so ist die Lage anders. Es gibt keine Zielgröße. Wir wissen nicht, was die "wahre Kundengruppe" von Herrn Casper Bussi-Ness ist. Wir sagen eher, "OK, die drei Typen sind sich irgendwie ähnlich, sie werden wohl zum selben Typen von Kunden gehören". Wir tappen in Dunkeln, was die "Wahrheit" ist. Unser Modell muss ohne Hinweise darauf, was richtig ist auskommen. Man spricht daher in diesem Fall von *Lernen ohne Anleitung*\index{Lernen ohne Anleitung} oder *ungeleitetes Modellieren* (engl. *unsupervised learning*\index{unsupervised learning}).




<!-- ### Modelle zur Erklärung vs. Modelle zur Vorhersage -->
<!-- Man kann statistische Modelle danach unterscheiden, ob sie sich das Innenleben der schwarzen Kiste interessieren oder nicht. Manchmal will man einfach nur (möglichst) gute Vorhersagen treffen; in anderen Situationen will man erklären, warum sich "die Natur" so verhält, wie sie es tut. -->

<!-- Erklären wir das Innenleben der schwarzen Kiste genau(er), so sprechen wir von einem *Modell zur Erklärung*; spezifieren wir das Innenleben der schwarzen Kiste nicht oder weniger genau sondern fokussieren und auf die Vorhersagegüte, so kann man von einem *Modell zur Vorhersage* sprechen. -->


<!-- Ein Beispiel für ein einfaches "erklärendes Modell" ist: -->

<!-- >    Für je 5kg Körpergewicht steigt die Schuhgröße um 1 Nummer, wobei 50kg bei Schuhgröße 36 aufgehangen ist. -->

<!-- Was ist hier die Erklärung? Die Erklärung liegt darin, dass wir eine mathematische Funktion unterstellen - die Schuhgröße wird als Funktion des Körpergewichts modelliert. Diese mathematische Funktion soll "die Natur", d.h. den Gegenstandsbereich, widerspiegeln, so unsere Hoffnung.  -->

<!-- Ein Beispiel für ein nicht-erkländeres Modell, das sich nur für Vorhersagegüte interessiert, ist: -->

<!-- >    Schau mal, was die Schuhgröße von Leuten mit ähnlicher Größe ist. -->
<!--      Bilde den Mittelwert dieser Schuhgrößen. -->
<!--      Gib diesen Mittelwert als Schätzwert an. -->


<!-- Dieses Modell liefert keine "Erklärung", in dem Sinn, dass eine (einfache) mathematische Funktion, Eingabe- und Ausgabegröße verbindet. Es werden lediglich Vorhersagen getroffen. -->



## Wann welches Modell?

Tja, mit dieser Frage lässt sich ein Gut teil des Kopfzerbrechens in diesem Metier erfassen. Die einfache Antwort lautet: Es gibt kein "bestes Modell", aber es mag für *einen bestimmten Gegenstandsbereich*, in *einem bestimmten (historisch-kulturellen) Kontext*, für *ein bestimmtes Ziel* und mit *einer bestimmten Stichprobe* ein best mögliches Modell geben. Dazu einige Eckpfeiler:

- Unter sonst gleichen Umständen sind einfachere Modelle den komplexeren vorzuziehen. Gott sei Dank.

- Je nach Ziel der Modellierung ist ein erklärendes Modell oder ein Modell mit reinem Vorhersage-Charakter vorzuziehen.

- Man sollte stets mehrere Modelle vergleichen, um abzuschätzen, welches Modell in der aktuellen Situation geeigneter ist.



## Einfache vs. komplexe Modelle: Unter- vs. Überanpassung
Je komplexer ein Modell, desto besser passt sie meistens auf den Gegenstandsbereich. Eine grobe, Holzschnitt artige Theorie ist doch schlechter als eine, die feine Nuancen berücksichtigt, oder nicht? Einiges spricht dafür; aber auch einiges dagegen. Schauen wir uns ein Problem mit komplexen Modellen an.





<div class="figure" style="text-align: center">
<img src="060_Modellieren_files/figure-html/overfitting-4-plots-1.png" alt="Welches Modell passt am besten zu diesen Daten?" width="90%" />
<p class="caption">(\#fig:overfitting-4-plots)Welches Modell passt am besten zu diesen Daten?</p>
</div>

Der 1. Plot (links) von Abb. \@ref(fig:overfitting-4-plots) zeigt den Datensatz ohne Modell; der 2. Plot legt ein lineares Modell (rote Gerade) in die Daten. Der 3. Plot zeigt ein Modell, welches die Daten exakt erklärt - die (blaue) Linie geht durch alle Punkte. Der 4. Plot zeigt ein Modell (grüne Linie), welches die Punkte gut beschreibt, aber nicht exakt trifft.

Welchem Modell würden Sie (am meisten) vertrauen? Das "blaue" Modell beschreibt die Daten sehr gut, aber hat das Modell überhaupt eine "Idee" vom Gegenstandsbereich, eine "Ahnung", wie Y und X zusammenhängen, bzw. wie X einen Einfluss auf Y ausübt? Offenbar nicht. Das Modell ist "übergenau" oder zu komplex. Man spricht von *Überanpassung*\index{Überanpassung} (engl. *overfitting*\index{overfitting}). Das Modell scheint zufälliges, bedeutungsloses Rauschen zu ernst zu nehmen. Das Resultat ist eine zu wackelige Linie - ein schlechtes Modell, da wir wenig Anleitung haben, auf welche Y-Werte wir tippen müssten, wenn wir neue, unbekannte X-Werte bekämen.

Was das "blaue Modell" zu detailverliebt ist, ist das "rote Modell" zu simpel. Die Gerade beschreibt die Y-Werte nur sehr schlecht. Man hätte gleich den Mittelwert von Y als Schätzwert für jedes einzelne $Y_i$ hernehmen können. Dieses lineare Modell ist *unterangepasst*\index{Unteranpassung}, könnte man sagen (engl. *underfittting*\index{underfitting}). Auch dieses Modell wird uns wenig helfen können, wenn es darum geht, zukünftige Y-Werte vorherzusagen (gegeben jeweils einen bestimmten X-Wert).

Ah! Das *grüne Modell* scheint das Wesentliche, die "Essenz" der "Punktebewegung" zu erfassen. Nicht die Details, die kleinen Abweichungen, aber die "große Linie" scheint gut getroffen. Dieses Modell erscheint geeignet, zukünftige Werte gut zu beschreiben. Das grüne Modell ist damit ein Kompromiss aus Einfachheit und Komplexität und würde besonders passen, wenn es darum gehen sollte, zyklische Veränderungen zu erklären[^208].


>    Je komplexer ein Modell ist, desto besser beschreibt es einen bekannten Datensatz (Trainings-Stichprobe). Allerdings ist das Modell, welches den Trainings-Datensatz am besten beschreibt, nicht zwangsläufig das Modell, welches neue, unbekannte Daten am besten beschreibt. Oft im Gegenteil!


Je komplexer das Modell, desto kleiner der Fehler im *Trainings*-Datensatz. Allerdings: Die Fehler-Kurve im *Test-*Datensatz ist *U-förmig*: Mit steigender Komplexität wird der Fehler einige Zeit lang kleiner; ab einer gewissen Komplexität steigt der Fehler im Test-Datensatz wieder!

<img src="images/overfitting.pdf" width="70%" style="display: block; margin: auto;" />


## Bias-Varianz-Abwägung

Einfache Modelle bilden (oft) verfehlen oft wesentliche Aspekte des Gegenstandsbereich; die Wirklichkeit ist häufig zu komplex für einfache Modelle. Die resultierende *Verzerrung* in den vorhergesagten Werten nennt man auch *Bias*\index{Bias}. Mit anderen Worten: ist ein Modell zu einfach, passt es zu wenig zu den Daten (engl. *underfitting*). Auf der anderen Seite ist das Modell aber *robust*\index{robust} in dem Sinne, dass sich die vorhergesagten Werte kaum ändern, falls sich der Trainings-Datensatz etwas ändert.


Ist das Modell aber zu reichhaltig ("komplex"), bildet es alle Details des Trainings-Datensatzes ab, wird es auch zufällige Variation des Datensatzes vorhersagen; Variation, die nicht relevant ist, der nichts Eigentliches abbildet. Das Modell ist "überangepasst" (engl. *overfitting*); geringfügige Änderungen im Datensatz können das Modell stark verändern. Das Model ist nicht robust. Auf der positiven Seite werden die Nuancen der Daten gut abgebildet; der Bias ist gering bzw. tendenziell geringer als bei einfachen Modellen.

>    Einfache Modelle: Viel Bias, wenig Varianz.
     Komplexe Modelle: Wenig Bias, viel Varianz.
     
     
Dieser Sachverhalt ist in folgendem Diagramm dargestellt[^228].


<img src="060_Modellieren_files/figure-html/plot-bias-variance-1.png" width="70%" style="display: block; margin: auto;" />

Der linke Plot zeigt ein komplexes Modell[^260]; das Modell (blaue Linie) erscheint "zittrig"; kleine Änderungen in den Daten können große Auswirkungen auf das Modell (Verlauf der blauen Linie) haben. Darüber hinaus sind einige Details des Modells unplausibel: es gibt viele kleine "Hügel", die nicht augenscheinlich plausibel sind.

Der Plot auf der rechten Seiten hingegen ist sehr einfach und robust. Änderungen in den Daten werden vergleichsweise wenig Einfluss auf das Modell (die beiden roten Linien) haben.


## Training- vs. Test-Stichprobe
Wie wir gerade gesehen haben, kann man *immer* ein Modell finden, welches die *vorhandenen* Daten sehr gut beschreibt. Das gleicht der Tatsache, dass man im Nachhinein (also bei vorhandenen Daten) leicht eine Erklärung findet. Ob diese Erklärung sich in der Zukunft, bei unbekannten Daten bewahrheitet, steht auf einem ganz anderen Blatt. 

Daher sollte man *immer* sein Modell an einer Stichprobe *entwickeln* ("trainieren" oder "üben") und an einer zweiten Stichprobe *testen*. Die erste Stichprobe nennt man auch *training sample* (Trainings-Stichprobe) und die zweite *test sample* (Test-Stichprobe). Entscheidend ist, dass das Test-Sample beim Entwickeln des Modells unbekannt war bzw. nicht verwendet wurde.

>    Die Güte des Modells sollte nur anhand eines - bislang nicht verwendeten - Test-Samples überprüft werden. Das Test-Sample darf bis zur Modellüberprüfung nicht analysiert werden.


Die Modellgüte ist im Trainings-Sample meist deutlich besser als im Test-Sample (vgl. die Fallstudie dazu: \@ref(overfitting_casestudy) [Fallstudie zu Overfitting]).


```r
set.seed(42)
train <- wo_men %>% 
  sample_frac(.8, replace = FALSE)  # Stichprobe von 80%, ohne Zurücklegen

test <- wo_men %>% 
  anti_join(train)  # Alle Zeilen von "wo_men", die nicht in "train" vorkommen
```




Damit haben wir ein Trainings-Sample (`train`), in dem wir ein oder besser mehrere Modelle entwickeln können. 

So schön wie dieses Vorgehen auch ist, es ist nicht perfekt. Ein Nachteil ist, dass unsere Modellgüte wohl *anders* wäre, hätten wir andere Fälle im Test-Sample erwischt. Würden wir also ein neues Trainings-Sample und ein neues Test-Sample aus diesen Datensatz ziehen, so hätten wir wohl andere Ergebnisse. Was wenn diese Ergebnisse nun deutlich von den ersten abweichen? Dann würde unser Vertrauen in die die Modellgüte sinken. Wir bräuchten also noch ein Verfahren, welches *Variabilität* in der Modellgüte widerspiegelt.



## Modellgüte

Wie "gut" ist mein Modell? Modelle bewerten bzw. vergleichend bewerten ist einer der wichtigsten Aufgaben beim Modellieren. Die Frage der Modellgüte hat viele feine technisch-statistische Verästelungen, aber einige wesentlichen Aspekte kann man gut zusammenfassen.

>    Kriterium der theoretischen Plausibilität: Ein statistisches Modell sollte theoretisch plausibel sein.

Anstelle "alles mit allem" durchzuprobieren, sollte man sich auf Modelle konzentrieren, die theoretisch plausibel sind. Die Modellwahl ist theoretisch zu begründen.

>    Kriterium der guten Vorhersage: Die Vorhersagen eines Modells sollen präzise und überraschend sein.

Dass ein Modell die Wirklichkeit präzise vorhersagen soll, liegt auf der Hand. Hier verdient nur der Term *vorher*sagen Beachtung. Es ist einfach, im Nachhinein Fakten (Daten) zu erklären. Jede Nachbesprechung eines Bundesliga-Spiels liefert reichlich Gelegenheit, *posthoc* Erklärungen zu hören. Schwieriger sind Vorhersagen[^233]. Die Modellgüte ist also idealerweise an *in der Zukunft liegende* Ereignisse bzw. deren Vorhersage zu messen. Zur Not kann man auch schon in der Vergangenheit angefallene Daten hernehmen. Dann müssen diese Daten aber *für das Modell* neu sein.

Was ist mit überraschend gemeint? Eine Vorhersage, dass die Temperatur morgen in Nürnberg zwischen -30 und +40°C liegen wird, ist sicherlich sehr treffend, aber nicht unbedingt präzise und nicht wirklich überraschend. Die Vorhersage, dass der nächste Chef der Maurer-Innung (wenn es diese geben sollte) ein Mann sein wird, und nicht eine Frau, kann zwar präzise sein, ist aber nicht überraschend. Wir werden also in dem Maße unseren Hut vor dem Modell ziehen, wenn die Vorhersagen sowohl präzise als auch überraschen sind. Dazu später mehr Details.

>    Kriterium der Situationsangemessenheit: Die Güte des Modells ist auf die konkrete Situation abzustellen.

Ein Klassifikationsmodell muss anders beurteilt werden als ein Regressionsmodell. Reduktionsmodelle müssen wiederum anders beurteilt werden. In den entsprechenden Kapiteln werden diese Unterschiede präzisiert.


## Auswahl von Prädiktoren

Wie oben diskutiert, stellen wir ein Modell gerne als ein Pfaddiagramm des Typs $X \rightarrow Y$ dar (wobei X ein Vektor sein kann). Nehmen wir an das Kriterium $Y$ als gesetzt an; bleibt die Frage: Welche Prädiktoren ($X$) wählen wir, um das Kriterium möglichst gut vorherzusagen?

Eine einfache Frage. Keine leichte Antwort. Es gibt zumindest drei Möglichkeiten, die Prädiktoren zu bestimmen: theoriegeleitet, datengetrieben oder auf gut Glück.

- theoriegeleitet: Eine starke Theorie macht präzise Aussagen, welche Faktoren eine Rolle spielen und welche nicht. Auf dieser Basis wählen wir die Prädiktoren. Diese Situation ist wünschenswert; nicht nur, weil Sie Ihnen das Leben leicht macht, sondern weil es nicht die Gefahr gibt, die Daten zu "overfitten", "Rauschen als Muster" zu bewerten - kurz: zu optimistisch bei der Interpretation von Statistiken zu sein.

- datengetrieben: Kurz gesagt werden die Prädiktoren ausgewählt, welche das Kriterium am besten vorhersagen. Das ist einerseits stimmig, andererseits birgt es die Gefahr, dass Zufälligkeiten in den Daten für echte Strukturen, die sich auch in zukünftigen Stichproben finden würden, missverstanden werden.

- auf gut Glück: tja, kann man keine Theorie zu Rate ziehen und sind die Daten wenig aussagekräftig oder man nicht willens ist, sie nicht genug zu ~~quälen~~ analysieren, so neigen Menschen dazu, zuerst sich selbst und dann andere von der Plausibilität der Entscheidung zu überzeugen. Keine sehr gute Strategie.


In späteren Kapiteln betrachten wir Wege, um Prädiktoren für bestimmte Modelle auszuwählen.


## Aufgaben

### Erfolg beim Online-Dating

Lesen Sie diesen^[https://thewinnower.com/papers/5202-the-effect-of-a-status-symbol-on-success-in-online-dating-an-experimental-study-data-paper?review_it=true] Artikel [@sauer_wolff]. Zeichnen Sie ein Pfaddiagramm zum Modell!^[Status $\rightarrow$ Erfolg beim Online-Dating].


### Ziele des Modellierens

Welche drei Ziele des Modellierens kann man unterscheiden?^[\@ref(Ziele)]


### Bias-Varianz-Abwägung

Betrachten Sie Abb. \@ref(fig:plot-bias-variance2). Welches der beiden  Modelle (visualiert im jeweiligen Plot) ist wahrscheinlich...

- mehr bzw. weniger robust gegenüber Änderungen im Datensatz?
- mehr oder weniger präzise?


<img src="060_Modellieren_files/figure-html/plot-bias-variance2-1.png" width="70%" style="display: block; margin: auto;" />


### Richtig oder falsch?^[R, F, F, F, R]


\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">Richtig oder Falsch!?

1. Die Aussage "Pro Kilo Schoki steigt der Hüftumfang um einen Zentimeter" kann als Beispiel für ein deterministisches Modell herhalten.
1. Gruppiert man Kunden nach ähnlichen Kaufprofilen, so ist man insofern an "Reduzieren" der Datenmenge interessiert.
1. Grundsätzlich gilt: Je komplexer ein Modell, desto besser.
1. Mit "Bias" ist gemeint, dass ein Modell "zittrig" oder "wackelig" ist - sich also bei geringer Änderung der Stichprobendaten massiv in den Vorhersagen ändert.
1. In der Gleichung $Y=f(x)+\epsilon$ steht $\epsilon$ für den Teil der Kriteriums, der nicht durch das Modell erklärt wird.


</div>\EndKnitrBlock{rmdexercises}



## Verweise

- Einige Ansatzpunkte zu moderner Statistik ("Data Science") finden sich bei Peng und Matsui [-@peng2015art].

- Chester Ismay erläutert einige Grundlagen von R und RStudio, die für Modellierung hilfreich sind: https://bookdown.org/chesterismay/rbasics/.  





[^41]: Unter "Wirklichkeit" sei hier ein beliebiges empirisches System vorhanden, mit einer Menge von Objekten *O* und einer Menge von Beziehungen (Relationen) *R* zwischen den Objekten.



[^42]: Da keine Wiedergabe der Wirklichkeit perfekt ist, sind streng genommen alle Modelle "falsch" in diesem Sinne.


[^208]: Tatsächlich wurden die Y-Werte als Sinus-Funktion plus etwas normalverteiltes Rauschen simuliert.


[^228]: Basierend auf [@kuhn2013applied]

[^233]: Gerade wenn sie die Zukunft betreffen; ein Bonmot, das Yogi Berra nachgesagt wird.

[^260]: Genauer gesagt ein Polynom vom Grad 5.

<!--chapter:end:060_Modellieren.Rmd-->


# Der p-Wert


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Den p-Wert erläutern können.
- Den p-Wert kritisieren können.
</div>\EndKnitrBlock{rmdcaution}



<div class="figure" style="text-align: center">
<img src="images/Ronald_Fisher.jpg" alt="Der größte Statistiker des 20. Jahrhunderts (p &lt; .05)" width="10%" />
<p class="caption">(\#fig:sir-fisher)Der größte Statistiker des 20. Jahrhunderts (p < .05)</p>
</div>

## Der p-Wert sagt nicht das, was viele denken


Der p-Wert, entwickelt von Sir Ronald Fisher (Abb. \@ref(fig:sir-fisher)), ist die heilige Kuh der Forschung. Das ist nicht normativ, sondern deskriptiv gemeint. Der p-Wert entscheidet (häufig) darüber, was publiziert wird, und damit, was als Wissenschaft sichtbar ist - und damit, was Wissenschaft ist (wiederum deskriptiv, nicht normativ gemeint). Kurz: Dem p-Wert wird viel Bedeutung zugemessen. 


<div class="figure" style="text-align: center">
<img src="images/p_value_who_said.png" alt="Der p-Wert wird oft als wichtig erachtet" width="234" />
<p class="caption">(\#fig:who-said)Der p-Wert wird oft als wichtig erachtet</p>
</div>


Was sagt uns der p-Wert? Eine gute intuitive Definition ist:

>    Der p-Wert sagt, wie gut die Daten zur Nullhypothese passen.


Je größer p, desto besser passen die Daten zur Nullhypothese.

Allerdings hat der p-Wert seine Probleme. Vor allem: Er wird missverstanden. Jetzt kann man sagen, dass es dem p-Wert (dem armen) nicht anzulasten, dass andere/ einige ihm missverstehen. Auf der anderen Seite finde ich, dass sich Technologien dem Nutzer anpassen sollten (soweit als möglich) und nicht umgekehrt. Die (genaue) Definition des p-Werts ist aber auch so kompliziert, man kann sie leicht missverstehen:

> Der p-Wert gibt die Wahrscheinlichkeit P unserer Daten D an (und noch extremerer), unter der Annahme, dass die getestete Hypothese H wahr ist (und wenn wir den Versuch unendlich oft wiederholen würden, unter identischen Bedingungen und ansonsten zufällig).
p = P(D|H)

Viele Menschen - inkl. Professoren und Statistik-Dozenten - haben Probleme mit dieser Definition [@Gigerenzer2004]. Das ist nicht deren Schuld: Die Definition ist kompliziert. Vielleicht denken viele, der p-Wert sage das, was tatsächlich interessant ist: die Wahrscheinlichkeit der (getesteten) Hypothese H, gegeben der Tatsache, dass bestimmte Daten D vorliegen. Leider ist das *nicht* die Definition des p-Werts. Also:

$$ P(D|H) \ne P(H|D) $$


Formeln haben die merkwürdige Angewohnheit vor dem inneren Auge zu verschwimmen; Bilder sind für viele Menschen klarer, scheint's. Übersetzen wir die obige Formel in folgenden Satz:

>   Wahrscheinlichkeit, Moslem zu sein, wenn man Terrorist ist UNGLEICH zur 
Wahrscheinlichkeit, Terrorist zu sein, wenn man Moslem ist.


Oder kürzer:


$$ P(M|T) \ne P(T|M) $$




![](images/moslems_terroristen_crop.pdf)<!-- -->


Das Bild (Abb. \@ref(fig:fig-moslems)) zeigt den Anteil der Moslems an den Terroristen (sehr hoch). Und es zeigt den Anteil der Terroristen von allen Moslems (sehr gering). Dabei können wir uns Anteil mit Wahrscheinlichkeit übersetzen. Kurz: Die beiden Anteile (Wahrscheinlichkeiten) sind nicht gleich. Man denkt leicht, der p-Wert sei die *Wahrscheinlichkeit, Terrorist zu sein, wenn man Moslem ist*. Das ist falsch. Der p-Wert ist die *Wahrscheinlichkeit, Moslem zu sein, wenn man Terrorist ist*. Ein großer Unterschied^[die Größe der Anteile sind frei erfunden].


## Weitere Kritik am p-Wert

Der p-Wert ist für weitere Dinge kritisiert worden [@Wagenmakers2007, @uncertainty]; z.B. dass die "5%-Hürde" einen zu schwachen Test für die getestete Hypothese bedeutet. Letzterer Kritikpunkt ist aber nicht dem p-Wert anzulasten, denn dieses Kriterium ist beliebig, könnte konservativer gesetzt werden und jegliche mechanisierte Entscheidungsmethode kann ausgenutzt werden. Ähnliches kann man zum Thema "P-Hacking" argumentieren [@Head2015, @Wicherts2016]; andere statistische Verfahren können auch gehackt werden.

Ein wichtiger Anklagepunkt lautet, dass der p-Wert nicht nur eine Funktion der Effektgröße ist, sondern auch der Stichprobengröße. Sprich: Bei großen Stichproben wird jede Hypothese signifikant. Damit verliert der p-Wert an Nützlichkeit. Die Verteitigung argumentiert hier, dass das "kein Bug, sondern ein Feature" sei: Wenn man z.B. die Hypothese prüfe, dass der Gewichtsunteschied zwischen Männern und Frauen 0,000000000kg sei und man findet 0,000000123kg Unterschied, ist die getestete Hypothese falsch. Punkt. Der p-Wert gibt demnach das korrekte Ergebnis. Meiner Ansicht nach ist die Antwort zwar richtig, geht aber an den Anforderungen der Praxis vorbei.

Meine Meinung ist, dass der p-Wert ein problematisch ist (und ein Dinosaurier) und nicht oder weniger benutzt werden sollte (das ist eine normative Aussage). Da der p-Wert aber immer noch der Platzhirsch auf vielen Forschungsauen ist, führt kein Weg um ihn herum. Er muss genau verstanden werden: Was er sagt und - wichtiger noch - was er nicht sagt.


<img src="images/meme_pwert_1iw22a_pvalue_dino.jpg" width="250" style="display: block; margin: auto;" />


## Mythen zum p-Wert

Falsche Lehrmeinungen sterben erst aus, wenn die beteiligten Professoren in Rente gehen, heißt es. Jedenfalls halten sich eine Reihe von Mythen hartnäckig; sie sind alle falsch.


>    Wenn der p-Wert kleiner als 5% ist, dann ist meine Hypothese (H1) sicher richtig.

Richtig ist: "Wenn der p-Wert kleines ist als 5% (oder allgemeiner: kleiner als $\alpha$, dann sind die Daten (oder noch extereme) unwahrscheinlich, vorausgesetzt die H0 gilt".

>    Wenn der p-Wert kleiner als 5% ist, dann habe ich die Ursache eines Phänomens gefunden.

Richtig ist: Keine Statistik kann für sich genommen eine Ursache erkennen. Bestenfalls kann man sagen: hat man alle konkurrierenden Ursachen ausgeschlossen *und* sprechen die Daten für die Ursache *und* sind die Daten eine plausible Erklärung, so erscheint es der beste Schluss, anzunehmen, dass man *eine* Ursache gefunden hat - im Rahmen des Geltungsbereichs einer Studie.

>    Wenn der p-Wert kleiner als 5% ist, dann kann ich meine Studie veröffentlichen.

Richtig. Leider entscheidet zu oft der p-Wert über das Wohl und Wehe einer Studie.


## Zur Philosophie des p-Werts

Der p-Wert basiert auf der Idee, dass man ein Experiment *unendlich* oft wiederholen könnte; und das unter *zufälligen* aber *ansonsten komplett gleichen* Bedingungen.

Ob es im Universum irgendetwas gibt, das unendlich ist, ist umstritten [@ruckerinfinity]. Jedenfalls ist die Vorstellung, das Experiment unendlich oft zu wiederholen, unrealistisch. Inwieweit Zufälligkeit und Vergleichbarkeit hergestellt werden kann, kann auch kritisiert werden [@uncertainty].


<!--chapter:end:061_Inferenzstatistik.Rmd-->

# III GELEITETES MODELLIEREN {-}

<!--chapter:end:070_geleitetes_Modellieren.Rmd-->





# Klassische lineare (numerische) Regression


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Wissen, was man unter Regression versteht.
- Die Annahmen der Regression überprüfen können.
- Regression mit kategorialen Prädiktoren durchführen können.
- Die Regression inferenzstatisisch absichern können.
- Die Modellgüte bei der Regression bestimmen können.
- Vertiefende Aspekte beherrschen, wie Modellwahl und Interaktionen.

</div>\EndKnitrBlock{rmdcaution}


Benötigte Pakete:

```r
library(caret)  # Modellieren
library(tidyverse)  # Datenjudo, Visualisierung,...
library(gridExtra)  # Mehrere Plots kombinieren
```


## Einfache Regression
Wir werden weiter den Datensatz *tips* analysieren [@bryant1995practical].

Sofern noch nicht geschehen, können Sie in [hier](https://goo.gl/whKjnl) als `csv`-Datei herunterladen:

```r
tips <- read.csv("https://sebastiansauer.github.io/data/tips.csv")
```

Zur Unterstützung der Analyse wird (wieder) das Paket `mosaic` verwendet; außerdem laden wir `ggplot2` für `qplot`:


```r
library(mosaic)
library(ggplot2)
```

Wie hängen Trinkgeldhöhe `tip` und Rechnungshöhe `total_bill` zusammen? Kann die Höhe des Trinkgeldes als *lineare* Funktion der Rechnungshöhe linear modelliert werden? 
$$tip_i=\beta_0+\beta_1\cdot total\_bill_i+\epsilon_i$$

Zunächst eine visuelle Analyse mi Hilfe eines Scatterplots.

```r
qplot(y = tip, x = total_bill, data = tips)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-2-1.png" width="70%" style="display: block; margin: auto;" />

Es scheint einen positiven Zusammenhang zu geben. Modellieren wir die **abhängige** Variable `tip` (inhaltliche Entscheidung!) als lineare Funktion der **unabhängigen** Variable `total_bill`:

```r
LinMod.1 <- lm(tip ~ total_bill, data=tips)
summary(LinMod.1)
#> 
#> Call:
#> lm(formula = tip ~ total_bill, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -3.198 -0.565 -0.097  0.486  3.743 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)  0.92027    0.15973    5.76  2.5e-08 ***
#> total_bill   0.10502    0.00736   14.26  < 2e-16 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.02 on 242 degrees of freedom
#> Multiple R-squared:  0.457,	Adjusted R-squared:  0.454 
#> F-statistic:  203 on 1 and 242 DF,  p-value: <2e-16
```
Der Achsenabschnitt (`intercept`) wird mit 0.92 geschätzt, die Steigung in Richtung `total_bill` mit 0.11: steigt `total_bill` um einen Dollar, steigt im *Durchschnitt* `tip` um 0.11. 

Die (Punkt-)Prognose für `tip` lautet also

`tip` = 0.92 + 0.11 * `total_bill`

Die Koeffzienten werden dabei so geschätzt, dass $\sum \epsilon_i^2$ minimiert wird. Dies wird auch als  *Kleinste Quadrate* (*Ordinary Least Squares*, *OLS*) Kriterium bezeichnet. Eine robuste Regression ist z. B. mit der Funktion `rlm()` aus dem Paket `MASS` möglich.


In mosaic kann ein solches Modell einfach als neue Funktion definiert werden:

```r
LinMod.1Fun <- makeFun(LinMod.1)
```
Die (Punkt-)Prognose für die Trinkgeldhöhe, bspw. für eine Rechnung von 30$ kann dann berechnet werden

```r
LinMod.1Fun(total_bill=30)
#>    1 
#> 4.07
```
also 4.07$.

In mosaic kann die Modellgerade über 

```r
plotModel(LinMod.1)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-6-1.png" width="70%" style="display: block; margin: auto;" />

betrachtet werden. Das Bestimmtheitsmaß R² ist mit 0.46 "ok": 46-\% der Variation des Trinkgeldes wird im Modell erklärt.

## Überprüfung der Annahmen der linearen Regression

Aber wie sieht es mit den Annahmen aus?

- Die Linearität des Zusammenhangs haben wir zu Beginn mit Hilfe des Scatterplots "überprüft".
- Zur Überprüfung der Normalverteilung der Residuen zeichnen wir ein Histogramm. Die *Residuen*\index{Residuen} können über den Befehl `resid()` aus einem Linearen Modell extrahiert werden. Hier scheint es zu passen:


```r
resid_df <- data.frame(Residuen = resid(LinMod.1))
qplot(x = Residuen, data = resid_df)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-7-1.png" width="70%" style="display: block; margin: auto;" />


- *Konstante Varianz*: Dies kann z. B. mit einem Scatterplot der Residuen auf der y-Achse und den angepassten Werten auf der x-Achse überprüft werden. Die angepassten (geschätzten) Werte werden über den Befehl `fitted()`[^3] extrahiert. Diese Annahme scheint verletzt zu sein (siehe unten): je größer die Prognose des Trinkgeldes, desto größer wirkt die Streuung der Residuen. Dieses Phänomen ließ sich schon aus dem ursprünglichen Scatterplot 
`qplot(x = tip, y = total_bill, data=tips)` erahnen. Das ist auch inhaltlich plausibel: je höher die Rechnung, desto höher die Varianz beim Trinkgeld. Die Verletzung dieser Annahme beeinflusst *nicht* die Schätzung der Steigung, sondern die Schätzung des Standardfehlers, also des p-Wertes des Hypothesentests, d. h., $H_0:\beta_1=0$. 


```r
resid_df$fitted <- fitted(LinMod.1)
qplot(x = Residuen, y = fitted, data = resid_df)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-8-1.png" width="70%" style="display: block; margin: auto;" />

- *Extreme Ausreißer*: Wie am Plot der Linearen Regression `plotModel(LinMod.1)` erkennbar, gibt es vereinzelt Ausreißer nach oben, allerdings ohne einen extremen Hebel.


Hängt die Rechnungshöhe von der Anzahl der Personen ab? Bestimmt, aber wie?

```r
xyplot(total_bill ~ size, data=tips)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-9-1.png" width="70%" style="display: block; margin: auto;" />

Da bei diskreten metrischen Variablen (hier `size`) Punkte übereinander liegen können, sollte man "jittern" ("schütteln"), d. h., eine (kleine) Zufallszahl addieren:

```r
qplot(x = total_bill, y = size, data = tips, geom = "jitter")
```

<img src="071_Regression_files/figure-html/unnamed-chunk-10-1.png" width="70%" style="display: block; margin: auto;" />




\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">1.  Um wie viel Dollar steigt im Durchschnitt das Trinkgeld, wenn eine Person mehr am Tisch sitzt?

2.  Für wie aussagekräftig halten Sie Ihr Ergebnis aus 1.?
</div>\EndKnitrBlock{rmdexercises}



## Regression mit kategorialen Prädiktoren
Der Wochentag `day` ist eine kategoriale Variable. Wie sieht eine Regression des Trinkgeldes darauf aus?

Zunächst grafisch:

```r
qplot(x = tip,y = day, data=tips)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-11-1.png" width="70%" style="display: block; margin: auto;" />

Und als Lineares Modell:

```r
LinMod.2 <- lm(tip ~ day, data=tips)
summary(LinMod.2)
#> 
#> Call:
#> lm(formula = tip ~ day, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.245 -0.993 -0.235  0.538  7.007 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   2.7347     0.3161    8.65  7.5e-16 ***
#> daySat        0.2584     0.3489    0.74     0.46    
#> daySun        0.5204     0.3534    1.47     0.14    
#> dayThur       0.0367     0.3613    0.10     0.92    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.38 on 240 degrees of freedom
#> Multiple R-squared:  0.0205,	Adjusted R-squared:  0.00823 
#> F-statistic: 1.67 on 3 and 240 DF,  p-value: 0.174
```

Die im Modell angegebenen Schätzwerte sind die Änderung der Trinkgeldprognose, wenn z. B. der Tag ein Samstag (`daySat`) im Vergleich zu einer Referenzkategorie. Dies ist in R das erste Element des Vektors der Faktorlevel. Welcher dies ist ist über den Befehl `levels()` zu erfahren

```r
levels(tips$day)
#> [1] "Fri"  "Sat"  "Sun"  "Thur"
```
hier also Fri (aufgrund der standardmäßig aufsteigenden alphanumerischen Sortierung). Dies kann über `relevel()` geändert werden. Soll z. B. die Referenz der Donnerstag, `Thur` sein:

```r
tips$day <- relevel(tips$day, ref = "Thur")
levels(tips$day)
#> [1] "Thur" "Fri"  "Sat"  "Sun"
```
Das Modell ändert sich entsprechend:

```r
LinMod.3 <- lm(tip ~ day, data=tips)
summary(LinMod.3)
#> 
#> Call:
#> lm(formula = tip ~ day, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.245 -0.993 -0.235  0.538  7.007 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   2.7715     0.1750   15.84   <2e-16 ***
#> dayFri       -0.0367     0.3613   -0.10    0.919    
#> daySat        0.2217     0.2290    0.97    0.334    
#> daySun        0.4837     0.2358    2.05    0.041 *  
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.38 on 240 degrees of freedom
#> Multiple R-squared:  0.0205,	Adjusted R-squared:  0.00823 
#> F-statistic: 1.67 on 3 and 240 DF,  p-value: 0.174
```
sowie als Plot:

```r
plotModel(LinMod.3)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-16-1.png" width="70%" style="display: block; margin: auto;" />

Eine Alternative zu `relevel()` zur Bestimmung der Referenzkategorie ist es, innerhalb von `factor()` die Option `levels=` direkt in der gewünschten Sortierung zu setzen.

```r
day <- factor(tips$day, levels=c("Thur", "Fri", "Sat",  "Sun"))
```


Die (Punkt-)Prognose für die Trinkgeldhöhe, bspw. an einen Freitag kann dann berechnet werden

```r
LinMod.3Fun <- makeFun(LinMod.3)
LinMod.3Fun(day="Fri")
#>    1 
#> 2.73
```




\BeginKnitrBlock{rmdexercises}<div class="rmdexercises">3.  Wie verändert sich die Rechnungshöhe im Durchschnitt, wenn die Essenszeit Dinner statt Lunch ist?
4.  Wie viel \% der Variation der Rechnungshöhe können Sie durch die Essenszeit modellieren?
</div>\EndKnitrBlock{rmdexercises}





## Multiple Regression
Aber wie wirken sich die Einflussgrößen *zusammen* auf das Trinkgeld aus?

```r
LinMod.4 <- lm(tip ~ total_bill + size + sex  + smoker + day + time, data=tips)
summary(LinMod.4)
#> 
#> Call:
#> lm(formula = tip ~ total_bill + size + sex + smoker + day + time, 
#>     data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.848 -0.573 -0.103  0.476  4.108 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   0.6416     0.4976    1.29    0.199    
#> total_bill    0.0945     0.0096    9.84   <2e-16 ***
#> size          0.1760     0.0895    1.97    0.051 .  
#> sexMale      -0.0324     0.1416   -0.23    0.819    
#> smokerYes    -0.0864     0.1466   -0.59    0.556    
#> dayFri        0.1623     0.3934    0.41    0.680    
#> daySat        0.0408     0.4706    0.09    0.931    
#> daySun        0.1368     0.4717    0.29    0.772    
#> timeLunch     0.0681     0.4446    0.15    0.878    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.02 on 235 degrees of freedom
#> Multiple R-squared:  0.47,	Adjusted R-squared:  0.452 
#> F-statistic: 26.1 on 8 and 235 DF,  p-value: <2e-16
```
Interessant sind die negativen Vorzeichen vor den Schätzwerten für `sexMale` und `smokerYes` -- anscheinend geben Männer und Raucher weniger Trinkgeld, wenn alle anderen Faktoren konstant bleiben. Bei einer rein univariaten Betrachtung wäre etwas anderes herausgekommen.

```r
summary(lm(tip ~ sex, data=tips))
#> 
#> Call:
#> lm(formula = tip ~ sex, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.090 -1.090 -0.090  0.667  6.910 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    2.833      0.148   19.14   <2e-16 ***
#> sexMale        0.256      0.185    1.39     0.17    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.38 on 242 degrees of freedom
#> Multiple R-squared:  0.0079,	Adjusted R-squared:  0.0038 
#> F-statistic: 1.93 on 1 and 242 DF,  p-value: 0.166
summary(lm(tip ~ smoker, data=tips))
#> 
#> Call:
#> lm(formula = tip ~ smoker, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.009 -0.994 -0.100  0.558  6.991 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   2.9919     0.1128   26.52   <2e-16 ***
#> smokerYes     0.0169     0.1828    0.09     0.93    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.39 on 242 degrees of freedom
#> Multiple R-squared:  3.51e-05,	Adjusted R-squared:  -0.0041 
#> F-statistic: 0.00851 on 1 and 242 DF,  p-value: 0.927
```
Diese *Umkehrung* des modellierten Effektes liegt daran, dass es auch einen positiven Zusammenhang zur Rechnungshöhe gibt:

```r
summary(lm(total_bill ~ sex, data=tips))
#> 
#> Call:
#> lm(formula = total_bill ~ sex, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -14.99  -6.02  -1.94   3.99  30.07 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   18.057      0.946   19.08   <2e-16 ***
#> sexMale        2.687      1.180    2.28    0.024 *  
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 8.83 on 242 degrees of freedom
#> Multiple R-squared:  0.021,	Adjusted R-squared:  0.0169 
#> F-statistic: 5.19 on 1 and 242 DF,  p-value: 0.0236
summary(lm(total_bill ~ smoker, data=tips))
#> 
#> Call:
#> lm(formula = total_bill ~ smoker, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -17.69  -6.46  -1.89   4.58  30.05 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   19.188      0.723   26.53   <2e-16 ***
#> smokerYes      1.568      1.172    1.34     0.18    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 8.89 on 242 degrees of freedom
#> Multiple R-squared:  0.00735,	Adjusted R-squared:  0.00325 
#> F-statistic: 1.79 on 1 and 242 DF,  p-value: 0.182
```

Im vollem Modell `LinMod.4` sind alle unabhängigen Variablen berücksichtigt, die Koeffizienten beziehen sich dann immer auf: gegeben, die anderen Variablen bleiben konstant, d. h. ceteris paribus.

Vergleichen wir mal zwei Modelle:

```r
LinMod.5a <- lm(tip ~  sex, data=tips)
coef(LinMod.5a) # Koeffizienten extrahieren
#> (Intercept)     sexMale 
#>       2.833       0.256
LinMod.5b <- lm(tip ~  sex + total_bill, data=tips)
coef(LinMod.5b) # Koeffizienten extrahieren
#> (Intercept)     sexMale  total_bill 
#>      0.9333     -0.0266      0.1052
```
Ohne die Berücksichtigung der **Kovariable/Störvariable** Rechnungshöhe geben 
 Male  
 ein um im Durchschnitt 0.26
 *höheres* Trinkgeld, bei Kontrolle, d. h. gleicher Rechnungshöhe ein um 
 0.03
 *niedrigeres* Trinkgeld als die Referenzklasse 
 Female (`levels(tips$sex)[1]`). 

## Inferenz in der linearen Regression
Kehren wir noch einmal zur multivariaten Regression (`LinMod.4`) zurück. 

```r
summary(LinMod.4)
#> 
#> Call:
#> lm(formula = tip ~ total_bill + size + sex + smoker + day + time, 
#>     data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.848 -0.573 -0.103  0.476  4.108 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)   0.6416     0.4976    1.29    0.199    
#> total_bill    0.0945     0.0096    9.84   <2e-16 ***
#> size          0.1760     0.0895    1.97    0.051 .  
#> sexMale      -0.0324     0.1416   -0.23    0.819    
#> smokerYes    -0.0864     0.1466   -0.59    0.556    
#> dayFri        0.1623     0.3934    0.41    0.680    
#> daySat        0.0408     0.4706    0.09    0.931    
#> daySun        0.1368     0.4717    0.29    0.772    
#> timeLunch     0.0681     0.4446    0.15    0.878    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.02 on 235 degrees of freedom
#> Multiple R-squared:  0.47,	Adjusted R-squared:  0.452 
#> F-statistic: 26.1 on 8 and 235 DF,  p-value: <2e-16
```

In der 4. Spalte der, mit Zeilennamen versehenen Tabelle `Coefficients` stehen die p-Werte der Nullhypothese, die unabhängige Variable hat, gegeben alle anderen Variablen im Modell, keinen linearen Einfluss auf die abhängige Variable: $H_0: \beta_i=0$. Zur Bestimmung des p-Wertes wird der Schätzer (`Estimate`) durch den Standardfehler (`Std. Error`) dividiert. Der resultierende t-Wert (`t value`) wird dann, zusammen mit der Anzahl an Freiheitsgraden zur Berechnung des p-Wertes (`Pr(>|t|)`) verwendet. Ein einfacher t-Test! 

Zur schnelleren Übersicht finden sich dahinter "Sternchen" und "Punkte", die die entsprechenden Signifikanzniveaus symbolisieren: `***` bedeutet eine Irrtumswahrscheinlichkeit, Wahrscheinlichkeit für Fehler 1. Art, von unter 0.001, d. h. unter 0,1\%. `**` entsprechend 1\%, `*` 5\% und `.` 10\%. 

Zum Signifikanzniveau von 10\% sind hier also zwei Faktoren und der Achsenabschnitt (`(Intercept)`) signifikant -- nicht notwendigerweise relevant: Rechnungshöhe `total_bill` sowie Anzahl Personen `size`. Beides wirkt sich linear positiv auf die Trinkgeldhöhe aus: Mit jedem Dollar Rechnungshöhe steigt im Mittelwert die Trinkgeldhöhe um 0.09 Dollar, 
mit jeder Person um 0.18 Dollar -- gegeben alle anderen Faktoren bleiben konstant. Das Bestimmtheitsmaß R² (`Multiple R-squared:`) liegt bei 
0.47, also 47\% der Variation des Trinkgeldes wird im Modell erklärt.

Außerdem wird getestet, ob alle Koeffizienten der unabhängigen Variablen gleich Null sind:
$$H_0: \beta_1=\beta_2=\cdots=\beta_k=0$$
Das Ergebnis des zugrundeliegenden F-Tests (vgl. Varianzanalyse) wird in der letzten Zeile angegeben (`F-Statistic`). Hier wird $H_0$ also verworfen.


## Modellgüte bei Regressionsmodellen
In einem Regressionsmodell lautet die grundlegenden Überlegung zur Modellgüte so:

>    Wie groß ist der Unterschied zwischen Vorhersage und Wirklichkeit?

Die Größe des Unterschieds (Differenz, "Delta") zwischen vorhergesagten (geschätzten) Wert und Wirklichkeit, bezeichnet man als *Fehler*, *Residuum* oder Vohersagefehler, häufig mit $\epsilon$ (griechisch e wie "error") abgekürzt.

Graphisch kann man das gut veranschaulichen:

<img src="071_Regression_files/figure-html/resids-plot-1.png" width="70%" style="display: block; margin: auto;" />

Betrachten Sie die beiden Plots. Die rote Linie gibt die vorhergesagten (geschätzten) Werte wieder; die Punkte die beobachteten ("echten") Werte. Je länger die blauen Linien, desto größer die Vorhersagefehler. 

>   Je kürzer die typische "Abweichungslinie", desto besser die Vohersage.


Sagt mein Modell voraus, dass Ihre Schuhgröße 49 ist, aber in Wahrheit liegt sie bei 39, so werden Sie dieses Modell als schlecht beurteilen.

Leider ist es nicht immer einfach zu sagen, wie groß der Fehler sein muss, damit das Modell als "schlecht" gilt. Man kann argumentieren, dass es keine wissenschaftliche Frage sei, wie viel "viel" oder "genug" ist [@uncertainty]. Das ist zwar plausibel, hilft aber nicht, wenn ich eine Entscheidung treffen muss. Stellen Sie sich vor: Ich zwinge Sie mit der Pistole auf der Brust, meine Schuhgröße zu schätzen.

Eine einfache Lösung ist, das beste Modell unter mehreren Kandidaten zu wählen.

Ein anderer Ansatz ist, die Vorhersage in Bezug zu einem Kriterium zu setzen. Dieses "andere Kriterium" könnte sein "einfach raten". Oder, etwas intelligenter, Sie schätzen meine Schuhgröße auf einen Wert, der eine gewisse Plausibiliät hat, also z.B. die durchschnittliche Schuhgröße des deutschen Mannes. Auf dieser Basis kann man dann quantifizieren, ob und wieviel besser man als dieses Referenzkriterium ist.

### Mittlere Quadratfehler
Eine der häufigsten Gütekennzahlen ist der *mittlere quadrierte Fehler* (engl. "mean squared error", MSE), wobei Fehler wieder als Differenz zwischen Vorhersage (`pred`) und beobachtete Wirklichkeit (`obs`, `y`) definiert ist. Dieser berechnet für jede Beobachtung den Fehler, quadriert diesen Fehler und bilden dann den Mittelwert dieser "Quadratfehler", also einen *mittleren Quadratfehler*. Die englische Abkürzung *MSE* ist auch im Deutschen gebräuchlich.

$$ MSE = \frac{1}{n} \sum{(pred - obs)^2} $$

Konzeptionell ist dieses Maß an die Varianz angelehnt. Zieht man aus diesem Maß die Wurzel, so erhält man den sog. *root mean square error* (RMSE), welchen man sich als die Standardabweichung der Vorhesagefehler vorstellen kann. In Pseudo-R-Syntax:


```pseudo
RMSE <- sqrt(mean((df$pred - df$obs)^2))
```

Der RMSE hat die selben Einheiten wie die zu schätzende Variable, also z.B. Schuhgrößen-Nummern.

Übrigens: Der RMSE hat eine Reihe von wünschenswerten statistischen Eigenschaften, über die wir uns hier ausschweigen 




### R-Quadrat ($R^2$)
$R^2$, auch Bestimmtheitsmaß oder Determinationskoeffizient genannt, gibt die Vorhersagegüte im Verhältnis zu einem "Nullmodell" an. Das Nullmodell hier würde sagen, wenn es sprechen könnte: "Keine Ahnung, was ich schätzen soll, mich interessieren auch keine Prädiktoren, ich schätzen einfach immer den Mittelwert der Grundgesamtheit!".

Damit gibt $R^2$ an, wie gut unsere Vorhersagen im Verhältnis zu den Vorhersagen des Nullmodells sind. Ein $R^2$ von 25% (0.25) hieße, dass unser Vorhersagefehler 25% *kleiner* ist als der der Nullmodells. Ein $R^2$ von 100% (1) heißt also, dass wir den kompletten Fehler reduziert haben (Null Fehler übrig) - eine perfekte Vorhersage. Etwas formaler, kann man $R^2$ so definieren:

$$ R^2 = 1 - (\frac{Nullmodellfehler - Vorhersagefehler}{Nullmodellfehler})$$

Präziser, in R-Syntax:


```r
R2 <- 1 - sum((df$pred - df$obs)^2) / sum((mean(df$obs) - df$obs)^2)
```

Praktischerweise gibt es einige R-Pakete, die diese Berechnung für uns besorgen:


```r
library(caret)
postResample(obs = obs, pred = pred)
```

Hier steht`obs` für beobachtete Werte und `pred` für die vorhergesagten Werte. Dieser Befehl gibt sowohl RMSE als auch $R^2$ wieder.

### Likelihood and Friends
Der *Likelihood* $L$ beantwortet folgende Frage:

>   Angenommen, ein Modell M ist wahr. Wie wahrscheinlich ist es dann, die Daten D zu beobachten?

Zum Beispiel: Eine faire Münze wird 10 Mal geworfen (Modell M: faire Münze). Wie wahrscheinlich ist es, 10 Mal Zahl zu werfen? Die Wahrscheinlichkeit hierfür liegt bei ca. 0.1%. Der Likelihood wäre also hier ~0.1%.

Bei komplexen Modellen kann der Likelihood sehr klein werden. Damit haben Computer Probleme, weil z.B. nur eine begrenzte Anzahl von Dezimalen berücksichtigt werden. Werden zuviele Dezimalstellen gerundet, kann es das Ergebnis verfälschen. Daher wird der Likelihood häufig logarithmiert; man spricht dann vom *log Likelihood*. Der Logarithmus von einer positiven, sehr kleine Zahl ist eine negative Zahl mit großen Absolutwert. Man verwendet meist den natürlichen Logarithmus, wobei das eigentlich keine Rolle spielt. Manchmal dreht man noch das Vorzeichen um, damit der Log Likelihood wieder positiv ist. 

Gütekriterien wie AIC, BIC, CAIC oder die Devianz (engl. *deviance*) sind vom Likelihood abgeleitet. Meist wird noch berücksichtigt, wie komplex das Modell ist; komplexe Modelle tun sich leichter als einfachere Modelle, die Daten zu erklären. Aber sie könnten die Daten auch "überanpassen". Um die mögliche Scheingenauigkeit komplexerer Modelle auszugleichen, wird der Likelihood vom AIC etc. mit einem Strafwert belegt, der proportional zur Komplexität des Modells ist [@zumel2014practical].



\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Man sollte in der Regel die Korrelation (r) nicht als Gütekriterium verwenden. Der Grund ist, dass die Korrelation sich nicht verändert, wenn man die Variablen skaliert. Die Korrelation zieht allein auf das Muster der Zusammenhänge - nicht die Größe der Abstände - ab. In der Regel ist die Größe der Abstände zwischen beobachteten und vorhergesagten Werten das, was uns interessiert.
</div>\EndKnitrBlock{rmdcaution}



## Vertiefungen zum Regressionmodell

### Modellwahl
Das Modell mit allen Variablen des Datensatzes, d. h., mit 6 unabhängigen (`LinMod.4`) erklärt 47.01% der Variation, das Modell *nur* mit der Rechnungshöhe als erklärende Variable (`LinMod.1`) schon 45.66%, der Erklärungszuwachs liegt also gerade einmal bei 1.35 Prozentpunkten. In der Statistik ist die Wahl des *richtigen* Modells eine der größten Herausforderungen, auch deshalb, weil das wahre Modell in der Regel nicht bekannt ist und es schwer ist, die richtige Balance zwischen Einfachheit und Komplexität zu finden. Aufgrund des Zufalls kann es immer passieren, dass das Modell sich zu sehr an die *zufälligen* Daten anpasst (Stichwort: Overfitting). Es gibt unzählige Modellwahlmethoden, und leider garantiert keine, dass immer das beste Modell gefunden wird. Eine Möglichkeit ist die sogenannte Schrittweise-Rückwärtsselektion auf Basis des Akaike-Informationskriteriums (AIC)^[siehe z. B. Rob J Hyndman & George Athanasopoulos, Forecasting: principles and practice, Kapitel 5.3: Selecting predictors,   [https://www.otexts.org/fpp/5/3](https://www.otexts.org/fpp/5/3)]. Diese ist nicht nur recht weit verbreitet - und liefert unter bestimmten Annahmen das "richtige" Modell - sondern in R durch den Befehl `step()` einfach umsetzbar:

```r
step(LinMod.4)
#> Start:  AIC=20.5
#> tip ~ total_bill + size + sex + smoker + day + time
#> 
#>              Df Sum of Sq RSS   AIC
#> - day         3       0.6 247  15.1
#> - time        1       0.0 247  18.5
#> - sex         1       0.1 247  18.6
#> - smoker      1       0.4 247  18.9
#> <none>                    247  20.5
#> - size        1       4.1 251  22.5
#> - total_bill  1     101.6 348 102.7
#> 
#> Step:  AIC=15.1
#> tip ~ total_bill + size + sex + smoker + time
#> 
#>              Df Sum of Sq RSS  AIC
#> - time        1       0.0 247 13.1
#> - sex         1       0.0 247 13.2
#> - smoker      1       0.4 248 13.5
#> <none>                    247 15.1
#> - size        1       4.3 251 17.4
#> - total_bill  1     101.7 349 97.2
#> 
#> Step:  AIC=13.1
#> tip ~ total_bill + size + sex + smoker
#> 
#>              Df Sum of Sq RSS  AIC
#> - sex         1       0.0 247 11.2
#> - smoker      1       0.4 248 11.5
#> <none>                    247 13.1
#> - size        1       4.3 251 15.4
#> - total_bill  1     103.3 350 96.3
#> 
#> Step:  AIC=11.2
#> tip ~ total_bill + size + smoker
#> 
#>              Df Sum of Sq RSS  AIC
#> - smoker      1       0.4 248  9.5
#> <none>                    247 11.2
#> - size        1       4.3 252 13.4
#> - total_bill  1     104.3 351 95.0
#> 
#> Step:  AIC=9.53
#> tip ~ total_bill + size
#> 
#>              Df Sum of Sq RSS  AIC
#> <none>                    248  9.5
#> - size        1       5.2 253 12.6
#> - total_bill  1     106.3 354 94.7
#> 
#> Call:
#> lm(formula = tip ~ total_bill + size, data = tips)
#> 
#> Coefficients:
#> (Intercept)   total_bill         size  
#>      0.6689       0.0927       0.1926
```
In den letzten Zeilen der Ausgabe steht das beste Modell, das diese Methode (schrittweise, rückwärts) mit diesem Kriterium (AIC) bei diesen Daten findet (Punktprognose, d. h. ohne Residuum):

`tip =  0.66894 +  0.09271 * total_bill + 0.19260 * size`

Der Ausgabe können Sie auch entnehmen, welche Variablen in welcher Reihenfolge *entfernt* wurden: Zunächst `day`, dann `time`, danach `sex` und schließlich `smoker`. Hier sind also dieselben Variablen noch im Modell, die auch in `LinMod.4` signifikant zum Niveau 10\% waren, eine Auswahl der dort signifikanten Variablen hätte also dasselbe Modell ergeben. Das ist häufig so, aber nicht immer!

### Interaktionen 

Wir haben gesehen, dass es einen Zusammenhang zwischen der Trinkgeldhöhe und der Rechnungshöhe gibt. Vielleicht unterscheidet sich der Zusammenhang je nachdem, ob geraucht wurde, d. h., vielleicht gibt es eine Interaktion (Wechselwirkung). Die kann in `lm` einfach durch ein `*` zwischen den unabhängigen Variablen modelliert werden:


```r
LinMod.6 <- lm(tip ~ smoker*total_bill, data = tips)
summary(LinMod.6)
#> 
#> Call:
#> lm(formula = tip ~ smoker * total_bill, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.679 -0.524 -0.120  0.475  4.900 
#> 
#> Coefficients:
#>                      Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)           0.36007    0.20206    1.78  0.07601 .  
#> smokerYes             1.20420    0.31226    3.86  0.00015 ***
#> total_bill            0.13716    0.00968   14.17  < 2e-16 ***
#> smokerYes:total_bill -0.06757    0.01419   -4.76  3.3e-06 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 0.979 on 240 degrees of freedom
#> Multiple R-squared:  0.506,	Adjusted R-squared:   0.5 
#> F-statistic: 81.9 on 3 and 240 DF,  p-value: <2e-16
```

Der Schätzwert für die Interaktion steht bei `:`. Hier also: Wenn geraucht wurde, ist die Steigung im Durchschnitt um 6,8 Cent geringer. Aber wenn geraucht wurde, ist die Rechnung im Achsenabschnitt erstmal um 1,20\$ höher (Effekt, ceteris paribus). Wer will, kann ausrechnen, ab welcher Rechnungshöhe Rauchertische im Mittelwert lukrativer sind... 

Das gleiche Bild (höhere Achsenabschnitt, geringere Steigung) ergibt sich übrigens bei getrennten Regressionen:

```r
lm(tip~total_bill, data=tips, subset = smoker=="Yes")
#> 
#> Call:
#> lm(formula = tip ~ total_bill, data = tips, subset = smoker == 
#>     "Yes")
#> 
#> Coefficients:
#> (Intercept)   total_bill  
#>      1.5643       0.0696
lm(tip~total_bill, data=tips, subset = smoker=="No")
#> 
#> Call:
#> lm(formula = tip ~ total_bill, data = tips, subset = smoker == 
#>     "No")
#> 
#> Coefficients:
#> (Intercept)   total_bill  
#>       0.360        0.137
```

### Weitere Modellierungsmöglichkeiten

Über das Formelinterface `y~x` können auch direkt z. B. Polynome modelliert werden. Hier eine quadratische Funktion:

```r
summary(lm(tip~I(total_bill^2)+total_bill, data=tips))
#> 
#> Call:
#> lm(formula = tip ~ I(total_bill^2) + total_bill, data = tips)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -3.200 -0.559 -0.098  0.484  3.776 
#> 
#> Coefficients:
#>                  Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)      8.91e-01   3.47e-01    2.57  0.01078 *  
#> I(total_bill^2) -5.71e-05   6.02e-04   -0.09  0.92457    
#> total_bill       1.08e-01   3.08e-02    3.51  0.00054 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 1.02 on 241 degrees of freedom
#> Multiple R-squared:  0.457,	Adjusted R-squared:  0.452 
#> F-statistic:  101 on 2 and 241 DF,  p-value: <2e-16
```

D. h., die geschätzte Funktion ist eine "umgedrehte Parabel" (negatives Vorzeichen bei `I(total_bill^2) `), bzw. die Funktion ist konkav, die Steigung nimmt ab. Allerdings ist der Effekt nicht signifikant. **Hinweis:** Um zu "rechnen" und nicht beispielsweise Interaktion zu modellieren, geben Sie die Variablen in der Formel in der Funktion `I()` (*As Is*) ein.


### Prognoseintervalle

Insgesamt haben wir viel "Unsicherheit" u. a. aufgrund von Variabilität in den Beobachtungen und in den Schätzungen. Wie wirken sich diese auf die Prognose aus?

Dazu können wir über die Funktion `predict.lm` Prognoseintervalle berechnen -- hier für das einfache Modell `LinMod.1`:

```r
newdat <- data.frame(total_bill = seq(0, 75))
preddat <- predict(LinMod.1, newdata = newdat, interval = "prediction")
head(preddat)
#>    fit    lwr  upr
#> 1 0.92 -1.117 2.96
#> 2 1.03 -1.010 3.06
#> 3 1.13 -0.903 3.16
#> 4 1.24 -0.797 3.27
#> 5 1.34 -0.690 3.37
#> 6 1.45 -0.583 3.47
tail(preddat)
#>     fit  lwr  upr
#> 71 8.27 6.13 10.4
#> 72 8.38 6.23 10.5
#> 73 8.48 6.33 10.6
#> 74 8.59 6.43 10.7
#> 75 8.69 6.53 10.9
#> 76 8.80 6.63 11.0
matplot(newdat$total_bill, preddat, lty = c(1,2,2), type="l" )
points(x=tips$total_bill, y=tips$tip)
```

<img src="071_Regression_files/figure-html/unnamed-chunk-28-1.png" width="70%" style="display: block; margin: auto;" />

Sie sehen, dass 95\% Prognoseintervall ist recht breit: über den gewählten Rechnungsbereich von $0-75$\$ im Mittelwert bei 4.11\$. 


```r
favstats((preddat[,3]-preddat[,2]))
#>   min   Q1 median   Q3  max mean     sd  n missing
#>  4.03 4.04   4.07 4.17 4.34 4.12 0.0904 76       0
```

Zu den Rändern hin wird es breiter. Am schmalsten ist es übrigens beim Mittelwert der unabhängigen Beobachtungen, hier also bei 19.79\$.

***

## Übung: Teaching Rating
Dieser Datensatz analysiert u. a. den Zusammenhang zwischen Schönheit und Evaluierungsergebnis von Dozenten [@hamermesh2005beauty]. Sie können ihn, sofern noch nicht geschehen, von [https://goo.gl/6Y3KoK](https://goo.gl/6Y3KoK) als `csv` herunterladen.


Versuchen Sie, das Evaluierungsergebnis als abhängige Variable anhand geeigneter Variablen des Datensatzes zu erklären. Wie groß ist der Einfluss der Schönheit? Sind die Modellannahmen erfüllt und wie beurteilen Sie die Modellgüte?



## Fallstudie zu Overfitting {#overfitting_casestudy}

Vergleichen wir im ersten Schritt eine Regression, die die Modellgüte anhand der *Trainingsstichprobe* schätzt mit einer Regression, bei der die Modellgüte in einer *Test-Stichprobe* überprüft wird.


Zuerst führen wir dafür eine simple Regression aus und lassen uns $R^2$ ausgeben.

```r
df <-  read_csv("https://sebastiansauer.github.io/data/wo_men.csv")

lm1 <- lm(shoe_size ~ height, data = df)
summary(lm1)$r.squared
#> [1] 0.306
```


Im zweiten Schritt teilen wir die Stichprobe in eine Trainings- und eine Test-Stichprobe auf. Wir "trainineren" das Modell anhand der Daten aus der Trainings-Stichprobe:

```r
train <- df %>% 
  sample_frac(.8, replace = FALSE)  # Stichprobe von 80%, ohne Zurücklegen

test <- df %>% 
  anti_join(train)  # Alle Zeilen von "df", die nicht in "train" vorkommen

lm2 <- lm(shoe_size ~ height, data = train)
```


Dann testen wir (die Modellgüte) anhand der Test-Stichprobe. Also los, `lm2`, mach Deine Vorhersage:


```r
lm2_predict <- predict(lm2, newdata = test)
```

Diese Syntax sagt:

\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Speichere unter dem Namen "lm2_predict" das Ergebnis folgender Berechnung:  
Mache eine Vorhersage ("to predict") anhand des Modells "lm2",   
wobei frische Daten ("data = test") verwendet werden sollen. 
</div>\EndKnitrBlock{rmdpseudocode}

Als Ergebnis bekommen wir einen Vektor, der für jede Beobachtung des Test-Samples den geschätzten (vorhergesagten) Trinkgeld-Wert speichert.


```r
caret::postResample(pred = lm2_predict, obs = test$shoe_size)
#>     RMSE Rsquared 
#>   10.540    0.634
```

Die Funktion `postResample` aus dem Paket `caret` liefert uns zentrale Gütekennzahlen unser Modell. Wir sehen, dass die Modellgüte im Test-Sample deutlich schlechter ist als im Trainings-Sample. Ein typischer Fall, der uns warnt, nicht vorschnell optimistisch zu sein!





## Literatur


- David M. Diez, Christopher D. Barr, Mine &Ccedil;etinkaya-Rundel (2014): *Introductory Statistics with Randomization and Simulation*, [https://www.openintro.org/stat/textbook.php?stat_book=isrs](https://www.openintro.org/stat/textbook.php?stat_book=isrs),  Kapitel 5, 6.1-6.3
- Nicholas J. Horton, Randall Pruim, Daniel T. Kaplan (2015): Project MOSAIC Little Books *A Student's Guide to R*,  [https://github.com/ProjectMOSAIC/LittleBooks/raw/master/StudentGuide/MOSAIC-StudentGuide.pdf](https://github.com/ProjectMOSAIC/LittleBooks/raw/master/StudentGuide/MOSAIC-StudentGuide.pdf), Kapitel 5.4, 10.2
 - Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani (2013): *An Introduction to Statistical Learning -- with Applications in R*, [http://www-bcf.usc.edu/~gareth/ISL/](http://www-bcf.usc.edu/~gareth/ISL/), Kapitel 3
- Maike Luhmann (2015): *R für Einsteiger*, Kapitel 16, 17.1-17.3
- Andreas Quatember (2010): *Statistik ohne Angst vor Formeln*, Kapitel 3.11
- Daniel Wollschläger (2014): *Grundlagen der Datenanalyse mit R*, Kapitel 6

***

Diese Übung basiert teilweise auf Übungen zum Buch [OpenIntro](https://www.openintro.org/stat/index.php?stat_book=isrs) von Andrew Bray und Mine &Ccedil;etinkaya-Rundel unter der Lizenz [Creative Commons Attribution-ShareAlike 3.0 Unported](http://creativecommons.org/licenses/by-sa/3.0). 




<!--chapter:end:071_Regression.Rmd-->



# Klassifizierende Regression


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Lernziele:

- Die Idee der logistischen Regression verstehen.
- Die Koeffizienten der logistischen Regression interpretieren können.
- Vertiefungen wie Modellgüte kennen.

</div>\EndKnitrBlock{rmdcaution}

## Vorbereitung
Hier werden wir den Datensatz *Aktienkauf* der Universität Zürich ([Universität Zürich, Methodenberatung](http://www.methodenberatung.uzh.ch/de/datenanalyse/zusammenhaenge/lreg.html)) analysieren. Es handelt es sich hierbei um eine Befragung einer Bank im Zusammenhang mit den Fakten, die mit der Wahrscheinlichkeit, dass jemand Aktien erwirbt, zusammenhängen. Es wurden 700 Personen befragt. Folgende Daten wurden erhoben: Aktienkauf (0 = nein, 1 = ja), Jahreseinkommen (in Tausend CHF), Risikobereitschaft (Skala von 0 bis 25) und  Interesse an der aktuellen Marktlage (Skala von 0 bis 45).

Den Datensatz können Sie in so als `csv`-Datei herunterladen:


```r
Aktien <- read.csv2("https://raw.githubusercontent.com/luebby/Datenanalyse-mit-R/master/Daten/Aktienkauf.csv")
```

Zur Unterstützung der Analyse wird (wieder) `mosaic` und `ggplot2` verwendet.

```r
library(mosaic)
library(ggplot2)
```

## Problemstellung
Können wir anhand der Risikobereitschaft abschätzen, ob die Wahrscheinlichkeit für einen Aktienkauf steigt? Schauen wir uns zunächst ein Streudiagramm an:


```r
xyplot(Aktienkauf ~ Risikobereitschaft, data = Aktien)
```

<img src="072_klassifizierende_Regression_files/figure-html/unnamed-chunk-4-1.png" width="70%" style="display: block; margin: auto;" />

Der Zusammenhang scheint nicht sehr ausgeprägt zu sein. Lassen Sie uns dennoch ein lineare Regression durchführen und das Ergebnis auswerten und graphisch darstellen.


```r
lm1 <- lm(Aktienkauf ~ Risikobereitschaft, data = Aktien)
summary(lm1)
#> 
#> Call:
#> lm(formula = Aktienkauf ~ Risikobereitschaft, data = Aktien)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -0.684 -0.243 -0.204  0.348  0.814 
#> 
#> Coefficients:
#>                    Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)         0.18246    0.02001    9.12  < 2e-16 ***
#> Risikobereitschaft  0.05083    0.00762    6.67  5.2e-11 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 0.427 on 698 degrees of freedom
#> Multiple R-squared:  0.0599,	Adjusted R-squared:  0.0586 
#> F-statistic: 44.5 on 1 and 698 DF,  p-value: 5.25e-11
plotModel(lm1)
```

<img src="072_klassifizierende_Regression_files/figure-html/unnamed-chunk-5-1.png" width="70%" style="display: block; margin: auto;" />

Der Schätzer für die Steigung für `Risikobereitschaft` ist signifikant. Das Bestimmtheitsmaß $R^2$ ist allerdings sehr niedrig, aber wir haben bisher ja auch nur eine unabhängige Variable für die Erklärung der abhängigen Variable herangezogen.

Doch was bedeutet es, dass die Wahrscheinlichkeit ab einer Risikobereitsschaft von ca. 16 über 1 liegt?

Wahrscheinlichkeiten müssen zwischen 0 und 1 liegen. Daher brauchen wir eine Funktion, die das Ergebnis einer linearen Regression in einen Bereich von 0 bis 1 bringt, die sogenannte *Linkfunktion*. Eine häufig dafür verwendete Funktion ist die logistische Funktion: $$p(y=1)=\frac{e^\eta}{1+e^\eta}=\frac{1}{1+e^{-\eta}}$$

$\eta$, das sogenannte *Logit*, ist darin die Linearkombination der Einflussgrößen: $$\eta=\beta_0+\beta_1\cdot x_1+\dots$$

Exemplarisch können wir die logistische Funktion für einen Bereich von $\eta=-10$ bis $+10$ darstellen:

<img src="072_klassifizierende_Regression_files/figure-html/unnamed-chunk-6-1.png" width="70%" style="display: block; margin: auto;" />

## Die Idee der logistischen Regression
Die logistische Regression ist eine Anwendung des allgemeinen linearen Modells (*general linear model, GLM*). Die Modellgleichung lautet: $$p(y_i=1)=L\bigl(\beta_0+\beta_1\cdot x_{i1}+\dots+\beta_K\cdot x_{ik}\bigr)+\epsilon_i$$

> $L$ ist die Linkfunktion, in unserer Anwendung die logistische Funktion.  
$x_{ik}$ sind die beobachten Werte der unabhängigen Variablen $X_k$.  
$k$ sind die unabhängigen Variablen $1$ bis $K$.

Die Funktion `glm` führt die logistische Regression durch. Wir schauen uns im Anschluss zunächst den Plot an.


```r
glm1 <- glm(Aktienkauf ~ Risikobereitschaft, family = binomial("logit"),
            data = Aktien)
plotModel(glm1)
```

<img src="072_klassifizierende_Regression_files/figure-html/unnamed-chunk-7-1.png" width="70%" style="display: block; margin: auto;" />

> Es werden ein Streudiagramm der beobachten Werte sowie die *Regressionslinie* ausgegeben. Wir können so z. B. ablesen, dass ab einer Risikobereitschaft von etwa 7 die Wahrscheinlichkeit für einen Aktienkauf nach unserem Modell bei mehr als 50 % liegt.

Die Zusammenfassung des Modells zeigt folgendes:


```r
summary(glm1)
#> 
#> Call:
#> glm(formula = Aktienkauf ~ Risikobereitschaft, family = binomial("logit"), 
#>     data = Aktien)
#> 
#> Deviance Residuals: 
#>    Min      1Q  Median      3Q     Max  
#> -1.653  -0.738  -0.677   0.825   1.823  
#> 
#> Coefficients:
#>                    Estimate Std. Error z value Pr(>|z|)    
#> (Intercept)         -1.4689     0.1184   -12.4  < 2e-16 ***
#> Risikobereitschaft   0.2573     0.0468     5.5  3.8e-08 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> (Dispersion parameter for binomial family taken to be 1)
#> 
#>     Null deviance: 804.36  on 699  degrees of freedom
#> Residual deviance: 765.86  on 698  degrees of freedom
#> AIC: 769.9
#> 
#> Number of Fisher Scoring iterations: 4
```

Der Achsenabschnitt (`intercept`) des logits $\eta$ wird mit -1.47 geschätzt, die Steigung in Richtung `Risikobereitschaft` mit 0.26. Die (Punkt-)Prognose für die Wahrscheinlickeit eines Aktienkaufs $p(y=1)$ benötigt anders als in der linearen Regression noch die Linkfunktion und ergibt sich somit zu:
$$p(\texttt{Aktienkauf}=1)=\frac{1}{1+e^{-(-1.47 + 0.26 \cdot \texttt{Risikobereitschaft})}}$$

Die p-Werte der Koeffizienten können in der Spalte `Pr(>|z|)` abgelesen werden. Hier wird ein *Wald*-Test durchgeführt, nicht wie bei der linearen Regression ein t-Test, ebenfalls mit der $H_0:\beta_i=0$. Die Teststastistik (`z value`) wird wie in der linearen Regression durch Divisions des Schätzers (`Estimate`) durch den Standardfehler (`Std. Error`) ermittelt. Im *Wald*-Test ist die Teststatistik allerdings $\chi^2$-verteilt mit einem Freiheitsgrad.

## Welche Unterschiede zur linearen Regression gibt es in der Ausgabe?
Es gibt kein $R^2$ im Sinne einer erklärten Streuung der $y$-Werte, da die beobachteten $y$-Werte nur $0$ oder $1$ annehmen können. Das Gütemaß bei der logistischen Regression ist das *Akaike Information Criterion* (*AIC*). Hier gilt allerdings: je **kleiner**, desto **besser**. (Anmerkung: es kann ein Pseudo-$R^2$ berechnet werden -- kommt später.)

Es gibt keine F-Statistik (oder ANOVA) mit der Frage, ob das Modell als Ganzes signifikant ist. (Anmerkung: es kann aber ein vergleichbarer Test durchgeführt werden -- kommt später.)

## Interpretation der Koeffizienten
### y-Achsenabschnitt (`Intercept`) $\beta_0$ 
Für $\beta_0>0$ gilt, dass selbst wenn alle anderen unabhängigen Variablen $0$ sind, es eine Wahrscheinlichkeit von mehr als 50% gibt, dass das modellierte Ereignis eintritt. Für $\beta_0<0$ gilt entsprechend das Umgekehrte.

### Steigung $\beta_i$ mit $i=1,2,...,K$
Für $\beta_i>0$ gilt, dass mit zunehmenden $x_i$ die Wahrscheinlichkeit für das modellierte Ereignis steigt. Bei $\beta_i<0$ nimmt die Wahrscheinlichkeit entsprechend ab.

Eine Abschätzung der Änderung der Wahrscheinlichkeit (*relatives Risiko*, *relative risk* $RR$) kann über das Chancenverhältnis (*Odds Ratio* $OR$) gemacht werden.^[Wahrscheinlichkeit vs. Chance: Die Wahrscheinlichkeit bei einem fairen Würfel, eine 6 zu würfeln, ist $1/6$. Die Chance (*Odd*), eine 6 zu würfeln, ist die Wahrscheinlichkeit dividiert durch die Gegenwahrscheinlichkeit, also $\frac{1/6}{5/6}=1/5$.] Es ergibt sich vereinfacht $e^{\beta_i}$. Die Wahrscheinlichkeit ändert sich näherungsweise um diesen Faktor, wenn sich $x_i$ um eine Einheit erhöht. **Hinweis:** $RR\approx OR$ gilt nur, wenn der Anteil des modellierten Ereignisses in den beobachteten Daten sehr klein ($<5\%$) oder sehr groß ist ($>95\%$).

*Übung*: Berechnen Sie das relative Risiko für unser Beispielmodell, wenn sich die `Risikobereitschaft` um 1 erhöht (Funktion `exp()`). Vergleichen Sie das Ergebnis mit der Punktprognose für `Risikobereitschaft `$=7$ im Vergleich zu `Risikobereitschaft `$=8$. Zur Erinnerung: Sie können `makeFun(model)` verwenden.



```r
# aus Koeffizient abgeschätzt
exp(coef(glm1)[2])
#> Risikobereitschaft 
#>               1.29
```

In Worten: "Mit jedem Punkt mehr Risikobereitschaft steigen die Chancen (das OR) für Aktienkauf um 1.293".



```r

# mit dem vollständigen Modell berechnet
fun1 <- makeFun(glm1)
fun1(Risikobereitschaft = 1)
#>     1 
#> 0.229
fun1(Risikobereitschaft = 8)
#>     1 
#> 0.643
# als Faktor ausgeben
fun1(Risikobereitschaft = 8)/fun1(Risikobereitschaft = 1)
#>   1 
#> 2.8
```

Bei einer Risikobereitschaft von 1 beträgt die Wahrscheinlichkeit für $y=1$, d.h. für das Ereignis "Aktienkauf", 0.23. Bei einer Risikobereitschaft von 8 liegt diese Wahrscheinlichkeit bei 0.64.


Sie sehen also, die ungefähr abgeschätzte Änderung der Wahrscheinlichkeit weicht hier doch deutlich von der genau berechneten Änderung ab. Der Anteil der Datensätze mit `Risikobereitschaft`$=1$ liegt allerdings auch bei 0.26.

## Kategoriale Variablen
Wie schon in der linearen Regression können auch in der logistschen Regression kategoriale Variablen als unabhängige Variablen genutzt werden. Als Beispiel nehmen wir den Datensatz `tips` und versuchen abzuschätzen, ob sich die Wahrscheinlichkeit dafür, dass ein Raucher bezahlt hat (`smoker == yes`), in Abhängigkeit vom Wochentag ändert. 

Sofern noch nicht geschehen, können Sie so als `csv`-Datei herunterladen:

```r
tips <- read.csv("https://sebastiansauer.github.io/data/tips.csv")
```


Zunächst ein Plot:

```r
xyplot(jitter(as.numeric(smoker)) ~ day, data = tips)
```

<img src="072_klassifizierende_Regression_files/figure-html/jitter_tips-1.png" width="70%" style="display: block; margin: auto;" />

**Hinweis:** Um zu sehen, ob es an manchen Tagen mehr Raucher gibt, sollten Sie zumindest eine Variable "verrauschen" ("*jittern*"). Da die Variable `smoker` eine nominale Variable ist und die Funktion `jitter()` nur mit numerischen Variablen arbeitet, muss sie mit `as.numeric()` in eine numerische Variable umgewandelt werden.

Die relativen Häufigkeiten zeigt folgende Tabelle:


```r
(tab_smoke <- tally(smoker ~ day, data = tips, format = "proportion"))
#>       day
#> smoker   Fri   Sat   Sun  Thur
#>    No  0.211 0.517 0.750 0.726
#>    Yes 0.789 0.483 0.250 0.274
```

Hinweis: Durch die Klammerung wird das Objekt `tab_smoke` direkt ausgegeben.

Probieren wir die logistische Regression aus:


```r
glmtips <- glm(smoker ~ day, family = binomial("logit"),data = tips)
summary(glmtips)
#> 
#> Call:
#> glm(formula = smoker ~ day, family = binomial("logit"), data = tips)
#> 
#> Deviance Residuals: 
#>    Min      1Q  Median      3Q     Max  
#> -1.765  -0.801  -0.758   1.207   1.665  
#> 
#> Coefficients:
#>             Estimate Std. Error z value Pr(>|z|)    
#> (Intercept)    1.322      0.563    2.35  0.01883 *  
#> daySat        -1.391      0.602   -2.31  0.02093 *  
#> daySun        -2.420      0.622   -3.89    1e-04 ***
#> dayThur       -2.295      0.631   -3.64  0.00027 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> (Dispersion parameter for binomial family taken to be 1)
#> 
#>     Null deviance: 324.34  on 243  degrees of freedom
#> Residual deviance: 298.37  on 240  degrees of freedom
#> AIC: 306.4
#> 
#> Number of Fisher Scoring iterations: 4
```

Auch hier können wir die Koeffizienten in Relation zur Referenzkategorie (hier: Freitag) interpretieren. Die Wahrscheinlichkeit ist an einem Samstag niedriger, der Wert für `daySat` ist negativ. Eine Abschätzung erhalten wir wieder mit $e^{\beta_i}$:


```r
exp(coef(glmtips)[2])
#> daySat 
#>  0.249
```

Daher ist das Chancenverhältnis (*Odds Ratio*), dass am Samstag ein Raucher am Tisch sitzt, näherungsweise um den Faktor 0.25 niedriger als am Freitag[^173]: 


$${OR=\frac{\frac{P(Raucher|Samstag)}{1-P(Raucher|Samstag)}}
{\frac{P(Raucher|Freitag)}{1-P(Raucher|Freitag)}}
=\frac{\frac{0.483}{0.517}}
{\frac{0.79}{0.21}}
\approx 0.249}$$

Die Wahrscheinlichkeit für einen Raucher am Samstag können wir uns wieder komfortabel so ausgeben lassen:


```r
fun2 <- makeFun(glmtips)
fun2(day = "Sat")
#>     1 
#> 0.483
```



## Multiple logistische Regression
Wir kehren wieder zurück zu dem Datensatz *Aktienkauf*. Können wir unser Model `glm1` mit nur einer erklärenden Variable verbessern, indem weitere unabhängige Variablen hinzugefügt werden?



```r
glm2 <- glm(Aktienkauf ~ Risikobereitschaft + Einkommen + Interesse, 
            family = binomial("logit"), data = Aktien)
plotModel(glm2)
summary(glm2)
#> 
#> Call:
#> glm(formula = Aktienkauf ~ Risikobereitschaft + Einkommen + Interesse, 
#>     family = binomial("logit"), data = Aktien)
#> 
#> Deviance Residuals: 
#>    Min      1Q  Median      3Q     Max  
#> -2.130  -0.715  -0.539   0.518   3.214  
#> 
#> Coefficients:
#>                    Estimate Std. Error z value Pr(>|z|)    
#> (Intercept)        -1.66791    0.27903   -5.98  2.3e-09 ***
#> Risikobereitschaft  0.34781    0.08822    3.94  8.1e-05 ***
#> Einkommen          -0.02157    0.00564   -3.83  0.00013 ***
#> Interesse           0.08520    0.01775    4.80  1.6e-06 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> (Dispersion parameter for binomial family taken to be 1)
#> 
#>     Null deviance: 804.36  on 699  degrees of freedom
#> Residual deviance: 679.01  on 696  degrees of freedom
#> AIC: 687
#> 
#> Number of Fisher Scoring iterations: 5
```

<img src="072_klassifizierende_Regression_files/figure-html/glm2_tips-1.png" width="70%" style="display: block; margin: auto;" />




Alle Schätzer sind signifkant zum 0.1 %-Niveau (`***` in der Ausgabe). Zunehmende Risikobereitschaft (der Einfluss ist im Vergleich zum einfachen Modell stärker geworden) und zunehmendes Interesse erhöhen die Wahrscheinlichkeit für einen Aktienkauf. Steigendes Einkommen hingegen senkt die Wahrscheinlichkeit.

Ist das Modell besser als das einfache? Ja, da der AIC-Wert von 769.86 auf 687.01 gesunken ist.

Die Graphik zeigt die Verläufe in Abhängigkeit von den verschiedenen Variablen und den Kombinationen der Variablen.


## Modell- bzw. Klassifikationsgüte
Logistische Regressionsmodelle werden häufig zur Klassifikation verwendet, z. B. ob der Kredit für einen Neukunden ein "guter" Kredit ist oder nicht. Daher sind die Klassifikationseigenschaften bei logistischen Modellen wichtige Kriterien.

Hierzu werden die aus dem Modell ermittelten Wahrscheinlichkeiten ab einem Schwellenwert (*cutpoint*), häufig $0.5$, einer geschätzten $1$ zugeordnet, unterhalb des Schwellenwertes einer $0$. Diese aus dem Modell ermittelten Häufigkeiten werden dann in einer sogenannten Konfusionsmatrix (*confusion matrix*) mit den beobachteten Häufigkeiten verglichen.

Daher sind wichtige Kriterien eines Modells, wie gut diese Zuordnung erfolgt. Dazu werden die Sensitivität (*True Positive Rate, TPR*), also der Anteil der mit $1$ geschätzten an allen mit $1$ beobachten Werten, und die Spezifität (*True Negative Rate*) berechnet. Ziel ist es, dass beide Werte möglichst hoch sind.

Sie können die Konfusionsmatrix "zu Fuß" berechnen, in dem Sie eine neue Variable einfügen, die ab dem cutpoint $1$ und sonst $0$ ist und mit dem Befehl `tally()` ausgeben. Alternativ können Sie das Paket `SDMTools` verwenden mit der Funktion `confusion.matrix()`. Ein Parameter ist `cutpoint`, der standardmäßig auf $0.5$ steht.


```r
# Konfusionsmatrix "zu Fuß" berechnen
# cutpoint = 0.5 setzen
# neue Variable predicted anlegen mit 1, wenn modellierte Wahrscheinlichkeit > 1 ist
cutpoint = 0.5
Aktien$predicted <- ((glm1$fitted.values) > cutpoint)*1
# Kreuztabelle berechnen
(cm <- tally(~predicted+Aktienkauf, data = Aktien))
#>          Aktienkauf
#> predicted   0   1
#>         0 509 163
#>         1   8  20
# Sensitivität (TPR)
cm[2,2]/sum(cm[,2])
#> [1] 0.109
# Spezifität (TNR)
cm[1,1]/sum(cm[,1])
#> [1] 0.985

# mit Hilfe des Pakets SDMTools
# ggf. install.packages("SDMTools")
library(SDMTools)
# optional noch Parameter cutpoint = 0.5  angeben
(cm <- confusion.matrix(Aktien$Aktienkauf, glm1$fitted.values)) 
#>     obs
#> pred   0   1
#>    0 509 163
#>    1   8  20
#> attr(,"class")
#> [1] "confusion.matrix"
sensitivity(cm)
#> [1] 0.109
specificity(cm)
#> [1] 0.985
```



Wenn die Anteile der $1$ in den beobachteten Daten sehr gering sind (z. B. bei einem medizinischem Test auf eine seltene Krankheit, Klicks auf einen Werbebanner oder Kreditausfall), kommt eine Schwäche der logistischen Regression zum Tragen: Das Modell wird so optimiert, dass die Wahrscheinlichkeiten $p(y=1)$ alle unter $0.5$ liegen. Das würde zu einer Sensitität von $0$ und einer Spezifiät von $1$ führen. Daher kann es sinnvoll sein, den Cutpoint zu varieren. Daraus ergibt sich ein verallgemeinertes Gütemaß, die *ROC*-Kurve (*Return Operating Characteristic*) und den daraus abgeleiteten *AUC*-Wert (*Area Under Curve*). 

Hierzu wird der Cutpoint zwischen 0 und 1 variiert und die Sensitivität gegen $1-$Spezifität (welche Werte sind als $1$ modelliert worden unter den beobachten $0$, *False Positive Rate, FPR*). Um diese Werte auszugeben, benötigen Sie das Paket `ROCR` und die Funktion `performance()`.


```r
# ggf. install.packages("ROCR")
library(ROCR)
# Ein für die Auswertung notwendiges prediction Objekt anlegen
pred <- prediction(glm1$fitted.values, Aktien$Aktienkauf)
# ROC Kurve
perf <- performance(pred,"tpr","fpr")
plot(perf)
abline(0,1, col = "grey")
# Area under curve (ROC-Wert)
performance(pred,"auc")@y.values
#> [[1]]
#> [1] 0.636
```

<img src="072_klassifizierende_Regression_files/figure-html/unnamed-chunk-15-1.png" width="70%" style="display: block; margin: auto;" />



AUC liegt zwischen $0.5$, wenn das Modell gar nichts erklärt (im Plot die graue Linie) und $1$. Hier ist der Wert also recht gering. Akzeptable Werte liegen bei $0.7$ und größer, gute Werte sind es ab $0.8$.^[Hosmer/Lemeshow, Applied Logistic Regression, 3rd Ed. (2013), S. 164]

## Vertiefung

### Modellschätzung
Das Modell wird nicht wie bei der lineare Regression über die Methode der kleinsten Quadrate (OLS) geschätzt, sondern über die *Maximum Likelihood* Methode. Die Koeffizienten werden so gewählt, dass die beobachteten Daten am wahrscheinlichsten (*Maximum Likelihood*) werden.

Das ist ein iteratives Verfahren (OLS erfolgt rein analytisch), daher wird in der letzten Zeile der Ausgabe auch die Anzahl der Iterationen (`Fisher Scoring Iterations`) ausgegeben.

Die Devianz des Modells (`Residual deviance`) ist $-2$ mal die logarithmierte Likelihood. Die Nulldevianz (`Null deviance`) ist die Devianz eines Nullmodells, d. h., alle $\beta$ außer der Konstanten sind 0.

### Likelihood Quotienten Test
Der Likelihood Quotienten Test (*Likelihood Ratio Test, LR-Test*) vergleicht die Likelihood $L_0$ des Nullmodels mit der Likelihood $L_{\beta}$ des geschätzten Modells. Die Prüfgröße des LR-Tests ergibt sich aus: $${T=-2\cdot ln\left( \frac{L_0}{L_{\beta}}\right)}$$
$T$ ist näherungsweise $\chi ^2$-verteilt mit $k$ Freiheitsgraden.

In R können Sie den Test mit `lrtest()` aufrufen. Sie benötigen dazu das Paket `lmtest`.


```r
library(lmtest)
lrtest(glm2)
#> Likelihood ratio test
#> 
#> Model 1: Aktienkauf ~ Risikobereitschaft + Einkommen + Interesse
#> Model 2: Aktienkauf ~ 1
#>   #Df LogLik Df Chisq Pr(>Chisq)    
#> 1   4   -340                        
#> 2   1   -402 -3   125     <2e-16 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```


Das Modell `glm2` ist als Ganzes signifikant, der p-Wert ist sehr klein.

Den Likelihood Quotienten Test können Sie auch verwenden, um zwei Modelle miteinander zu vergleichen, z. B., wenn Sie eine weitere Variable hinzugenommen haben und wissen wollen, ob die Verbesserung auch signifikant war.



```r
lrtest(glm1, glm2)
#> Likelihood ratio test
#> 
#> Model 1: Aktienkauf ~ Risikobereitschaft
#> Model 2: Aktienkauf ~ Risikobereitschaft + Einkommen + Interesse
#>   #Df LogLik Df Chisq Pr(>Chisq)    
#> 1   2   -383                        
#> 2   4   -340  2  86.9     <2e-16 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```



Ja, die Modelle `glm1` (mit einer erklärenden Variable) und `glm2` unterscheiden sich signifikant voneinander.


### Pseudo-$R^2$ 
Verschiedene Statistiker haben versucht, aus der Likelihood eine Größe abzuleiten, die dem $R^2$ der linearen Regression entspricht. Exemplarisch sei hier McFaddens $R^2$ gezeigt: $${R^2=1-\frac{ln(L_{\beta})}{ln(L_0)}}$$ Wie bei bei dem $R^2$ der linearen Regression liegt der Wertebereich zwischen 0 und 1. Ab einem Wert von 0,4 kann die Modellanpassung als gut eingestuft werden. Wo liegen  $R^2$ der beiden Modelle `glm1` und `glm2`? Sie können es direkt berechnen oder das Paket `BaylorEdPsych` verwenden.


```r
# direkte Berechnung
1 - glm1$deviance/glm1$null.deviance
#> [1] 0.0479
1 - glm2$deviance/glm2$null.deviance
#> [1] 0.156
# ggf. install.packages("BaylorEdPsych")
library(BaylorEdPsych)
PseudoR2(glm1)
#>         McFadden     Adj.McFadden        Cox.Snell       Nagelkerke 
#>           0.0479           0.0404           0.0535           0.0783 
#> McKelvey.Zavoina           Effron            Count        Adj.Count 
#>           0.0826           0.0584           0.7557           0.0656 
#>              AIC    Corrected.AIC 
#>         769.8624         769.8796
PseudoR2(glm2)
#>         McFadden     Adj.McFadden        Cox.Snell       Nagelkerke 
#>           0.1558           0.1434           0.1640           0.2400 
#> McKelvey.Zavoina           Effron            Count        Adj.Count 
#>           0.2828           0.1845           0.7614           0.0874 
#>              AIC    Corrected.AIC 
#>         687.0068         687.0644
```



Insgesamt ist die Modellanpassung, auch mit allen Variablen, als schlecht zu bezeichnen. **Hinweis:** Die Funktion `PseudoR2(model)` zeigt verschiedene Pseudo-$R^2$ Statistiken, die jeweils unter bestimmten Bedingungen vorteilhaft einzusetzen sind. Für weitere Erläuterungen sei auf die Literatur verwiesen.



## Übung: Rot- oder Weißwein?

Der Datensatz untersucht den Zusammenhang zwischen der Qualität und physiochemischen Eigenschaften von portugisieschen Rot- und Weißweinen [@cortez2009modeling].


Sie können in unter <https://goo.gl/Dkd7nK> herunterladen. Die Originaldaten finden Sie im UCI Machine Learning Repository[^336].

Versuchen Sie anhand geeigneter Variablen, Rot- und Weißweine (richtig) zu klassifizieren[^338]. 

**Zusatzaufgabe:** Die Originaldaten bestehen aus einem Datensatz für Weißweine und einem für Rotweine. Laden Sie diese, beachten Sie die Fehlermeldung und beheben die damit verbundenen Fehler und fassen beide Datensätze zu einem gemeinsamen Datensatz zusammen, in dem eine zusätzliche Variable `color` aufgenommen wird (Rot = 0, Weiß = 1).


## Literatur


- David M. Diez, Christopher D. Barr, Mine &Ccedil;etinkaya-Rundel (2014): *Introductory Statistics with Randomization and Simulation*, [https://www.openintro.org/stat/textbook.php?stat_book=isrs](https://www.openintro.org/stat/textbook.php?stat_book=isrs),  Kapitel 6.4
- Nicholas J. Horton, Randall Pruim, Daniel T. Kaplan (2015): Project MOSAIC Little Books *A Student's Guide to R*,  [https://github.com/ProjectMOSAIC/LittleBooks/raw/master/StudentGuide/MOSAIC-StudentGuide.pdf](https://github.com/ProjectMOSAIC/LittleBooks/raw/master/StudentGuide/MOSAIC-StudentGuide.pdf), Kapitel 8
 - Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani (2013): *An Introduction to Statistical Learning -- with Applications in R*, [http://www-bcf.usc.edu/~gareth/ISL/](http://www-bcf.usc.edu/~gareth/ISL/), Kapitel 4.1-4.3
- Maike Luhmann (2015): *R für Einsteiger*, Kapitel 17.5
- Daniel Wollschläger (2014): *Grundlagen der Datenanalyse mit R*, Kapitel 8.1



[^173]: Am Freitag liegen die Chancen (das OR) für einen Raucher bei 3.75. Das OR für Samstag ist das Produkt dieser beiden OR. Um das OR zu einer Wahrscheinlichkeit umzurechnen kann man, möchte vom "von Hand" arbeiten, diese Formel verwenden: $p = OR / (OR + 1)$.


[^336]: http://archive.ics.uci.edu/ml/datasets/Wine+Quality

[^338]: Anregungen zu dieser Übung stammen von INTW Statistics: https://www.inwt-statistics.de/blog-artikel-lesen/Logistische_Regression_Beispiel_mit_R.html

<!--chapter:end:072_klassifizierende_Regression.Rmd-->



# Fallstudien zum geleiteten Modellieren

## Überleben auf der Titanic
In dieser YACSDA (Yet-another-case-study-on-data-analysis) geht es um die beispielhafte Analyse nominaler Daten anhand des "klassischen" Falls zum Untergang der Titanic. Eine Frage, die sich hier aufdrängt, lautet: Kann (konnte) man sich vom Tod freikaufen, etwas polemisch formuliert. Oder neutraler: Hängt die Überlebensquote von der Klasse, in der derPassagiers reist, ab?



### Daten und Pakete laden



```r
library("titanic")
data(titanic_train)
```

Man beachte, dass ein Paket nur *einmalig* zu installieren ist (wie jede Software). Dann aber muss das Paket bei jedem Starten von R wieder von neuem gestartet werden. Außerdem ist es wichtig zu wissen, dass das Laden eines Pakets nicht automatisch die Datensätze aus dem Paket lädt. Man muss das oder die gewünschten Pakete selber (mit `data(...)`) laden. Und: Der Name eines Pakets (z.B. `titanic`) muss nicht identisch sein mit dem oder den Datensätzen des Pakets (z.B. `titanic_train`).


```r
library(tidyverse)
```


### Erster Blick
Werfen wir einen ersten Blick in die Daten:
  

```r
# install.packages("dplyr", dependencies = TRUE) # ggf. vorher installieren
glimpse(titanic_train)
#> Observations: 891
#> Variables: 12
#> $ PassengerId <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,...
#> $ Survived    <int> 0, 1, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 1, 0,...
#> $ Pclass      <int> 3, 1, 3, 1, 3, 3, 1, 3, 3, 2, 3, 1, 3, 3, 3, 2, 3,...
#> $ Name        <chr> "Braund, Mr. Owen Harris", "Cumings, Mrs. John Bra...
#> $ Sex         <chr> "male", "female", "female", "female", "male", "mal...
#> $ Age         <dbl> 22, 38, 26, 35, 35, NA, 54, 2, 27, 14, 4, 58, 20, ...
#> $ SibSp       <int> 1, 1, 0, 1, 0, 0, 0, 3, 0, 1, 1, 0, 0, 1, 0, 0, 4,...
#> $ Parch       <int> 0, 0, 0, 0, 0, 0, 0, 1, 2, 0, 1, 0, 0, 5, 0, 0, 1,...
#> $ Ticket      <chr> "A/5 21171", "PC 17599", "STON/O2. 3101282", "1138...
#> $ Fare        <dbl> 7.25, 71.28, 7.92, 53.10, 8.05, 8.46, 51.86, 21.07...
#> $ Cabin       <chr> "", "C85", "", "C123", "", "", "E46", "", "", "", ...
#> $ Embarked    <chr> "S", "C", "S", "S", "S", "Q", "S", "S", "S", "C", ...
```

### Welche Variablen sind interessant?
Von 12 Variablen des Datensatzes interessieren uns offenbar `Pclass` und `Survived`; Hilfe zum Datensatz kann man übrigens mit `help(titanic_train)` bekommen. Diese beiden Variablen sind kategorial (nicht-metrisch), wobei sie in der Tabelle mit Zahlen kodiert sind. Natürlich ändert die Art der Codierung (hier als Zahl) nichts am eigentlichen Skalenniveau. Genauso könnte man "Mann" mit `1` und "Frau" mit `2` kodieren; ein Mittelwert bliebe genauso (wenig) aussagekräftig. Zu beachten ist hier nur, dass sich manche R-Befehle verunsichern lassen, wenn nominale Variablen mit Zahlen kodiert sind. Daher ist es oft besser, nominale Variablen mit Text-Werten zu benennen (wie "survived" vs. "drowned" etc.). Wir kommen später auf diesen Punkt zurück.

### Univariate Häufigkeiten
Bevor wir uns in kompliziertere Fragestellungen stürzen, halten wir fest: Wir untersuchen zwei nominale Variablen. Sprich: wir werden Häufigkeiten auszählen. Häufigkeiten (und relative Häufigkeiten, also Anteile oder Quoten) sind das, was uns hier beschäftigt.

Zählen wir zuerst die univariaten Häufigkeiten aus: Wie viele Passagiere gab es pro Klasse? Wie viele Passagiere gab es pro Wert von `Survived` (also die überlebten bzw. nicht überlebten)?


```r
c1 <- dplyr::count(titanic_train, Pclass)
c1
#> # A tibble: 3 × 2
#>   Pclass     n
#>    <int> <int>
#> 1      1   216
#> 2      2   184
#> 3      3   491
```


\BeginKnitrBlock{rmdcaution}<div class="rmdcaution">Achtung - Namenskollision! Sowohl im Paket `mosaic` als auch im Paket `dplyr` gibt es einen Befehl `count`. Für `select` gilt das gleiche. Das arme R weiß nicht, welchen von beiden wir meinen und entscheidet sich im Zweifel für den falschen. Da hilft, zu sagen, aus welchem Paket wir den Befehl beziehen wollen. Das macht der Operator `::`.
</div>\EndKnitrBlock{rmdcaution}


Aha. Zur besseren Anschaulichkeit können wir das auch plotten (ein Diagramm dazu malen). 


```r
# install.packages("ggplot2", dependencies = TRUE)
library(ggplot2)
qplot(x = Pclass, y = n, data = c1)
```

<img src="075_Fallstudie_Titanic_files/figure-html/plot-titanic1-1.png" width="70%" style="display: block; margin: auto;" />

Der Befehl `qplot` zeichnet automatisch Punkte, wenn auf beiden Achsen "Zahlen-Variablen" stehen (also Variablen, die keinen "Text", sondern nur Zahlen beinhalten. In R sind das Variablen vom Typ `int` (integer), also Ganze Zahlen oder vom Typ `num` (numeric), also reelle Zahlen).


```r

c2 <- dplyr::count(titanic_train, Survived)
c2
#> # A tibble: 2 × 2
#>   Survived     n
#>      <int> <int>
#> 1        0   549
#> 2        1   342
```

Man beachte, dass der Befehl `count` stehts eine Tabelle (data.frame bzw. `tibble`) verlangt und zurückliefert.


### Bivariate Häufigkeiten
OK, gut. Jetzt wissen wir die Häufigkeiten pro Wert von `Survived` (dasselbe gilt für `Pclass`). Eigentlich interessiert uns aber die Frage, ob sich die relativen Häufigkeiten der Stufen von `Pclass` innerhalb der Stufen von `Survived` unterscheiden. Einfacher gesagt: Ist der Anteil der Überlebenden in der 1. Klasse größer als in der 3. Klasse?

Zählen wir zuerst die Häufigkeiten für alle Kombinationen von `Survived` und `Pclass`:
  

```r
c3 <- dplyr::count(titanic_train, Survived, Pclass)
c3
#> Source: local data frame [6 x 3]
#> Groups: Survived [?]
#> 
#>   Survived Pclass     n
#>      <int>  <int> <int>
#> 1        0      1    80
#> 2        0      2    97
#> 3        0      3   372
#> 4        1      1   136
#> 5        1      2    87
#> 6        1      3   119
```

Da `Pclass` 3 Stufen hat (1., 2. und 3. Klasse) und innerhalb jeder dieser 3 Klassen es die Gruppe der Überlebenden und der Nicht-Überlebenden gibt, haben wir insgesamt 3*2=6 Gruppen.

Es ist hilfreich, sich diese Häufigkeiten wiederum zu plotten; wir nehmen den gleichen Befehl wie oben.


```r
qplot(x = Pclass, y = n, data = c3)
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-5-1.png" width="70%" style="display: block; margin: auto;" />

Hm, nicht so hilfreich. Schöner wäre, wenn wir (farblich) erkennen könnten, welcher Punkt für "Überlebt" und welcher Punkt für "Nicht-Überlebt" steht. Mit `qplot` geht das recht einfach: Wir sagen der Funktion `qplot`, dass die Farbe (`color`) der Punkte den Stufen von `Survived` zugeordnet werden sollen:
  

```r
qplot(x = Pclass, y = n, color = Survived, data = c3)
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-6-1.png" width="70%" style="display: block; margin: auto;" />

Viel besser. Was noch stört, ist, dass `Survived` als metrische Variable verstanden wird. Das Farbschema lässt Nuancen, feine Farbschattierungen, zu. Für nominale Variablen macht das keinen Sinn; es gibt da keine Zwischentöne. Tot ist tot, lebendig ist lebendig. Wir sollten daher der Funktion sagen, dass es sich um nominale Variablen handelt:
  

```r
qplot(x = factor(Pclass), y = n, color = factor(Survived), data = c3)
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-7-1.png" width="70%" style="display: block; margin: auto;" />

Viel besser. Jetzt noch ein bisschen Schnickschnack:
  
  

```r
qplot(x = factor(Pclass), y = n, color = factor(Survived), data = c3) + 
  labs(x = "Klasse", 
       title = "Überleben auf der Titanic",
       colour = "Überlebt?")
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-8-1.png" width="70%" style="display: block; margin: auto;" />


### Signifikanztest

Manche Leute mögen Signifikanztests. Ich persönlich stehe ihnen kritisch gegenüber, da ein p-Wert eine Funktion der Stichprobengröße ist und außerdem zumeist missverstanden wird (er gibt *nicht* die Wahrscheinlichkeit der getesteten Hypothese an, was die Frage aufwirft, warum er mich dann interessieren sollte). Aber seisdrum, berechnen wir mal einen p-Wert. Es gibt mehrere statistische Tests, die sich hier potenziell anböten (was die Frage nach der Objektivität von statistischen Tests in ein ungünstiges Licht rückt). Nehmen wir den $\chi^2$-Test.


```r
chisq.test(titanic_train$Survived, titanic_train$Pclass)
#> 
#> 	Pearson's Chi-squared test
#> 
#> data:  titanic_train$Survived and titanic_train$Pclass
#> X-squared = 100, df = 2, p-value <2e-16
```

Der p-Wert ist kleiner als 5%, daher entscheiden wir uns, entsprechend der üblichen Gepflogenheit, gegen die H0 und für die H1: "Es gibt einen Zusammenhang von Überlebensrate und Passagierklasse".


### Effektstärke
Abgesehen von der Signifikanz, und interessanter, ist die Frage, wie sehr die Variablen zusammenhängen. Für Häufigkeitsanalysen mit 2*2-Feldern bietet sich das "Odds Ratio" (OR), das Chancenverhältnis an. Das Chancen-Verhältnis beantwortet die Frage: "Um welchen Faktor ist die Überlebenschance in der einen Klasse größer als in der anderen Klasse?". Eine interessante Frage, als schauen wir es uns an. 

Das OR ist nur definiert für 2*2-Häufigkeitstabellen, daher müssen wir die Anzahl der Passagierklassen von 3 auf 2 verringern. Nehmen wir nur 1. und 3. Klasse, um den vermuteten Effekt deutlich herauszuschälen:
  

```r
t2 <- filter(titanic_train, Pclass != 2)  # "!=" heißt "nicht"
```

Alternativ (synonym) könnten wir auch schreiben:
  

```r
t2 <- filter(titanic_train, Pclass == 1 | Pclass == 3)  # "|" heißt "oder"
```

Und dann zählen wir wieder die Häufigkeiten aus pro Gruppe:
  

```r
c4 <- dplyr::count(t2, Pclass)
c4
#> # A tibble: 2 × 2
#>   Pclass     n
#>    <int> <int>
#> 1      1   216
#> 2      3   491
```


Schauen wir nochmal den p-Wert an, da wir jetzt ja mit einer veränderten Datentabelle operieren:
  

```r
chisq.test(t2$Survived, t2$Pclass)
#> 
#> 	Pearson's Chi-squared test with Yates' continuity correction
#> 
#> data:  t2$Survived and t2$Pclass
#> X-squared = 100, df = 1, p-value <2e-16
```

Ein $\chi^2$-Wert von ~96 bei einem *n* von 707.

Dann berechnen wir die Effektstärke (OR) mit dem Paket `compute.es` (muss ebenfalls installiert sein).

```r
library(compute.es)
chies(chi.sq = 96, n = 707)
#> Mean Differences ES: 
#>  
#>  d [ 95 %CI] = 0.79 [ 0.63 , 0.95 ] 
#>   var(d) = 0.01 
#>   p-value(d) = 0 
#>   U3(d) = 78.6 % 
#>   CLES(d) = 71.2 % 
#>   Cliff's Delta = 0.42 
#>  
#>  g [ 95 %CI] = 0.79 [ 0.63 , 0.95 ] 
#>   var(g) = 0.01 
#>   p-value(g) = 0 
#>   U3(g) = 78.6 % 
#>   CLES(g) = 71.2 % 
#>  
#>  Correlation ES: 
#>  
#>  r [ 95 %CI] = 0.37 [ 0.3 , 0.43 ] 
#>   var(r) = 0 
#>   p-value(r) = 0 
#>  
#>  z [ 95 %CI] = 0.39 [ 0.31 , 0.46 ] 
#>   var(z) = 0 
#>   p-value(z) = 0 
#>  
#>  Odds Ratio ES: 
#>  
#>  OR [ 95 %CI] = 4.21 [ 3.15 , 5.61 ] 
#>   p-value(OR) = 0 
#>  
#>  Log OR [ 95 %CI] = 1.44 [ 1.15 , 1.73 ] 
#>   var(lOR) = 0.02 
#>   p-value(Log OR) = 0 
#>  
#>  Other: 
#>  
#>  NNT = 3.57 
#>  Total N = 707
```

Die Chance zu überleben ist also in der 1. Klasse mehr als 4 mal so hoch wie in der 3. Klasse. Es scheint: Money buys you live...


### Logististische Regression
Berechnen wir noch das Odds Ratio mit Hilfe der logistischen Regression. Zum Einstieg: Ignorieren Sie die folgende Syntax und schauen Sie sich das Diagramm an. Hier sehen wir die (geschätzten) Überlebens-Wahrscheinlichkeiten für Passagiere der 1. Klasse vs. Passagiere der 3. Klasse.


```r
titanic2 <- titanic_train %>% 
  filter(Pclass %in% c(1,3)) %>% 
  mutate(Pclass = factor(Pclass))

glm1 <- glm(data = titanic2, 
            formula = Survived ~ Pclass, 
            family = "binomial")

exp(coef(glm1))
#> (Intercept)     Pclass3 
#>       1.700       0.188

titanic2$pred_prob <- predict(glm1, type = "response")
```


<img src="075_Fallstudie_Titanic_files/figure-html/fig-titanic-1.png" width="70%" style="display: block; margin: auto;" />

Wir sehen, dass die Überlebens-Wahrscheinlichkeit in der 1. Klasse höher ist als in der 3. Klasse. Optisch grob geschätzt, ~60% in der 1. Klasse und ~25% in der 3. Klasse.

Schauen wir uns die logistische Regression an: Zuerst haben wir den Datensatz auf die Zeilen beschränkt, in denen Personen aus der 1. und 3. Klasse vermerkt sind (zwecks Vergleichbarkeit zu oben). Dann haben wir mit `glm` und `family = "binomial"` eine *logistische* Regression angefordert. Man beachte, dass der Befehl sehr ähnlich zur normalen Regression (`lm(...)`) ist.

Da die Koeffizienten in der Logit-Form zurückgegeben werden, haben wir sie mit der Exponential-Funktion in die "normale" Odds-Form gebracht (delogarithmiert, boa). Wir sehen, dass die Überlebens-*Chance* (Odds) 1.7 zu 1 betrug - bei der *ersten* Stufe von `Pclass` (`1`)^[Darum haben wir `Pclass` in eine Faktor-Variable umgewandelt. Die "erste Klasse" ist jetzt die Referenzklasse, also sozusagen x = 0. Hätten wir `Pclass` als numerische Variable beibehalten, so würde der Achsenabschnitt die Überlebensrat für die "nullte" Klasse geben, was wenig Sinn macht.]; von 27 Menschen überlebten in dieser Gruppe also 17 (17/27 = .63 Überlebens-*Wahrscheinlichkeit*); s. `Intercept`; der Achsenabschnitt gibt den Odds an, wenn die Prädiktor-Variable(n) den Wert "Null" hat/ haben, bzw. die erste Ausprägung, hier 1. 

Im Vergleich dazu wird die Überlebens-Chance deutlich schlechter, wenn man die nächste Gruppe von `Pclass` (3) betrachtet. Die Odds verändern sich um den Faktor ~0.2. Da der Faktor *kleiner* als 1 ist, ist das kein gutes Zeichen. Die Überlebens-Chance *sinkt*; etwas genauer auf: 1.7 * 0.2 ≈ 0.34. Das heißt, die Überlebens-Chance ist in der 3. Klasse nur noch ca. 1 zu 3 (Überlebens-Wahrscheinlichkeit: ~25%).

Komfortabler können wir uns die Überlebens-*Wahrscheinlichkeiten* mit der Funktion `predict` ausgeben lassen.


```r
predict(glm1, newdata = data.frame(Pclass = factor("1")), type = "response")
#>    1 
#> 0.63
predict(glm1, newdata = data.frame(Pclass = factor("3")), type = "response")
#>     1 
#> 0.242
```

Alternativ kann man die Häufigkeiten auch noch "per Hand" bestimmen: 
  

```r
titanic_train %>% 
  filter(Pclass %in% c(1,3)) %>% 
  dplyr::select(Survived, Pclass) %>% 
  group_by(Pclass, Survived) %>% 
  summarise(n = n() ) %>% 
  mutate(Anteil = n / sum(n))
#> Source: local data frame [4 x 4]
#> Groups: Pclass [2]
#> 
#>   Pclass Survived     n Anteil
#>    <int>    <int> <int>  <dbl>
#> 1      1        0    80  0.370
#> 2      1        1   136  0.630
#> 3      3        0   372  0.758
#> 4      3        1   119  0.242
```


Übersetzen wir dies Syntax auf Deutsch:


\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Nehme den Datensatz "titanic_train" UND DANN  
Filtere nur die 1. und die 3. Klasse heraus UND DANN  
wähle nur die Spalten "Survived" und "Pclass" UND DANN  
gruppiere nach "Pclass" und "Survived" UND DANN  
zähle die Häufigkeiten für jede dieser Gruppen aus UND DANN  
berechne den Anteil an Überlebenden bzw. Nicht-Überlebenden  
für jede der beiden Passagierklassen. FERTIG.  
 
</div>\EndKnitrBlock{rmdpseudocode}


   



### Effektstärken visualieren
Zum Abschluss schauen wir uns die Stärke des Zusammenhangs noch einmal graphisch an. Wir berechnen dafür die relativen Häufigkeiten pro Gruppe (im Datensatz ohne 2. Klasse, der Einfachheit halber).


```r
c5 <- dplyr::count(t2, Pclass, Survived)
c5$prop <- c5$n / 707
c5
#> Source: local data frame [4 x 4]
#> Groups: Pclass [?]
#> 
#>   Pclass Survived     n  prop
#>    <int>    <int> <int> <dbl>
#> 1      1        0    80 0.113
#> 2      1        1   136 0.192
#> 3      3        0   372 0.526
#> 4      3        1   119 0.168
```

Genauer gesagt haben die Häufigkeiten pro Gruppe in Bezug auf die Gesamtzahl aller Passagiere berechnet; die vier Anteile addieren sich also zu 1 auf. 

Das visualisieren wir wieder


```r
qplot(x = factor(Pclass), y = prop, fill = factor(Survived), data = c5, geom = "col")
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-11-1.png" width="70%" style="display: block; margin: auto;" />

Das `geom = "col"` heißt, dass als "geometrisches Objekt" dieses Mal keine Punkte, sondern Säulen (columns) verwendet werden sollen.


```r
qplot(x = factor(Pclass), y = prop, fill = factor(Survived), data = c5, geom = "col")
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-12-1.png" width="70%" style="display: block; margin: auto;" />

Ganz nett, aber die Häufigkeitsunterscheide von `Survived` zwischen den beiden Werten von `Pclass` stechen noch nicht so ins Auge. Wir sollten es anders darstellen.

Hier kommt der Punkt, wo wir von `qplot` auf seinen großen Bruder, `ggplot` wechseln sollten. `qplot` ist in Wirklichkeit nur eine vereinfachte Form von `ggplot`; die Einfachheit wird mit geringeren Möglichkeiten bezahlt. Satteln wir zum Schluss dieser Fallstudie also um:
  

```r
ggplot(data = c5) +
  aes(x = factor(Pclass), y = n, fill = factor(Survived)) + 
  geom_col(position = "fill") +
  labs(x = "Passagierklasse", fill = "Überlebt?", caption = "Nur Passagiere, keine Besatzung")
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-13-1.png" width="70%" style="display: block; margin: auto;" />

Jeden sehen wir die Häufigkeiten des Überlebens bedingt auf die Passagierklasse besser. Wir sehen auf den ersten Blick, dass sich die Überlebensraten deutlich unterscheiden: Im linken Balken überleben die meisten; im rechten Balken ertrinken die meisten. 

Diese letzte Analyse zeigt deutlich die Kraft von (Daten-)Visualisierungen auf. Der zu untersuchende Effekt tritt hier am stärken zu Tage; außerdem ist die Analyse relativ einfach.

Eine alternative Darstellung ist diese:
  

```r
c5 %>% 
  ggplot +
  aes(x = factor(Pclass), y = factor(Survived), fill = n) +
  geom_tile()
```

<img src="075_Fallstudie_Titanic_files/figure-html/unnamed-chunk-14-1.png" width="70%" style="display: block; margin: auto;" />

Hier werden die vier "Fliesen" gleich groß dargestellt; die Fallzahl wird durch die Füllfarbe besorgt.


### Fazit
In der Datenanalyse (mit R) kommt man mit wenigen Befehlen schon sehr weit; `dplyr` und `ggplot2` zählen (zu Recht) zu den am häufigsten verwendeten Paketen. Beide sind flexibel, konsistent und spielen gerne miteinander. Die besten Einblicke haben wir aus deskriptiver bzw. explorativer Analyse (Diagramme) gewonnen. Signifikanztests oder komplizierte Modelle waren nicht zentral. In vielen Studien/Projekten der Datenanalyse gilt ähnliches: Daten umformen und verstehen bzw. "veranschaulichen" sind zentrale Punkte, die häufig viel Zeit und Wissen fordern. Bei der Analyse von nominalskalierten sind Häufigkeitsauswertungen ideal.







<!--chapter:end:075_Fallstudie_Titanic.Rmd-->




## Außereheliche Affären

Wovon ist die Häufigkeit von Affären (Seitensprüngen) in Ehen abhängig? Diese Frage soll anhand des Datensates `Affair` untersucht werden.

Quelle: <http://statsmodels.sourceforge.net/0.5.0/datasets/generated/fair.html>

Der Datensatz findet sich (in ähnlicher Form) auch im R-Paket `COUNT` (https://cran.r-project.org/web/packages/COUNT/index.html).

Laden wir als erstes den Datensatz in R. Wählen Sie zuerst das Verzeichnis als Arbeitsverzeichnis, in dem die Daten liegen. Dann laden Sie z.B. mit dem R-Commander (s. Skript) oder "per Hand" z.B. bei mir so:


```r
Affair <- read.csv("data/Affairs.csv")
```

Schauen wir mal, ob es funktioniert hat ("Datenmatrix betrachten"):


```r
head(Affair)
#>   X affairs gender age yearsmarried children religiousness education
#> 1 1       0   male  37        10.00       no             3        18
#> 2 2       0 female  27         4.00       no             4        14
#> 3 3       0 female  32        15.00      yes             1        12
#> 4 4       0   male  57        15.00      yes             5        18
#> 5 5       0   male  22         0.75       no             2        17
#> 6 6       0 female  32         1.50       no             2        17
#>   occupation rating
#> 1          7      4
#> 2          6      4
#> 3          1      4
#> 4          6      5
#> 5          6      3
#> 6          5      5
```


Ok scheint zu passen. Was jetzt?


### Zentrale Statistiken

Geben Sie zentrale deskriptive Statistiken an für Affärenhäufigkeit und Ehezufriedenheit!


```r
# nicht robust:
mean(Affair$affairs, na.rm = T)
#> [1] 1.46
sd(Affair$affairs, na.rm = T)
#> [1] 3.3
# robust:
median(Affair$affair, na.rm = T)
#> [1] 0
IQR(Affair$affair, na.rm = T)
#> [1] 0
```

Es scheint, die meisten Leute haben keine Affären:


```r
table(Affair$affairs)
#> 
#>   0   1   2   3   7  12 
#> 451  34  17  19  42  38
```


Man kann sich viele Statistiken mit dem Befehl `describe` aus `psych` ausgeben lassen, das ist etwas praktischer:


```r
library(psych)
                 
describe(Affair$affairs)
#>    vars   n mean  sd median trimmed mad min max range skew kurtosis   se
#> X1    1 601 1.46 3.3      0    0.55   0   0  12    12 2.34     4.19 0.13
describe(Affair$rating)
#>    vars   n mean  sd median trimmed  mad min max range  skew kurtosis   se
#> X1    1 601 3.93 1.1      4    4.07 1.48   1   5     4 -0.83    -0.22 0.04
```

Dazu muss das Paket `psych` natürlich vorher installiert sein. Beachten Sie, dass man ein Paket nur *einmal* installieren muss, aber jedes Mal, wenn Sie R starten, auch starten muss (mit `library`).


```r
install.packages("psych")
```


### Visualisieren

Visualisieren Sie zentrale Variablen!

Sicherlich sind Diagramme auch hilfreich. Dies geht wiederum mit dem R-Commander oder z.B. mit folgenden Befehlen:


```r

library(ggplot2)
qplot(x = affairs, data = Affair)
qplot(x = rating, data = Affair)
```

<img src="076_Fallstudie_Affairs_files/figure-html/unnamed-chunk-8-1.png" width="70%" style="display: block; margin: auto;" /><img src="076_Fallstudie_Affairs_files/figure-html/unnamed-chunk-8-2.png" width="70%" style="display: block; margin: auto;" />

Die meisten Menschen (dieser Stichprobe) scheinen mit Ihrer Beziehung sehr zufrieden zu sein.


### Wer ist zufriedener mit der Partnerschaft: Personen mit Kindern oder ohne?

Nehmen wir dazu mal ein paar `dplyr`-Befehle:


```r
library(dplyr)
Affair %>% 
  group_by(children) %>% 
  summarise(rating_children = mean(rating, na.rm = T))
#> # A tibble: 2 × 2
#>   children rating_children
#>     <fctr>           <dbl>
#> 1       no            4.27
#> 2      yes            3.80
```

Ah! Kinder sind also ein Risikofaktor für eine Partnerschaft! Gut, dass wir das geklärt haben.

### Wie viele fehlende Werte gibt es? 

Was machen wir am besten damit?

Diesen Befehl könnten wir für jede Spalte auführen:


```r
sum(is.na(Affair$affairs))
#> [1] 0
```

Oder lieber alle auf einmal:


```r
Affair %>% 
  summarise_each(funs(sum(is.na(.))))
#>   X affairs gender age yearsmarried children religiousness education
#> 1 0       0      0   0            0        0             0         0
#>   occupation rating
#> 1          0      0
```


Übrigens gibt es ein gutes [Cheat Sheet](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf) für `dplyr`.

Ah, gut, keine fehlenden Werte. Das macht uns das Leben leichter.


### Wer ist glücklicher: Männer oder Frauen?


```r
Affair %>% 
  group_by(gender) %>% 
  summarise(rating_gender = mean(rating))
#> # A tibble: 2 × 2
#>   gender rating_gender
#>   <fctr>         <dbl>
#> 1 female          3.94
#> 2   male          3.92
```

Praktisch kein Unterschied. Heißt das auch, es gibt keinen Unterschied in der Häufigkeit der Affären?


```r
Affair %>% 
  group_by(gender) %>% 
  summarise(affairs_gender = mean(affairs))
#> # A tibble: 2 × 2
#>   gender affairs_gender
#>   <fctr>          <dbl>
#> 1 female           1.42
#> 2   male           1.50
```

Scheint auch kein Unterschied zu sein...

Und zum Abschluss noch mal etwas genauer: Teilen wir mal nach Geschlecht und nach Kinderstatus auf, also in 4 Gruppen. Theoretisch dürfte es hier auch keine Unterschiede/Zusammenhänge geben. Zumindest fällt mir kein sinnvoller Grund ein; zumal die vorherige eindimensionale Analyse keine Unterschiede zu Tage gefördert hat.



```r
Affair %>% 
  group_by(gender, children) %>% 
  summarise(affairs_mean = mean(affairs),
            rating_mean = mean(rating))
#> Source: local data frame [4 x 4]
#> Groups: gender [?]
#> 
#>   gender children affairs_mean rating_mean
#>   <fctr>   <fctr>        <dbl>       <dbl>
#> 1 female       no        0.838        4.40
#> 2 female      yes        1.685        3.73
#> 3   male       no        1.014        4.10
#> 4   male      yes        1.659        3.86

Affair %>% 
  group_by(children, gender) %>% 
  summarise(affairs_mean = mean(affairs),
            rating_mean = mean(rating))
#> Source: local data frame [4 x 4]
#> Groups: children [?]
#> 
#>   children gender affairs_mean rating_mean
#>     <fctr> <fctr>        <dbl>       <dbl>
#> 1       no female        0.838        4.40
#> 2       no   male        1.014        4.10
#> 3      yes female        1.685        3.73
#> 4      yes   male        1.659        3.86
```


### Effektstärken

Berichten Sie eine relevante Effektstärke!

Hm, auch keine gewaltigen Unterschiede. Höchstens für die Zufriedenheit mit der Partnerschaft bei kinderlosen Personen scheinen sich Männer und Frauen etwas zu unterscheiden. Hier stellt sich die Frage nach der Größe des Effekts, z.B. anhand Cohen's d. Dafür müssen wir noch die SD pro Gruppe wissen:



```r
Affair %>% 
  group_by(children, gender) %>% 
  summarise(rating_mean = mean(rating),
            rating_sd = sd(rating))
#> Source: local data frame [4 x 4]
#> Groups: children [?]
#> 
#>   children gender rating_mean rating_sd
#>     <fctr> <fctr>       <dbl>     <dbl>
#> 1       no female        4.40     0.914
#> 2       no   male        4.10     1.064
#> 3      yes female        3.73     1.183
#> 4      yes   male        3.86     1.046
```



```r
d <- (4.4 - 4.1)/(1)
```

Die Effektstärke beträgt etwa 0.3.


### Korrelationen

Berechnen und visualisieren Sie zentrale Korrelationen!


```r
Affair %>% 
  select_if(is.numeric) %>% 
  cor -> cor_tab

cor_tab
#>                     X  affairs     age yearsmarried religiousness
#> X              1.0000  0.57692  0.0362       0.1078       -0.1164
#> affairs        0.5769  1.00000  0.0952       0.1868       -0.1445
#> age            0.0362  0.09524  1.0000       0.7775        0.1938
#> yearsmarried   0.1078  0.18684  0.7775       1.0000        0.2183
#> religiousness -0.1164 -0.14450  0.1938       0.2183        1.0000
#> education     -0.0537 -0.00244  0.1346       0.0400       -0.0426
#> occupation    -0.0691  0.04961  0.1664       0.0446       -0.0397
#> rating        -0.1951 -0.27951 -0.1990      -0.2431        0.0243
#>               education occupation  rating
#> X              -0.05371    -0.0691 -0.1951
#> affairs        -0.00244     0.0496 -0.2795
#> age             0.13460     0.1664 -0.1990
#> yearsmarried    0.04000     0.0446 -0.2431
#> religiousness  -0.04257    -0.0397  0.0243
#> education       1.00000     0.5336  0.1093
#> occupation      0.53361     1.0000  0.0174
#> rating          0.10930     0.0174  1.0000

library(corrplot)
corrplot(cor_tab)
```

<img src="076_Fallstudie_Affairs_files/figure-html/unnamed-chunk-17-1.png" width="70%" style="display: block; margin: auto;" />



### Ehejahre und Affären

Wie groß ist der Einfluss (das Einflussgewicht) der Ehejahre bzw. Ehezufriedenheit auf die Anzahl der Affären?

Dazu sagen wir R: "Hey R, rechne mal ein lineares Modell", also eine normale 
(lineare) Regression. Dazu können wir entweder das entsprechende Menü im R-Commander auswählen, oder folgende R-Befehle ausführen:


```r
lm1 <- lm(affairs ~ yearsmarried, data = Affair)
summary(lm1)  # Ergebnisse der Regression zeigen
#> 
#> Call:
#> lm(formula = affairs ~ yearsmarried, data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -2.211 -1.658 -0.994 -0.597 11.366 
#> 
#> Coefficients:
#>              Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    0.5512     0.2351    2.34    0.019 *  
#> yearsmarried   0.1106     0.0238    4.65    4e-06 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.24 on 599 degrees of freedom
#> Multiple R-squared:  0.0349,	Adjusted R-squared:  0.0333 
#> F-statistic: 21.7 on 1 and 599 DF,  p-value: 4e-06
lm2 <- lm(affairs ~ rating, data = Affair)
summary(lm2)
#> 
#> Call:
#> lm(formula = affairs ~ rating, data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -3.906 -1.399 -0.563 -0.563 11.437 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    4.742      0.479    9.90   <2e-16 ***
#> rating        -0.836      0.117   -7.12    3e-12 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.17 on 599 degrees of freedom
#> Multiple R-squared:  0.0781,	Adjusted R-squared:  0.0766 
#> F-statistic: 50.8 on 1 and 599 DF,  p-value: 3e-12
```

Also: `yearsmarried` und `rating` sind beide statistisch signifikante Prädiktoren für die Häufigkeit von Affären. Das adjustierte $R^2$ ist allerdings in beiden Fällen nicht so groß.

### Ehezufriedenheit als Prädiktor

Um wie viel erhöht sich die erklärte Varianz (R-Quadrat) von Affärenhäufigkeit wenn man den Prädiktor Ehezufriedenheit zum Prädiktor Ehejahre hinzufügt? (Wie) verändern sich die Einflussgewichte (b)?


```r
lm3 <- lm(affairs ~ rating + yearsmarried, data = Affair)
lm4 <- lm(affairs ~ yearsmarried + rating, data = Affair)
summary(lm3)
#> 
#> Call:
#> lm(formula = affairs ~ rating + yearsmarried, data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -4.147 -1.650 -0.837 -0.162 11.894 
#> 
#> Coefficients:
#>              Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    3.7691     0.5671    6.65  6.8e-11 ***
#> rating        -0.7439     0.1200   -6.20  1.1e-09 ***
#> yearsmarried   0.0748     0.0238    3.15   0.0017 ** 
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.15 on 598 degrees of freedom
#> Multiple R-squared:  0.0931,	Adjusted R-squared:  0.0901 
#> F-statistic: 30.7 on 2 and 598 DF,  p-value: 2.01e-13
summary(lm4)
#> 
#> Call:
#> lm(formula = affairs ~ yearsmarried + rating, data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -4.147 -1.650 -0.837 -0.162 11.894 
#> 
#> Coefficients:
#>              Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    3.7691     0.5671    6.65  6.8e-11 ***
#> yearsmarried   0.0748     0.0238    3.15   0.0017 ** 
#> rating        -0.7439     0.1200   -6.20  1.1e-09 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.15 on 598 degrees of freedom
#> Multiple R-squared:  0.0931,	Adjusted R-squared:  0.0901 
#> F-statistic: 30.7 on 2 and 598 DF,  p-value: 2.01e-13
```

Ok. Macht eigentlich die Reihenfolge der Prädiktoren in der Regression einen 
Unterschied? Der Vergleich von Modell 3 vs. Modell 4 beantwortet diese Frage.




Wir sehen, dass beim 1. Regressionsmodell das R^2 0.03 war; beim 2. Modell 0.08 und beim 3. Modell liegt R^2 bei 0.09. Die Differenz zwischen Modell 1 und 3 liegt bei (gerundet) 0.06; wenig.
  
  




### Weitere Prädiktoren der Affärenhäufigkeit

Welche Prädiktoren würden Sie noch in die Regressionsanalyse aufnehmen?

Hm, diese Frage klingt nicht so, als ob der Dozent die Antwort selber wüsste... Naja, welche Variablen gibt es denn alles:


```
#>  [1] "X"             "affairs"       "gender"        "age"          
#>  [5] "yearsmarried"  "children"      "religiousness" "education"    
#>  [9] "occupation"    "rating"
```

Z.B. wäre doch interessant, ob Ehen mit Kinder mehr oder weniger Seitensprüngen aufweisen. Und ob die "Kinderfrage" die anderen Zusammenhänge/Einflussgewichte in der Regression verändert. Probieren wir es auch. Wir können wiederum im R-Comamnder ein Regressionsmodell anfordern oder es mit der Syntax probieren:


```r
lm5 <- lm(affairs~ rating + yearsmarried + children, data = Affair)
summary(lm5)
#> 
#> Call:
#> lm(formula = affairs ~ rating + yearsmarried + children, data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -4.354 -1.732 -0.893 -0.172 12.016 
#> 
#> Coefficients:
#>              Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    3.8524     0.5881    6.55  1.2e-10 ***
#> rating        -0.7486     0.1204   -6.22  9.6e-10 ***
#> yearsmarried   0.0833     0.0285    2.92   0.0036 ** 
#> childrenyes   -0.1881     0.3482   -0.54   0.5893    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.15 on 597 degrees of freedom
#> Multiple R-squared:  0.0936,	Adjusted R-squared:  0.089 
#> F-statistic: 20.5 on 3 and 597 DF,  p-value: 1.11e-12
r2_lm5 <- summary(lm5)$r.squared
```

Das Regressionsgewicht von `childrenyes` ist negativ. Das bedeutet, dass Ehen mit Kindern weniger Affären verbuchen (aber geringe Zufriedenheit, wie wir oben gesehen haben! Hrks!). Allerdings ist der p-Wert nich signifikant, was wir als Zeichen der Unbedeutsamkeit dieses Prädiktors verstehen können. $R^2$ lungert immer noch bei mickrigen 0.094 herum. Wir haben bisher kaum verstanden, wie es zu Affären kommt. Oder unsere Daten bergen diese Informationen einfach nicht.

Wir könnten auch einfach mal Prädiktoren, die wir haben, ins Feld schicken. Mal sehen, was dann passiert:


```r
lm6 <- lm(affairs ~ ., data = Affair)
summary(lm6)
#> 
#> Call:
#> lm(formula = affairs ~ ., data = Affair)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -5.162 -1.644 -0.484  1.016  9.509 
#> 
#> Coefficients:
#>                Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    0.612898   1.008088    0.61  0.54343    
#> X              0.010085   0.000634   15.92  < 2e-16 ***
#> gendermale    -0.222695   0.252198   -0.88  0.37759    
#> age           -0.029519   0.018987   -1.55  0.12054    
#> yearsmarried   0.120077   0.034656    3.46  0.00057 ***
#> childrenyes   -0.357956   0.293529   -1.22  0.22314    
#> religiousness -0.272637   0.094432   -2.89  0.00403 ** 
#> education      0.001544   0.053711    0.03  0.97708    
#> occupation     0.182340   0.074579    2.44  0.01478 *  
#> rating        -0.456198   0.101757   -4.48  8.8e-06 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 2.59 on 591 degrees of freedom
#> Multiple R-squared:  0.392,	Adjusted R-squared:  0.383 
#> F-statistic: 42.4 on 9 and 591 DF,  p-value: <2e-16
r2_lm6 <- round(summary(lm6)$r.squared, 2)
```

Der "." im Befehl `affairs ~ .` oben soll sagen: nimm "alle Variablen, die noch in der Datenmatrix übrig sind".

Insgesamt bleibt die erklärte Varian in sehr bescheidenem Rahmen: 0.39. Das zeigt uns, dass es immer noch nur schlecht verstanden ist -- im Rahmen dieser Analyse -- welche Faktoren die Affärenhäufigkeit erklärt.

### Unterschied zwischen den Geschlechtern

Unterscheiden sich die Geschlechter statistisch signifikant? Wie groß ist der Unterschied? Sollte hierlieber das d-Maß oder Rohwerte als Effektmaß  angegeben werden?

Hier bietet sich ein t-Test für unabhängige Gruppen an. Die Frage lässt auf eine ungerichtete Hypothese schließen ($\alpha$ sei .05). Mit dem entsprechenden Menüpunkt im R-Commander oder mit folgender Syntax lässt sich diese Analyse angehen:


```r
t1 <- t.test(affairs ~ gender, data = Affair)
t1
#> 
#> 	Welch Two Sample t-test
#> 
#> data:  affairs by gender
#> t = -0.3, df = 600, p-value = 0.8
#> alternative hypothesis: true difference in means is not equal to 0
#> 95 percent confidence interval:
#>  -0.607  0.452
#> sample estimates:
#> mean in group female   mean in group male 
#>                 1.42                 1.50
```


Der p-Wert ist mit 0.774 > $\alpha$. Daher wird die $H_0$ beibehalten. Auf Basis der Stichprobendaten entscheiden wir uns für die $H_0$. Entsprechend umschließt das 95%-KI die Null.

Da die Differenz nicht signifikant ist, kann argumentiert werden, dass wir `d` auf 0 schätzen müssen. Man kann sich den d-Wert auch z.B. von {MBESS} schätzen lassen.

Dafür brauchen wir die Anzahl an Männer und Frauen: 315, 286.



```r
library(MBESS)
ci.smd(ncp = t1$statistic,
    n.1 = 315,
    n.2 = 286)
#> $Lower.Conf.Limit.smd
#> [1] -0.184
#> 
#> $smd
#>       t 
#> -0.0235 
#> 
#> $Upper.Conf.Limit.smd
#> [1] 0.137
```

Das Konfidenzintervall ist zwar relativ klein (die Schätzung also aufgrund der recht großen Stichprobe relativ präzise), aber der Schätzwert für d `smd` liegt sehr nahe bei Null. Das stärkt unsere Entscheidung, von einer Gleichheit der Populationen (Männer vs. Frauen) auszugehen.

### Kinderlose Ehe vs. Ehen mit Kindern

Rechnen Sie die Regressionsanalyse getrennt für kinderlose Ehe und Ehen mit Kindern!

Hier geht es im ersten Schritt darum, die entsprechenden Teil-Mengen der Datenmatrix zu erstellen. Das kann man natürlich mit Excel o.ä. tun. Alternativ könnte man es in R z.B. so machen:


```r
Affair2 <- Affair[Affair$children == "yes", ]
lm7 <- lm(affairs~ rating, data = Affair2)
summary(lm7)
#> 
#> Call:
#> lm(formula = affairs ~ rating, data = Affair2)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#> -4.190 -1.488 -0.587 -0.488 11.413 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    5.091      0.570    8.93  < 2e-16 ***
#> rating        -0.901      0.144   -6.25  9.8e-10 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 3.34 on 428 degrees of freedom
#> Multiple R-squared:  0.0837,	Adjusted R-squared:  0.0815 
#> F-statistic: 39.1 on 1 and 428 DF,  p-value: 9.84e-10

Affair3 <- Affair[Affair$children == "no", ]
lm8 <- lm(affairs~ rating, data = Affair3)
summary(lm8)
#> 
#> Call:
#> lm(formula = affairs ~ rating, data = Affair3)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#>  -2.55  -1.05  -0.55  -0.55  11.45 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)   
#> (Intercept)    3.045      0.914    3.33   0.0011 **
#> rating        -0.499      0.208   -2.40   0.0177 * 
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 2.68 on 169 degrees of freedom
#> Multiple R-squared:  0.0328,	Adjusted R-squared:  0.0271 
#> F-statistic: 5.74 on 1 and 169 DF,  p-value: 0.0177
```
  
  
Übrigens, einfacher geht das "Subsetten" so:


```r
library(dplyr)
Affair4 <- filter(Affair, children == "yes")
head(Affair4)
#>    X affairs gender age yearsmarried children religiousness education
#> 1  3       0 female  32           15      yes             1        12
#> 2  4       0   male  57           15      yes             5        18
#> 3  8       0   male  57           15      yes             2        14
#> 4  9       0 female  32           15      yes             4        16
#> 5 11       0   male  37           15      yes             2        20
#> 6 12       0   male  27            4      yes             4        18
#>   occupation rating
#> 1          1      4
#> 2          6      5
#> 3          4      4
#> 4          1      2
#> 5          7      2
#> 6          6      4
```


### Halodries

Rechnen Sie die Regression nur für "Halodries"; d.h. für Menschen mit Seitensprüngen. Dafür müssen Sie alle Menschen ohne Affären aus den Datensatz entfernen.


Also, rechnen wir nochmal die Standardregression (`lm1`). Probieren wir den Befehl `filter` dazu nochmal aus:


```r
Affair5 <- filter(Affair, affairs != 0)
lm9 <- lm(affairs ~ rating, data = Affair5)
summary(lm9)
#> 
#> Call:
#> lm(formula = affairs ~ rating, data = Affair5)
#> 
#> Residuals:
#>    Min     1Q Median     3Q    Max 
#>  -6.06  -3.52  -0.06   3.69   7.48 
#> 
#> Coefficients:
#>             Estimate Std. Error t value Pr(>|t|)    
#> (Intercept)    8.757      1.023    8.56  1.3e-14 ***
#> rating        -0.848      0.280   -3.03   0.0029 ** 
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 4.14 on 148 degrees of freedom
#> Multiple R-squared:  0.0584,	Adjusted R-squared:  0.052 
#> F-statistic: 9.18 on 1 and 148 DF,  p-value: 0.00289
```


### logistische Regression

Berechnen Sie für eine logistische Regression mit "Affäre ja vs. nein" als Kriterium, wie stark der Einfluss von Geschlecht, Kinderstatus, Ehezufriedenheit und Ehedauer ist!


```r

Affair %>% 
  mutate(affairs_dichotom = if_else(affairs == 0, 0, 1)) %>% 
  glm(affairs_dichotom ~gender + children + rating + yearsmarried, data = ., family = "binomial") -> lm10

summary(lm10)
#> 
#> Call:
#> glm(formula = affairs_dichotom ~ gender + children + rating + 
#>     yearsmarried, family = "binomial", data = .)
#> 
#> Deviance Residuals: 
#>    Min      1Q  Median      3Q     Max  
#> -1.420  -0.764  -0.617  -0.443   2.171  
#> 
#> Coefficients:
#>              Estimate Std. Error z value Pr(>|z|)    
#> (Intercept)    0.0537     0.4299    0.12     0.90    
#> gendermale     0.2416     0.1966    1.23     0.22    
#> childrenyes    0.3935     0.2831    1.39     0.16    
#> rating        -0.4654     0.0874   -5.33    1e-07 ***
#> yearsmarried   0.0221     0.0212    1.04     0.30    
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> (Dispersion parameter for binomial family taken to be 1)
#> 
#>     Null deviance: 675.38  on 600  degrees of freedom
#> Residual deviance: 630.26  on 596  degrees of freedom
#> AIC: 640.3
#> 
#> Number of Fisher Scoring iterations: 4
```

Wenn `if_else` unbekannt ist, lohnt sich ein Blick in die Hilfe mit `?if_else` (`dplyr` muss vorher geladen sein).

Aha, signifikant ist die Ehezufriedenheit: Je größer `rating` desto geringer die Wahrscheinlickeit für `affairs_dichotom`. Macht Sinn!


Übrigens, die Funktion `lm` und `glm` spucken leider keine brave Tabelle in Normalform aus. Aber man leicht eine schöne Tabelle (data.frame) bekommen mit dem Befehl `tidy` aus `broom`:


```r
library(broom)
tidy(lm10) 
#>           term estimate std.error statistic  p.value
#> 1  (Intercept)  0.51578   0.07934      6.50 1.69e-10
#> 2   gendermale  0.03794   0.03422      1.11 2.68e-01
#> 3  childrenyes  0.05403   0.04631      1.17 2.44e-01
#> 4       rating -0.09034   0.01598     -5.65 2.47e-08
#> 5 yearsmarried  0.00395   0.00379      1.04 2.98e-01
```


Und Tabellen (d.h. brave Dataframes) kann man sich schön ausgeben lassen z.B. mit dem Befehl `knitr::kable`:


```r
library(knitr)
tidy(lm10) %>% kable
```



term            estimate   std.error   statistic   p.value
-------------  ---------  ----------  ----------  --------
(Intercept)        0.516       0.079        6.50     0.000
gendermale         0.038       0.034        1.11     0.268
childrenyes        0.054       0.046        1.17     0.244
rating            -0.090       0.016       -5.65     0.000
yearsmarried       0.004       0.004        1.04     0.298


### Zum Abschluss

Visualisieren wir mal was!

Ok, wie wäre es damit:


```r
Affair %>% 
   select(affairs, gender, children, rating) %>%
  ggplot(aes(x = affairs, y = rating)) + geom_jitter(aes(color = gender, shape = children)) 
```

<img src="076_Fallstudie_Affairs_files/figure-html/unnamed-chunk-32-1.png" width="70%" style="display: block; margin: auto;" />



```r
Affair %>% 
   mutate(rating_dichotom = ntile(rating, 2)) %>% 
   ggplot(aes(x = yearsmarried, y = affairs)) + geom_jitter(aes(color = gender)) +
  geom_smooth()
```

<img src="076_Fallstudie_Affairs_files/figure-html/unnamed-chunk-33-1.png" width="70%" style="display: block; margin: auto;" />


Puh. Geschafft!


### Versionshinweise und SessionInfo
* Datum erstellt: 2017-04-12
* R Version: 3.3.2
* `dplyr` Version: 0.5.0




```r
sessionInfo()
#> R version 3.3.2 (2016-10-31)
#> Platform: x86_64-apple-darwin13.4.0 (64-bit)
#> Running under: macOS Sierra 10.12.3
#> 
#> locale:
#> [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8
#> 
#> attached base packages:
#> [1] stats     graphics  grDevices utils     datasets  base     
#> 
#> other attached packages:
#> [1] knitr_1.15.1   broom_0.4.2    MBESS_4.2.0    corrplot_0.77 
#> [5] dplyr_0.5.0    ggplot2_2.2.1  psych_1.7.3.21
#> 
#> loaded via a namespace (and not attached):
#>  [1] Rcpp_0.12.10        magrittr_1.5        mnormt_1.5-5       
#>  [4] munsell_0.4.3       colorspace_1.3-2    lattice_0.20-34    
#>  [7] R6_2.2.0            highr_0.6           stringr_1.2.0      
#> [10] plyr_1.8.4          tools_3.3.2         parallel_3.3.2     
#> [13] grid_3.3.2          nlme_3.1-130        gtable_0.2.0       
#> [16] DBI_0.6-1           htmltools_0.3.5     assertthat_0.1     
#> [19] yaml_2.1.14         lazyeval_0.2.0.9000 rprojroot_1.2      
#> [22] digest_0.6.12       tibble_1.3.0        bookdown_0.3       
#> [25] tidyr_0.6.1         reshape2_1.4.2      codetools_0.2-15   
#> [28] evaluate_0.10       rmarkdown_1.4       labeling_0.3       
#> [31] stringi_1.1.5       methods_3.3.2       scales_0.4.1       
#> [34] backports_1.0.5     foreign_0.8-67
```



  
  

<!--chapter:end:076_Fallstudie_Affairs.Rmd-->

# IV UNGELEITETES MODELLIEREN {-}








<!--chapter:end:080_ungeleitetes_Modellieren.Rmd-->






# Clusteranalyse



Wir werden einen *simulierten* Datensatz  aus *Chapman & Feit (2015): R for Marketing Research and Analytics. Springer* analysieren ([http://r-marketing.r-forge.r-project.org](http://r-marketing.r-forge.r-project.org)). Näheres dazu siehe Kapitel 5 dort.

Sie können ihn von [hier](https://goo.gl/eUm8PI) als `csv`-Datei herunterladen:

```r
#download.file("https://goo.gl/eUm8PI", destfile = "segment.csv")
```

Das Einlesen erfolgt, sofern die Daten im Arbeitsverzeichnis liegen, wieder über:

```r
segment <- read.csv2("https://goo.gl/eUm8PI")
```

Ein Überblick über die Daten:

```r
str(segment)
#> 'data.frame':	300 obs. of  7 variables:
#>  $ Alter         : num  50.2 40.7 43 40.3 41.1 ...
#>  $ Geschlecht    : Factor w/ 2 levels "Frau","Mann": 2 2 1 2 1 2 1 2 1 1 ...
#>  $ Einkommen     : num  51356 64411 71615 42728 71641 ...
#>  $ Kinder        : int  0 3 2 1 4 2 5 1 1 0 ...
#>  $ Eigenheim     : Factor w/ 2 levels "Ja","Nein": 2 2 1 2 2 1 2 2 2 2 ...
#>  $ Mitgliedschaft: Factor w/ 2 levels "Ja","Nein": 2 2 2 2 2 2 1 1 2 2 ...
#>  $ Segment       : Factor w/ 4 levels "Aufsteiger","Gemischte Vorstadt",..: 2 2 2 2 2 2 2 2 2 2 ...
head(segment)
#>   Alter Geschlecht Einkommen Kinder Eigenheim Mitgliedschaft
#> 1  50.2       Mann     51356      0      Nein           Nein
#> 2  40.7       Mann     64411      3      Nein           Nein
#> 3  43.0       Frau     71615      2        Ja           Nein
#> 4  40.3       Mann     42728      1      Nein           Nein
#> 5  41.1       Frau     71641      4      Nein           Nein
#> 6  40.2       Mann     60325      2        Ja           Nein
#>              Segment
#> 1 Gemischte Vorstadt
#> 2 Gemischte Vorstadt
#> 3 Gemischte Vorstadt
#> 4 Gemischte Vorstadt
#> 5 Gemischte Vorstadt
#> 6 Gemischte Vorstadt
```

Zur Unterstützung der Analyse wird (wieder) `mosaic` und `tidyverse` verwendet:

```r
library(tidyverse)
library(mosaic)
```

Das Ziel einer Clusteranalyse ist es, Gruppen von Beobachtungen (d. h. *Cluster*) zu finden, die innerhalb der Cluster möglichst homogen, zwischen den Clustern möglichst heterogen sind. Um die Ähnlichkeit von Beobachtungen zu bestimmen, können verschiedene Distanzmaße herangezogen werden. Für metrische Merkmale wird z. B. häufig die euklidische Metrik verwendet, d. h., Ähnlichkeit und Distanz werden auf Basis des euklidischen Abstands bestimmt. Aber auch andere Abstände wie Manhatten oder Gower sind möglich. Letztere haben den Vorteil, dass sie nicht nur für metrische Daten sondern auch für gemischte Variablentypen verwendet werden können.

Auf Basis der drei metrischen Merkmale (d. h. `Alter`, `Einkommen` und `Kinder`) ergeben sich für die ersten sechs Beobachtungen folgende Abstände:

```r
dist(head(segment))
#>         1       2       3       4       5
#> 2 19941.8                                
#> 3 30946.1 11004.3                        
#> 4 13179.5 33121.3 44125.6                
#> 5 30985.9 11044.0    39.9 44165.3        
#> 6 13700.4  6241.5 17245.8 26879.9 17285.5
```

Sie können erkennen, dass die Beobachtungen `5` und `3` den kleinsten Abstand haben, während `5` und `4` den größten haben. Allerdings zeigen die Rohdaten auch, dass die euklidischen Abstände von der Skalierung der Variablen abhängen (`Einkommen` streut stärker als `Kinder`). Daher kann es evt. sinnvoll sein, die Variablen vor der Analyse zu standardisieren (z. B. über `scale()`). Die Funktion `daisy()` aus dem Paket `cluster` bietet hier nützliche Möglichkeiten.


```r
library(cluster)

daisy(head(segment))
#> Dissimilarities :
#>       1     2     3     4     5
#> 2 0.307                        
#> 3 0.560 0.390                  
#> 4 0.219 0.184 0.502            
#> 5 0.516 0.220 0.242 0.404      
#> 6 0.401 0.206 0.239 0.268 0.426
#> 
#> Metric :  mixed ;  Types = I, N, I, I, N, N, N 
#> Number of objects : 6
```


## Hierarchische Clusteranalyse

Bei hierarchischen Clusterverfahren werden Beobachtungen sukzessiv zusammengefasst (agglomerativ). Zunächst ist jede Beobachtung ein eigener Cluster, die dann je nach Ähnlichkeitsmaß zusammengefasst werden. 

Fassen wir die Beobachtungen *ohne* die Segmentvariable `Segment`, Variable 7, zusammen:

```r
seg.dist <- daisy(segment[,-7]) # Abstände
seg.hc <- hclust(seg.dist) # Hierarchische Clusterung
```

Das Ergebnis lässt sich schön im Dendrogramm darstellen:

```r
plot(seg.hc)
```

<img src="082_Clusteranalyse_files/figure-html/unnamed-chunk-9-1.png" width="70%" style="display: block; margin: auto;" />

Je höher (`Height`) die Stelle ist, an der zwei Beobachtungen oder Cluster zusammengefasst werden, desto größer ist die Distanz. D. h., Beobachtungen bzw. Cluster, die unten zusammengefasst werden, sind sich ähnlich, die, die oben zusammengefasst werden unähnlich.

Hier wurde übrigens die Standardeinstellung für die Berechnung des Abstands von Clustern verwendet: Complete Linkage bedeutet, dass die Distanz zwischen zwei Clustern auf Basis des maximalen Abstands der Beobachtungen innerhalb des Clusters gebildet wird.

Es ist nicht immer einfach zu entscheiden, wie viele Cluster es gibt. In der Praxis und Literatur finden sich häufig Zahlen zwischen 3 und 10. Evt. gibt es im Dendrogramm eine Stelle, an der der Baum gut geteilt werden kann. In unserem Fall vielleicht bei einer Höhe von $0.6$, da sich dann 3 Cluster ergeben:

```r
plot(seg.hc)
rect.hclust(seg.hc, h=0.6, border="red")
```

<img src="082_Clusteranalyse_files/figure-html/unnamed-chunk-10-1.png" width="70%" style="display: block; margin: auto;" />

Das Ergebnis, d. h. die Clusterzuordnung, kann durch den Befehl `cutree()` den Beobachtungen zugeordnet werden.

```r
segment$hc.clust <- cutree(seg.hc, k=3)
```

Z. B. haben wir folgende Anzahlen für Beobachtungen je Cluster:

```r
mosaic::tally(~hc.clust, data=segment)
#> hc.clust
#>   1   2   3 
#> 140 122  38
```
Cluster 3  ist also mit Abstand der kleinste Cluster (mit 38 Beobachtungen).

Für den Mittelwert des Alters je Cluster gilt:

```r

segment %>% 
  group_by(hc.clust) %>% 
  summarise(Alter_nach_Cluster = mean(Alter))
#> # A tibble: 3 × 2
#>   hc.clust Alter_nach_Cluster
#>      <int>              <dbl>
#> 1        1               38.5
#> 2        2               46.4
#> 3        3               34.5
```
D. h. die Durchschnittsalter ist in Cluster der Cluster unterscheiden sich.

Das spiegelt sich auch im Einkommen wieder:

```r
segment %>% 
  group_by(hc.clust) %>% 
  summarise(Einkommen_nach_Cluster = mean(Einkommen))
#> # A tibble: 3 × 2
#>   hc.clust Einkommen_nach_Cluster
#>      <int>                  <dbl>
#> 1        1                  49452
#> 2        2                  54355
#> 3        3                  44113
```

Allerdings sind die Unterschiede in der Geschlechtsverteilung eher gering:

```r
mosaic::tally(Geschlecht~hc.clust, data=segment, format="proportion")
#>           hc.clust
#> Geschlecht     1     2     3
#>       Frau 0.543 0.549 0.526
#>       Mann 0.457 0.451 0.474
```


## k-Means Clusteranalyse

Beim k-Means Clusterverfahren handelt es sich im Gegensatz zur hierarchischen Clusteranalyse um ein partitionierendes Verfahren. Die Daten werde in k Cluster aufgeteilt -- dabei muss die Anzahl der Cluster im vorhinein feststehen. Ziel ist es, dass die Quadratsumme der Abweichungen der Beobachtungen im Cluster zum Clusterzentrum minimiert wird. 

Der Ablauf des Verfahrens ist wie folgt:

1.  Zufällige Beobachtungen als Clusterzentrum
2.  Zuordnung der Beobachtungen zum nächsten Clusterzentrum (Ähnlichkeit, z. B. über die euklidische Distanz)
3.  Neuberechnung der Clusterzentren als Mittelwert der dem Cluster zugeordneten Beobachtungen

Dabei werden die Schritte 2. und 3. solange wiederholt, bis sich keine Änderung der Zuordnung mehr ergibt -- oder eine maximale Anzahl an Iterationen erreicht wurde.

*Hinweis:* Die (robuste) Funktion `pam()` aus dem Paket `cluster` kann auch mit allgemeinen Distanzen umgehen. Außerdem für gemischte Variablentypen gut geeignet: Das Paket [`clustMixType`](https://cran.r-project.org/web/packages/clustMixType/index.html).


Zur Vorbereitung überführen wir die nominalen Merkmale in logische, d. h. binäre Merkmale, und löschen die Segmente sowie das Ergebnis der hierarchischen Clusteranalyse:

```r
segment.num <- segment %>%
  mutate(Frau = Geschlecht=="Frau") %>%
  mutate(Eigenheim = Eigenheim=="Ja") %>%
  mutate(Mitgliedschaft = Mitgliedschaft=="Ja") %>%
  dplyr::select(-Geschlecht, -Segment, -hc.clust)
```

Über die Funktion `mutate()` werden Variablen im Datensatz erzeugt oder verändert. Über `select()` werden einzene Variablen ausgewählt. Die "Pfeife" `%>%` übergeben das Ergebnis der vorherigen Funktion an die folgende.

Aufgrund von (1.) hängt das Ergebnis einer k-Means Clusteranalyse vom Zufall ab. Aus Gründen der Reproduzierbarkeit sollte daher der Zufallszahlengenerator gesetzt werden. Außerdem bietet es sich an verschiedene Startkonfigurationen zu versuchen. in der Funktion `kmeans()` erfolgt dies durch die Option `nstart=`. Hier mit `k=4` Clustern:


```r
set.seed(1896)

seg.k <- kmeans(segment.num, centers = 4, nstart = 10)
seg.k
#> K-means clustering with 4 clusters of sizes 111, 26, 58, 105
#> 
#> Cluster means:
#>   Alter Einkommen Kinder Eigenheim Mitgliedschaft  Frau
#> 1  42.9     46049  1.649     0.505         0.1081 0.568
#> 2  56.4     85973  0.385     0.538         0.0385 0.538
#> 3  27.0     22608  1.224     0.276         0.2069 0.414
#> 4  43.6     62600  1.505     0.457         0.1238 0.590
#> 
#> Clustering vector:
#>   [1] 1 4 4 1 4 4 4 1 2 4 1 1 4 4 1 1 1 1 1 4 4 4 1 4 1 1 1 1 4 1 4 4 1 1 2
#>  [36] 1 4 1 1 4 4 4 1 4 4 4 4 1 1 1 1 1 2 1 1 4 4 4 4 1 4 1 4 1 1 1 1 4 4 4
#>  [71] 4 1 1 4 1 1 4 4 4 4 1 4 1 3 1 4 1 1 1 1 4 4 4 1 1 4 1 4 4 4 3 3 3 3 3
#> [106] 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3
#> [141] 3 3 3 3 3 3 3 3 3 3 1 2 4 2 2 4 1 1 2 2 4 4 1 1 4 2 4 4 1 2 2 3 4 1 2
#> [176] 2 4 2 3 4 4 4 1 1 1 1 1 1 4 3 1 4 4 4 4 1 1 1 2 4 4 1 2 4 4 1 4 2 1 2
#> [211] 4 3 4 2 2 4 2 1 4 3 1 2 2 4 2 4 4 1 4 4 1 1 1 1 1 3 1 1 4 1 4 3 1 4 1
#> [246] 4 1 4 1 4 4 4 4 1 1 1 4 4 1 1 1 1 1 1 4 1 1 1 1 1 2 4 4 1 4 1 1 1 1 2
#> [281] 4 4 4 4 1 4 1 4 4 4 1 4 1 4 1 4 1 1 4 1
#> 
#> Within cluster sum of squares by cluster:
#> [1] 3.18e+09 2.22e+09 1.69e+09 2.81e+09
#>  (between_SS / total_SS =  90.6 %)
#> 
#> Available components:
#> 
#> [1] "cluster"      "centers"      "totss"        "withinss"    
#> [5] "tot.withinss" "betweenss"    "size"         "iter"        
#> [9] "ifault"
```
Neben der Anzahl Beobachtungen im Cluster (z. B. 26 in Cluster 2) werden auch die Clusterzentren ausgegeben. Diese können dann direkt verglichen werden. Sie sehen z. B., dass das Durchschnittsalter in Cluster 3 mit 27 am geringsten ist. Der Anteil der Eigenheimbesitzer ist mit 54 \% in Cluster 2 am höchsten.

Einen Plot der Scores auf den beiden ersten Hauptkomponenten können Sie über die Funktion `clusplot()` aus dem Paket `cluster` erhalten.

```r
clusplot(segment.num, seg.k$cluster, 
         color = TRUE, shade = TRUE, labels = 4)
```

<img src="082_Clusteranalyse_files/figure-html/unnamed-chunk-18-1.png" width="70%" style="display: block; margin: auto;" />
Wie schon im deskriptiven Ergebnis: Die Cluster `1` und `4` unterscheiden sich (in den ersten beiden Hauptkomponenten) nicht wirklich. Vielleicht sollten dies noch zusammengefasst werden, d. h., mit `centers=3` die Analyse wiederholt werden?^[Das Paket `NbClust`, siehe Malika Charrad, Nadia Ghazzali, Veronique Boiteau, Azam Niknafs (2014) *NbClust: An R Package for Determining the Relevant Number of Clusters in a Data Set*, Journal of Statistical Software, 61(6), 1-36. [http://dx.doi.org/10.18637/jss.v061.i06](http://dx.doi.org/10.18637/jss.v061.i06), bietet viele Möglichkeiten die Anzahl der Cluster optimal zu bestimmen.]

***

## Übung: B3 Datensatz

Der B3 Datensatz *Heilemann, U. and Münch, H.J. (1996): West German Business Cycles 1963-1994: A Multivariate Discriminant Analysis. CIRET–Conference in Singapore, CIRET–Studien 50.* enthält Quartalsweise Konjunkturdaten aus (West-)Deutschland.

Er kann von [https://goo.gl/0YCEHf](https://goo.gl/0YCEHf) heruntergeladen werden.

1. Wenn die Konjunkturphase `PHASEN` nicht berücksichtigt wird, wie viele Cluster könnte es geben? Ändert sich das Ergebnis, wenn die Variablen standardisiert werden?
2. Führen Sie eine k-Means Clusteranalyse mit 4 Clustern durch. Worin unterscheiden sich die gefundenen Segmente?


### Literatur

- Chris Chapman, Elea McDonnell Feit (2015): *R for Marketing Research and Analytics*, Kapitel 11.3
- Reinhold Hatzinger, Kurt Hornik, Herbert Nagel (2011): *R -- Einführung durch angewandte Statistik*. Kapitel 12
- Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani (2013): *An Introduction to Statistical Learning -- with Applications in R*, [http://www-bcf.usc.edu/~gareth/ISL/](http://www-bcf.usc.edu/~gareth/ISL/), Kapitel 10.3, 10.5


***
Diese Übung orientiert sich am Beispiel aus Kapitel 11.3 aus Chapman und Feit (2015) und steht unter der Lizenz [Creative Commons Attribution-ShareAlike 3.0 Unported](http://creativecommons.org/licenses/by-sa/3.0). Der Code steht unter der [Apache Lizenz 2.0](http://www.apache.org/licenses/LICENSE-2.0)


<!--chapter:end:082_Clusteranalyse.Rmd-->

# VI Anhang {-}


# Studienpfade
Je nach Lernziel, Zeit und Interessen bieten sich unterschiedliche Studienpfade durch dieses Buch an. Im folgenden sind einige aufgezählt - untergliedert nach Fachrichtung, Vorerfahrung und Zeit.


## konsequtiver Master of Science in Wirtschaftspsychologie

Anahmen: 

- Zeitumfang: 44 UE für Lehre

- Vorerfahrung: Deskriptive Statistik, Inferenzstatistik, Grundlagen R, Grundlagen Visualisierung


Termin    Thema/ Kapitel                      
-------   --------------------------------------                              
1         Organisatorisches
          Einführung
          Rahmen
          Daten einlesen
2         Datenjudo
3         Daten visualisieren
4         Fallstudie
5         Daten modellieren     
          Der p-Wert
6         Lineare Regression - Grundlagen
7         Lineare Regression - Vertiefung
8         Fallstudie
9         Textmining
10        Clusteranalyse
11        Wiederholung

          
Die einzelnen Kapitel sind dabei nicht umfassend abzuarbeiten. Der Lehrende/ Lernende kann hier eine Auswahl treffen. Teilweise ist der Stoff eines Kapitels - ja nach Vorerfahrung der Lernenden - zu viel für einen Termin (mit jeweils 4 UE).


<!--chapter:end:110_Studienpfade_Anhang.Rmd-->

# Literaturverzeichnis

# Literaturverzeichnis {-}

<!--chapter:end:120_Literatur.Rmd-->
