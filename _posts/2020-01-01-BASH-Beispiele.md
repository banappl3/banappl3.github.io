---
layout: post
title: Bash Script Beispiele
date: 2020-01-01
last_modified_at: 2023-02-10
cover_image: 2022-01-04-feature.png
author: Yongguang Lin
categories: bash
excerpt_separator: <!--more-->
---
Bash-Skripte können für verschiedene Zwecke verwendet werden, z. B. um einen Shell-Befehl auszuführen, mehrere Befehle gleichzeitig auszuführen, administrative Aufgaben 
anzupassen, Aufgaben zu automatisieren usw. Daher ist es für jeden Linux-Benutzer wichtig, die Grundlagen der Bash-Programmierung zu kennen. Dieser Artikel wird Ihnen 
helfen, die Grundlagen der Bash-Programmierung zu verstehen..

<!--more-->

Die meisten gängigen Operationen der Bash-Programmierung werden hier mit sehr einfachen Beispielen erklärt. Folgende Themen der Bash-Programmierung werden in diesem Artikel behandelt:
- Hello World
- Kommentaren
- Mehrzeilige Kommentare
- While-Schleife
- For-Schleife
- Benutzereingabe
- Funktion

---
## Hello World
Sie können ein Bash-Skript vom Terminal aus oder durch Ausführen einer beliebigen Bash-Datei ausführen. Führen Sie den folgenden Befehl über das Terminal aus, 
um eine sehr einfache Bash-Anweisung auszuführen. Die Ausgabe des Befehls wird "Hello World" sein.

```cmd
$ echo "Hello World"
```
Öffnen Sie einen beliebigen Editor, um eine Bash-Datei zu erstellen. Hier wird der nano-Editor verwendet, um die Datei zu erstellen, und der Dateiname wird 
als "first.sh" festgelegt
```cmd
$ nano first.sh
```
Fügen Sie der Datei das folgende Bash-Skript hinzu und speichern Sie die Datei.
```cmd
#!/bin/bash
echo "Hello World"
```
Sie können die Bash-Datei auf zwei Arten ausführen. Zum einen können Sie den Bash-Befehl verwenden, zum anderen können Sie die Ausführungsberechtigung für die 
Bash-Datei festlegen und die Datei ausführen. Beide Wege werden hier gezeigt.
```cmd
$ bash first.sh
```
Oder:
```cmd
$ chmod a+x first.sh
$ ./first.sh
```
---
## Verwendung von Kommentaren
Das Symbol '#' wird verwendet, um einen einzeiligen Kommentar in ein Bash-Skript einzufügen. Erstellen Sie eine neue Datei mit dem Namen "comment.sh" 
und fügen Sie das folgende Skript mit einzeiligem Kommentar hinzu.
```cmd
#!/bin/bash

# Add two numeric value
((sum=20+30))

#Print the result
echo $sum
```
Führen Sie die Datei mit dem Bash-Befehl aus.
```cmd
$ bash comment.sh
```
---
## Verwendung von mehrzeiligen Kommentaren:

Sie können mehrzeilige Kommentare in der Bash auf verschiedene Arten verwenden. Ein einfacher Weg wird im folgenden Beispiel gezeigt. Erstellen Sie eine neue Bash 
mit dem Namen 'multiline-comment.sh' und fügen Sie das folgende Skript hinzu. Hier werden die Symbole ':' und " ' " verwendet, um einen mehrzeiligen Kommentar in ein
Bash-Skript einzufügen. Das folgende Skript wird das Quadrat von 5 berechnen.
```cmd
#!/bin/bash
: '
The following script calculates
the square value of the number, 7.
'
((area=7*7))
echo $area
```
---
## Verwendung der While-Schleife:

Erstellen Sie eine Bash-Datei mit dem Namen 'while.sh', um die Verwendung der while-Schleife kennenzulernen. In diesem Beispiel wird die while-Schleife 5 Mal durchlaufen. Der Wert der Variablen count wird bei jedem Schritt um 1 erhöht. Wenn der Wert der Zählvariablen 5 beträgt, wird die while-Schleife beendet.
```cmd
#!/bin/bash
valid=true
count=1
while [ $valid ]
do
echo $count
if [ $count -eq 5 ];
then
break
fi
((count++))
done
```
---
## Verwendung von For-Schleife:

Die grundlegende for-Schleifen-Deklaration wird im folgenden Beispiel gezeigt. Erstellen Sie eine Datei mit dem Namen 'for.sh' und fügen Sie das folgende Skript mit 
der for-Schleife ein. Hier wird die for-Schleife 10-mal durchlaufen und alle Werte der Variable "counter" in einer einzigen Zeile ausgeben.
```cmd
#!/bin/bash
for (( counter=10; counter>0; counter-- ))
do
echo -n "$counter "
done
printf "\n"
```
---
## Benutzereingabe erhalten:

Der Befehl 'read' wird verwendet, um Eingaben vom Benutzer in der Bash zu erhalten. Erstellen Sie eine Datei mit dem Namen 'user_input.sh' und fügen Sie das folgende Skript hinzu, um Eingaben vom Benutzer entgegenzunehmen. Hier wird ein String-Wert vom Benutzer genommen und der Wert durch die Kombination anderer String-Werte angezeigt.
```cmd
#!/bin/bash
echo "Enter Your Name"
read name
echo "Welcome $name"
```
---
## Funktion mit Parametern:
Die Bash kann keine Funktionsparameter oder Argumente zum Zeitpunkt der Funktionsdeklaration angeben. Aber Sie können Parameter in der Funktion verwenden, indem Sie andere Variablen verwenden. Wenn zwei Werte zum Zeitpunkt des Funktionsaufrufs übergeben werden, werden die Variablen $1 und $2 zum Lesen der Werte verwendet. Erstellen Sie eine Datei mit dem Namen 'function.sh' und fügen Sie den folgenden Code ein. Hier wird die Funktion 'Rectangle_Area' die Fläche eines Rechtecks auf der Grundlage der Parameterwerte berechnen.

```cmd
#!/bin/bash

Rectangle_Area() {
area=$(($1 * $2))
echo "Area is : $area"
}

Rectangle_Area 10 20
```

