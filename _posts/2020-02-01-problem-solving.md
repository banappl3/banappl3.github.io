---
layout: post
title: Problemlösen mit Algorithmen und Datenstrukturen
date: 2020-02-01
last_modified_at: 2023-02-11
cover_image: 2021-05-03-feature.jpg
author: Yongguang Lin
categories: solving problems
excerpt_separator: <!--more-->
---

> Photo by [Levi Stute](https://unsplash.com/@levi_stute_cinematography).

Die Art und Weise, wie wir über das Programmieren denken, hat sich in den Jahren seit den ersten elektronischen Computern, die Verbindungskabel und Schalter benötigten, um Anweisungen von Menschen an Maschinen zu übermitteln, stark verändert. Wie in vielen anderen Bereichen der Gesellschaft bieten die Veränderungen in der Computertechnologie auch den Informatikern eine wachsende Anzahl von Werkzeugen und Plattformen, auf denen sie ihr Handwerk ausüben können. 
<!--more-->
Fortschritte wie schnellere Prozessoren, Hochgeschwindigkeitsnetzwerke und große Speicherkapazitäten haben eine Spirale der Komplexität geschaffen, durch die sich IT Experte bewegen müssen. Bei all dieser rasanten Entwicklung sind einige Grundprinzipien konstant geblieben. Die Informatik befasst sich mit dem Einsatz von Computern zur `Lösung von Problemen`. Sie haben zweifellos viel Zeit damit verbracht, die Grundlagen des Problemlösens zu erlernen, und sind hoffentlich zuversichtlich, dass Sie in der Lage sind, eine Problemstellung zu erfassen und eine Lösung zu entwickeln. Sie haben auch gelernt, dass das Schreiben von Computerprogrammen oft schwierig ist. Die `Komplexität von großen Problemen` und die entsprechende Komplexität der Lösungen können dazu führen, dass die grundlegenden Ideen im Zusammenhang mit dem Problemlösungsprozess.

<!--more-->

In diesem Artikel werden zwei wichtige Bereiche für den Rest des Textes hervorgehoben. 

  - Erstens wird der Rahmen erläutert, in den sich das Studium von `Algorithmen und Datenstrukturen` einfügen müssen, insbesondere die Gründe, warum wir diese Themen studieren müssen und wie das Verständnis dieser Themen uns hilft, bessere Problemlöser zu werden. 

  - Zweitens geben wir einen Überblick über die `Programmiersprache Python`. Obwohl wir keine detaillierte, erschöpfende Referenz bieten können, werden wir Beispiele und Erklärungen für die grundlegenden Konstrukte und Ideen geben, die in den restlichen Artikeln vorkommen werden.

# Datentypen und Datenstrukturen
Alle Daten im Computer werden als Zeichenketten aus binären Ziffern dargestellt. Um diesen Zeichenfolgen eine Bedeutung zu geben, brauchen wir Datentypen. `Datentypen` bieten eine Interpretation für diese binären Daten, so dass wir über die Daten in Begriffen nachdenken können, die in Bezug auf das zu lösende Problem Sinn machen. Grundsätzlich wird zwischen primitiven und komplexen Datentypen unterschieden. Die primitiven Datentypen liefern die Bausteine für die Entwicklung von Algorithmen, wogegen die komplexen Datentypen (`Datenstrukturen`) als Methode zur Problemlösung fungieren kann.

Insgesamt gibt es acht `primitive Datentypen`. Beispiele hierfür sind Integer, Boolean, Double, Char. Beispiele für komplexe Datentypen sind Klassen, Bäume, Listen und Dictionary, auf die wir später darauf eingehen.

## Liste
Eine `Liste` ist eine Sammlung von Elementen, bei der jedes Element eine relative Position zu den anderen einnimmt. Genauer gesagt, bezeichnen wir diese Art von Liste als ungeordnete Liste. Die Liste kann ein erstes Element, ein zweites Element, ein drittes Element und so weiter enthalten. Wir können uns auch auf den Anfang der Liste (das erste Element) oder das Ende der Liste (das letzte Element) beziehen. Der Einfachheit halber gehen wir davon aus, dass Listen keine doppelten Einträge (Redundanz) enthalten können.

Zum Beispiel könnte die Sammlung der ganzen Zahlen 52, 28, 95, 19, 79 und 30 eine einfache ungeordnete Liste von Prüfungsergebnissen darstellen. Beachten Sie, dass wir sie als kommagetrennte Werte geschrieben haben, eine übliche Art, die Listenstruktur darzustellen. Natürlich würde Python diese Liste wie folgt darstellen: 
```python
[52, 28, 95, 19, 79, 30]
```

## Klassen
In Python ist eine `Klasse` ein Bauplan für die Erstellung von Objekten. `Objekte`, die aus einer Klasse erzeugt werden, nennt man `Instanzen der Klasse`. Mit Klassen können Sie die Daten und das Verhalten von Objekten auf strukturierte Weise definieren.


```python
class Car:
    def __init__(self, make, model, year, speed):
        self.make = make
        self.model = model
        self.year = year
        self.speed = speed

    def start(self):
        print(f"{self.make} {self.model} started")

    def stop(self):
        print(f"{self.make} {self.model} stopped")

    def accelerate(self, rate):
        self.speed += rate
        print(f"{self.make} {self.model} accelerating, speed = {self.speed} mph")

    def brake(self, rate):
        self.speed -= rate
        print(f"{self.make} {self.model} braking, speed = {self.speed} mph")

my_car = Car("Audi", "A3", 2020, 0)
my_car.start()
my_car.accelerate(30)
my_car.accelerate(20)
my_car.brake(10)
my_car.stop()
```
#### Erklärung:
In diesem Beispiel hat die Klasse Car vier `Attribute`: Marke, Modell, Jahr und Geschwindigkeit. Die Methode __init__ ist eine spezielle Methode in Python, die aufgerufen wird, wenn ein Objekt der Klasse erstellt wird. Sie wird verwendet, um die Attribute des Objekts zu initialisieren. Die Klasse hat außerdem vier `Methoden`: start, stop, accelerate und brake, die verschiedene Aktionen im Zusammenhang mit dem Starten, Anhalten, Beschleunigen und Bremsen des Autos ausführen.

Eine Instanz der Klasse Car kann erstellt werden, indem die Klasse als Funktion aufgerufen und die erforderlichen Argumente übergeben werden. In diesem Beispiel wird eine Instanz my_car erstellt und es werden verschiedene Methoden aufgerufen, um die Funktionsweise der Klasse zu demonstrieren.


## Dictionary
Ein `Wörterbuch` oder `Dictionary` in Python ist eine Sammlung von Schlüssel-Wert-Paaren, wobei jeder Schlüssel eindeutig ist und einem bestimmten Wert entspricht. Wörterbücher sind als Hash-Tabellen implementiert und bieten eine effiziente Möglichkeit zum Speichern und Abrufen von Werten auf der Grundlage von Schlüsseln. 

```python
# Creating a dictionary
person = {"name": "John Doe", "age": 32, "gender": "male"}

# Accessing values
print("Name:", person["name"])
print("Age:", person["age"])
```

## (Binäre) Bäume
Ein Baum ist eine Datenstruktur, die aus durch Kanten verbundenen Knoten besteht. Es handelt sich um eine hierarchische Struktur, die zur Darstellung verschiedener Beziehungen zwischen Elementen verwendet werden kann. Bäume werden häufig für Aufgaben wie das Suchen, Sortieren und Organisieren von Daten verwendet. Wir wollen num mit binären Bäumen auseinandersetzen:

Ein `Binärbaum` ist eine Datenstruktur, die aus `Knoten` besteht, wobei jeder Knoten höchstens zwei `Kinder` hat. Die Kinder werden als linkes Kind und rechtes Kind bezeichnet. Der oberste Knoten im Baum wird als `Wurzel` bezeichnet, und Knoten ohne Kinder werden als `Blattknoten` bezeichnet.

```python
class Node:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right

class BinaryTree:
    def __init__(self, root=None):
        self.root = root

    def insert(self, value):
        new_node = Node(value)
        if not self.root:
            self.root = new_node
            return
        current = self.root
        while current:
            if value <= current.value:
                if not current.left:
                    current.left = new_node
                    break
                current = current.left
            else:
                if not current.right:
                    current.right = new_node
                    break
                current = current.right

    def search(self, value):
        current = self.root
        while current:
            if value == current.value:
                return True
            elif value < current.value:
                current = current.left
            else:
                current = current.right
        return False
```
#### Erklärung:
In diesem Beispiel stellt die Klasse Node einen Knoten im Binärbaum dar. Sie hat einen Wert und zwei Zeiger auf ihre linken und rechten Kinder. Die Klasse BinaryTree stellt einen Binärbaum dar und verfügt über ein Wurzelattribut, das den Wurzelknoten speichert. Die insert-Methode fügt dem Baum einen neuen Knoten hinzu, indem sie bei der Wurzel beginnt und den Baum durchläuft, bis sie die richtige Position für den neuen Knoten auf der Grundlage seines Wertes findet. Die Suchmethode sucht nach einem Wert im Baum, indem sie bei der Wurzel beginnt und den linken oder rechten Zeigern folgt, je nachdem, ob der Zielwert kleiner oder größer als der Wert des aktuellen Knotens ist.

#### Baum sortieren
```python
    def in_order_traversal(self, node, result):
        if node:
            self.in_order_traversal(node.left, result)
            result.append(node.data)
            self.in_order_traversal(node.right, result)
        return result

    def sort(self):
        result = []
        sorted_list = self.in_order_traversal(self.root, result)
        return sorted_list
```
#### Erklärung:
Bei dieser Implementierung der Sortierung von Binärbäumen wird ein in-order traversal verwendet. Beim In-Order-Traversal wird zuerst der linke Teilbaum, dann der aktuelle Knoten und schließlich der rechte Teilbaum besucht. Diese Reihenfolge der Besuche der Knoten stellt sicher, dass die Werte in der richtigen Reihenfolge an die Ergebnisliste angehängt werden, was zu einer sortierten Liste führt. Die Methode sort gibt diese sortierte Liste zurück.

#### Baumvergleich
```python
    def are_equal(self, other_tree):
        return self._are_equal(self.root, other_tree.root)

    def _are_equal(self, node1, node2):
        if node1 is None and node2 is None:
            return True
        if node1 is None or node2 is None:
            return False
        if node1.value != node2.value:
            return False
        return self._are_equal(node1.left, node2.left) and self._are_equal(node1.right, node2.right)
```
#### Erklärung:
In diesem Beispiel verfügt die Klasse BinaryTree über eine are_equal-Methode, die die beiden Bäume durch den Aufruf der _are_equal-Methode vergleicht. Die _are_equal-Methode ist eine rekursive Funktion, die die Werte der einzelnen Knoten in den Bäumen vergleicht. Wenn die Werte nicht gleich sind, gibt die Funktion False zurück. Sind die Werte gleich, vergleicht die Funktion rekursiv die linken und rechten Teilbäume der Knoten. Wenn beide Teilbäume gleich sind, gibt die Funktion True zurück. Die Basisfälle sind, wenn beide Knoten keine Werte haben, in diesem Fall gibt die Funktion True zurück, oder wenn ein Knoten keine Werte hat und der andere nicht, in diesem Fall gibt die Funktion False zurück.

#### Baumerstellung
```python
    def create_from_list(self, values):
        self.root = self._create_from_list(values, 0, len(values) - 1)

    def _create_from_list(self, values, start, end):
        if start > end:
            return None
        mid = (start + end) // 2
        node = Node(values[mid])
        node.left = self._create_from_list(values, start, mid - 1)
        node.right = self._create_from_list(values, mid + 1, end)
        return node
```
#### Baum/Knoten löschen
```python
    def delete_tree(self):
        self.root = None

    def delete_node(self, value):
        self.root = self._delete_node(self.root, value)

    def _delete_node(self, node, value):
        if node is None:
            return node
        if value < node.data:
            node.left = self._delete_node(node.left, value)
        elif value > node.data:
            node.right = self._delete_node(node.right, value)
        else:
            if node.left is None:
                return node.right
            elif node.right is None:
                return node.left
            min_node = self._find_min(node.right)
            node.data = min_node.data
            node.right = self._delete_node(node.right, min_node.data)
        return node
```
#### Baumknoten löschen
```python
    def remove_node(self, value):
        parent, node = None, self.root
        while node and node.value != value:
            parent = node
            if value < node.value:
                node = node.left
            else:
                node = node.right
        if node is None:
            return
        if node.left and node.right:
            min_node_parent, min_node = node, node.right
            while min_node.left:
                min_node_parent, min_node = min_node, min_node.left
            node.value = min_node.value
            parent, node = min_node_parent, min_node
        child = node.left if node.left else node.right
        if parent is None:
            self.root = child
        elif parent.left == node:
            parent.left = child
        else:
            parent.right = child
```
#### Erklärung:
In diesem Beispiel verfügt die Klasse BinaryTree über eine remove_node-Methode, die einen Knoten mit dem Wert value entfernt, indem sie den Knoten zunächst in einer while-Schleife sucht. Wenn der Knoten nicht gefunden wird, kehrt die Methode zurück, ohne etwas zu tun. Wenn der Knoten gefunden wird, prüft die Methode, ob der Knoten ein oder zwei Kinder hat. Wenn der Knoten zwei Kinder hat, findet die Methode den kleinsten Knoten im rechten Teilbaum (oder den größten Knoten im linken Teilbaum), ersetzt den Wert des Knotens durch den Wert des kleinsten Knotens (oder den Wert des größten Knotens) und entfernt dann den kleinsten Knoten (oder den größten Knoten). Wenn der Knoten ein Kind hat, setzt die Methode den Verweis des Elternteils auf den Knoten auf das einzige Kind des Knotens. Wenn der Knoten keine Kinder hat, setzt die Methode den Verweis des Elternteils auf den Knoten auf None.


#### Baumknoten zählen
```python
    def count_nodes(self):
        return self._count_nodes(self.root)

    def _count_nodes(self, node):
        if node is None:
            return 0
        left_count = self._count_nodes(node.left)
        right_count = self._count_nodes(node.right)
        return 1 + left_count + right_count
```
In diesem Beispiel verfügt die Klasse BinaryTree über eine count_nodes-Methode, die die Anzahl der Knoten im Baum durch Aufruf der _count_nodes-Methode zurückgibt. Die Methode _count_nodes ist eine rekursive Funktion, die jeden Knoten im Baum besucht und 1 plus die Summe der Anzahl der Knoten im linken und rechten Teilbaum zurückgibt. Der Basisfall ist, wenn der Knoten None ist, in diesem Fall gibt die Funktion 0 zurück.


# Algorithmen als Problemlösungsmethode
`Algorithmen` beschreiben die Lösung eines Problems in Form der Daten, die zur Darstellung des Problemfall zu repräsentieren, und die Menge der Schritte, die notwendig sind, um das beabsichtigte Ergebnis zu erzielen. 

Es ist üblich, Algorithmen miteinander zu vergleichen. Denn oft wird eine interessante Frage gestellt: Wenn zwei Algorithmen das gleiche Problem lösen, aber unterschiedlich aussehen, ist dann der eine Algorithmus besser als der andere?

> ### Viele Wege führen nach Rom.

Mit dieser Redewendung will man sagen, dass es mehrere Möglichkeiten oder Wege gibt, zu einem gewünschten Ziel zu kommen. Und genauso ist es bei Algorithmen. Über die Vergleichbarkeit und Laufzeit von Algorithmen können Sie [hier](https://de.wikipedia.org/wiki/Komplexit%C3%A4tstheorie) weiterlesen.

## Problemlösen mit Rekursion

`Rekursion` ist eine Methode (Algorithmus) zur Lösung von Problemen, bei der ein Problem in immer kleinere Unterprobleme zerlegt wird, bis das Problem so klein ist, dass es trivial gelöst werden kann (`Divide-and-Conquer-Methode`).

Normalerweise beinhaltet die Rekursion eine Funktion, die sich selbst aufruft. Auch wenn es auf den ersten Blick nicht viel erscheint, ermöglicht es uns, elegante Lösungen für Probleme zu schreiben, die sonst sehr schwer zu programmieren wären. Ein bekanntes Beispiel für elegante Lösung mittels Rekursion sind die `Türme von Hanoi`.

> `Isaac Asimov`, ein russisch-amerikanischer Bürger, ist einer der weltweit berühmtesten Schriftsteller der Science Fiction. Seine Werke erweitern den Lebensraum der Menschheit literarisch ins Universum. In seinen Romanen und Erzählungen widmete er sich vor allem dem Verhältnis zwischen Mensch und Roboter.

Damit die Algorithmen korrekt funktionieren und terminieren, müssen diese bestimmte Regel folgen. Wie die [Roboter von Asimov](https://www.planet-wissen.de/technik/computer_und_roboter/roboter_mechanische_helfer/pwieisaacasimov100.html) (Asimovs Robotergesetze) müssen alle rekursiven Algorithmen drei wichtigen Gesetzen gehorchen:

  1. Ein rekursiver Algorithmus muss einen Basisfall haben.
  2. Ein rekursiver Algorithmus muss seinen Zustand ändern und sich in Richtung des Basisfalls bewegen.
  3. Ein rekursiver Algorithmus muss sich selbst aufrufen, rekursiv.

Verwendung von Rekursion: 

  - Berechne die Summe aus einer Liste von Zahlen rekursiv, z.B. [52, 28, 95, 19, 79, 30].
```python
def sum(lst):
  '''
  lst {list}: a list of numbers
  return: the sum of the numbers
  '''
  if len(lst) == 0: 
    return 0
  elif len(lst) == 1:   # Basisfall
    return lst[0]
  else:
    return lst[0] + sum(lst[1:])  # Rekursiver Aufruf
```

  - Berechnung von der n-ten Fibonacci-Zahl (Goldener Schnitt)
```python
def factorial(n):
  '''
  n {integer}: a number
  return: the factorial of the number n
  '''
  if n == 0:
      return 1
  else:
      return n * factorial(n-1)   # Rekursiver Aufruf
```

  - Visualisierung der Rekursion unter Verwendung von Python’s turtle Grafiken

  - Sierpinski-Dreieck

  - Türme von Hanoi (Komplexes rekursives Problem)

# Sortier- und Suchalgorithmen
Wir werden uns nun einigen der häufigsten Probleme zuwenden, die bei der Datenverarbeitung auftreten, nämlich dem `Suchen und Sortieren`. In diesem Abschnitt werden wir uns mit der Suche beschäftigen. Auf das Sortieren werden wir später zurückkommen. Suchen ist der algorithmische Prozess des Auffindens eines bestimmten Elements in einer Sammlung von Elementen. Eine Suche beantwortet in der Regel die Frage, ob das Element vorhanden ist, entweder mit Wahr oder Falsch. Gelegentlich kann sie so modifiziert werden, dass sie zurückgibt, wo das Element gefunden wurde. Für unsere Zwecke wollen wir uns hier nur mit der Frage der Zugehörigkeit beschäftigen.

## Die sequentielle Suche

Wenn Datenelemente in einer Sammlung, z. B. in einer Liste, gespeichert werden, spricht man von einer linearen oder sequentielle Beziehung. Jedes Datenelement wird an einer Position relativ zu den anderen gespeichert. In Python-Listen sind diese relativen Positionen die Indexwerte der einzelnen Elemente. Da diese Indexwerte geordnet sind, ist es möglich, sie nacheinander aufzurufen. Aus diesem Vorgang ergibt sich unsere erste Suchtechnik, die sequentielle Suche.

## Die binäre Suche

Die geordnete Liste lässt sich noch besser nutzen, wenn wir unsere Vergleiche geschickt einsetzen. Wenn wir bei der sequentiellen Suche mit dem ersten Element vergleichen, gibt es höchstens 𝑛 - 1 weitere Elemente, die wir durchsehen müssen, wenn das erste Element nicht das ist, wonach wir suchen. 

Anstatt die Liste der Reihe zudurchsuchen, beginnt eine binäre Suche mit der Untersuchung des mittleren Eintrags. Wenn dieser Eintrag der gesuchte ist, ist die Suche beendet. Wenn es nicht der richtige Eintrag ist, können wir die geordnete Natur der Liste nutzen, um die Hälfte der verbleibenden Einträge zu eliminieren. Wenn das gesuchte Element größer ist als der mittlere Eintrag, wissen wir, dass die gesamte untere Hälfte der Liste und auch der mittlere Eintrag von der weiteren Betrachtung ausgeschlossen werden kann. Wenn das Element in der Liste enthalten ist, muss es sich in der oberen Hälfte befinden.

---
## Sortieren
Beim Sortieren werden die Elemente einer Sammlung in eine bestimmte Reihenfolge gebracht. Ein Beispiel, eine Liste von Wörtern kann alphabetisch oder nach Länge sortiert werden. Eine Liste von Städten kann sortiert werden nach Bevölkerung, nach Gebiet oder nach Postleitzahl sortiert werden. Wir haben bereits eine Reihe von Algorithmen gesehen, die von einer sortierten Liste profitieren konnten (vgl. Binäre Suche). Folgende Sortieralgorithmen gibt es:

  - Bubble Sort 
  - Selection Sort 
  - Insertion Sort 
  - Shell Sort 
  - Merge Sort 
  - Quick Sort 

Im nächsten Schritt betrachten wir nun die Sortieralgorithmen einzeln und gehen auf die Implementierung der Algorithmen in Python ein und erklären dabei auch wie sie funktionieren.

---

#### Bubble Sort 
ist ein einfacher Sortieralgorithmus, der die Liste wiederholt durchläuft, benachbarte Elemente vergleicht und sie vertauscht, wenn sie in der falschen Reihenfolge sind. Der Algorithmus wiederholt diesen Vorgang, bis die Liste sortiert ist.

```python
def bubble_sort(arr):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr
```
#### Erklärung:
In diesem Beispiel nimmt die Funktion bubble_sort ein Array arr als Eingabe, sortiert es mit dem Bubble-Sort-Algorithmus und gibt das sortierte Array zurück. Die äußere Schleife wird n-mal durchlaufen, wobei n die Länge des Arrays ist, und die innere Schleife vergleicht jedes Paar benachbarter Elemente und tauscht sie aus, wenn sie in der falschen Reihenfolge sind. Dieser Vorgang wird n-mal wiederholt, so dass alle Elemente verglichen und sortiert sind.

---

#### Selection Sort 
ist ein einfacher Sortieralgorithmus, bei dem wiederholt das kleinste Element aus dem unsortierten Teil der Liste gesucht und mit dem ersten unsortierten Element vertauscht wird.

```python
def selection_sort(arr):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''
    for i in range(len(arr)):
        min_index = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr
```
#### Erklärung:
In diesem Beispiel durchläuft die äußere Schleife die gesamte Liste, während die innere Schleife das kleinste Element im unsortierten Teil der Liste findet. Das gefundene kleinste Element wird dann mit dem ersten unsortierten Element vertauscht, wodurch das kleinste Element an seine endgültige Position in der sortierten Liste verschoben wird. Der Vorgang wird für den Rest des unsortierten Teils der Liste wiederholt, bis alle Elemente sortiert sind.

---

#### Insertion Sort
ist ein einfacher Sortieralgorithmus, bei dem die Eingabeliste in zwei Teile geteilt wird: einen sortierten und einen unsortierten Teil. Der Algorithmus beginnt mit einem leeren sortierten Teil und nimmt iterativ Elemente aus dem unsortierten Teil und fügt sie an der richtigen Stelle im sortierten Teil ein. 

```python
def insertion_sort(arr):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''
    for i in range(1, len(arr)):
        key = arr[i]
        j = i-1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr
```
#### Erklärung:
In dieser Implementierung durchläuft die äußere for-Schleife len(arr) - 1 mal, wobei arr die zu sortierende Eingabeliste ist. Die innere while-Schleife findet die richtige Position für das aktuelle Element, indem größere Elemente nach rechts verschoben werden. Das Element wird dann an der richtigen Stelle eingefügt, indem der Wert in arr[j + 1] aktualisiert wird.

---

#### Shell Sort 
ist ein Sortieralgorithmus, der auf der Einfügesortierung basiert, aber mit einigen Optimierungen, die ihn für größere Arrays schneller machen. Er funktioniert, indem er das Eingabe-Array in kleinere Unter-Arrays unterteilt und dann jedes Unter-Array mit Insertion Sort sortiert.

```python
def shell_sort(arr):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''
    n = len(arr)
    gap = n//2
    while gap > 0:
        for i in range(gap, n):
            temp = arr[i]
            j = i
            while j >= gap and arr[j-gap] > temp:
                arr[j] = arr[j-gap]
                j -= gap
            arr[j] = temp
        gap //= 2
    return arr
```
#### Erklärung:
In diesem Beispiel nimmt die Funktion shell_sort ein Eingabe-Array arr und sortiert es mit dem Shell-Sort-Algorithmus. Die Lückenvariable wird mit der halben Länge des Eingabefeldes initialisiert und schrittweise um die Hälfte reduziert, bis sie 0 erreicht. Bei jedem Schritt der Schleife wird das Eingabefeld in Unterfelder mit der angegebenen Lücke unterteilt, und jedes Unterfeld wird mit Insertion Sort sortiert. Das Ergebnis ist ein vollständig sortiertes Array.

---

#### Merge Sort
ist ein Sortieralgorithmus, der zum Sortieren eines Arrays einen Divide-and-Conquer-Ansatz verwendet. Dabei wird das Eingabefeld in zwei Hälften geteilt, jede Hälfte rekursiv sortiert und dann die beiden sortierten Hälften wieder zusammengeführt.

```python
def merge_sort(array):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''

    if len(array) <= 1:
        return array

    mid = len(array) // 2
    left_half = array[:mid]
    right_half = array[mid:]

    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)

    return merge(left_half, right_half)

def merge(left, right):
    result = []
    left_index = 0
    right_index = 0

    while left_index < len(left) and right_index < len(right):
        if left[left_index] < right[right_index]:
            result.append(left[left_index])
            left_index += 1
        else:
            result.append(right[right_index])
            right_index += 1

    while left_index < len(left):
        result.append(left[left_index])
        left_index += 1

    while right_index < len(right):
        result.append(right[right_index])
        right_index += 1

    return result
```
#### Erklärung:
Die Funktion merge_sort prüft zunächst, ob das Eingabefeld 1 oder weniger Elemente hat. Ist dies der Fall, ist das Array bereits sortiert und wird zurückgegeben. Ist dies nicht der Fall, wird das Array in zwei Hälften geteilt, und jede Hälfte wird mit merge_sort rekursiv sortiert. Die beiden sortierten Hälften werden dann mit der merge-Funktion zusammengeführt. Die merge-Funktion nimmt zwei sortierte Arrays und erstellt ein neues Array, das alle Elemente der beiden Eingabe-Arrays in sortierter Reihenfolge enthält.

---

#### Quick Sort 
ist ein Divide-and-Conquer-Algorithmus zum Sortieren von Arrays. Dabei wird ein Pivot-Element ausgewählt und die anderen Elemente werden in zwei Unterfelder aufgeteilt, je nachdem, ob sie kleiner oder größer als das Pivot-Element sind. Die Unterfelder werden dann rekursiv sortiert.

```python
def quick_sort(arr):
    '''
    arr {list}: a list of numbers
    return: a sorted list of numbers
    '''

    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]
        less = [x for x in arr[1:] if x <= pivot]
        greater = [x for x in arr[1:] if x > pivot]
        return quick_sort(less) + [pivot] + quick_sort(greater)
```
#### Erklärung:
In dieser Implementierung nimmt die Funktion quick_sort ein Array als Eingabe und gibt eine sortierte Version des Arrays zurück. Der Basisfall ist, wenn das Array die Länge 0 oder 1 hat, in diesem Fall wird das Array so zurückgegeben, wie es ist. In allen anderen Fällen wird das erste Element des Arrays als Drehpunkt ausgewählt, und die anderen Elemente werden in zwei Unter-Arrays aufgeteilt, je nachdem, ob sie kleiner oder größer als der Drehpunkt sind. Die Unterfelder werden dann rekursiv mit der gleichen quick_sort-Funktion sortiert. Das Endergebnis ergibt sich aus der Verkettung der sortierten Unterfelder mit dem Pivot.