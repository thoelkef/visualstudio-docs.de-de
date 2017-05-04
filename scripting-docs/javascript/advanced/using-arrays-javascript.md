---
title: "Verwenden von Arrays (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Arrays [JavaScript]"
  - "Arrays [JavaScript], Objekte"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Verwenden von Arrays (JavaScript)
In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] haben Arrays eine *geringe Dichte*.  Das heißt, wenn ein Array mit drei Elementen mit den Nummern 0, 1 und 2 gegeben ist, können Sie das Element 50 erstellen, ohne sich über die Elemente 3 bis 49 Gedanken machen zu müssen.  Wenn das Array eine automatische Längenvariable \(unter [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md) finden Sie eine Erläuterung der automatischen Überwachung der Arraylänge\) besitzt, wird die Längenvariable auf 51 und nicht auf 4 festgelegt.  Sie können Arrays erstellen, deren Nummerierung der Elemente keine Lücken aufweist, dies ist jedoch nicht erforderlich.  
  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sind Objekte und Arrays miteinander fast identisch.  Die beiden Hauptunterschiede bestehen darin, dass Objekte, die kein Array sind, keine automatische Längeneigenschaft besitzen, und dass Arrays nicht die Eigenschaften und Methoden eines Objekts aufweisen.  
  
## Adressieren von Arrays  
 Arrays werden mithilfe von Klammern \(\[\]\) adressiert, wie im folgenden Beispiel gezeigt.  Die Klammern schließen entweder einen numerischen Wert oder einen Ausdruck ein, der zu einer ganzen Zahl ausgewertet wird.  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## Objekte als assoziative Arrays  
 Im Allgemeinen wird der Punktoperator "." verwendet, um auf die Eigenschaften eines Objekts zuzugreifen.  Beispiel:  
  
```javascript  
myObject.aProperty  
```  
  
 In diesem Fall ist der Eigenschaftenname ein Bezeichner.  Sie können auch mithilfe des Indexoperators \(\[\]\) auf die Eigenschaften eines Objekts zugreifen.  In diesem Fall behandeln Sie das Objekt als *assoziatives Array,*, in dem Datenwerte Zeichenfolgen zugeordnet sind.  Beispiel:  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 Der Indexoperator wird meist mit dem Zugriff auf Arrayelemente verknüpft.  Wenn er mit Objekten verwendet wird, ist der Index ein Zeichenfolgenliteral, das den Eigenschaftennamen darstellt.  
  
 Beachten Sie die wichtigen Unterschiede zwischen den beiden Methoden des Zugriffs auf Objekteigenschaften.  
  
1.  Eigenschaftennamen, die wie Bezeichner behandelt werden \(die Punktsyntax \(.\)\), können nicht wie Daten behandelt werden.  
  
2.  Eigenschaftennamen, die wie ein Index behandelt werden \(die Klammernsyntax \(\[\]\)\), können wie Daten bearbeitet werden.  
  
 Dieser Unterschied ist vor allem dann nützlich, wenn die Eigenschaftennamen erst zur Laufzeit bekannt sind \(z. B. beim Erstellen von Objekten, die auf Benutzereingaben basieren\).  Sie müssen die `for…in`\-Schleife verwenden, um alle Eigenschaften aus einem assoziativen Array zu extrahieren.