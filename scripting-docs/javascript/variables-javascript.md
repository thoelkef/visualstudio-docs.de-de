---
title: "Variablen (JavaScript) | Microsoft Docs"
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
  - "Berücksichtigung der Groß-/Kleinschreibung, JavaScript-Variablenname"
  - "Erzwungene Konvertierung"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Variablen (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] enthält eine Variable einen Wert, wie z. B. "Hello" oder 5.  Wenn Sie die Variable verwenden, verweisen Sie auf die entsprechenden Daten, beispielsweise `NumberOfDaysLeft = EndDate – TodaysDate`.  
  
 Sie verwenden Variablen, um im Code vorhandene Werte zu speichern, abzurufen und zu bearbeiten.  Versuchen Sie, den Variablen aussagekräftige Namen zu geben, um anderen Personen das Verständnis für Ihren Code zu erleichtern.  
  
## Deklarieren von Variablen  
 Das erste Vorkommen einer Variable im Skript ist die Deklaration.  Bei der ersten Erwähnung der Variable wird diese im Arbeitsspeicher eingerichtet, sodass Sie später im Skript auf diese verweisen können.  Vor der Verwendung sollten die Variablen deklariert werden.  Verwenden Sie hierzu das Schlüsselwort `var`.  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Wenn Sie die Variable nicht in der Anweisung `var` initialisieren, übernimmt diese automatisch den Wert `undefined`.  
  
## Benennen von Variablen  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ist eine Sprache, in der zwischen Groß\- und Kleinschreibung unterschieden wird.  Daher unterscheidet sich der Variablenname "myCounter" vom Variablennamen "MYCounter".  Variablennamen können beliebig lang sein.  Beim Erstellen von zulässigen Variablennamen müssen folgenden Regeln beachtet werden:  
  
-   Das erste Zeichen muss ein ACSII\-Buchstabe \(Großbuchstabe oder Kleinbuchstabe\) oder ein Unterstrich \(\_\) sein.  Beachten Sie, dass als erstes Zeichen keine Zahl verwendet werden darf.  
  
-   Alle weiteren Zeichen können Buchstaben, Zahlen oder Unterstriche \(\_\) sein.  
  
-   [Reservierte Wörter](../javascript/reference/javascript-reserved-words.md) dürfen nicht als Variablennamen verwendet werden.  
  
 Im Folgenden finden Sie einige Beispiele für gültige Variablennamen:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Im Folgenden finden Sie einige Beispiele für ungültige Variablennamen:  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Wenn Sie eine Variable deklarieren und initialisieren, ihr jedoch keinen bestimmten Wert geben möchten, weisen Sie ihr den Wert `null` zu.  Im Folgenden ein Beispiel.  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Wenn Sie eine Variable deklarieren, ohne einen Wert zuzuweisen, weist diese den Wert `undefined` auf.  Im Folgenden ein Beispiel.  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 Der Wert `null` verhält sich wie die Zahl 0, während sich `undefined` wie der spezielle Wert `NaN` verhält \(keine Zahl\).  Wenn Sie einen `null`\-Wert und einen `undefined`\-Wert vergleichen, sind diese identisch.  
  
 Sie können eine Variable deklarieren, ohne das Schlüsselwort `var` in der Deklaration zu verwenden, und ihr einen Wert zuweisen.  Dies ist eine implizite Deklarierung.  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Sie können keine Variable verwenden, die nicht deklariert wurde.  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## Konvertierung  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ist im Gegensatz zu stark typisierten Sprachen wie C\+\+ eine lose typisierte Sprache.  Dies bedeutet, dass JavaScript\-Variablen keinen vordefinierten Typ aufweisen.  Stattdessen ist der Typ einer Variablen der Typ des Werts.  Daher können Sie einen Wert so behandeln, als ob es sich um einem anderen Typ handelte.  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] können Sie Vorgänge mit Werten unterschiedlichen Datentyps ausführen, ohne dass der Compiler eine Ausnahme auslöst.  Der [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Interpreter konvertiert oder *wandelt* einen der Datentypen implizit in den vom des anderen um, und führt anschließend den Vorgang aus.  Bei der Umwandlung der Zeichenfolge, der Anzahl und der booleschen Werte gelten die folgenden Regeln:  
  
-   Wenn Sie eine Zahl und eine Zeichenfolge hinzufügen, wird die Zahl in eine Zeichenfolge konvertiert.  
  
-   Wenn Sie einen booleschen Wert und eine Zeichenfolge hinzufügen, wird der boolesche Wert in eine Zeichenfolge umgewandelt.  
  
-   Wenn Sie eine Zahl und einen booleschen Wert hinzufügen, wird der boolesche Wert in eine Zahl umgewandelt.  
  
 Im folgenden Beispiel wird eine Zahl, die einer Zeichenfolge hinzugefügt wurde, zu einer Zeichenfolge.  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Zeichenfolgen werden zu Vergleichszwecken automatisch in entsprechende Zahlen konvertiert.  Mit der [parseInt\-Funktion](../javascript/reference/parseint-function-javascript.md) können Sie eine Zeichenfolge explizit in eine ganze Zahl konvertieren.  Mit der [parseFloat\-Funktion](../javascript/reference/parsefloat-function-javascript.md) können Sie eine Zeichenfolge explizit in eine Zahl konvertieren.