---
title: "Formatieren von Code in Python Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: c1d7a19438b796c5666daecef33052e43d1f720f
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-python-code"></a>Formatieren von Python-Code

Mithilfe der Codeformatierung in Python Tools für Visual Studio (PTVS) Version 2.0 und höher können Sie Code schnell neu formatieren, um ihn an vorkonfigurierte Formatierungsoptionen anzupassen.

- Zum Formatieren von ausgewähltem Code wählen Sie **Bearbeiten > Erweitert > Auswahl formatieren** aus oder drücken STRG+E, F.
- Um die gesamte Datei zu formatieren, wählen Sie **Bearbeiten > Erweitert > Dokument formatieren** oder drücken STRG+E, D.

Optionen werden über **Tools > Optionen > Text-Editor > Python > Formatierung** und die zugehörigen untergeordneten Registerkarten festgelegt. Standardmäßig sind sie so festgelegt, dass sie einer Obermenge des [PEP 8-Styleguides](http://www.python.org/dev/peps/pep-0008/) entsprechen. Auf der Registerkarte **Allgemein** wird festgelegt, wann die Formatierung angewendet wird. Die drei weiteren untergeordneten Registerkarten werden in den folgenden Abschnitten erläutert.

PTVS fügt dem Menü **Bearbeiten > Erweitert** auch den nützlichen Befehl [Kommentarabsatz ausfüllen](#fill-comment-paragraph) hinzu, wie unten beschrieben.

## <a name="spacing"></a>Abstand

**Abstand** steuert, an welchen Stellen in verschiedenen Sprachkonstrukten Leerzeichen eingefügt oder entfernt werden. Jede Option verfügt über drei mögliche Werte:

- Aktiviert: Stellt sicher, dass Leerzeichen angewendet werden.
- Deaktiviert: Entfernt alle Leerzeichen.
- Unbestimmt: Behält die ursprüngliche Formatierung bei.

In den folgenden Tabellen finden Sie Beispiele für die verschiedenen Optionen.

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

**Anweisungen** steuern das automatische Neuschreiben verschiedener Anweisungen in Python-ähnlichere Formen.

| Option | Vor der Formatierung | Nach der Formatierung |
| --- | --- | --- |
| Importierte Module in neuer Zeile platzieren | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Unnötige Semikolons entfernen | `x = 42;` | `x = 42` |
| Mehrere Anweisungen in neuen Zeilen platzieren | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>Umbruch

Mit der Option **Umbruch** können Sie die **Maximale Breite für Kommentare** festlegen (Standardwert: 80), sodass PTVS beim Festlegen der Option **Umbruch für Kommentare, die die maximale Breite überschreiten** Kommentare neu formatiert, damit diese die Breite nicht überschreiten.

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

Der Befehl **Bearbeiten > Erweitert > Kommentarabsatz ausfüllen** (STRG+E, STRG+P) formatiert Kommentartext und umbricht ihn neu, indem kurze Zeilen zusammengefasst und lange Zeilen geteilt werden.

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
