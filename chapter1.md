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
gespendet wurde? Speichern Sie Ihren Schätzwert unter dem Objektnamen `betadach`.
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
test_error()

success_msg("Fantastisch! Du hast deine ersten Punkte verdient.
Bleib dabei und lerne weiter mit unserem interaktiven Öko-Kurs!")
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:7806ca24d2
## What's that data type?

Der in vorangegangen Aufgabenteil berechnete Durchschnittswert (`0.0025`) könnte als der Schätzwert des
unbekannten Parameters `beta` aufgefasst werden. Ein Verhaltensforscher vertritt die Hypothese,
dass im Durchschnitt etwa `0.5` Prozent des Jahreseinkommens gespendet werden.
Halten Sie diese Hypothese angesichts des von Ihnen berechneten Schätzwertes von `0.0025`
für plausibel?

In the workspace (you can see what it contains by typing [`ls()`](http://www.rdocumentation.org/packages/base/functions/ls) in the console), some variables have already been defined. Which statement concerning these variables are correct?

*** =instructions
- `a`'s class is `integer`, `b` is a `character`, `c` is a `boolean`.
- `a`'s class is `character`, `b` is a `character` as well, `c` is a `logical`.
- `a`'s class is `numeric`, `b` is a `string`, `c` is a `logical`.
- `a`'s class is `numeric`, `b` is a `character`, `c` is a `logical`.

*** =hint
You can find out the data type of the `a` variable for example by typing `class(a)`. You can do similar things for `b` and `c`.

*** =pre_exercise_code
```{r}
a <- 42
b <- "forty-two"
c <- FALSE
```

*** =sct
```{r}
msg1 <- "`boolean` is not the class for logical values. Try again."
msg2 <- "`a` is of the class `numeric`, give it another go."
msg3 <- "`string` is not a class in R. `character` is!"
msg4 <- "Nice one. Let's step it up a notch and start coercing variables!"
test_mc(correct = 4, feedback_msgs = c(msg1, msg2, msg3, msg4))
```
