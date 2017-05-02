---
title: "switch-Anweisung (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch-Anweisung"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch-Anweisung (JavaScript)
Ermöglicht die Ausführung einer oder mehrerer Anweisungen, wenn der Wert eines festgelegten Ausdrucks einer Bezeichnung entspricht.  
  
## Syntax  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## Parameter  
 `expression`  
 Der auszuwertende Ausdruck.  
  
 `label`  
 Ein Bezeichner, der mit `expression` verglichen werden soll.  Wenn `label` ein `expression` ist, wird die Ausführung mit der `statementlist` unmittelbar nach dem Doppelpunkt begonnen und solange fortgesetzt, bis entweder eine optionale `break`\-Anweisung oder das Ende der `switch`\-Anweisung erreicht wird.  
  
 `statementlist`  
 Eine oder mehrere auszuführende Anweisungen.  
  
## Hinweise  
 Mithilfe der `default`\-Klausel können Sie eine Anweisung bereitstellen, die ausgeführt werden soll, wenn keiner der Werte der Bezeichnungen mit `expression` übereinstimmt.  Die Klausel kann an einer beliebigen Stelle im `switch`\-Codeblock stehen.  
  
 Es können keine oder mehrere `label`\-Blöcke angegeben werden.  Falls keine Entsprechung zwischen `label` und dem Wert von `expression` gefunden wird und kein `default`\-Fall angegeben worden ist, werden keine Anweisungen ausgeführt.  
  
 Die Ausführung einer `switch`\-Anweisung verläuft wie folgt:  
  
-   Zunächst wird `expression` ausgewertet und ein sequenzieller Vergleich mit `label` durchgeführt, bis eine Entsprechung gefunden wird.  
  
-   Wenn ein `label`\-Wert `expression` entspricht, wird die zugehörige `statementlist`\-Anweisungsliste ausgeführt.  
  
     Die Ausführung wird fortgesetzt, bis eine `break`\-Anweisung gefunden wird oder die `switch`\-Anweisung endet.  Dies bedeutet, dass mehrere `label`\-Blöcke ausgeführt werden, wenn keine `break` \-Anweisung verwendet wird.  
  
-   Wenn kein `label`\-Wert `expression` entspricht, wird zum `default`\-Fall gewechselt.  Ist kein `default`\-Fall vorhanden, wird der letzte Schritt ausgeführt.  
  
-   Die Ausführung wird mit der Anweisung fortgesetzt, die auf das Ende des `switch`\-Codeblocks folgt.  
  
## Beispiel  
 Im folgenden Beispiel soll der Typ eines Objekts ermittelt werden.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Beispiel  
 Der folgende Code zeigt, was geschieht, wenn keine `break`\-Anweisung angegeben wird.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [if...else\-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)