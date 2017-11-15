---
title: Verwenden von Arrays (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="using-arrays-javascript"></a>Verwenden von Arrays (JavaScript)
Bei Arrays in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] handelt es sich um *Sparse*-Arrays. Dies bedeutet Folgendes: Wenn Sie ein Array mit drei Elementen erstellen, die mit 0, 1 und 2 nummeriert sind, können Sie das 50. Element erstellen, ohne sich um die Elemente 3 bis 49 kümmern zu müssen. Wenn das Array eine automatisch festgelegte Längenvariable besitzt (weitere Informationen zur automatischen Überwachung der Arraylänge finden Sie unter [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)), wird dieser Variablen nicht der Wert 4, sondern 51 zugewiesen. Sie können selbstverständlich Arrays erstellen, die keine lückenhafte Elementnummerierung aufweist, aber dies ist nicht erforderlich.  
  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sind Objekte und Arrays nahezu identisch. Die beiden Hauptunterschiede sind, dass Objekte, die nicht Arrays sind, über keine automatische festgelegte Längeneigenschaft verfügen und dass Arrays über keine Objekteigenschaften und -methoden verfügen.  
  
## <a name="addressing-arrays"></a>Zugriff auf Arrays  
 Wie im folgenden Beispiel gezeigt wird, können Sie mit Klammern ([]) auf ein Array zugreifen. Die Klammern schließen entweder einen numerischen Wert oder einen Ausdruck ein, dessen Auswertung eine Ganzzahl ergibt.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Objekte als assoziative Arrays  
 Im Allgemeinen verwenden Sie den Punktoperator „.“, um auf Objekteigenschaften zuzugreifen. Beispiel:  
  
```JavaScript  
myObject.aProperty  
```  
  
 In diesem Fall ist der Eigenschaftenname ein Bezeichner. Sie können auch mithilfe des Indexoperators ([]) auf Eigenschaften des Objekts zugreifen. In diesem Fall behandeln Sie das Objekt allerdings als *assoziatives Array*, in dem Datenwerten Zeichenfolgen zugeordnet sind. Beispiel:  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 Der Indexoperator wird häufig beim Zugriff auf Elemente des Arrays verwendet. Wenn er mit Objekten verwendet wird, ist der Index ein Zeichenfolgenliteral, das den Eigenschaftennamen darstellt.  
  
 Beachten Sie, dass es bei den beiden Zugriffsmöglichkeiten auf Objekteigenschaften wichtige Unterschiede gibt.  
  
1.  Ein Eigenschaftenname, der mit der Punkt-Syntax (.) wie ein Bezeichner behandelt wird, kann nicht wie Daten geändert werden.  
  
2.  Im Gegensatz dazu kann ein Eigenschaftenname, der mit der Klammer-Syntax ([]) wie ein Index behandelt wird, durchaus wie Daten geändert werden.  
  
 Dieser Unterschied ist nützlich, wenn die Eigenschaftennamen bis zur Laufzeit unbekannt sind (z.B. beim Erstellen von Objekten, die auf Benutzereingaben basieren). Um alle Eigenschaften aus einem assoziativen Array zu extrahieren, verwenden Sie die `for...in`-Schleife.