---
title: Math.ABS-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Math.abs-Funktion (JavaScript)
Gibt den absoluten Wert einer Zahl (der Wert ohne Berücksichtigung von, ob es sich um positiv oder negativ ist). Beispielsweise ist der Absolute Wert des-5 identisch mit den absoluten Wert von 5.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Parameter  
 Die erforderliche `number` Argument ist ein numerischer Ausdruck, der für den der Absolute Wert erforderlich ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Absolute Wert der `number` Argument.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `abs`-Funktion.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Math-Objekt](../../javascript/reference/math-object-javascript.md)