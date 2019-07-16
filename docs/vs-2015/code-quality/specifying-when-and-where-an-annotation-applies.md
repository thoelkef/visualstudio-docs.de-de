---
title: Angeben, wann und wo eine Anmerkung gültig | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ba14fdbc23968fcaf10355f73517ab6cd54f8797
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142189"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Angeben, wann und wo eine Anmerkung gültig ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Anmerkung bedingte ist, kann es andere Anmerkungen an, die an die Analyse erforderlich.  Beispielsweise verfügt eine Funktion eine Variable, die entweder synchron oder asynchron sein kann, verhält sich die Funktion wie folgt: In den synchronen Fall immer schließlich erfolgreich ist, aber bei asynchronen Vorgängen einen Fehler gemeldet, wenn er sofort nicht ordnungsgemäß ausgeführt werden. Wenn die Funktion synchron aufgerufen wird, bietet das Überprüfen des Ergebniswerts kein Wert, der Code-Analyzer, da er würde nicht zurückgegeben haben.  Wenn die Funktion wird asynchron aufgerufen, und das Ergebnis der Funktion nicht aktiviert ist, kann jedoch ein schwerwiegender Fehler auftreten. Dieses Beispiel veranschaulicht eine Situation, in dem Sie mithilfe, der `_When_` Anmerkung – weiter unten in diesem Artikel beschriebenen – zu aktivieren.  
  
## <a name="structural-annotations"></a>Strukturelle Anmerkungen  
 Um zu steuern, wann und wo Anmerkungen gelten, verwenden Sie die folgenden strukturellen Anmerkungen.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` ist ein Ausdruck, der einen l-Wert ergibt. Die Anmerkungen im `anno-list` gelten für das Objekt, das von dem Namen `expr`. Für jede Anmerkung in `anno-list`, `expr` wird im Voraussetzung interpretiert, wenn die Anmerkung wird im Voraussetzung interpretiert, und in nachbedingung, wenn die Anmerkung wird in der nachbedingung interpretiert.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` ist ein Ausdruck, der einen l-Wert ergibt. Die Anmerkungen im `anno-list` gelten für das Objekt, das von dem Namen `expr`. Für jede Anmerkung in `anno-list`, `expr` wird im Voraussetzung interpretiert, wenn die Anmerkung in Vorbedingung, und in nachbedingung Wenn die Anmerkung in der nachbedingung interpretiert wird.<br /><br /> `iter` Der Name einer Variablen, die für die Anmerkung bezieht (schließt `anno-list`). `iter` verfügt über einen impliziten Typ `long`. Auswertung werden gleichnamige Variablen in einem beliebigen einschließenden Bereich ausgeblendet.<br /><br /> `elem-count` ist ein Ausdruck, der eine ganze Zahl ergibt.|  
|`_Group_(anno-list)`|Die Anmerkungen im `anno-list` gelten alle über alle Qualifizierer verfügen, die für die Gruppe-Anmerkung gilt, die für jede Anmerkung gilt.|  
|`_When_(expr, anno-list)`|`expr` ist ein Ausdruck, der zu konvertierenden `bool`. Wenn es sich um einen Wert ungleich (`true`), die Anmerkungen, die im angegebenen `anno-list` als anwendbar betrachtet werden.<br /><br /> Standardmäßig wird für jede Anmerkung in `anno-list`, `expr` wie die Verwendung der Eingabewerten aus, wenn die Anmerkung eine Vorbedingung ist, und wie die Ausgabewerte zu verwenden, wenn die Anmerkung eine nachbedingung ist interpretiert wird. Um die Standardeinstellung zu überschreiben, können Sie die `_Old_` systeminterne beim Auswerten einer nachbedingung, um anzugeben, dass der Eingabewerten verwendet werden soll. **Hinweis**:  Andere Anmerkungen können aktiviert werden, daher mit `_When_` bei dem Wert des änderbar, z. B. `*pLength`– ist erforderlich, da ausgewerteten Ergebnisses des `expr` in Vorbedingung weicht möglicherweise von ausgewerteten Ergebnis nach der Bedingung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen von Kommentaren Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
