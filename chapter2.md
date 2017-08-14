---
title       : Übungsblatt 2
description : Annahmen des einfachen linearen Regressionsmodells, Erwartungswert und Varianz von Zufallsvariablen, Wiederholte Stichproben und Normalverteilung

--- type:NormalExercise lang:r xp:100 skills:1 key:3f15f6c27a
## Würfelbeispiel - Aufgabe 2.1
Berechnen Sie mit den Erwartungswert der Zufallsvariable `u1 = Geworfene Augenzahl bei einmaligem Würfeln` und geben Sie dem Erwartungswert den Namen `E.u1`. Definieren Sie zu diesem Zweck im Quelltext-Fenster den Vektor `u1`, welcher die sechs möglichen Ausprägungen der Zufallsvariable `u1` enthält und nutzen Sie den Befehl `mean(u1)`, der das arithmetische Mittel des Vektors `u1` berechnet. Lassen Sie sich den Wert von `E.u1` anzeigen.

*** =instructions
1. Erzeugen Sie einen Vektor `u1`, der alle möglichen Ausprägungen bei einmaligem Würfeln annehmen könnte.
2. Mithilfe des Befehls `mean` berechnen Sie den Erwartungswert der Zufallsvariable `u1`.
3. Führe ein Experiment durch, indem es zehnmal gewürfelt wird. Verwenden Sie hierfür den Befehl `sample` und setzen Sie dabei das Argument `replace=TRUE`. Um mehr über die Funktionalität des Befehls zu erfahren, geben Sie `help(sample)` oder `?sample` in der R-Konsole an. Anschließend speichern Sie die Ergebnisse der zehnmaligen Würfeln unter dem Objektsnamen `wuerfeln.1` ab. 
4. Berechnen Sie den Durchschnitt aus den zehn geworfenen Werten.
5. Erzeugen Sie eine Stichprobe mit 10000-maligem Würfeln. Speichern Sie die Werte unter dem Objektnamen `wuerfeln.2` ab. Anschließend berechnen Sie den Durchschnitt aus 10000 Ausprägungen.
6.  Berechne die Abweichungen der sechs möglichen Ausprägungen vom Erwartungswert und speichern Sie die Ergebnisse unter dem Namen `abweichung.u1` ab.
7.  Berechnen Sie die Varianz der Zufallsvariable `u1` und speichern Sie es unter dem Namen `Var.u1` ab. Beachten Sie bitte, dass der Befehl `var` die Stichproben-Varianz und nicht die Varianz der Zufallsvariable berechnet.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# 1. Definiere die möglichen Ausprägungen der Zufallsvariable u1:
 
# 2. Berechne den Erwartungswert der Zufallsvariable u1:
   

# 3. Erzeuge eine Stichprobe für 10-maliges Würfeln-Experiment und speichere die Realisationen unter dem Namen wuerfeln.1:

# 4. Berechnen den Durchschnitt aus den geworfenen Werten:


# 5. Erzeuge eine Stichprobe für 10000-maliges Würfeln und gib ihm den Namen wuerfeln.2:


# 5. Berechnen den Durchschnitt aus den geworfenen Werten:


# Fazit: Mit Erhöhung des Stichprobenumfangs, nähert sich der Mittelwert dem Erwartungswert an.

# 6. Berechne die Abweichungen der sechs möglichen Ausprägungen vom Erwartungswert:

# 7. Berechne die Varianz der Zufallsvariable u1:

```

*** =solution
```{r}
# Definiere die möglichen Ausprägungen der Zufallsvariable u1:
u1 <- c(1,2,3,4,5,6)  
# Berechne den Erwartungswert der Zufallsvariable u1:
E.u1 <- mean(u1)      


# Erzeuge eine Stichprobe für 10-maliges Würfeln-Experiment und speichere die Realisationen unter dem Namen wuerfeln.1:
wuerfeln.1 <- sample(u1, size = 10, replace = TRUE)
# Berechnen den Durchschnitt aus den geworfenen Werten:
mean(wuerfeln.1)

# Erzeuge eine Stichprobe für 10000-maliges Würfeln und gib ihm den Namen wuerfeln.2:
wuerfeln.2 <- sample(u1, size = 10000, replace = TRUE)

# Berechnen den Durchschnitt aus den geworfenen Werten:
mean(wuerfeln.2)

# Fazit: Mit Erhöhung des Stichprobenumfangs, nähert sich der Mittelwert dem Erwartungswert an.

# Berechne die Abweichungen der sechs möglichen Ausprägungen vom Erwartungswert:
abweichung.u1 <- u1 - E.u1
# Berechne die Varianz der Zufallsvariable u1:
Var.u1 <- mean(abweichung.u1^2)
```

*** =sct
```{r}
test_object("u1")
test_object("E.u1 ")
test_object("wuerfeln.1")
test_function("mean", args="x")
test_object("wuerfeln.2")
test_function("mean", args="x")
test_object("abweichung.u1")
test_object("Var.u1")
success_msg("Sehr gut. Weiter so!")
```
