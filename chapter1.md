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

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ec4c028f5b
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
```

*** =sct
```{r}
```
*** =sct
```{r}

msg_bad = 'Ihre Auswahl ist leider nicht korrekt, versuchen Sie erneut!'
msg_success = 'Ganz genau! Anhand nur wenigen Beobachtungen lässt sich keine fundamentale Aussage widerlegen.'
test_mc(correct = 1, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))

```






