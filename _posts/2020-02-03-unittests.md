---
layout: post
title: Tests und Fehlerbehandlung in Python
date: 2020-02-03
last_modified_at: 2023-02-12
cover_image: 2021-05-10-feature.jpg
author: Yongguang Lin
categories: tests
excerpt_separator: <!--more-->
---

# Testen
Das Unit-Testing-Framework `unittest` wurde ursprünglich von JUnit inspiriert und ähnelt den wichtigsten Unit-Testing-Frameworks in anderen Sprachen. Es unterstützt die Testautomatisierung, die gemeinsame Nutzung von Setup- und Shutdown-Code für Tests, die Zusammenfassung von Tests in Sammlungen und die Unabhängigkeit der Tests vom Reporting Framework.
<!--more-->
Um dies zu erreichen, unterstützt unittest einige wichtige Konzepte auf objektorientierte Weise:
- Eine `Testfixture` stellt die Vorbereitungen dar, die für die Durchführung eines oder mehrerer Tests erforderlich sind, sowie alle damit verbundenen Bereinigungsaktionen. Dies kann z.B. das Erstellen von temporären oder Proxy-Datenbanken, Verzeichnissen oder das Starten eines Serverprozesses beinhalten.
- Ein `Testfall` ist die individuelle Einheit eines Tests. Er prüft eine bestimmte Reaktion auf einen bestimmten Satz von Eingaben. unittest bietet eine Basisklasse, TestCase, die zur Erstellung neuer Testfälle verwendet werden kann.
- Eine `Testsuite` ist eine Sammlung von Testfällen, Testsuiten oder beidem. Sie wird verwendet, um Tests zusammenzufassen, die gemeinsam ausgeführt werden sollen.
- Ein `Test-Runner` ist eine Komponente, die die Ausführung von Tests orchestriert und dem Benutzer das Ergebnis zur Verfügung stellt. Der Runner kann eine grafische oder eine textuelle Schnittstelle verwenden oder einen speziellen Wert zurückgeben, um die Ergebnisse der Testausführung anzuzeigen.

Das Modul unittest bietet einen umfangreichen Satz von Werkzeugen für die Erstellung und Ausführung von Tests. Dieser Abschnitt zeigt, dass eine kleine Teilmenge der Werkzeuge ausreicht, um die Bedürfnisse der meisten Benutzer zu erfüllen.

Hier ist ein kurzes Skript, um drei String-Methoden zu testen:
```python
import unittest

class TestStringMethods(unittest.TestCase):

    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())
        self.assertFalse('Foo'.isupper())

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):
            s.split(2)

if __name__ == '__main__':
    unittest.main()
```
|Methode|Prüffall|
|---|---|
|assertEqual(a, b)| a == b|
|assertNotEqual(a, b)|a != b|
|assertTrue(x)|bool(x) is True|
|assertFalse(x)|bool(x) is False|
|assertIs(a, b)|a is b|	
|assertIsNot(a, b)|a is not b|
|assertIsNone(x)|x is None|
|assertIsNotNone(x)|x is not None|
|assertIn(a, b)|a in b|
|assertNotIn(a, b)|a not in b|
|assertIsInstance(a, b)|isinstance(a, b)|
|assertNotIsInstance(a, b)|not isinstance(a, b)|


Es gibt verschiedene Arten von Tests bei automatisierten Tests. Einige von ihnen sind Unit-Tests, Integrationstests, End-to-End-Tests, Stresstests usw.

# Fehlerbehandlung

Ein Python-Programm bricht ab, sobald es auf einen Fehler stößt. In Python kann ein Fehler ein Syntaxfehler oder eine Ausnahme (`Exception`) sein. Selbst wenn eine Anweisung oder ein Ausdruck syntaktisch korrekt ist, kann es zu einem Fehler kommen, wenn versucht wird, sie auszuführen. Fehler, die während der Ausführung entdeckt werden, werden als Ausnahmen bezeichnet.

In diesem Artikel werden Sie sehen, was eine Ausnahme ist und wie sie sich von einem Syntaxfehler unterscheidet. Danach lernen Sie, wie man Ausnahmen auslöst und Behauptungen aufstellt. Den Abschluss bildet eine Demonstration des try- und except-Blocks.

Syntaxfehler treten auf, wenn der Parser eine falsche Anweisung erkennt. Beachten Sie das folgende Beispiel:
```cmd
>>> print( 0 / 0 ))
  File "<stdin>", line 1
    print( 0 / 0 ))
                  ^
SyntaxError: invalid syntax
```
Der Pfeil zeigt an, wo der Parser auf den Syntaxfehler gestoßen ist. In diesem Beispiel gab es eine Klammer zu viel. Entfernen Sie diese und führen Sie den Code erneut aus:
```cmd
>>> print( 0 / 0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero
```
Dieses Mal sind Sie auf einen Ausnahmefehler gestoßen. Diese Art von Fehler tritt immer dann auf, wenn syntaktisch korrekter Python-Code zu einem Fehler führt. In der letzten Zeile der Meldung wird angegeben, auf welche Art von Ausnahmefehler Sie gestoßen sind.

Anstatt die Meldung Ausnahmefehler anzuzeigen, gibt Python an, welche Art von Ausnahmefehler aufgetreten ist. In diesem Fall handelte es sich um einen ZeroDivisionError. Python verfügt über verschiedene eingebaute Ausnahmen sowie über die Möglichkeit, selbst definierte Ausnahmen zu erstellen.

Wir können `raise` verwenden, um eine Ausnahme auszulösen, wenn eine Bedingung eintritt. Die Anweisung kann durch eine benutzerdefinierte Ausnahme ergänzt werden. Wenn Sie beim Auftreten einer bestimmten Bedingung mit raise einen Fehler auslösen wollen, können Sie wie folgt vorgehen:

```python
x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
```
Wenn Sie diesen Code ausführen, erhalten Sie die folgende Ausgabe:
```cmd
Traceback (most recent call last):
  File "<input>", line 4, in <module>
Exception: x should not exceed 5. The value of x was: 10
```

Anstatt darauf zu warten, dass ein Programm auf halbem Weg abstürzt, können Sie auch damit beginnen, eine Behauptung in Python aufzustellen. Wir behaupten, dass eine bestimmte Bedingung erfüllt ist. Wenn sich diese Bedingung als wahr herausstellt, dann ist das hervorragend! Das Programm kann fortgesetzt werden. Stellt sich heraus, dass die Bedingung falsch ist, können Sie das Programm eine AssertionError-Ausnahme auslösen lassen.

Sehen Sie sich das folgende Beispiel an, in dem behauptet wird, dass der Code auf einem Linux-System ausgeführt wird:#
```python
import sys
assert ('linux' in sys.platform), "This code runs on Linux only."
```
Wenn Sie diesen Code auf einem Linux-Rechner ausführen, wird die Behauptung bestätigt. Wenn Sie diesen Code auf einem Windows-Rechner ausführen würden, wäre das Ergebnis der Behauptung __False__ und das Ergebnis wäre das folgende:
```cmd
Traceback (most recent call last):
  File "<input>", line 2, in <module>
AssertionError: This code runs on Linux only.
```
In diesem Beispiel ist das Auslösen einer AssertionError-Ausnahme das letzte, was das Programm tun wird. Das Programm kommt zum Stillstand und wird nicht fortgesetzt.


Der try- und except-Block wird in Python zum Abfangen und Behandeln von Ausnahmen verwendet. Python führt den Code, der auf die try-Anweisung folgt, als "normalen" Teil des Programms aus. Der Code, der auf die except-Anweisung folgt, ist die Reaktion des Programms auf Ausnahmen in der vorhergehenden try-Klausel.

Wie Sie bereits gesehen haben, wirft Python einen Ausnahmefehler, wenn syntaktisch korrekter Code auf einen Fehler stößt. Dieser Ausnahmefehler führt zum Absturz des Programms, wenn er nicht behandelt wird. Die except-Klausel bestimmt, wie Ihr Programm auf Ausnahmen reagiert.

Die folgende Funktion kann Ihnen helfen, den try- und except-Block zu verstehen:
```python
def linux_interaction():
    assert ('linux' in sys.platform), "Function can only run on Linux systems."
    print('Doing something.')
```
Die Funktion linux_interaction() kann nur auf einem Linux-System ausgeführt werden. Das Assert in dieser Funktion löst eine AssertionError-Ausnahme aus, wenn Sie sie auf einem anderen Betriebssystem als Linux aufrufen.

Sie können die Funktion mit folgendem Code ausprobieren:
```python
try:
    linux_interaction()
except AssertionError as error:
    print(error)
    print('The linux_interaction() function was not executed')
```
Wenn Sie diese Funktion auf einem Windows-Rechner ausführen, erhalten Sie die folgende Ausgabe:
```
Function can only run on Linux systems.
The linux_interaction() function was not executed
```
Die erste Meldung ist der AssertionError, der Sie darüber informiert, dass die Funktion nur auf einem Linux-Rechner ausgeführt werden kann. Die zweite Meldung sagt Ihnen, welche Funktion nicht ausgeführt wurde.

In Python können Sie mit der else-Anweisung ein Programm anweisen, einen bestimmten Codeblock nur dann auszuführen, wenn keine Ausnahmen vorliegen. Stellen Sie sich vor, Sie müssten immer irgendeine Aktion implementieren, um nach der Ausführung Ihres Codes aufzuräumen. In Python können Sie dies mit der finally-Klausel tun.

Eine Übersicht über die Arten der Programmfehler finden Sie in der folgenden Darstellung:
```
BaseException
 ├── BaseExceptionGroup
 ├── GeneratorExit
 ├── KeyboardInterrupt
 ├── SystemExit
 └── Exception
      ├── ArithmeticError
      │    ├── FloatingPointError
      │    ├── OverflowError
      │    └── ZeroDivisionError
      ├── AssertionError
      ├── AttributeError
      ├── BufferError
      ├── EOFError
      ├── ExceptionGroup [BaseExceptionGroup]
      ├── ImportError
      │    └── ModuleNotFoundError
      ├── LookupError
      │    ├── IndexError
      │    └── KeyError
      ├── MemoryError
      ├── NameError
      │    └── UnboundLocalError
      ├── OSError
      │    ├── BlockingIOError
      │    ├── ChildProcessError
      │    ├── ConnectionError
      │    │    ├── BrokenPipeError
      │    │    ├── ConnectionAbortedError
      │    │    ├── ConnectionRefusedError
      │    │    └── ConnectionResetError
      │    ├── FileExistsError
      │    ├── FileNotFoundError
      │    ├── InterruptedError
      │    ├── IsADirectoryError
      │    ├── NotADirectoryError
      │    ├── PermissionError
      │    ├── ProcessLookupError
      │    └── TimeoutError
      ├── ReferenceError
      ├── RuntimeError
      │    ├── NotImplementedError
      │    └── RecursionError
      ├── StopAsyncIteration
      ├── StopIteration
      ├── SyntaxError
      │    └── IndentationError
      │         └── TabError
      ├── SystemError
      ├── TypeError
      ├── ValueError
      │    └── UnicodeError
      │         ├── UnicodeDecodeError
      │         ├── UnicodeEncodeError
      │         └── UnicodeTranslateError
      └── Warning
           ├── BytesWarning
           ├── DeprecationWarning
           ├── EncodingWarning
           ├── FutureWarning
           ├── ImportWarning
           ├── PendingDeprecationWarning
           ├── ResourceWarning
           ├── RuntimeWarning
           ├── SyntaxWarning
           ├── UnicodeWarning
           └── UserWarning
```