---
title: Math.hypot-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638260"
---
# <a name="mathhypot-function-javascript"></a>Math.hypot-Funktion (JavaScript)
Gibt die Quadratwurzel der Summe der Quadrate der Argumente zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Parameter  
 `value1`  
 Erforderlich. Die erste Zahl.  
  
 `value2`  
 Dies ist optional. Die zweite Zahl.  
  
 `values`  
 Dies ist optional. Eine oder mehrere Zahlen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Argument NaN lautet, gibt die Funktion NaN zurück. Wenn keine Argumente angegeben sind, gibt die Funktion 0 zurück.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die `Math.hypot`-Funktion verwendet wird.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]