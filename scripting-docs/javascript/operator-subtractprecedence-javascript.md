---
title: "Operatorrangfolge (JavaScript) | Microsoft Docs"
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
  - "Operatorrangfolge"
  - "Rangfolge"
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Operatorrangfolge (JavaScript)
Die Operatorrangfolge definiert die Reihenfolge, in der Vorgänge ausgeführt werden, wenn ein Ausdruck ausgewertet wird.  Operationen mit höherem Vorrang werden vor solchen mit niedrigerem Vorrang durchgeführt.  Beispielsweise wird eine Multiplikation vor einer Addition durchgeführt.  
  
## [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Operatoren  
 Die folgende Tabelle zeigt die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Operatoren von der höchsten bis zur niedrigsten Rangfolge.  Operatoren mit der gleichen Rangfolge werden von links nach rechts ausgewertet.  
  
|Operator|Beschreibung|  
|--------------|------------------|  
|. \[ \] \( \)|Feldzugriff, Arrayindizierung, Funktionsaufrufe und Gruppieren von Ausdrücken|  
|\+\+ \-\- \- ~ \! delete new typeof void|Unäre Operatoren, Rückgabedatentyp, Objekterstellung, nicht definierte Werte|  
|\* \/ %|Multiplikation, Division, Modulo\-Division|  
|\+ \- \+|Addition, Subtraktion, Zeichenfolgenverkettung|  
|\<\< \>\> \>\>\>|Bit\-Verschiebung|  
|\< \<\= \> \>\= instanceof|Kleiner als, kleiner oder gleich, größer als, größer oder gleich, instanceof \(Instanz von\)|  
|\=\= \!\= \=\=\= \!\=\=|Gleichheit, Ungleichheit, strikte Gleichheit und strikte Ungleichheit|  
|&|Bitweises AND|  
|^|Bitweises XOR|  
|&#124;|Bitweises OR|  
|&&|Logisches AND|  
|&#124;&#124;|Logisches OR|  
|?:|Bedingt|  
|\= *OP*\=|Zuweisung, Zuweisung mit Vorgang \(wie \+\= und &\=\)|  
|,|Mehrfache Auswertung|  
  
 Mit Klammern wird die Reihenfolge der Auswertung, wie sie durch die Operatorrangfolge bestimmt wird, geändert.  Dies bedeutet, dass ein Ausdruck in Klammern vollständig ausgewertet wird, bevor sein Wert im Rest des Ausdrucks verwendet wird.  
  
 Beispiel:  
  
```javascript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 Im ersten Ausdruck sind drei Operatoren enthalten: \=, \* und \+.  Gemäß den Operatorrangfolgeregeln werden sie in der folgenden Reihenfolge ausgewertet: \*, \+, \= \(78 \* 96 \= 7488, 7488 \+ 3 \= 7491\).  
  
 Im zweiten Ausdruck wird der \(\)\-Operator zuerst ausgewertet, damit der Additionsausdruck vor der Multiplikation ausgewertet wird \(9 \+ 3 \= 12, 12 \* 78 \= 936\).  
  
 Das folgende Beispiel zeigt eine Anweisung, die eine Reihe von Operatoren einschließt und sich in `true` auflöst.  
  
```javascript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Die Operatoren werden in dieser Reihenfolge ausgewertet: \(\) für das Gruppieren, \*, \+ \(innerhalb der Gruppierung\), "." für die Funktion, \(\) für die Funktion, \/, \=\=, \=\=\= und &&.