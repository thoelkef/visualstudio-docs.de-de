---
title: Concat-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat-Methode (Array) (JavaScript)
Kombiniert zwei oder mehr Arrays.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Parameter  
 `array1`  
 Erforderlich. Die `Array` -Objekt, das das andere Arrays verkettet werden.  
  
 `item1,. . ., itemN`  
 Dies ist optional. Zusätzliche Elemente, die am Ende hinzugefügt `array1`.  
  
## <a name="remarks"></a>Hinweise  
 Die `concat` Methode gibt ein `Array` Objekt, das die Verkettung von enthält `array1` und aller anderen angegebenen Elemente.  
  
 Die Elemente hinzugefügt werden (*item1 ItemN*), das Array hinzugefügt werden sollen, in der Reihe nach beginnend mit dem ersten Element in der Liste. Wenn eines der Elemente ein Array ist, werden dessen Inhalt am Ende hinzugefügt `array1`. Wenn das Element etwas anderes als ein Array ist, wird es als ein einzelnes Arrayelement bis zum Ende des Arrays hinzugefügt.  
  
 Elemente des Quellarrays werden wie folgt auf das resultierende Array kopiert:  
  
-   Wenn ein Objekt von einem beliebigen der Arrays verkettet werden, in das neue Array kopiert wird, wird der Objektverweis weiterhin auf dasselbe Objekt zeigen. Eine Änderung in das neue Array oder das ursprüngliche Array führt zu einer Änderung in den anderen.  
  
-   Wenn ein Wert eine Zahl oder Zeichenfolge in das neue Array hinzugefügt wird, wird nur der Wert kopiert. Ändern des Werts in einem Array wirkt sich nicht auf den Wert in der anderen aus.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die `concat` Methode, wenn mit einem Array verwendet:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Concat-Methode (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [join-Methode (Array)](../../javascript/reference/join-method-array-javascript.md)