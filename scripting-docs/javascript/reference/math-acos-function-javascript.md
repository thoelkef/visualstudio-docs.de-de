---
title: Math.acos-Funktion (JavaScript) | Microsoft Docs
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos-Funktion (JavaScript)
Gibt den Arkuskosinus (oder umgekehrten Kosinus) einer Zahl.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Parameter  
 Das erforderliche `number`-Argument ist ein numerischer Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Arkuskosinus von der `number` -Arguments im Bogenmaß.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `acos`-Funktion veranschaulicht.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Hinweise  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Math.ASIN-Funktion](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.ATAN-Funktion](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.Cos-Funktion](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.Sin-Funktion](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan-Funktion](../../javascript/reference/math-tan-function-javascript.md)   
 [Math-Objekt](../../javascript/reference/math-object-javascript.md)