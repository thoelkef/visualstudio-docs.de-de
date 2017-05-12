---
title: "Error-Objekt (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Error"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Error-Objekt"
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Error-Objekt (JavaScript)
Enthält Informationen über Fehler.  
  
## Syntax  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## Parameter  
 `errorObj`  
 Erforderlich.  Der Variablenname, dem das `Error`\-Objekt zugewiesen wird.  Die Variablenzuweisung wird ausgelassen, wenn Sie den Fehler mithilfe einer `throw`\-Anweisung erstellen.  
  
 `number`  
 Dies ist optional.  Numerischer Wert, der einem Fehler zugewiesen wird.  Null \(0\), wenn das Argument ausgelassen wird.  
  
 `description`  
 Dies ist optional.  Kurze Zeichenfolge, in der ein Fehler beschrieben wird.  Eine leere Zeichenfolge, falls das Argument ausgelassen wird.  
  
## Hinweise  
 Wenn ein Laufzeitfehler auftritt, wird für die Fehlerbeschreibung eine Instanz des `Error`\-Objekts erstellt.  Diese Instanz hat zwei systeminterne Eigenschaften, in denen die Beschreibung des Fehlers \(`description`\-Eigenschaft\) und der Fehlernummer \(`number`\- Eigenschaft\) enthalten sind.  Weitere Informationen finden Sie unter [JavaScript\-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md).  
  
 Eine Fehlernummer ist ein 32\-Bit\-Wert.  Das obere 16\-Bit\-Wort ist der Einrichtungscode, während das untere Wort den eigentlichen Fehlercode darstellt.  
  
 Unter Verwendung der oben aufgeführten Syntax können `Error`\-Objekte auch explizit erstellt oder mithilfe der `throw`\-Anweisung ausgelöst werden.  In beiden Fällen können Sie beliebige Eigenschaften hinzufügen, um die Funktion des `Error`\-Objekts zu erweitern.  
  
 In der Regel verweist die in einer **try...catch**\-Anweisung erstellte lokale Variable auf das implizit erstellte `Error`\-Objekt.  Fehlernummer und \-beschreibung können daher beliebig verwendet werden.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des `Error`\-Objekts.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des implizit erstellten `Error`\-Objekts veranschaulicht.  
  
```javascript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## Methoden  
 [toString\-Methode \(Fehler\)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf\-Methode \(Datum\)](../../javascript/reference/valueof-method-date.md)  
  
## Eigenschaften  
 [constructor\-Eigenschaft \(Fehler\)](../../javascript/reference/constructor-property-error.md) &#124; [description\-Eigenschaft](../../javascript/reference/description-property-error-javascript.md) &#124; [message\-Eigenschaft](../../javascript/reference/message-property-error-javascript.md) &#124; [name\-Eigenschaft](../../javascript/reference/name-property-error-javascript.md) &#124; [number\-Eigenschaft](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype\-Eigenschaft \(Fehler\)](../../javascript/reference/prototype-property-error.md) &#124; [stack\-Eigenschaft \(Fehler\)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit\-Eigenschaft \(Fehler\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Siehe auch  
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw\-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var\-Anweisung](../../javascript/reference/var-statement-javascript.md)   
 [Beispiel\-App für Hilo JavaScript \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)