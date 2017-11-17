---
title: Switch-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>switch-Anweisung (JavaScript)
Aktiviert die Ausführung einer oder mehrerer Anweisungen, wenn der Wert eines festgelegten Ausdrucks einer Marke entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Parameter  
 `expression`  
 Der Ausdruck ausgewertet werden soll.  
  
 `label`  
 Ein Bezeichner, mit dem verglichen werden `expression`. Wenn `label` ist ein `expression`, Ausführung beginnt mit der `statementlist` unmittelbar hinter dem Doppelpunkt und wird fortgesetzt, bis er entweder trifft eine `break` -Anweisung, die optional ist, oder das Ende der `switch` Anweisung.  
  
 `statementlist`  
 Eine oder mehrere auszuführende Anweisungen.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der `default` -Klausel, um eine Anweisung, die ausgeführt werden, wenn keines der Bezeichnung Übereinstimmungen Werte `expression`. Sie können überall innerhalb der `switch` Codeblock.  
  
 NULL oder mehr `label` Blöcke können angegeben werden. Wenn kein `label` entspricht dem Wert `expression`, und ein `default` Fall nicht angegeben ist, wird keine Anweisungen ausgeführt werden.  
  
 Ausführung durchläuft eine `switch` Anweisung wie folgt:  
  
-   Auswerten `expression` und sehen Sie sich `label` in der Reihenfolge, bis eine Übereinstimmung gefunden wird.  
  
-   Wenn eine `label` Wert einem `expression`, führen Sie die zugehörigen `statementlist`.  
  
     Fortsetzen der Ausführung, bis eine `break` Anweisung festgestellt wird, oder die `switch` -Anweisung endet. Dies bedeutet, dass mehrere `label` -Blöcke werden ausgeführt, wenn eine `break` Anweisung wird nicht verwendet.  
  
-   Wenn kein `label` gleich `expression`, wechseln Sie zu der `default` Fall. Es ist keine `default` Fall müssen Sie zum letzten Schritt.  
  
-   Fortsetzen der Ausführung an die Anweisung nach dem Ende der `switch` Codeblock.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel testet ein Objekt für seinen Typ.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Der folgende code zeigt, was geschieht, wenn Sie nicht verwenden, eine `break` Anweisung.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [if...else-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)