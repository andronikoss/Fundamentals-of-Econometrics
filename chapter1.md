---
title       : Übungsblatt 1
description : Grundlagen, Datensatztypen
attachments :
slides_link : https://www.dropbox.com/s/kabya657zvc4kga/U1.pdf





--- type:NormalExercise lang:r xp:50 skills:1 key:2f1c6f32e6
## Aufgabe 1
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
## Aufgabe 2

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
## Aufgabe 3
Sie erhalten für die drei Familien auch die Daten der Jahre 2012 und 2013 (in Euro). Die Informationen sind in Vektoren `x12`,`x13` für Einkommen und `y12`, `y13` für Spenden der jeweiligen Jahre abgespeichert.  

*** =instructions
- Fassen Sie die vier Vektoren in eine Matrix mit dem Namen `salary.panel` zusammen. Verwenden Sie dafür den Befehl `cbind`.
- Benennen Sie die Spalten von `salary.panel`  mit den folgenden Namen: `x2012`, `y2012` und `x2013`, `y2013`. Verwenden Sie dabei den Befehl `colnames()`. 
- Benennen Sie die Zeilen von `salary.panel` mit den drei Familiennamen `Meier`, `Schmidt` und `Hubert`. Verwenden Sie dabei den Befehl `rownames()`. 
*** =hint

*** =pre_exercise_code
```{r}
# Einkommen- und Spendevektoren sind für Sie bereits erzeugt:
x12 <- c(30000, 84000, 40000)
y12 <- c(90, 252, 120)
x13 <- c(34000, 88000, 41000)
y13 <- c(50, 252, 100)

# Fassen Soe die Vektoren in eine Matrix mit dem Namen salary.panel zusammen:

# Benennen Sie die Spalten der Matrix salary.panel :

# Benennen Sie die Zeilen der Matrix salary.panel :


```

*** =sample_code
```{r}

x12 <- c(30000, 84000, 40000)
y12 <- c(90, 252, 120)
x13 <- c(34000, 88000, 41000)
y13 <- c(50, 252, 100)


salary.panel <- cbind(x12, y12, x13, y13, x14 ,y14)
colnames(salary.panel) <- c("x2012", "y2012", "x2013", "y2013", "x2014", "y2014")
rownames(salary.panel) <- c("Meier", "Schmidt", "Huber")
spenden
```

*** =solution
```{r}

```

*** =sct
```{r}

```
