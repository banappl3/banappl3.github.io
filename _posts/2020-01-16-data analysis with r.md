---
layout: post
title: Datenanalyse mit R
date: 2020-01-16
last_modified_at: 2023-02-11
cover_image: 2021-05-03-feature.jpg
author: Yongguang Lin
categories: data analysis
excerpt_separator: <!--more-->
---

> Photo by [Levi Stute](https://unsplash.com/@levi_stute_cinematography).

Unter Datenanalyse versteht man den Prozess der Bereinigung, Umwandlung und Modellierung von Daten, um daraus sinnvolle Erkenntnisse und Wissen zu gewinnen. R ist eine beliebte Programmiersprache für die Datenanalyse mit einem reichhaltigen Ökosystem von Bibliotheken und Tools, die die Durchführung komplexer Datenanalyse- und Modellierungsaufgaben erleichtern.
<!--more-->

# Datenanalyse
R ist eine beliebte Programmiersprache für Datenanalyse und statistische Berechnungen. Sie verfügt über ein reichhaltiges Ökosystem von Bibliotheken und Tools für die Durchführung komplexer Datenanalysen und Modellierungsaufgaben.

Im Folgenden werden einige der wichtigsten Bibliotheken und Tools des R-Ökosystems für die Datenanalyse vorgestellt:

- dplyr und tidyr: Bibliotheken zur Datenmanipulation, die eine schnelle und übersichtliche Möglichkeit bieten, Datenrahmen zu manipulieren und allgemeine Datenbereinigungs- und -umwandlungsaufgaben durchzuführen.

- ggplot2: Eine Bibliothek für die Datenvisualisierung, die eine breite Palette von Optionen für die Erstellung von Diagrammen, Plots und Visualisierungen zum besseren Verständnis der Daten bietet.

- caret: Eine Bibliothek für maschinelles Lernen, die eine einheitliche Schnittstelle für das Trainieren und Testen von Modellen mit einer Vielzahl von Algorithmen bietet.

- randomForest: Eine Bibliothek für Random Forests, die Funktionen zur Erstellung und Auswertung von Random-Forest-Modellen bietet.

- broom: Eine Bibliothek zum Aufräumen von Modellen, die eine bequeme Möglichkeit bietet, Informationen aus komplexen Modellen zu extrahieren und zu manipulieren.

- Shiny: Eine Bibliothek zur Erstellung interaktiver Webanwendungen, mit der Benutzer dynamische, interaktive Datenvisualisierungen und Dashboards erstellen können.

- R Markdown: Ein Dokumentformat, das R-Code und Text kombiniert, um reproduzierbare Berichte und Präsentationen zu erstellen.

Dies sind einige der am häufigsten verwendeten Bibliotheken im R-Datenanalytik-Ökosystem, aber es gibt noch viele weitere. Welche Bibliotheken und Tools Sie im Einzelnen verwenden, hängt von dem Problem ab, das Sie zu lösen versuchen, aber insgesamt bietet R eine leistungsstarke und flexible Plattform für Datenanalysen und statistische Berechnungen.

```r
# Load the necessary libraries
library(dplyr)
library(ggplot2)

# Load the data
data(mtcars)

# Filter the data to include only cars with a horsepower of more than 150
mtcars_filtered <- filter(mtcars, hp > 150)

# Calculate the mean miles per gallon for the filtered data
mean_mpg <- mean(mtcars_filtered$mpg)
print(mean_mpg)

# Visualize the relationship between horsepower and miles per gallon
ggplot(mtcars_filtered, aes(x = hp, y = mpg)) + geom_point() + geom_smooth(method = "lm")
```
In diesem Beispiel verwenden wir den in R enthaltenen Datensatz "mtcars" und filtern ihn so, dass er nur Autos mit einer Leistung von mehr als 150 PS enthält. Anschließend berechnen wir den durchschnittlichen Benzinverbrauch für die gefilterten Daten und visualisieren die Beziehung zwischen Leistung und Benzinverbrauch mithilfe eines Streudiagramms und einer linearen Regressionslinie.

Dies ist nur ein einfaches Beispiel, aber die "dplyr"-Bibliothek bietet eine breite Palette von Funktionen für die Datenmanipulation und -analyse, einschließlich Filtern, Aggregieren, Gruppieren und Verbinden von Daten, was sie zu einem leistungsstarken Werkzeug für die Datenexploration und -analyse macht.

# Prädiktive Analyse
Die prädiktive Analyse ist eine Art der Datenanalyse, die sich auf die Verwendung historischer Daten konzentriert, um Vorhersagen über zukünftige Ereignisse oder Trends zu treffen. R ist eine beliebte Programmiersprache für die prädiktive Analyse und verfügt über ein reichhaltiges Ökosystem von Bibliotheken und Tools, die die Durchführung komplexer prädiktiver Modellierungsaufgaben erleichtern.

Im Folgenden werden einige der wichtigsten Bibliotheken und Tools des R-Ökosystems für prädiktive Analysen vorgestellt:

- caret: Eine Bibliothek für maschinelles Lernen, die eine einheitliche Schnittstelle für das Trainieren und Testen von Modellen für eine breite Palette von Algorithmen, einschließlich Regression, Klassifizierung und Clustering, bietet.

- randomForest: Eine Bibliothek für Random-Forest-Modelle, die Funktionen zum Erstellen und Bewerten von Random-Forest-Modellen bereitstellt. Diese werden häufig in der prädiktiven Analyse verwendet, da sie große Datensätze verarbeiten und Vorhersagen auf der Grundlage nichtlinearer Beziehungen in den Daten machen können.

- glmnet: Eine Bibliothek für regularisierte Regressionsmodelle, wie z. B. Ridge- und Lassoregression, die Funktionen zum Erstellen und Bewerten von Modellen bietet, die große Datensätze und komplexe Beziehungen in den Daten verarbeiten können.

- xgboost: Eine Bibliothek für Gradient-Boosting, die Funktionen zum Erstellen und Bewerten von Gradient-Boosting-Modellen bereitstellt, die aufgrund ihrer Fähigkeit, große Datensätze und komplexe Beziehungen in den Daten zu verarbeiten, häufig in der prädiktiven Analyse verwendet werden.

- R Markdown: Ein Dokumentformat, das R-Code und Text kombiniert, um reproduzierbare Berichte und Präsentationen zu erstellen, die nützlich sind, um die Ergebnisse der prädiktiven Analyse den Beteiligten mitzuteilen.

Dies sind einige der am häufigsten verwendeten Bibliotheken im Ökosystem der prädiktiven Analyse mit R, aber es gibt noch viele andere. Welche Bibliotheken und Tools Sie im Einzelnen verwenden, hängt von dem Problem ab, das Sie zu lösen versuchen, aber insgesamt bietet R eine leistungsstarke und flexible Plattform für die prädiktive Analyse und Modellierung.

```r
# Load the necessary libraries
library(caret)
library(ggplot2)

# Load the data
data(mtcars)

# Split the data into a training set and a test set
set.seed(123)
index <- createDataPartition(mtcars$mpg, p = 0.7, list = FALSE)
train_data <- mtcars[index, ]
test_data <- mtcars[-index, ]

# Train a linear regression model on the training data
model <- train(mpg ~ ., data = train_data, method = "lm")

# Use the model to make predictions on the test data
predictions <- predict(model, test_data)

# Evaluate the model's performance
performance <- mean((test_data$mpg - predictions)^2)
print(performance)

# Visualize the model's predictions and actual values
ggplot(test_data, aes(x = predictions, y = mpg)) + geom_point() + geom_abline(intercept = 0, slope = 1)
```
In diesem Beispiel verwenden wir den in R enthaltenen Datensatz "mtcars" und unterteilen ihn in einen Trainings- und einen Testdatensatz. Anschließend trainieren wir ein lineares Regressionsmodell mit der Funktion "train" aus der "caret"-Bibliothek und erstellen Vorhersagen für die Testdaten mit der Funktion "predict". Schließlich bewerten wir die Leistung des Modells anhand des mittleren quadratischen Fehlers und stellen die Vorhersagen und die tatsächlichen Werte in einem Streudiagramm dar.

Dies ist nur ein einfaches Beispiel, aber die "caret"-Bibliothek bietet eine breite Palette von Funktionen und Optionen für komplexere Vorhersageanalyseaufgaben, einschließlich Modellauswahl, Kreuzvalidierung und Abstimmung.

#

```r
# Load the necessary libraries
library(dplyr)
library(ggplot2)

# Load the data
data(mtcars)

# Summarize the data to get the mean and standard deviation of each variable
summary_data <- mtcars %>%
  summarize_all(mean_sd)
print(summary_data)

# Visualize the distribution of miles per gallon
ggplot(mtcars, aes(x = mpg)) + geom_histogram(binwidth = 2) + geom_vline(xintercept = mean(mtcars$mpg), color = "red", linetype = "dashed")
```
In diesem Beispiel verwenden wir den in R enthaltenen Datensatz "mtcars" und fassen ihn zusammen, um den Mittelwert und die Standardabweichung jeder Variablen mithilfe der Funktion "summarize_all" aus der Bibliothek "dplyr" zu ermitteln. Anschließend visualisieren wir die Verteilung der Meilen pro Gallone mithilfe eines Histogramms und einer roten gestrichelten Linie für den Mittelwert.

Dies ist nur ein einfaches Beispiel, aber die "dplyr"-Bibliothek bietet eine breite Palette von Funktionen für die Datenmanipulation und -analyse, einschließlich des Zusammenfassens, Filterns, Aggregierens, Gruppierens und Verbindens von Daten, was sie zu einem leistungsstarken Werkzeug für die Datenexploration und -analyse macht.

# Advanced Analytics
Hier sind einige der Techniken, die in der Advanced Analytics mit R verwendet werden:

- Prädiktive Modellierung: R verfügt über mehrere Bibliotheken für die Erstellung und Auswertung von Vorhersagemodellen, wie "caret", "glmnet", "randomForest", "xgboost" und "lightgbm". Mit diesen Bibliotheken können Benutzer Modelle für Regression, Klassifizierung und Zeitreihenvorhersage erstellen.

- Maschinelles Lernen: R bietet mehrere Bibliotheken zur Implementierung von Algorithmen des maschinellen Lernens wie "caret", "e1071", "randomForest", "xgboost" und "mlr". Mit diesen Bibliotheken lassen sich gängige Algorithmen wie Entscheidungsbäume, Random Forests, Support Vector Machines, k-nearest neighbors und neuronale Netze implementieren.

- Text Mining und Verarbeitung natürlicher Sprache: R verfügt über mehrere Bibliotheken für Text Mining und die Verarbeitung natürlicher Sprache, wie z. B. "tm", "quanteda", "wordcloud" und "NLP". Mit diesen Bibliotheken können Benutzer Aufgaben wie Textbereinigung, Tokenisierung, Stemming und Sentimentanalyse durchführen.

- Dimensionalitätsreduktion: R bietet mehrere Bibliotheken zur Reduzierung der Dimensionalität von Daten, wie z. B. "PCA", "MDS", "tsne" und "umap". Diese Bibliotheken ermöglichen es den Benutzern, hochdimensionale Daten zur Visualisierung und Analyse auf niedrigere Dimensionen zu reduzieren.

- Zeitreihenanalyse: R verfügt über mehrere Bibliotheken für die Zeitreihenanalyse, wie z. B. "forecast", "prophet" und "tsoutliers". Mit diesen Bibliotheken können Benutzer Aufgaben wie die Trendanalyse, die Analyse der Saisonalität und die Erkennung von Ausreißern in Zeitreihendaten durchführen.

Dies ist nur ein Beispiel für die vielen Techniken, die in der Advanced Analytics mit R zur Verfügung stehen. R verfügt über ein reichhaltiges Ökosystem von Bibliotheken und Paketen für eine breite Palette von Data Science-Aufgaben, was es zu einer leistungsstarken Plattform für Advanced Analytics macht.

```r
# Load the necessary libraries
library(caret)
library(ggplot2)
library(dplyr)

# Load the data
data(mtcars)

# Split the data into training and test sets
set.seed(123)
split_index <- createDataPartition(mtcars$mpg, p = 0.7, list = FALSE)
train_data <- mtcars[split_index, ]
test_data <- mtcars[-split_index, ]

# Train a random forest model
model <- train(mpg ~ ., data = train_data, method = "rf")

# Make predictions on the test data
predictions <- predict(model, newdata = test_data)

# Evaluate the model
confusion_matrix <- confusionMatrix(predictions, test_data$mpg)
print(confusion_matrix)

# Visualize the model performance
ggplot(test_data, aes(x = mpg, y = predictions)) + geom_point() + geom_abline(slope = 1, intercept = 0, color = "red")
```

In diesem Beispiel verwenden wir den Datensatz "mtcars" und unterteilen ihn in einen Trainings- und einen Testsatz. Anschließend verwenden wir die Funktion "train" aus der Bibliothek "caret", um ein Random-Forest-Modell zu trainieren, das auf der Grundlage der anderen Variablen im Datensatz Meilen pro Gallone (mpg) vorhersagt. Nach den Vorhersagen für die Testdaten wird das Modell mit der Funktion "confusionMatrix" ausgewertet und die Leistung des Modells in einem Streudiagramm mit einer roten Linie dargestellt, die die perfekten Vorhersagen repräsentiert.

Dies ist nur ein einfaches Beispiel, aber die "caret"-Bibliothek bietet eine breite Palette von Funktionen für das Trainieren, Abstimmen und Auswerten von Modellen, was sie zu einem leistungsstarken Werkzeug für die Vorhersagemodellierung in R macht.

# Data Science with R
Data Science ist der Prozess der Nutzung von Daten, statistischen Algorithmen und maschinellen Lerntechniken, um aus Daten aussagekräftige Erkenntnisse und Wissen zu gewinnen. Hier ist ein Beispiel für die Durchführung von Data-Science-Aufgaben in R mit den "tidyverse"-Bibliotheken:
```r
# Load the necessary libraries
library(tidyverse)

# Load the data
data(mtcars)

# Explore the data
head(mtcars)
summary(mtcars)
ggplot(mtcars, aes(x = wt, y = mpg)) + geom_point()

# Transform the data
mtcars_transformed <- mtcars %>% 
  mutate(cyl = as.factor(cyl), am = as.factor(am)) %>% 
  select(-vs)

# Train a linear regression model
model <- lm(mpg ~ ., data = mtcars_transformed)

# Make predictions
predictions <- predict(model, newdata = mtcars_transformed)

# Evaluate the model
residuals <- residuals(model)
ggplot(mtcars_transformed, aes(x = predictions, y = residuals)) + geom_point()

# Apply the model to new data
new_data <- data.frame(wt = 5, qsec = 17, cyl = 6, am = 0)
predict(model, newdata = new_data)
```
In diesem Beispiel verwenden wir den Datensatz "mtcars" und untersuchen ihn, indem wir uns die ersten Zeilen und eine Zusammenfassung der Variablen ansehen. Wir erstellen auch ein Streudiagramm, um die Beziehung zwischen Gewicht (wt) und Meilen pro Gallone (mpg) zu visualisieren. Als Nächstes transformieren wir die Daten, indem wir Faktoren für die Anzahl der Zylinder (cyl) und den Getriebetyp (am) erstellen und die Variable "vs" entfernen. Anschließend trainieren wir ein lineares Regressionsmodell zur Vorhersage von mpg auf der Grundlage der anderen Variablen. Nach den Vorhersagen für die ursprünglichen Daten bewerten wir das Modell, indem wir ein Streudiagramm der Residuen erstellen und die Kilometerleistung für einen neuen Datensatz vorhersagen.

Dies ist nur ein einfaches Beispiel, aber die "tidyverse"-Bibliotheken bieten eine breite Palette von Funktionen für die Datenexploration, -transformation, -modellierung und -visualisierung, was sie zu einem leistungsstarken Werkzeug für die Datenwissenschaft in R macht.