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
$$y_{t}=\beta x_{t}$$ 
besteht, wobei $y_{t}$ die Spende und $$ x_{t} $$ das Jahreseinkommen der Familie
$t$ darstellen.

*** =instructions
- Verschaffen Sie einen ersten Überblick über den Datensatz `salary`.
- Verwenden Sie den Befehl `plot()`, um eine Punktwolke zu erzeugen. Geben Sie dabei auf der horizontalen Achse die Werte von  `salary$Einkommen` und auf der vertikalen Achse `salary$Spenden` an.

*** =hint
Verwenden Sie den befehl `str` um den ersten Überblick über einen fremden Datensatz zu verschaffen. 

*** =pre_exercise_code
```{r}
x14 <- c(28000, 84000, 42000)
y14 <- c(70, 252, 84)
salary <- data.frame(Einkommen = x14, Spenden = y14) 
```

*** =sample_code
```{r}
# Verschaffe den ersten Überblick über den Datensatz salary:


# Erzeuge die Punktwolke mit dem plot-Befehl:


```

*** =solution
```{r}
# Verschaffe den ersten Überblick über den Datensatz salary:
str(salary)

# Erzeuge die Punktwolke mit dem plot-Befehl:
plot(salary$Einkommen, salary$Spenden)
```

*** =sct
```{r}
test_function("str", args = "object",
              not_called_msg = "Verwende die Funktion `str()`!",
              incorrect_msg = "Verwende `str(object = ...)` mit dem Korrekten Argument, `object`.")

test_function("plot", args = "x")
test_function("plot", args = "y")

test_error()

success_msg("Fantastisch! Bleib dabei und lerne weiter mit unserem interaktiven Öko-Kurs!")
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8d6675ca91
## Aufgabe 


*** =instructions
- Adventure
- Action
- Animation
- Comedy

*** =hint
Have a look at the plot. Which color does the point with the lowest rating have?

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

library(ggplot2)

ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```















