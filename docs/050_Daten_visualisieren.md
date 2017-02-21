


# Daten visualisieren

Benötigte Pakete:

```r
library(tidyverse)
library(wesanderson)
library(car)
library(RColorBrewer)
library(GGally)
library(knitr)
library(gridExtra)
```


Ein Bild sagt bekanntlich mehr als 1000 Worte. Schauen wir uns zur Verdeutlichung das berühmte Beispiel von Anscombe[^9] an. Es geht hier um vier Datensätze mit zwei Variablen (Spalten; X und Y). Offenbar sind die Datensätze praktisch identisch: Alle X haben den gleichen Mittelwert und die gleiche Varianz; dasselbe gilt für die Y. Die Korrelation zwischen X und Y ist in allen vier Datensätzen gleich. Allerdings erzählt eine Visualisierung der vier Datensätze eine ganz andere Geschichte.


<img src="images/anscombe.pdf" width="70%" style="display: block; margin: auto;" />


Offenbar "passieren" in den vier Datensätzen gänzlich unterschiedliche Dinge. Dies haben die Statistiken nicht aufgedeckt; erst die Visualisierung erhellte uns... Kurz: Die Visualisierung ist ein unverzichtbares Werkzeug, um zu verstehen, was in einem Datensatz (und damit in der zugrundeliengenden "Natur") passiert. 


Es gibt viele Möglichkeiten, Daten zu visualieren (in R). Wir werden uns hier auf einen Weg bzw. ein Paket konzentrieren, der komfortabel, aber mächtig ist und gut zum Prinzip des Durchpfeifens passt: `ggplot2`.

Laden wir dazu den Datensatz `nycflights::flights`.


```r
data(flights, package = "nycflights13")
```





```r
qplot(x = carrier, y = arr_delay, geom = "boxplot", data = flights)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-5-1.png" width="70%" style="display: block; margin: auto;" />

Offenbar gibt es viele Extremwerte, was die Verspätung betrifft. Das erscheint mir nicht unplausibel (Schneesturm im Winter, Flugzeug verschwunden...). Vor dem Hintergrund der Extremwerte erscheinen die mittleren Verspätungen (Mediane) in den Boxplots als ähnlich. Vielleicht ist der Unterschied zwischen den Monaten ausgeprägter?


```r
qplot(x = factor(month), y = arr_delay, geom = "boxplot", data = flights)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-6-1.png" width="70%" style="display: block; margin: auto;" />

Kaum Unterschied; das spricht gegen die Schneesturm-Idee als Grund für Verspätung. Aber schauen wir uns zuerst die Syntax von `qplot` näher an. "q" in `qplot` steht für "quick". Tatsächlich hat `qplot` einen großen Bruder, `ggplot`[^10], der deutlich mehr Funktionen aufweist - und daher auch die umfangreichere (=komplexere) Syntax. Fangen wir mit `qplot` an.


Diese Syntax des letzten Beispiels ist recht einfach, nämlich:


```r
qplot (x = X_Achse, y = Y_Achse, data = mein_dataframe, geom = "ein_geom")
```

Wir definieren mit `x`, welche Variable der X-Achse des Diagramms zugewiesen werden soll, z.B. `month`; analog mit Y-Achse. Mit `data` sagen wir, in welchem Dataframe die Spalten "wohnen" und als "geom" ist die Art des statistischen "*geom*etrischen Objects" gemeint, also Punkte, Linien, Boxplots, Balken...

## Häufige Arten von Diagrammen
Unter den vielen Arten von Diagrammen und vielen Arten, diese zu klassifizieren greifen wir uns ein paar häufige Diagramme heraus und schauen uns diese der Reihe nach an.


### Eine kontinuierliche Variable

Schauen wir uns die Verteilung der Schuhgrößen von Studierenden an.


```r
wo_men <- read.csv("data/wo_men.csv")

qplot(x = shoe_size, data = wo_men)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-8-1.png" width="70%" style="display: block; margin: auto;" />

Weisen wir nur der X-Achse (aber nicht der Y-Achse) eine kontinuierliche Variable zu, so wählt `ggplot2` automatisch als Geom automatisch ein Histogramm; wir müssen daher nicht explizieren, dass wir ein Histogramm als Geom wünschen (aber wir könnten es hinzufügen). Alternativ wäre ein Dichtediagramm hier von Interesse:


```r
# qplot(x = shoe_size, data = wo_men)  wie oben

qplot(x = shoe_size, data = wo_men, geom = "density")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-9-1.png" width="70%" style="display: block; margin: auto;" />

Was man sich merken muss, ist, dass hier nur das Geom mit Anführungsstrichen zu benennen ist, die übrigen Parameter *ohne*.

Vielleicht wäre es noch schön, beide Geome zu kombinieren in einem Diagramm. Das ist etwas komplizierter; wir müssen zum großen Bruder `ggplot` umsteigen, da `qplot` nicht diese Funktionen anbietet.


```r
ggplot(data = wo_men) +
  aes(x = shoe_size) +
  geom_histogram(aes(y = ..density..), alpha = .7) +
  geom_density(color = "blue")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-10-1.png" width="70%" style="display: block; margin: auto;" />

Zuerst haben wir mit dem Parameter `data` den Dateframe benannt. `aes` definiert, welche Variablen welchen Achsen (oder auch z.B. Füllfarben) zugewiesen werden. Hier sagen wir, dass die Schuhgröße auf X-Achse stehen soll. Das `+`-Zeichen trennt die einzelnen Bestandteile des `ggplot`-Aufrufs voneinander. Als nächstes sagen wir, dass wir gerne ein Histogram hätten: `geom_histogram`. Dabei soll aber nicht wie gewöhnlich auf der X-Achse die Häufigkeit stehen, sondern die Dichte. `ggplot` berechnet selbständig die Dichte und nennt diese Variable `..density..`; die vielen Punkte sollen wohl klar machen, dass es sich nicht um eine "normale" Variable aus dem eigenen Dateframe handelt, sondern um eine "interne" Varialbe von `ggplot` - die wir aber nichtsdestotrotz verwenden können. `alpha` bestimmt die "Durchsichtigkeit" eines Geoms; spielen Sie mal etwas damit herum. Schließlich malen wir noch ein blaues Dichtediagramm *übe*r das Histogramm.

Wünsche sind ein Fass ohne Boden... Wäre es nicht schön, ein Diagramm für Männer und eines für Frauen zu haben, um die Verteilungen vergleichen zu können?


```r
qplot(x = shoe_size, data = wo_men, geom = "density", color = sex)
qplot(x = shoe_size, data = wo_men, geom = "density", fill = sex, alpha = I(.7))
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-11-1.png" width="70%" style="display: block; margin: auto;" /><img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-11-2.png" width="70%" style="display: block; margin: auto;" />

Hier sollten vielleicht noch die Extremwerte entfernt werden, um den Blick auf das Gros der Werte nicht zu verstellen:


```r

wo_men %>% 
  filter(shoe_size <= 47) -> wo_men2

qplot(x = shoe_size, data = wo_men2, geom = "density", fill = sex, alpha = I(.7))
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-12-1.png" width="70%" style="display: block; margin: auto;" />

Besser. Man kann das Durchpfeifen auch bis zu `qplot` weiterführen:


```r
wo_men %>% 
  filter(shoe_size <= 47) %>% 
  qplot(x = shoe_size, data = ., geom = "density", fill = sex, alpha = I(.7))
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-13-1.png" width="70%" style="display: block; margin: auto;" />

Die Pfeife versucht im Standard, das Endprodukt des lezten Arbeitsschritts an den *ersten* Parameter des nächsten Befehls weiterzugeben. Ein kurzer Blick in die Hilfe von `qplot` zeigt, dass der erste Parameter nicht `data` ist, sondern `x`. Daher müssen wir explizit sagen, an welchen Parameter wir das Endprodukt des lezten Arbeitsschritts geben wollen. Netterweise müssen wir dafür nicht viel tippen: Mit einem schlichten Punkt `.` können wir sagen "nimm den Dataframe, so wie er vom letzten Arbeitsschritt ausgegeben wurde".

Mit `fill = sex` sagen wir `qplot`, dass er für Männer und Frauen jeweils ein Dichtediagramm erzeugen soll; jedem Dichtediagramm wird dabei eine Farbe zugewiesen (die uns `ggplot2` im Standard voraussucht). Mit anderen Worten: Die Werte von `sex` werden der Füllfarbe der Histogramme zugeordnet. Anstelle der Füllfarbe hätten wir auch die Linienfarbe verwenden können; die Syntax wäre dann: `color = sex`.

### Zwei kontinuierliche Variablen

Ein Streudiagramm ist die klassiche Art, zwei metrische Variablen darzustellen. Das ist mit `qplot` einfach:


```r
qplot(x = height, y = shoe_size, data = wo_men)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-14-1.png" width="70%" style="display: block; margin: auto;" />

Wir weisen wieder der X-Achse und der Y-Achse eine Variable zu; handelt es sich in beiden Fällen um Zahlen, so wählt `ggplot2` automatisch ein Streudiagramm - d.h. Punkte als Geom (`geom = "point"`). Wir sollten aber noch die Extremwerte herausnehmen:


```r
wo_men %>% 
  filter(height > 150, height < 210, shoe_size < 55) %>% 
  qplot(x = height, y = shoe_size, data = .)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-15-1.png" width="70%" style="display: block; margin: auto;" />

Der Trend ist deutlich erkennbar: Je größer die Person, desto länger die Füß´. Zeichnen wir noch eine Trendgerade ein.



```r
wo_men %>% 
  filter(height > 150, height < 210, shoe_size < 55) %>% 
  qplot(x = height, y = shoe_size, data = .) +
  geom_smooth(method = "lm")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-16-1.png" width="70%" style="display: block; margin: auto;" />

Synonym könnten wir auch schreiben:


```r
wo_men %>% 
  filter(height > 150, height < 210, shoe_size < 55) %>% 
  ggplot() +
  aes(x = height, y = shoe_size) +
  geom_point() +
  geom_smooth(method = "lm")
```

Da `ggplot` als *ersten* Parameter die Daten erwartet, kann die Pfeife hier problemlos durchgereicht werden. *Innerhalb* eines `ggplot`-Aufrufs werden die einzelen Teile durch ein Pluszeichen `+` voneinander getrennt. Nachdem wir den Dataframe benannt haben, definieren wir die Zuweisung der Variablen zu den Achsen mit `aes` ("aes" wie "aesthetics", also das "Sichtbare" eines Diagramms, die Achsen etc., werden definiert). Ein "Smooth-Geom" ist eine Linie, die sich schön an die Punkte anschmiegt, in diesem Falls als Gerade (lineares Modell, `lm`).

Wenn man dies verdaut hat, wächst der Hunger nach einer Aufteilung in Gruppen.


```r
wo_men %>% 
  filter(height > 150, height < 210, shoe_size < 55) %>% 
  qplot(x = height, y = shoe_size, color = sex, data = .)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-18-1.png" width="70%" style="display: block; margin: auto;" />

Mit `color = sex` sagen wir, dass die Linienfarbe (der Punkte) entsprechend der Stufen von `sex` eingefärbt werden sollen. Die genaue Farbwahl übernimmt `ggplot2` für uns.

### Eine diskrete Variable
Bei diskreten Variablen, vor allem nominalen Variablen, geht es in der Regel darum, Häufigkeiten auszuzählen. Wie viele Männer und Frauen sind in dem Datensatz?


```r
qplot(x = sex, data = wo_men)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-19-1.png" width="70%" style="display: block; margin: auto;" />

Falls nur die X-Achse definiert ist und dort eine Faktorvariable oder eine Text-Variable steht, dann nimmt `qplot` automatisch ein Balkendiagramm als Geom.

Entfernen wir vorher noch die fehlenden Werte:


```r
wo_men %>% 
  na.omit() %>% 
  qplot(x = sex, data = .)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-20-1.png" width="70%" style="display: block; margin: auto;" />

Wir könnten uns jetzt die Frage stellen, wie viele kleine und viele große Menschen es bei Frauen und bei den Männern gibt. Dazu müssen wir zuerst eine Variable wie "Größe gruppiert" erstellen mit zwei Werten: "klein" und "groß". Nennen wir sie `groesse_gruppe`


```r
wo_men$groesse_gruppe <- car::recode(wo_men$height, "lo:175 = 'klein'; else = 'gross'")

wo_men %>% 
  filter(height > 150, height < 210, shoe_size < 55) %>% 
  na.omit -> wo_men2
  
qplot(x = sex, fill = groesse_gruppe, data = wo_men2)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-21-1.png" width="70%" style="display: block; margin: auto;" />

In Worten sagt der `recode`-Befehl hier in etwa: "Kodiere `wo_men$height` um, und zwar vom kleinsten (`lo`) Wert bis 170 soll den Wert `klein` bekommen, ansonsten bekommt eine Größe den Wert `gross`".

Hier haben wir `qplot` gesagt, dass der die Balken entsprechend der Häufigkeit von `groesse_gruppe` füllen soll. Und bei den Frauen sind bei dieser Variablen die Wete `klein` häufig; bei den Männern hingegen die Werte `gross`.

Schön wäre noch, wenn die Balken Prozentwerte angeben würden. Das geht mit `qplot` (so) nicht; wir schwenken auf `ggplot` um[^3].


```r
wo_men2 %>% 
  ggplot() +
  aes(x = sex, fill = groesse_gruppe) +
  geom_bar(position = "fill")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-22-1.png" width="70%" style="display: block; margin: auto;" />

Die einzige Änderung in den Parametern ist `position = "fill"`. Dieser Parameter weist `ggplot` an, die Positionierung der Balken auf die Darstellung von Anteilen auszulegen. Damit haben alle Balken die gleiche Höhe, nämlich 100% (1). Aber die "Füllung" der Balken schwankt je nach der Häufigkeit der Werte von `groesse_gruppe` pro Balken (d.h. pro Wert von `sex`).

Wir sehen, dass die Anteile von großen bzw. kleinen Menschen bei den beiden Gruppen (Frauen vs. Männer) *unterschiedlich hoch* ist. Dies spricht für einen *Zusammenhang* der beiden Variablen; man sagt, die Variablen sind *abhängig* (im statistischen Sinne).

>    Je unterschiedlicher die "Füllhöhe", desto stärker sind die Variablen (X-Achse vs. Füllfarbe) voneinander abhängig (bzw. desto stärker der Zusammenhang). 



### Zwei diskrete Variablen 
Arbeitet man mit nominalen Variablen, so sind Kontingenztabellen Täglich Brot. Z.B.: Welche Produkte wurden wie häufig an welchem Standort verkauft? Wie ist die Verteilung von Alkoholkonsum und Körperform bei Menschen einer Single-Börse. Bleiben wir bei letztem Beispiel. 



```r
data(profiles, package = "okcupiddata")

profiles %>% 
  count(drinks, body_type) %>% 
  ggplot +
  aes(x = drinks, y = body_type, fill = n) +
  geom_tile() +
  theme(axis.text.x = element_text(angle = 90))
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-23-1.png" width="70%" style="display: block; margin: auto;" />

Was haben wir gemacht? Also:




\BeginKnitrBlock{rmdpseudocode}<div class="rmdpseudocode">Nehme den Datensatz "profiles" UND DANN  
Zähle die Kombinationen von "drinks" und "body_type" UND DANN  
Erstelle ein ggplot-Plot UND DANN  
Weise der X-Achse "drinks" zu, der Y-Achse "body_type" und der Füllfarbe "n" UND DANN  
Male Fliesen UND DANN  
Passe das Thema so an, dass der Winkel für Text der X-Achse auf 90 Grad steht.  
</div>\EndKnitrBlock{rmdpseudocode}


     
Was sofort ins Auge sticht, ist dass "soziales Trinken", nennen wir es mal so, am häfigsten ist, unabhängig von der Körperformm. Ansonsten scheinen die Zusammenhäng nicht sehr stark zu sein.     

### Zusammenfassungen zeigen
Manchmal möchten wir *nicht* die Rohwerte einer Variablen darstellen, sondern z.B. die Mittelwerte pro Gruppe. Mittelwerte sind eine bestimmte *Zusammenfassung* einer Spalte; also fassen wir zuerst die Körpergröße zum Mittelwert zusammen - gruppiert nach Geschlecht.


```r
wo_men2 %>% 
  group_by(sex) %>% 
  summarise(Groesse_MW = mean(height)) -> wo_men3

wo_men3
#> # A tibble: 2 × 2
#>      sex Groesse_MW
#>   <fctr>      <dbl>
#> 1    man        183
#> 2  woman        167
```


Diese Tabelle schieben wir jetzt in `ggplot2`; natürlich hätten wir das gleich in einem Rutsch durchpfeifen können.


```r
wo_men3 %>% 
  qplot(x = sex, y = Groesse_MW, data = .)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-25-1.png" width="70%" style="display: block; margin: auto;" />

Das Diagramm besticht nicht durch die Tiefe und Detaillierung. Wenn wir noch zusätzlich die Mittelwerte nach `Groesse_Gruppe` ausweisen, wird das noch überschaubar bleiben.


```r
wo_men2 %>% 
  group_by(sex, groesse_gruppe) %>% 
  summarise(Groesse_MW = mean(height)) %>% 
  qplot(x = sex, color = factor(groesse_gruppe), y = Groesse_MW, data = .)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-26-1.png" width="70%" style="display: block; margin: auto;" />



## Farblehre
Erstens, nicht schaden - so könnte hier die Maßregel sein. Es ist leicht, zu grelle oder wenig kontrastierende Farben auszuwählen. Eine gute Farbauswahl (Palette) ist nicht so leicht und hängt vom Zweck der Darstellung ab.

Cynthia Brewer[^4] hat einige schöne Farbpaletten zusammengestellt; diese sind in R und in ggplot2 über das Paket `RcolorBrewer` verfügbar. 


```r
brewer.pal.info %>% rownames_to_column %>% rename(Name = rowname) %>% kable
```



Name        maxcolors  category   colorblind 
---------  ----------  ---------  -----------
BrBG               11  div        TRUE       
PiYG               11  div        TRUE       
PRGn               11  div        TRUE       
PuOr               11  div        TRUE       
RdBu               11  div        TRUE       
RdGy               11  div        FALSE      
RdYlBu             11  div        TRUE       
RdYlGn             11  div        FALSE      
Spectral           11  div        FALSE      
Accent              8  qual       FALSE      
Dark2               8  qual       TRUE       
Paired             12  qual       TRUE       
Pastel1             9  qual       FALSE      
Pastel2             8  qual       FALSE      
Set1                9  qual       FALSE      
Set2                8  qual       TRUE       
Set3               12  qual       FALSE      
Blues               9  seq        TRUE       
BuGn                9  seq        TRUE       
BuPu                9  seq        TRUE       
GnBu                9  seq        TRUE       
Greens              9  seq        TRUE       
Greys               9  seq        TRUE       
Oranges             9  seq        TRUE       
OrRd                9  seq        TRUE       
PuBu                9  seq        TRUE       
PuBuGn              9  seq        TRUE       
PuRd                9  seq        TRUE       
Purples             9  seq        TRUE       
RdPu                9  seq        TRUE       
Reds                9  seq        TRUE       
YlGn                9  seq        TRUE       
YlGnBu              9  seq        TRUE       
YlOrBr              9  seq        TRUE       
YlOrRd              9  seq        TRUE       


- Kontrastierende Darstellung (nominale/ qualitative Variablen) - z.B. Männer vs. Frauen


```r
display.brewer.all(type="qual")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-28-1.png" width="100%" style="display: block; margin: auto;" />

- Sequenzielle Darstellung (unipolare numerische Variablen) - z.B. Preis oder Häufigkeit

```r
display.brewer.all(type="seq")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-29-1.png" width="100%" style="display: block; margin: auto;" />


- Divergierende Darstellung (bipolare numerische Variablen) - z.B. semantische Potenziale oder Abstufung von "stimme überhaupt nicht zu" über "neutral" bis "stimme voll und ganz zu"


```r
display.brewer.all(type="div")
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-30-1.png" width="100%" style="display: block; margin: auto;" />

In `ggplot2` können wir folgendermaßen Paletten ändern.


```r

flights %>% 
  group_by(dest) %>% 
  count(dest) %>% 
  top_n(5)
#> # A tibble: 5 × 2
#>    dest     n
#>   <chr> <int>
#> 1   ATL 17215
#> 2   BOS 15508
#> 3   LAX 16174
#> 4   MCO 14082
#> 5   ORD 17283

p1 <- flights %>% 
  filter(dest %in% c("BOS", "ATL", "LAX")) %>% 
  ggplot() +
  aes(x = dest, y = arr_delay, color = dest) +
  geom_boxplot() +
  scale_color_brewer(palette = "Set1")

p2 <- flights %>% 
  filter(dest %in% c("BOS", "ATL", "LAX", "MCO", "ORD")) %>% 
  ggplot() +
  aes(x = dest, y = arr_delay, fill = dest) +
  geom_boxplot() +
  scale_fill_brewer(palette = "Set1")

grid.arrange(p1, p2, ncol = 2)
```

<img src="050_Daten_visualisieren_files/figure-html/brewerpal-1.png" width="100%" style="display: block; margin: auto;" />

`scale_color_brewer` meint hier: "Ordne der Variablen, die für 'color' zuständig ist, hier `sex`, eine Farbe aus der Brewer-Palette 'Set1' zu". Die Funktion wählt *automatisch* die richtige Anzahl von Farben.

Man beachte, dass die Linienfarbe über `color` und die Füllfarbe über `fill` zugewiesen wird. Punkte haben nur eine Linienfarbe, keine Füllfarbe.



Auch die Farbpaletten von Wes Anderson sind erbaulich[^5]. Diese sind nicht "hart verdrahtet" in ggplot2, sondern werden über `scale_XXX_manual` zugewiesen (wobei XXX z.B. `color` oder `fill` sein kann).


```r
data(tips, package = "reshape2")

p1 <- tips %>% 
  ggplot() +
  aes(x = total_bill, y = tip, color = day) +
  geom_point() +
  scale_color_manual(values = wes_palette("GrandBudapest")) +
  theme(legend.position = "bottom")

p2 <- tips %>% 
  ggplot() +
  aes(x = total_bill, y = tip, color = day) +
  geom_point() +
  scale_color_manual(values = wes_palette("Chevalier"))  +
  theme(legend.position = "bottom")

meine_farben <- c("red", "blue", "#009981", "#32F122")

p3 <- tips %>% 
  ggplot() +
  aes(x = total_bill, y = tip, color = day) +
  geom_point() +
  scale_color_manual(values = meine_farben)  +
  theme(legend.position = "bottom")

grid.arrange(p1, p2, p3, ncol = 3)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-31-1.png" width="70%" style="display: block; margin: auto;" />


Wer sich berufen fühlt, eigene Farben (oder die seiner Organisation zu verwenden), kommt auf ähnlichem Weg zu Ziel. Man definiere sich seine Palette, wobei ausreichend Farben definiert sein müssen. Diese weist man dann über `scale_XXX_manual` dann zu. Man kann einerseits aus den in R definierten Farben auswählen[^6] oder sich selber die RBG-Nummern (in Hexadezimal-Nummern) heraussuchen.



## Prinzipien

## Erweiterungen für ggplot

### ggpairs

Um eine Streudiagramm-Matrix darzustellen, ist der Befehl `GGally::ggpairs` praktisch:


```r

tips %>% 
  ggpairs(aes(color = sex), columns = c("total_bill", "smoker", "tip"))
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-32-1.png" width="70%" style="display: block; margin: auto;" />

Dabei gibt man an, welche Variable (hier `sex`) für die Farben im Diagramm zuständig sein soll (wir ordnen den Werten von `sex` jeweils eine Farbe zu). Mit `columns` sagen wir, welche Spalten des Dataframes wir dargestellt haben möchten. Lassen wir diesen Parameter weg, so werden alle Spaltne des Dataframes dargestellt.


### Weitere
Hier[^7] finden sich viele weitere Ergänzungen für ggplot2.

## Fallstudie


Eine recht häufige Art von Daten in der Wirtschaft kommen von Umfragen in der Belegschaft. Diese Daten gilt es dann aufzubereiten und graphisch wiederzugeben. 


### Daten einlesen
Hier laden wir einen Datensatz zu einer Online-Umfrage:


```r
data <- read.csv("https://osf.io/meyhp/?action=download")
```

Der DOI für diesen Datensatz ist 10.17605/OSF.IO/4KGZH.

Der Datensatz besteht aus 10 Extraversions-Items (B5T nach Satow[^71]) sowie einigen Verhaltenskorrelaten (zumindest angenommenen). Uns interessieren also hier nur die 10 Extraversions-Items, die zusammen Extraversion als Persönlichkeitseigenschaft messen (sollen). Wir werden die Antworte der Befragten darstelle, aber uns hier keine Gedanken über Messqualität u.a. machen.


Die Umfrage kann hier[^8] eingesehen werden. Schauen wir uns die Daten mal an:

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




### Daten umstellen
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

### Diagramme für Anteile

Wir nutzen `ggplot2`, wie gesagt, und davon die Funktion `qplot` (q wie quick, nehme ich an.).


```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") 
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-37-1.png" width="70%" style="display: block; margin: auto;" />

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

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-39-1.png" width="70%" style="display: block; margin: auto;" />



### Um 90° drehen

Dazu nehmen wir `+ coord_flip()`, also "flippe das Koordinatensystem".

```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "fill") +
  coord_flip()
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-40-1.png" width="70%" style="display: block; margin: auto;" />


### Text-Labels für die Items

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

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-42-1.png" width="70%" style="display: block; margin: auto;" />


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

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-44-1.png" width="70%" style="display: block; margin: auto;" />


### Diagramm mit Häufigkeiten
Ach so, schön wäre noch die echten Zahlen an der Y-Achse, nicht Anteile. Dafür müssen wir unseren Diagrammtyp ändern, bzw. die Art der Anordnung ändern. Mit `position = "fill"` wird der Anteil (also mit einer Summe von 100%) dargestellt. Wir können auch einfach die Zahlen/Häufigkeiten anzeigen, in dem wir die Kategorien "aufeinander stapeln"



```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "stack") +
  coord_flip() +
  scale_x_discrete(labels = item_labels) 
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-45-1.png" width="70%" style="display: block; margin: auto;" />

### Farbschema
Ja, die Wünsche hören nicht auf... Also, noch ein anderes Farbschema:


```r
ggplot(data = data_long) +
  aes(x = items)  +
  geom_bar(aes(fill = Antwort), position = "stack") +
  coord_flip() +
  scale_x_discrete(labels = item_labels) +
  scale_fill_brewer(palette = 17)
```

<img src="050_Daten_visualisieren_files/figure-html/unnamed-chunk-46-1.png" width="70%" style="display: block; margin: auto;" />





## Verweise

- Edward Tufte gilt als Grand Seigneur der Datenvisualisierung; er hat mehrere lesenswerte Bücher zu dem Thema geschrieben [@1930824130; @1930824165; @1930824149].

- William Cleveland, ein amerikanischer Statistiker ist bekannt für seine grundlegenden, und weithin akzeptierten Ansätze für Diagramme, die die wesentliche Aussage schnörkellos transportieren [@Cleveland]. 




[^3]: Cleveland fände diese Idee nicht so gut.
[^4]: http://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3
[^5]: https://github.com/karthik/wesanderson
[^6]: http://sape.inf.usi.ch/quick-reference/ggplot2/colour
[^7]: https://www.ggplot2-exts.org
[^71]: https://www.zpid.de/pub/tests/PT_9006357_B5T_Forschungsbericht.pdf
[^8]: https://docs.google.com/forms/d/e/1FAIpQLSfD4wQuhDV_edx1WBfN3Qos7XqoVbe41VpiKLRKtGLeuUD09Q/viewform
[^9]: <https://de.wikipedia.org/wiki/Anscombe-Quartett>
[^10]: Achtung: Nicht `qqplot`, nicht `ggplot2`, nicht `gplot`...