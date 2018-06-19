---
title: Anweisung (JavaScript)-Funktion | Microsoft Docs
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636870"
---
# <a name="function-statement-javascript"></a>function-Anweisung (JavaScript)
Deklariert eine neue Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parameter  
 `functionname`  
 Erforderlich. Der Name der Funktion.  
  
 `arg1...argN`  
 Dies ist optional. Eine optionale durch Trennzeichen getrennte Liste von Argumenten, die die Funktion versteht.  
  
 `statements`  
 Dies ist optional. Eine oder mehrere[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Anweisungen.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die `function` -Anweisung zum Deklarieren einer Funktion für die spätere Verwendung. Der Code, der in enthalten ist `statements` wird nicht ausgeführt werden, bis die Funktion aus, an anderer Stelle im Skript aufgerufen wird.  
  
 Die [zurückgeben](../../javascript/reference/return-statement-javascript.md) Anweisung wird verwendet, um einen Wert aus der Funktion zurückzugeben. Sie müssen keine verwenden eine `return` Anweisung; zurückgeben, wenn das Ende der Funktion erreicht wird. Wenn kein `return` Anweisung in die Funktion ausgeführt wird oder wenn die `return` Anweisung verfügt über keinen Ausdruck, der die Funktion gibt den Wert `undefined`.  
  
> [!NOTE]
>  Wenn Sie eine Funktion aufrufen, achten Sie darauf, dass Sie die Klammern und alle erforderlichen Argumente enthalten. Aufrufen einer Funktion ohne Klammern gibt einen Verweis auf die Funktion, die nicht die Ergebnisse der Funktion.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `function`-Anweisung.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Beispiel  
 Eine Funktion kann einer Variablen zugewiesen werden. Dies wird im folgenden Beispiel illustriert.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)