---
title: Sort-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>sort-Methode (Array) (JavaScript)
Sortiert eine `Array`.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `sortFunction`  
 Dies ist optional. Der Name der Funktion verwendet, um die Reihenfolge der Elemente zu bestimmen. Wenn nicht angegeben, werden die Elemente in aufsteigender ASCII-Zeichen sortiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Das sortierte Array.  
  
## <a name="remarks"></a>Hinweise  
 Die `sort` -Methode sortiert die `Array` -Objekts; Nein neue `Array` -Objekt wird erstellt, während der Ausführung.  
  
 Wenn Sie angeben, dass eine Funktion in der `sortFunction` Argument, es muss zurückgegeben werden die folgenden Werte:  
  
-   Ein negativer Wert, wenn das erste übergebene Argument ist kleiner als das zweite Argument ist.  
  
-   NULL, wenn die beiden Argumente sind gleichwertig.  
  
-   Ein positiver Wert, wenn das erste Argument größer als das zweite Argument ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `sort`-Methode gezeigt.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]