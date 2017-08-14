---
title       : Übungsblatt 1
description : Grundlagen, Datensatztypen
attachments :
slides_link : https://www.dropbox.com/s/kabya657zvc4kga/U1.pdf





--- type:NormalExercise lang:r xp:50 skills:1 key:2f1c6f32e6
## Spendenbeispiel - Aufgabe 1.1
Für die Familien Meier, Schmidt und Huber kennen wir das jeweilige Jahreseinkommen und
die getätigten Spenden des Jahres 2014 (in Euro). Diese informationen sind im Datensatz  `salary` vorhanden.

Wir gehen davon aus, dass zwischen dem Jahreseinkommen und den Spenden der proportionale Zusammenhang
`y = beta*x`
besteht, wobei `y` die Spende und `x` das Jahreseinkommen der jeweiligen Familie darstellen.


*** =instructions
- Verschaffen Sie einen ersten Überblick über den Datensatz `salary`.
- Welchen Anteil ihres Jahreseinkommens haben die einzelnen Familien jeweils gespendet? Definieren Sie zu diesem
Zweck ein neues dreielementiges R-Objekt `x14` mit den Jahreseinkommen der drei Familien
und das entsprechende Objekt `y14` mit den jeweiligen Spenden. Speichern Sie die
drei berechneten Anteile im Objekt `anteile` und lassen Sie sich das Objekt anzeigen.
- Berechnen Sie, welcher Anteil des Jahreseinkommens im Durchschnitt der drei Familien
gespendet wurde? Speichern Sie Ihren Schätzwert unter dem Objektnamen `beta.dach`.
- Welchen Spendenbetrag würden Sie auf Basis Ihres Schätzwertes `beta.dach` bei einer Familie
mit einem Jahreseinkommen von 50000 Euro erwarten?
*** =hint
Verwenden Sie den befehl `str` um den ersten Überblick über einen fremden Datensatz zu verschaffen. 

*** =pre_exercise_code
```{r}
x <- c(28000, 84000, 42000)
y <- c(70, 252, 84)
salary <- data.frame(x, y) 
```

*** =sample_code
```{r}
# Verschaffe den ersten Überblick über den Datensatz salary:

# Definiere x14 als Jahreseinkommen und y14 als Spenden: 

# Berechne die Anteile des Jahreseinkommens, die gespendet wurden und speichere es unter dem Objekt anteile:

# Berechne welcher Anteil des Jahreseinkommens im Durchschnitt der drei Familien gespendet wurde?

# Erwarteter Spendebetrag bei einer Familie mit 50000 Euro Einkommen:

```

*** =solution
```{r}
# Verschaffe den ersten Überblick über den Datensatz salary:
str(salary)
# Definiere x14 als Jahreseinkommen und y14 als Spenden: 
x14 <- salary$x
y14 <- salary$y
# Berechne die Anteile des Jahreseinkommens, die gespendet wurden und speichere es unter dem Objekt anteile:
anteile <- y14/x14
# Berechne welcher Anteil des Jahreseinkommens im Durchschnitt der drei Familien gespendet wurde?
beta.dach <- mean(anteile)
# Erwarteter Spendebetrag bei einer Familie mit 50000 Euro Einkommen:
beta.dach * 50000
```

*** =sct
```{r}
test_function("str", args = "object",
              not_called_msg = "Verwende die Funktion `str()`!",
              incorrect_msg = "Verwende `str(object = ...)` mit dem Korrekten Argument, `object`.")
test_object("x14")
test_object("y14")
test_object("anteile")
test_object("beta.dach")
test_output_contains("beta.dach * 50000", 
incorrect_msg = "Ihre Berechnung war falsch. Tippen Sie `beta.dach * 50000` an!")
test_error()

success_msg("Fantastisch! Du hast deine ersten Punkte verdient.
Bleib dabei und lerne weiter mit unserem interaktiven Öko-Kurs!")
```



--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:7806ca24d2
## Spendenbeispiel - Aufgabe 1.2

Der in vorangegangen Aufgabenteil berechnete Durchschnittswert (`0.0025`) könnte als der Schätzwert des
unbekannten Parameters `beta` aufgefasst werden. Ein Verhaltensforscher vertritt die Hypothese,
dass im Durchschnitt etwa `0.5` Prozent des Jahreseinkommens gespendet werden.
Halten Sie diese Hypothese angesichts des von Ihnen berechneten Schätzwertes von `0.0025`
für plausibel?

*** =instructions
- Die obige Schätzung erfolgte auf Basis weniger Daten (drei Beobachtungen), sodass die Abweichung zu der Hypothese des Verhaltensforschers auch zufällig aufgetreten sein könnte.
- Die Hypothese des Verhaltensforscher stimmt und kann nicht widerlegt werden, weil die eine Spendenneigung von 0.5% normal ist.
- Die Schätzung folgt nicht nach einer Kleinstquadrat-Methode und deshalb ist wenig wahrhaft.
- Der Verhaltensforscher hat eine falsche Hypothese aufgestellt.

*** =hint
Die Beobachtungszahl ist für die korrekte Beantwortung dieser Aufgabe relevant!

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg1 <- "Korrekt! Unsere Schätzung beruht nur auf wenige Beobachtungen und kann nicht aussagekräftig sein!"
msg2 <- "Falsch"
msg3 <- "Falsch"
msg4 <- "Falsch"
test_mc(correct = 1, feedback_msgs = c(msg1, msg2, msg3, msg4))
```













--- type:NormalExercise lang:r xp:100 skills:1 key:1b80bb2a7d
## Spenden - Aufgabe 1.3
Sie erhalten für die drei Familien auch die Daten der Jahre 2012 und 2013 (in Euro). Die Informationen sind in Vektoren `x12`,`x13` für Einkommen und `y12`, `y13` für Spenden der jeweiligen Jahre abgespeichert.  

*** =instructions
- Fassen Sie die vier Vektoren in eine Matrix mit dem Namen `salary.panel` zusammen. Verwenden Sie dafür den Befehl `cbind`.
- Benennen Sie die Spalten von `salary.panel`  mit den folgenden Namen: `x2012`, `y2012` und `x2013`, `y2013`. Verwenden Sie dabei den Befehl `colnames()`. 
- Benennen Sie die Zeilen von `salary.panel` mit den drei Familiennamen `Meier`, `Schmidt` und `Hubert`. Verwenden Sie dabei den Befehl `rownames()`. 
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Einkommen- und Spendevektoren sind für Sie bereits erzeugt:
x12 <- c(30000, 84000, 40000)
y12 <- c(90, 252, 120)
x13 <- c(34000, 88000, 41000)
y13 <- c(50, 252, 100)

# Fassen Sie die Vektoren in eine Matrix mit dem Namen salary.panel zusammen:

# Benennen Sie die Spalten der Matrix salary.panel :

# Benennen Sie die Zeilen der Matrix salary.panel :

# Wiedergabe der Matrix:

```

*** =solution
```{r}
# Einkommen- und Spendevektoren sind für Sie bereits erzeugt:
x12 <- c(30000, 84000, 40000)
y12 <- c(90, 252, 120)
x13 <- c(34000, 88000, 41000)
y13 <- c(50, 252, 100)

# Fassen Sie die Vektoren in eine Matrix mit dem Namen salary.panel zusammen:
salary.panel <- cbind(x12, y12, x13, y13)
# Benennen Sie die Spalten der Matrix salary.panel :
colnames(salary.panel) <- c("x2012", "y2012", "x2013", "y2013")
# Benennen Sie die Zeilen der Matrix salary.panel :
rownames(salary.panel) <- c("Meier", "Schmidt", "Huber")
# Wiedergabe der Matrix:
salary.panel
```

*** =sct
```{r}
test_object("salary.panel")
test_function("colnames", "x")
test_function("rownames", "x")
success_msg("Bellissimo!")
```









--- type:NormalExercise lang:r xp:200 skills:1 key:9f8402e32e
## Trinkgeldbeispiel - Aufgabe 1.1
Die Gäste eines Restaurants hinterlassen dem Kellner mehr oder weniger hohe Trinkgeldbeträge.
Da der Kellner zu allen Gästen gleichbleibend freundlich ist, kann er sich die Unterschiede
in den Trinkgeldbeträgen nicht erklären. Er beauftragt deshalb einen befreundeten
Ökonometriker, die Ursache für die *Betragsschwankungen* herauszufinden. Dieser vermutet,
dass das Trinkgeld `y` eines Gastes durch den Rechnungsbetrag (`x`) dieses Gastes bestimmt
wird. Nehmen wir an, dass wir im Laufe des Abends zwei Gäste mit den folgenden
Daten beobachtet haben (jeweils in Euro):

```
Gast 1:  (x1, y1) = (10, 2)
Gast 2:  (x2, y2) = (30, 3)
```

*** =instructions
- Geben Sie zunächst den Befehl `rm(list=ls())` ein. Dieser Befehl ist lediglich eine
Vorsichtsmaßnahme. Er löscht alle im Arbeitsspeicher von R eventuell noch von früheren
Sitzungen enthaltenen Befehle und Objekte.
- Erstellen Sie anschließend in R aus den gegebenen Daten ein Objekt mit dem Namen `kellner`, das zeilenweise zwischen
Gästen und spaltenweise zwischen Rechnungsbetrag und Trinkgeld unterscheidet. Verwenden Sie hierfür entweder `rbind` oder `cbind`. Lassen Sie sich anschließend den Datensatz `kellner` anzeigen. 
- Gehen Sie von einem proportionalen Zusammenhang aus `y = beta*x` und berechnen
Sie in R separat für jede der beiden Beobachtungen das passende `beta1.dach` und `beta2.dach`. Bilden Sie
anschließend den Durchschnitt aus den beiden Werten und geben Sie diesem Wert
die Bezeichnung `beta.dach`.
- Berechnen Sie in R für die Rechnungsbeträge `10` und `30` Euro das in einer Welt ohne
Störeinflüsse zu erwartende Trinkgeld `y.dach`. Welche Störgrößenwerte sind gemäß unserer
bisherigen Berechnungen bei den zwei beobachteten Gästen eingetreten? Berechnen Sie die geschätzten Sörungen und speichern Sie letztere unter `u.dach` ab.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Entferne alle zuvor erzeugten Objekte aus dem R-Arbeitsspeicher:

# Definiere den Datensatz kellner: 

# Wiedergabe des Datensatzes:


# Berechne beta1.dach und lass es anzeigen:


# Berechne beta2.dach und lass es anzeigen:


# Berechne den Durchschnitt aus beiden beta.dach werten:


# Berechne die geschätzten Trinkgeldbeträge

# Berechne die Residuen:

```

*** =solution
```{r}
# Entferne alle zuvor erzeugten Objekte aus dem R-Arbeitsspeicher:
rm(list=ls())
# Definiere den Datensatz kellner: 
kellner <- rbind(c(10,2), c(30,3))
# Wiedergabe des Datensatzes:
kellner

# Berechne beta1.dach und lass es anzeigen:
beta1.dach <- 2/10
beta1.dach
# Berechne beta2.dach und lass es anzeigen:
beta2.dach <- 3/30
beta2.dach
# Berechne den Durchschnitt aus beiden beta.dach werten:
beta.dach <- mean(c(beta1.dach, beta2.dach))

# Berechne die geschätzten Trinkgeldbeträge
y.dach <- beta.dach*c(10,30)

# Berechne die Residuen:
u.dach <- c(2,3) - y.dach
```

*** =sct
```{r}
test_object("kellner")
test_object("beta1.dach")
test_object("beta2.dach")
test_object("beta.dach")
test_object("y.dach")
test_object("u.dach")
success_msg("Sehr gut!")

```
