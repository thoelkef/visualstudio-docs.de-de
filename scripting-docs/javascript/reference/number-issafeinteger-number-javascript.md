---
title: Number.isSafeInteger (Zahl) (JavaScript) | Microsoft Docs
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Zahl) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob eine Zahl gefahrlos in JavaScript dargestellt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn die Zahl zwischen `Number.MIN_SAFE_INTEGER` und `Number.MAX_SAFE_INTEGER` (einschließlich) liegt, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
 Eine sichere ganze Zahl in JavaScript ist eine IEEE 754-Zahl mit doppelter Genauigkeit vor Anwenden einer Rundung.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)