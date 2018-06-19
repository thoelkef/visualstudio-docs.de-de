---
title: LastIndexOf-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638060"
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf-Methode (Array) (JavaScript)
Gibt den Index des letzten Vorkommens eines angegebenen Werts in einem Array zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Das Arrayobjekt, gesucht werden soll.|  
|`searchElement`|Erforderlich. Der zu suchende Wert `array1`.|  
|`fromIndex`|Dies ist optional. Der Index des Arrays an dem die Suche zu starten. Wenn `fromIndex` wird weggelassen, die Suche beginnt an der letzte Index im Array.|  
  
## <a name="return-value"></a>Rückgabewert  
 Der Index des letzten Vorkommens von `searchElement` im Array, oder -1, wenn `searchElement` wurde nicht gefunden.  
  
## <a name="remarks"></a>Hinweise  
 Die `lastIndexOf` sucht die Methode ein Array für einen angegebenen Wert. Die Methode gibt den Index des ersten Vorkommens oder -1, wenn der angegebene Wert nicht gefunden wird.  
  
 Die Suche erfolgt in absteigender Reihenfolge (last Element zuerst). Um in aufsteigender Reihenfolge zu suchen, verwenden die [IndexOf-Methode (Array)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Die Elemente des Arrays sind im Vergleich zu der `searchElement` Wert durch strikte Gleichheit, ähnlich wie der Vergleich vorgenommen werden, indem die `===` Operator. Weitere Informationen finden Sie unter [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md).  
  
 Das optionale `fromIndex` -Argument gibt den Index des Arrays, an dem die Suche zu starten. Wenn `fromIndex` ist größer als oder gleich der Arraylänge, wird das gesamte Array gesucht. Wenn `fromIndex` ist negativ ist, die Suche beginnt an der Arraylänge plus `fromIndex`. Wenn der berechnete Index kleiner als 0 ist, wird-1 zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele veranschaulichen die Verwendung der `lastIndexOf` Methode.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [IndexOf-Methode (Array)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)