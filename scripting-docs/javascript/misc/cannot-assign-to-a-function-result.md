---
title: "Die Zuweisung zu einem Funktionsergebnis ist nicht m&#246;glich | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Die Zuweisung zu einem Funktionsergebnis ist nicht m&#246;glich
Sie haben versucht, dem Ergebnis einer Funktion einen Wert zuzuweisen.  Das Ergebnis einer Funktion kann einer Variablen zugewiesen, jedoch nicht als Variable verwendet werden.  Wenn Sie der Funktion selbst einen neuen Wert zuweisen möchten, lassen Sie die Klammern \(den Funktionsaufrufoperator\) weg.  Das folgende Beispiel zeigt eine Situation, in der dieser Fehler generiert wird.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie den Wert des Ergebnisses eines Funktionsaufrufs nicht als Element, auf das eine *Zuweisung erfolgen* kann.  Sie können das Ergebnis des Funktionsaufrufs jedoch *einer Variablen* zuweisen:  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   Alternativ können Sie die Funktion selbst \(und nicht ihren Rückgabewert\) einer Variablen zuweisen.  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## Siehe auch  
 [Function\-Objekt](../../javascript/reference/function-object-javascript.md)   
 [Schreiben von JavaScript\-Code](../../javascript/writing-javascript-code.md)   
 [Funktionen](../../javascript/functions-javascript.md)