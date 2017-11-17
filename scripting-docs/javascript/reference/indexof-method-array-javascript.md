---
title: IndexOf-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-array-javascript"></a>indexOf-Methode (Array) (JavaScript)
Gibt den Index des ersten Vorkommens eines Werts in einem Array zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Definition|  
|---------------|----------------|  
|`array1`|Erforderlich. Ein Arrayobjekt.|  
|`searchElement`|Erforderlich. Der zu suchende Wert `array1`.|  
|`fromIndex`|Dies ist optional. Der Index des Arrays an dem die Suche zu starten. Wenn `fromIndex` wird weggelassen, die Suche beginnt am Index 0.|  
  
## <a name="return-value"></a>Rückgabewert  
 Der Index des ersten Vorkommens des `searchElement` im Array, oder -1, wenn `searchElement` wurde nicht gefunden.  
  
## <a name="remarks"></a>Hinweise  
 Die `indexOf` sucht die Methode ein Array für einen angegebenen Wert. Die Methode gibt den Index des ersten Vorkommens oder -1, wenn der angegebene Wert nicht gefunden wird.  
  
 Die Suche erfolgt in aufsteigender Indexreihenfolge auf.  
  
 Die Elemente des Arrays sind im Vergleich zu den `searchElement` Wert durch strikte Gleichheit, ähnlich wie die `===` Operator. Weitere Informationen finden Sie unter [Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md).  
  
 Das optionale `fromIndex` -Argument gibt den Index des Arrays, an dem die Suche zu starten. Wenn `fromIndex` ist größer als oder gleich der Arraylänge, wird-1 zurückgegeben. Wenn `fromIndex` ist negativ ist, die Suche beginnt an der Arraylänge plus `fromIndex`.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele veranschaulichen die Verwendung der `indexOf` Methode.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Methoden](../../javascript/reference/javascript-methods.md)   
 [Array-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)