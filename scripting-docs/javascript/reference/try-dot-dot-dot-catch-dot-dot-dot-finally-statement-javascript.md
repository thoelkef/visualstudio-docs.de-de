---
title: "try … try...catch...finally-Anweisung (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="trycatchfinally-statement-javascript"></a>try...catch...finally-Anweisung (JavaScript)
Richtet Codeblöcke ein, in denen Fehler, die in einem Block ausgelöst werden, in einem anderen behandelt werden. Fehler, die innerhalb des `try`-Blocks ausgelöst werden, werden im `catch`-Block abgefangen. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="parameters"></a>Parameter  
 `tryStatements`  
 Erforderlich. Anweisungen, in denen ein Fehler auftreten kann.  
  
 `exception`  
 Erforderlich. Ein beliebiger Variablenname. Der Anfangswert von `exception` ist der Wert des ausgelösten Fehlers.  
  
 `catchStatements`  
 Dies ist optional. Anweisungen zur Behandlung von Fehlern, die in den zugehörigen `tryStatements` auftreten.  
  
 `finallyStatements`  
 Dies ist optional. Anweisungen, die ohne Bedingung ausgeführt werden, nachdem die Behandlung sämtlicher Fehler abgeschlossen ist.  
  
## <a name="remarks"></a>Hinweise  
 Die `try...catch...finally`-Anweisung stellt eine Möglichkeit zum Behandeln einiger oder aller Fehler dar, die in einem bestimmten Codeblock auftreten können, während der Code weiter ausgeführt wird. Wenn Fehler auftreten, die nicht behandelt werden, stellt [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] die normale Fehlermeldung bereit.  
  
 Der `try`-Block enthält Code, der möglicherweise einen Fehler verursacht, während der `catch`-Block den Code enthält, der einige oder alle Fehler behandelt. Wenn ein Fehler im `try`-Block auftritt, wird die Programmsteuerung an den `catch`-Block übergeben. Der Wert von `exception` ist der Wert des Fehlers, der im `try`-Block aufgetreten ist. Wenn kein Fehler auftritt, wird der Code im `catch`-Block niemals ausgeführt.  
  
 Sie können den Fehler an die nächste Ebene übergeben, indem Sie die `throw`-Anweisung verwenden, um den Fehler erneut auszulösen.  
  
 Nachdem alle Anweisungen im `try`-Block ausgeführt wurden und die Fehlerbehandlung im `catch`-Block abgeschlossen wurde, werden die Anweisungen im `finally`-Block unabhängig davon ausgeführt, ob ein Fehler behandelt wurde oder nicht. Der Code in der `finally` -Block wird auf jeden Fall ausgeführt, bis ein nicht behandelter Fehler auftritt (z. B. ein Laufzeitfehler innerhalb der **catch** Block).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden eine `ReferenceError`-Ausnahme ausgelöst und der Name des Fehlers und die zugehörige Meldung angezeigt.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Fehler und die Ausführung von geschachtelten `try...catch`-Blöcken erneut ausgelöst werden. Wenn der Fehler vom geschachtelten `try`-Block ausgelöst wird, wird er an den geschachtelten `catch`-Block übergeben, der ihn erneut auslöst. Der geschachtelte `finally`-Block wird ausgeführt, bevor der externe `catch`-Block den Fehler behandelt, und am Ende wird der externe `finally`-Block ausgeführt.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Beginnend mit Internet Explorer 8-Standards-Modus die **catch** Block ist nicht mehr erforderlich, damit `finally` ausgeführt.  
  
## <a name="see-also"></a>Siehe auch  
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [Beispiel-app für Script Junkie Konfiguration-Assistenten](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)