---
title: "Function-Objekt (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function-Objekt"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function-Objekt (JavaScript)
Erstellt eine neue Funktion.  
  
## Syntax  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## Syntax  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## Parameter  
 `functionName`  
 Erforderlich.  Der Name der neu erstellten Funktion  
  
 `argname1...argnameN`  
 Optional.  Eine Liste der Argumente, die die Funktion akzeptiert.  
  
 `body`  
 Optional.  Eine Zeichenfolge mit dem [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Codeblock, der ausgeführt werden soll, wenn die Funktion aufgerufen wird.  
  
## Hinweise  
 Die Funktion ist ein Basisdatentyp in [!INCLUDE[javascript](../../includes/javascript-md.md)].  Syntax 1 erstellt einen Funktionswert, den [!INCLUDE[javascript](../../includes/javascript-md.md)] gegebenenfalls in ein `Function`\-Objekt konvertiert.  [!INCLUDE[javascript](../../includes/javascript-md.md)] konvertiert `Function`\-Objekte, die von Syntax 2 erstellt wurden, beim Aufruf der Funktion in Funktionswerte.  
  
 Syntax 1 ist die Standardmethode zum Erstellen neuer Funktionen in [!INCLUDE[javascript](../../includes/javascript-md.md)].  Syntax 2 ist eine alternative Form zum expliziten Erstellen von Funktionsobjekten.  
  
 Beispielsweise können Sie eine Funktion, die zwei an sie übergebene Argumente addiert, auf eine der beiden folgenden Weisen deklarieren:  
  
## Beispiel 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## Beispiel 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 In beiden Fällen rufen Sie die Funktion mit einer Codezeile ähnlich der folgenden auf:  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  Achten Sie beim Aufrufen einer Funktion stets darauf, dass die Klammern sowie alle erforderlichen Argumente angegeben sind.  Das Aufrufen einer Funktion ohne Klammern führt dazu, dass die Funktion selbst, nicht jedoch der Rückgabewert der Funktion zurückgegeben wird.  
  
## Eigenschaften  
 [0...  
          n\-Eigenschaften](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments\-Eigenschaft](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee\-Eigenschaft](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller\-Eigenschaft](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor\-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length\-Eigenschaft \(Function\)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype\-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)  
  
## Methoden  
 [apply\-Methode](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind\-Methode](../../javascript/reference/bind-method-function-javascript.md) &#124; [call\-Methode](../../javascript/reference/call-method-function-javascript.md) &#124; [toString\-Methode](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf\-Methode](../../javascript/reference/valueof-method-object-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
## Siehe auch  
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)   
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var\-Anweisung](../../javascript/reference/var-statement-javascript.md)