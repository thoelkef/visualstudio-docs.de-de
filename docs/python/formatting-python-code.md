---
title: Formatieren von Python-Code
description: Automatisches Neuformatieren von Python-Code in Visual Studio einschließlich Leerzeichen, Anweisungen, Umbruch und Kommentaren.
ms.date: 07/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 36879efbb7fe95c33d73529e3438350a87226700
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="formatting-python-code"></a>Formatieren von Python-Code

Mit Visual Studio können Sie Code schnell neu formatieren, um die vorkonfigurierten Formatierungsoptionen zu erfüllen.

- Zum Formatieren von ausgewähltem Code wählen Sie **Bearbeiten > Erweitert > Auswahl formatieren** aus oder drücken STRG+E, F.
- Um die gesamte Datei zu formatieren, wählen Sie **Bearbeiten > Erweitert > Dokument formatieren** oder drücken STRG+E, D.

Optionen werden durch **Tools > Optionen > Text-Editor > Python > Formatierung** und die darin geschachtelten Registerkarten festgelegt. Sie müssen **Alle Einstellungen anzeigen** auswählen, damit diese Optionen angezeigt werden:

![Python-Formatierungsoptionen in Visual Studio](media/options-editor-formatting.png)

Für Formatierungsoptionen ist standardmäßig festgelegt, dass sie mit einem Superset des [PEP 8 Style Guide](http://www.python.org/dev/peps/pep-0008/) übereinstimmen. Auf der Registerkarte **Allgemein** wird festgelegt, wann die Formatierung angewendet wird. Die Einstellungen der drei weiteren Registerkarten werden in diesem Artikel beschrieben.

Die [Python-Unterstützung in Visual Studio](installing-python-support-in-visual-studio.md) fügt dem Menü **Bearbeiten > Erweitert** auch den nützlichen Befehl [Kommentarabsatz ausfüllen](#fill-comment-paragraph-command) hinzu, wie in einem späteren Abschnitt beschrieben.

## <a name="spacing"></a>Abstand

**Abstand** steuert, an welchen Stellen in verschiedenen Sprachkonstrukten Leerzeichen eingefügt oder entfernt werden. Jede Option verfügt über drei mögliche Werte:

- Aktiviert: Stellt sicher, dass Leerzeichen angewendet werden.
- Deaktiviert: Entfernt alle Leerzeichen.
- Unbestimmt: Behält die ursprüngliche Formatierung bei.

In den folgenden Tabellen finden Sie Beispiele für die verschiedenen Optionen:

| Option für Klassendefinitionen | Aktiviert | Deaktiviert |
| --- | --- | --- | 
| Leerzeichen zwischen dem Namen einer Klassendeklaration und der Basisliste einfügen | `class X (object): pass` | `class X(object): pass` | 
| Leerzeichen innerhalb der runden Klammern um Basisliste einfügen | `class X( object ): pass` | `class X(object): pass` |
| Leerzeichen innerhalb der runden Klammern um eine leere Basisliste einfügen | `class X( ): pass` | `class X(): pass` |

<br/>

| Option für Funktionsdefinitionen | Aktiviert | Deaktiviert |
| --- | --- | --- |
| Leerzeichen zwischen dem Namen einer Funktionsdeklaration und einer Parameterliste einfügen | `def X (): pass` | `def X(): pass` | 
| Leerzeichen innerhalb der runden Klammern um Parameterliste einfügen | `def X( a, b ): pass` | `def X(a, b): pass` |
| Leerzeichen innerhalb der runden Klammern um eine leere Parameterliste einfügen | `def X( ): pass` | `def X(): pass` |
| Leerzeichen um „=“ in Standardparameterwerten einfügen | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Leerzeichen vor und nach Operatoren zur Rückgabe von Anmerkungen einfügen | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Optionen für Operatoren | Aktiviert | Deaktiviert |
| --- | --- | --- |
| Leerzeichen um binäre Operatoren einfügen | `a + b` | `a+b` |
| Leerzeichen um Zuweisungen einfügen | `a = b` | `a=b` |

<br/>

| Optionen für Leerzeichen in Ausdrücken | Aktiviert | Deaktiviert |
| --- | --- | --- |
| Leerzeichen zwischen dem Namen eines Funktionsaufrufs und einer Argumentliste einfügen | `X ()` | `X()` |
| Leerzeichen zwischen runden Klammern um leere Argumentliste einfügen | `X( )` | `X()` |
| Leerzeichen zwischen runden Klammern um Argumentliste einfügen | `X( a, b )` | `X(a, b)` |
| Leerzeichen innerhalb der runden Klammern eines Ausdrucks einfügen | `( a )` | `(a)` |
| Leerzeichen innerhalb der runden Klammern um ein leeres Tupel einfügen | `( )` | `()` |
| Leerzeichen innerhalb der runden Klammern um ein Tupel einfügen | `( a, b )` | `(a, b)` |
| Leerzeichen zwischen leeren eckigen Klammern einfügen | `[ ]` | `[]` |
| Leerzeichen innerhalb der eckigen Klammern von Listen einfügen | `[ a, b ]` | `[a, b]` |
| Leerzeichen vor öffnender eckiger Klammer einfügen | `x [i]` | `x[i]` |
| Leerzeichen zwischen eckigen Klammern einfügen | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Anweisungen

Die **Anweisungsoptionen** steuern das automatische Neuschreiben verschiedener Anweisungen in Python-ähnlichere Formen.

| Option | Vor der Formatierung | Nach der Formatierung |
| --- | --- | --- |
| Importierte Module in neuer Zeile platzieren | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Unnötige Semikolons entfernen | `x = 42;` | `x = 42` |
| Mehrere Anweisungen in neuen Zeilen platzieren | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Umbruch

Durch einen **Umbruch** können Sie die **maximale Kommentarbreite** festlegen (der Standard ist 80). Wenn die Option **Umbruch für Kommentare, die die maximale Breite überschreiten** festgelegt ist, formatiert Visual Studio Kommentare erneut, sodass sie nie maximale Breite nicht mehr überschreiten.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Befehl „Kommentarabsatz ausfüllen“

Der Befehl **Bearbeiten > Erweitert > Kommentarabsatz ausfüllen** (STRG+E, P) formatiert Kommentartext und umbricht ihn neu, indem kurze Zeilen zusammengefasst und lange Zeilen geteilt werden.

Zum Beispiel:

```python
# foo
# bar
# baz
```

wird zu:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

wird zu:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
