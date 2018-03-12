---
title: Do...While-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while-Anweisung (JavaScript)
Führt einen Anweisungsblock einmal aus und wiederholt dann die Ausführung der Schleife, bis ein bedingter Ausdruck ergibt `false`.  
  
## <a name="syntax"></a>Syntax  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Parameter  
 `statement`  
 Erforderlich. Die auszuführende Anweisung Wenn `expression` ist `true`. Kann eine Verbundanweisung sein.  
  
 `expression`  
 Erforderlich. Ein Ausdruck, der in einen booleschen Wert umgewandelt werden kann `true` oder `false`. Wenn `expression` ist `true`, die Schleife erneut ausgeführt wird. Wenn `expression` ist `false`, wird die Schleife beendet.  
  
## <a name="remarks"></a>Hinweise  
 Im Gegensatz zu den `while` -Anweisung eine `do...while` Schleife einmal, bevor der bedingte Ausdruck ausgewertet wird.  
  
 Auf eine beliebige Zeile im ein `do...while` blockieren, können Sie die `break` -Anweisung dazu führen, dass den Programmfluss zum Beenden der Schleife, oder Sie können die `continue` Anweisung direkt zu gelangen die `while` Ausdruck.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Anweisungen in der `do...while` Schleife weiterhin so lange wie die Variable ausgeführt `i` kleiner als 10 ist.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Anweisungen innerhalb der Schleife einmal ausgeführt, auch wenn die Bedingung nicht erfüllt ist.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for... in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [While-Anweisung](../../javascript/reference/while-statement-javascript.md)   
 [Anweisung mit Bezeichnung](../../javascript/reference/labeled-statement-javascript.md)