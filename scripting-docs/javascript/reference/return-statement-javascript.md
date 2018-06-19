---
title: return-Anweisung (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639330"
---
# <a name="return-statement-javascript"></a>return-Anweisung (JavaScript)
Beendet die aktuelle Funktion und gibt einen Wert von dieser Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale *Ausdruck* Argument ist der Wert, der von der Funktion zurückgegeben werden. Ohne Angabe dieses Arguments gibt die Funktion keinen Wert zurück.  
  
 Verwenden Sie die `return` Anweisung zum Beenden der Ausführung einer Funktion und Rückgabe des Werts der *Ausdruck*. Wenn *Ausdruck* weggelassen wird, oder gar keine `return` Anweisung innerhalb der Funktion aus ausgeführt wird, wird der Ausdruck, der die aktuelle Funktion aufgerufen hat den Wert undefined.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `return`-Anweisung.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `return`-Anweisung zur Rückgabe einer Funktion.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [function-Anweisung](../../javascript/reference/function-statement-javascript.md)