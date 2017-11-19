---
title: Call-Methode (Funktion) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="call-method-function-javascript"></a>call-Methode (Funktion) (JavaScript)
Ruft eine Methode eines Objekts auf und ersetzt dabei das aktuelle Objekt durch ein anderes Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `thisObj`  
 Dies ist optional. Das Objekt, das als aktuelles Objekt verwendet werden soll.  
  
 `arg1, arg2, , argN`  
 Dies ist optional. Eine Liste von Argumenten, die an die Methode übergeben werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Die `call`-Methode wird verwendet, um eine Methode für ein anderes Objekt aufzurufen. Sie haben damit die Möglichkeit, das `this` -Objekt einer Funktion von seinem ursprünglichen Kontext in das neue Objekt ändern, das durch `thisObj` angegeben ist.  
  
 Wenn `thisObj` nicht angegeben wird, wird das `global`-Objekt als `thisObj` verwendet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `call`-Methode veranschaulicht.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [apply-Methode (Funktion)](../../javascript/reference/apply-method-function-javascript.md)