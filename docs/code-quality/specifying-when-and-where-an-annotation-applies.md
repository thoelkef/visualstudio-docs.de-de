---
title: Angeben, wann und wo eine Anmerkung gültig ist
ms.date: 11/04/2016
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
ms.openlocfilehash: 6c7adb310db9eece1d8d4a2881057cc1acde1062
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923817"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Angeben, wann und wo eine Anmerkung gültig ist
Wenn eine Anmerkung bedingt ist, sind möglicherweise andere Anmerkungen erforderlich, um dies für den Analyzer anzugeben.  Wenn eine Funktion z. b. eine Variable aufweist, die entweder synchron oder asynchron sein kann, verhält sich die Funktion wie folgt: Im synchronen Fall ist Sie immer schließlich erfolgreich, aber im asynchronen Fall meldet Sie einen Fehler, wenn Sie nicht sofort ausgeführt werden kann. Wenn die Funktion synchron aufgerufen wird, stellt die Überprüfung des Ergebnis Werts keinen Wert für den Code Analyse Wert dar, da er nicht zurückgegeben hätte.  Wenn die Funktion jedoch asynchron aufgerufen wird und das Ergebnis der Funktion nicht aktiviert ist, kann ein schwerwiegender Fehler auftreten. Dieses Beispiel veranschaulicht eine Situation, in der Sie die- `_When_` Anmerkung – weiter unten in diesem Artikel – zum Aktivieren der Überprüfung verwenden können.

## <a name="structural-annotations"></a>Strukturelle Anmerkungen
Verwenden Sie die folgenden strukturellen Anmerkungen, um zu steuern, wann und wo Anmerkungen angewendet werden.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`ein Ausdruck, der einen lvalue ergibt. Die Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von `expr`benannt wird. Für jede Anmerkung in `anno-list` `expr` wird in der Vorbedingung interpretiert, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Post Bedingung, wenn die Anmerkung in der Post-Bedingung interpretiert wird.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`ein Ausdruck, der einen lvalue ergibt. Die Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von `expr`benannt wird. Für jede Anmerkung in `anno-list` `expr` wird in der Vorbedingung interpretiert, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Post-Bedingung, wenn die Anmerkung in der nach Bedingung interpretiert wird.<br /><br /> `iter`der Name einer Variablen, die auf die Anmerkung (einschließlich `anno-list`) beschränkt ist. `iter`weist einen impliziten Typ `long`auf. Identisch benannte Variablen in jedem einschließenden Bereich werden aus der Auswertung ausgeblendet.<br /><br /> `elem-count`ein Ausdruck, der eine ganze Zahl ergibt.|
|`_Group_(anno-list)`|Die Anmerkungen in `anno-list` werden alle als Qualifizierer betrachtet, die für die Gruppen Anmerkung gelten, die auf jede Anmerkung angewendet wird.|
|`_When_(expr, anno-list)`|`expr`ein Ausdruck, der in `bool`konvertiert werden kann. Wenn der Wert ungleich 0 (`true`null) ist, gelten die Anmerkungen, die in `anno-list` angegeben sind, als anwendbar.<br /><br /> Standardmäßig `anno-list` `expr` wird für jede Anmerkung in als Verwendung der Eingabewerte interpretiert, wenn die Anmerkung eine Vorbedingung ist, und als die Ausgabewerte verwendet werden, wenn die Anmerkung eine nach Bedingung ist. Um die Standardeinstellung zu überschreiben, können `_Old_` Sie die systeminterne Funktion verwenden, wenn Sie eine nach Bedingung auswerten, um anzugeben, dass die Eingabewerte verwendet werden sollen. **Hinweis**:  Verschiedene Anmerkungen können als Folge der Verwendung `_When_` von aktiviert werden, wenn ein änderbarer Wert – beispielsweise – beteiligt ist, `*pLength`da das ausgewertete Ergebnis `expr` von in Vorbedingung möglicherweise von dem ausgewerteten Ergebnis in der nach Bedingung abweicht.|

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)