---
title: Let-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>let-Anweisung (JavaScript)
Deklariert eine blockbezogene Variable.  
  
## <a name="syntax"></a>Syntax  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Parameter  
 `variable1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die `let`-Anweisung zum Deklarieren einer Variablen, deren Bereich auf den Block beschränkt ist, in dem sie deklariert wurde. Den Variablen können in der Deklaration oder später im Skript Werte zugewiesen werden.  
  
 Eine Variable, die mit `let` deklariert wird, kann nicht vor ihrer Deklaration verwendet werden, andernfalls tritt ein Fehler auf.  
  
 Wenn Sie die Variable in der `let`-Anweisung nicht initialisieren, wird ihr automatisch der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Wert `undefined` zugewiesen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `let`-Anweisung.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [const-Anweisung](../../javascript/reference/const-statement-javascript.md)   
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)