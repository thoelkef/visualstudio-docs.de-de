---
title: Angeben, wann und wo eine Anmerkung gültig ist
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 288d422de6d4e4c0f372820d838d0173c990f2a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Angeben, wann und wo eine Anmerkung gültig ist
Wenn eine Anmerkung bedingte ist, kann es andere Anmerkungen angeben, dass der Analyzer belegen.  Beispielsweise verfügt eine Funktion eine Variable, die entweder synchron oder asynchron sein kann, die Funktion verhält sich wie folgt: In den synchronen Fall immer schließlich erfolgreich abgeschlossen wird, aber in der asynchronen Fall es einen Fehler meldet, wenn er sofort erfolgreich abgeschlossen werden kann. Wenn die Funktion synchron aufgerufen wird, bietet das Überprüfen des Ergebniswerts kein Wert für die Code-Analyzer, da würde nicht zurückgegeben haben.  Wenn die Funktion asynchron aufgerufen wird und das Ergebnis der Funktion nicht aktiviert ist, konnte jedoch ein schwerwiegender Fehler auftreten. Dieses Beispiel veranschaulicht eine Situation, in dem Sie mithilfe, der `_When_` Anmerkung – weiter unten in diesem Artikel beschrieben – zu aktivieren.

## <a name="structural-annotations"></a>Strukturelle Anmerkungen
 Um zu steuern, wann und wo Anmerkungen anzuwenden, verwenden Sie die folgenden strukturelle Anmerkungen.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` ist ein Ausdruck, der einen l-Wert ergibt. Die Anmerkungen in `anno-list` gelten für das Objekt mit dem Namen von `expr`. Für jede Anmerkung in `anno-list`, `expr` in Vorbedingung interpretiert, wenn die Anmerkung wird im Vorbedingung interpretiert, sodass in nachbedingung, wenn die Anmerkung in der nachbedingung interpretiert wird.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` ist ein Ausdruck, der einen l-Wert ergibt. Die Anmerkungen in `anno-list` gelten für das Objekt mit dem Namen von `expr`. Für jede Anmerkung in `anno-list`, `expr` in Vorbedingung interpretiert, wenn die Anmerkung in Vorbedingung, und in nachbedingung, wenn die Anmerkung in der nachbedingung interpretiert wird.<br /><br /> `iter` Der Name einer Variablen, die für die Anmerkung festgelegt ist (schließt `anno-list`). `iter` verfügt über einen impliziten `long`. In jedem Gültigkeitsbereich der einschließenden gleichnamigen Variablen werden aus der Auswertung ausgeblendet.<br /><br /> `elem-count` ist ein Ausdruck, der eine ganze Zahl ergibt.|
|`_Group_(anno-list)`|Die Anmerkungen in `anno-list` gelten alle, alle Qualifizierer verwenden, die für die Gruppe-Anmerkung gilt, die auf jede Anmerkung angewendet wird.|
|`_When_(expr, anno-list)`|`expr` ist ein Ausdruck, der konvertiert werden kann `bool`. Wenn es nicht 0 (null) ist (`true`), die Anmerkungen, die im angegebenen `anno-list` als anwendbar betrachtet werden.<br /><br /> Standardmäßig wird für jede Anmerkung in `anno-list`, `expr` als mit den Eingabewerten vornimmt, wenn die Anmerkung eine Vorbedingung ist und wie die Verwendung der Ausgabewerte, wenn die Anmerkung eine nachbedingung ist interpretiert wird. Um die Standardeinstellung zu überschreiben, können Sie die `_Old_` systeminterne bei der Auswertung einer nachbedingung, um anzugeben, dass die Eingabewerte verwendet werden soll. **Hinweis:** andere Anmerkungen können aktiviert werden, als Folge mit `_When_` Wenn änderbaren Werts – z. B. `*pLength`– ist erforderlich, da ausgewerteten Ergebnisses des `expr` in Vorbedingung weicht möglicherweise von der ausgewerteten Führen Sie nach der Bedingung ein.|

## <a name="see-also"></a>Siehe auch
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [Grundlegendes zu SAL](../code-quality/understanding-sal.md) [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md) [Funktionsverhalten](../code-quality/annotating-function-behavior.md) [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md) [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md) [systeminterne Funktionen](../code-quality/intrinsic-functions.md) [empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)