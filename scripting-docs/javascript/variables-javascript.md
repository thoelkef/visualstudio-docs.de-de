---
title: Variablen (JavaScript) | Microsoft-Dokumentation
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="variables-javascript"></a>Variablen (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] enthält eine Variable einen Wert, z.B. „hello“ oder 5. Wenn Sie die Variable verwenden, verweisen Sie auf die Daten, die sie darstellt, z.B. `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Sie verwenden Variablen, um Werte, die in Ihrem Code vorkommen, zu speichern, abzurufen und zu manipulieren. Versuchen Sie, Ihren Variablen aussagekräftige Namen zu geben, um anderen Leuten das Verstehen Ihres Codes zu erleichtern.  
  
## <a name="declaring-variables"></a>Deklarieren von Variablen  
 Wenn eine Variable zum ersten Mal in Ihrem Code auftaucht, ist das ihre Deklaration. Die erste Erwähnung der Variablen legt diese in Ihrem Arbeitsspeicher an, sodass Sie später in Ihrem Skript auf sie verweisen können. Sie sollten Variablen deklarieren, bevor Sie sie verwenden. Dies können Sie mit dem Schlüsselwort `var` machen.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Wenn Sie die Variable in der `var`-Anweisung nicht initialisieren, wird ihr automatisch der Wert `undefined` zugewiesen.  
  
## <a name="naming-variables"></a>Benennen von Variablen  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ist eine Sprache, bei der die Groß- und Kleinschreibung beachtet wird. Dies bedeutet, dass ein Variablenname wie z.B. **myCounter** sich vom Variablennamen **MYCounter** unterscheidet. Variablennamen können beliebig lang sein. Die Regeln für das Erstellen zulässiger Variablen sind die folgenden:  
  
-   Das erste Zeichen muss ein ASCII-Buchstabe (Großbuchstabe oder Kleinbuchstabe) oder ein Unterstrich (_) sein. Beachten Sie, dass eine Zahl nicht als erstes Zeichen verwendet werden kann.  
  
-   Die folgenden Zeichen müssen Buchstaben, Zahlen oder Unterstriche (_) sein.  
  
-   Der Variablenname darf kein [reserviertes Wort](../javascript/reference/javascript-reserved-words.md) sein.  
  
 Hier sind einige Beispiele zulässiger Variablennamen:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Hier sind einige Beispiele unzulässiger Variablennamen:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Wenn Sie eine Variable deklarieren und initialisieren, ihr aber keinen bestimmten Wert zuweisen möchten, geben Sie ihr den Wert `null`. Im Folgenden ein Beispiel.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Wenn Sie eine Variable ohne einen zugewiesenen Wert deklarieren, hat sie den Wert `undefined`. Im Folgenden ein Beispiel.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 Der Wert `null` verhält sich wie die Zahl 0, während sich `undefined` wie der besondere Wert `NaN` verhält (keine Zahl). Wenn Sie einen `null`-Wert und einen `undefined`-Wert vergleichen, sind diese gleich.  
  
 Sie können eine Variable deklarieren, ohne das Schlüsselwort `var` in der Deklaration zu verwenden, und ihr einen Wert zuweisen. Dies ist eine implizite Deklaration.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Sie können keine Variable verwenden, die noch nicht deklariert wurde.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Koersion  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ist eine Sprache mit flexibler Typbindung, im Gegensatz zu Sprachen mit starken Typbindung wie z.B. C++. Dies bedeutet, dass JavaScript-Variablen keinen vorbestimmten Typ haben. Stattdessen ist der Typ einer Variablen der Typ ihres Werts. Durch dieses Verhalten können Sie einen Wert behandeln, als habe er einen anderen Typ.  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] können Sie Vorgange mit Werten verschiedener Typen durchführen, ohne eine Ausnahme auszulösen. Der [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Konverter konvertiert oder *erzwingt* einen der Datentypen implizit in den des anderen, und führt den Vorgang dann durch. Die Regeln für die Koersion von Zeichenfolgen, Zahlen und booleschen Werten sind wie folgt:  
  
-   Wenn Sie eine Zahl oder Zeichenfolge hinzufügen, wird die Zahl zu einer Zeichenfolge erzwungen.  
  
-   Wenn Sie einen booleschen Wert oder eine Zeichenfolge hinzufügen, wird der boolesche Wert zu einer Zeichenfolge erzwungen.  
  
-   Wenn Sie einen Zahl oder einen booleschen Wert hinzufügen, wird der boolesche Wert zu einer Zahl erzwungen.  
  
 In folgendem Beispiel wird eine Zahl, die einer Zeichenfolge hinzugefügt wurde, zu einer Zeichenfolge.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Zeichenfolgen werden zu Vergleichszwecken automatisch in äquivalente Zahlen konvertiert. Um eine Zeichenfolge implizit in eine ganze Zahl zu konvertieren, verwenden Sie die [parseInt-Funktion](../javascript/reference/parseint-function-javascript.md). Um eine Zeichenfolge implizit in eine Zahl zu konvertieren, verwenden Sie die [parseFloat-Funktion](../javascript/reference/parsefloat-function-javascript.md).