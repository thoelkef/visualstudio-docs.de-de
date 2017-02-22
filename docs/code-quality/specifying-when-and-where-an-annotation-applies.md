---
title: "Angeben, wann und wo eine Anmerkung g&#252;ltig ist | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Angeben, wann und wo eine Anmerkung g&#252;ltig ist
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Anmerkung bedingt ist, benötigt sie möglicherweise weitere Anmerkungen, der auf den Analyzer anzugeben.  Wenn eine Funktion z eine Variable hat, die entweder synchron oder asynchron sein kann, verhält sich die Funktion, wie folgt: Im synchronen Fall folgt diese immer schließlich, aber im asynchronen Fall meldet sie über einen Fehler, wenn sie nicht sofort ausführen kann.  Wenn die Funktion synchron aufgerufen wird, wird das Überprüfen des Ergebniswerts keinen Wert an den Codeanalyzer bereit, da sie nicht zurückgegeben hat.  Wenn die Funktion asynchron aufgerufen wird und das Ergebnis der Funktion nicht überprüft wird, kann ein ernster Fehler auftreten.  Dieses Beispiel veranschaulicht eine Situation, in der Sie `_When_` verwenden können, das später in Anmerkung\-beschrieben wurde, aktivieren Artikel\-zu Überprüfung.  
  
## Strukturelle Anmerkungen  
 So steuern, wann und wo Anmerkungen gelten, die strukturellen folgenden verwenden Sie Anmerkungen.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_At_(expr, anno-list)`|`expr` ist ein Ausdruck, der ein L\-Wert führt.  Mit Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von `expr`.  Für jede Anmerkung in `anno-list`, wird `expr` in der Vorbedingung, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Nachbedingung interpretiert, wenn die Anmerkung in der Nachbedingung interpretiert wird.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` ist ein Ausdruck, der ein L\-Wert führt.  Mit Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von `expr`.  Für jede Anmerkung in `anno-list`, wird `expr` in der Vorbedingung, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Nachbedingung interpretiert, wenn die Anmerkung in der Nachbedingung interpretiert wird.<br /><br /> `iter` ist der Name einer Variablen, die die Anmerkungen erstreckt \(einschließlich `anno-list`\).  `iter` verfügt über einen impliziten Typ `long`.  Identisch benannte Variablen in einem einschließenden Bereich werden aus der Auswertung ausgeblendet.<br /><br /> `elem-count` ist ein Ausdruck, der eine ganze Zahl ausgewertet wird.|  
|`_Group_(anno-list)`|Alle Anmerkungen in `anno-list` betrachtet werden, jeden Qualifizierer verfügen, der auf die Gruppenanmerkung gilt, die jeder Anmerkung angewendet wird.|  
|`_When_(expr, anno-list)`|`expr` ist ein Ausdruck, der in `bool` konvertiert werden kann.  Wenn er \(`true`\) nicht 0 ist, die Anmerkungen, die in `anno-list` werden als anwendbar angegeben werden.<br /><br /> Standardmäßig für jede Anmerkung in `anno-list`, wird `expr` wie mit Eingabewerte, wenn die Anmerkung eine Vorbedingung ist, und wie mit die Ausgabewerte interpretiert, wenn die Anmerkung eine Nachbedingung ist.  Um den Standardwert überschreibt, können Sie die systeminterne Funktion `_Old_` verwenden Sie eine Nachbedingung auswerten dass Eingabewerte verwendet werden sollten. **Note:**  Verschiedene Anmerkungen würden als Folge der Anwendung von `_When_` wenn ein änderbares zum Beispiel `*pLength`, können möglicherweise alle Beteilgten eine reine \- ist, da das Ergebnis möglicherweise ausgewertete `expr` in der Vorbedingung aus dem ausgewerteten Ergebnis in der Nachbedingung unterscheidet.|  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)