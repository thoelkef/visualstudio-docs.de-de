---
title: "try...catch...finally-Anweisung (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "try-catch-Ausnahmebehandlung"
  - "try-catch-Ausnahmebehandlung, Informationen über try-catch-Ausnahmebehandlung"
  - "try-catch-Ausnahmebehandlung, Catch-Block"
  - "try-catch-Ausnahmebehandlung, Finally-Block"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# try...catch...finally-Anweisung (JavaScript)
Richtet Codeblöcke ein, in denen Fehler, die in einem Block ausgelöst werden, in einem anderen behandelt werden.  Fehler, die innerhalb des `try`\-Blocks ausgelöst werden, werden im `catch`\-Block abgefangen.  [!INCLUDE[javascript](../../includes/javascript-md.md)].  
  
## Syntax  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## Parameter  
 `tryStatements`  
 Erforderlich.  Anweisungen, in denen ein Fehler auftreten kann.  
  
 `exception`  
 Erforderlich.  Ein beliebiger Variablenname.  Der Anfangswert von `exception` ist der Wert des ausgelösten Fehlers.  
  
 `catchStatements`  
 Optional.  Anweisungen zur Behandlung von Fehlern, die in den zugehörigen `tryStatements` auftreten.  
  
 `finallyStatements`  
 Optional.  Anweisungen, die ohne Bedingung ausgeführt werden, nachdem die Behandlung sämtlicher Fehler abgeschlossen ist.  
  
## Hinweise  
 Die `try...catch...finally`\-Anweisung stellt eine Möglichkeit zum Behandeln einiger oder aller Fehler dar, die in einem bestimmten Codeblock auftreten können, während der Code weiter ausgeführt wird.  Wenn Fehler auftreten, die nicht behandelt werden, stellt [!INCLUDE[javascript](../../includes/javascript-md.md)] die normale Fehlermeldung bereit.  
  
 Der `try`\-Block enthält Code, der möglicherweise einen Fehler verursacht, während der `catch`\-Block den Code enthält, der einige oder alle Fehler behandelt.  Wenn ein Fehler im `try`\-Block auftritt, wird die Programmsteuerung an den `catch`\-Block übergeben.  Der Wert von `exception` ist der Wert des Fehlers, der im `try`\-Block aufgetreten ist.  Wenn kein Fehler auftritt, wird der Code im `catch`\-Block niemals ausgeführt.  
  
 Sie können den Fehler an die nächste Ebene übergeben, indem Sie die `throw`\-Anweisung verwenden, um den Fehler erneut auszulösen.  
  
 Nachdem alle Anweisungen im `try`\-Block ausgeführt wurden und die Fehlerbehandlung im `catch`\-Block abgeschlossen wurde, werden die Anweisungen im `finally`\-Block unabhängig davon ausgeführt, ob ein Fehler behandelt wurde oder nicht.  Der Code im `finally`\-Block wird auf jeden Fall ausgeführt, bis ein nicht behandelter Fehler auftritt \(beispielsweise ein Laufzeitfehler innerhalb des **catch**\-Blocks\).  
  
## Beispiel  
 Im folgenden Beispiel werden eine `ReferenceError`\-Ausnahme ausgelöst und der Name des Fehlers und die zugehörige Meldung angezeigt.  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Fehler und die Ausführung von geschachtelten `try…catch`\-Blöcken erneut ausgelöst werden.  Wenn der Fehler vom geschachtelten `try`\-Block ausgelöst wird, wird er an den geschachtelten `catch`\-Block übergeben, der ihn erneut auslöst.  Der geschachtelte `finally`\-Block wird ausgeführt, bevor der externe `catch`\-Block den Fehler behandelt, und am Ende wird der externe `finally`\-Block ausgeführt.  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../includes/jsv5-md.md)]  
  
> [!NOTE]
>  Beginnend mit dem Standards\-Modus von Internet Explorer 8 ist der **catch**\- Block nicht mehr erforderlich, damit `finally` ausgeführt wird.  
  
## Siehe auch  
 [throw\-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [Beispiel\-App für Script Junkie\-Konfigurations\-Assistent](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)