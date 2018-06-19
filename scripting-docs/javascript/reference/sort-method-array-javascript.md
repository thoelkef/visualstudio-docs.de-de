---
title: Sort-Methode (Array) (JavaScript) | Microsoft Docs
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987814"
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
  
 `sortFunction`akzeptiert zwei Argumente und muss einen der folgenden Werte zurückgeben:  
  
-   Ein negativer Wert (kleiner als 0), wenn das erste Argument übergebenen ist kleiner als das zweite Argument.  Das erste Argument ist auf einen niedrigeren Indexwert sortiert.
  
-   Null (0), wenn die beiden Argumente gleichwertig sind.  Die zwei Argumente werden in Bezug auf andere Elemente im Array sortiert, aber nicht zueinander sortiert sind.
  
-   Ein positiver Wert (größer als 0), wenn das erste Argument größer als das zweite Argument ist.  Das zweite Argument wird zu einem niedrigeren Index sortiert.
  
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