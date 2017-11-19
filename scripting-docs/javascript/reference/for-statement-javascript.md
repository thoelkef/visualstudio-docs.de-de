---
title: "für die Anweisung (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>for-Anweisung (JavaScript)
Führt einen Block mit Anweisungen für, solange eine angegebene Bedingung "true" ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Parameter  
 `initialization`  
 Dies ist optional. Ein Ausdruck. Dieser Ausdruck wird nur einmal ausgeführt werden, bevor die Schleife ausgeführt wird.  
  
 `test`  
 Dies ist optional. Ein boolescher Ausdruck. Wenn `test` ist `true`, `statement` ausgeführt wird. Wenn `test` Wenn `false`, wird die Schleife beendet.  
  
 `increment`  
 Dies ist optional. Ein Ausdruck. Increment-Ausdruck wird am Ende jeder Pass-through-Schleife ausgeführt.  
  
 `statement`  
 Dies ist optional. Eine oder mehrere Anweisungen ausgeführt werden, wenn `test` ist **"true"**. Kann eine Verbundanweisung sein.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie Sie in der Regel eine `for` Schleife, wenn die Schleife ist, werden eine bekannte Anzahl von Malen ausgeführt. Ein `for` Schleife eignet sich zum Durchlaufen von Arrays und für die sequenzielle Verarbeitung.  
  
 Der Test von einem bedingten Ausdruck erfolgt vor der Ausführung der Schleife, also eine `for` Anweisung NULL oder mehrmals ausgeführt.  
  
 Für jede beliebige Zeile in eine `for` Schleife Anweisungsblock, können Sie die `break` Anweisung zum Beenden der Schleife, oder Sie können die `continue` -Anweisung die Steuerung an die nächste Iteration der Schleife zu übertragen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel die `for` Anweisung führt die eingeschlossenen Anweisungen wie folgt aus:  
  
-   Zuerst wird der Anfangswert der Variablen `i` ausgewertet wird.  
  
-   Klicken Sie dann, solange der Wert der `i` ist kleiner oder gleich 9, die `document.write` Anweisungen werden ausgeführt und `i` neu ausgewertet wird.  
  
-   Wenn `i` ist größer als 9, ergibt die Auswertung der Bedingung "false" und die Steuerung wird außerhalb der Schleife übergeben.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Beispiel  
 Alle Ausdrücke für die `for` Anweisung sind optional. Im folgenden Beispiel die `for` Anweisungen erstellen Sie eine unendliche Schleife und einem `break` Anweisung wird verwendet, um die Schleife zu beenden.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [for... in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while-Anweisung](../../javascript/reference/while-statement-javascript.md)