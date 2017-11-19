---
title: const-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>const-Anweisung (JavaScript)
Deklariert eine blockbezogene Variable mit einem konstanten Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Parameter  
 `constant1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die `const`-Anweisung zum Deklarieren einer Variablen mit einem konstanten Wert, deren Bereich auf den Block beschränkt ist, in dem sie deklariert wurde. Der Wert dieser Variablen kann nicht geändert werden.  
  
 Eine Variable, die mit `const` deklariert wird, muss initialisiert werden, wenn sie deklariert wurde.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `const`-Anweisung.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Let-Anweisung](../../javascript/reference/let-statement-javascript.md)   
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)