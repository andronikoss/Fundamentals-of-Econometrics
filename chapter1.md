---
title       : Einfaches lineares Regressionsmodell
description : Insert the chapter description here
attachments :
slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8d6675ca91
## Aufgabe 1

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

--- type:NormalExercise lang:r xp:100 skills:1 key:0f9294ed70
## More movies

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```



--- type:NormalExercise lang:r xp:100 skills:1 key:2f1c6f32e6
## Aufgabe 1
Für die Familien Meier, Schmidt und Huber kennen wir das jeweilige Jahreseinkommen und
die getätigten Spenden des Jahres 2014 (in Euro). Diese informationen sind im Datensatz  `salary` vorhanden.


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
