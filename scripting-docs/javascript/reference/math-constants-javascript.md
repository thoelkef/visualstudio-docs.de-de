---
title: Math-Konstanten (JavaScript) | Microsoft Docs
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
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Math-Konstanten (JavaScript)
Math-Konstanten Konstante Werte zurückgeben, die Eigenschaften sind die `Math` Objekt.  
  
## <a name="math-object-constants"></a>Konstanten des Math-Objekts  
 Die folgende Tabelle enthält konstante Werte, die Eigenschaften sind die [Math-Objekt](../../javascript/reference/math-object-javascript.md).  
  
|Konstante|Beschreibung|Ungefährer Wert|  
|--------------|-----------------|-----------------------|  
|`Math.E`|Die mathematische Konstante e. Dies ist die eulersche Zahl, die Basis des natürlichen Logarithmus.|2.718|  
|`Math.LN2`|Der natürliche Logarithmus von 2.|0.693|  
|`Math.LN10`|Der natürliche Logarithmus von 10.|2.302|  
|`Math.LOG2E`|Der Logarithmus zur Basis 2 von e.|1.443|  
|`Math.LOG10E`|Der Logarithmus zur Basis 10 von e.|0.434|  
|`Math.PI`|Pi. Dies ist das Verhältnis vom Umfang eines Kreises zu dessen Durchmesser.|3.14159|  
|`Math.SQRT1_2`|Die Quadratwurzel von 0,5 oder, anders ausgedrückt, 1 dividiert durch die Quadratwurzel von 2.|0.707|  
|`Math.SQRT2`|Die Quadratwurzel von 2.|1.414|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die `Math.PI` konstant.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten des Number](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript-Konstanten](../../javascript/reference/javascript-constants.md)