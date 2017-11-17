---
title: Number.isNaN-Funktion (Zahl) (JavaScript) | Microsoft Docs
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Number.isNaN-Funktion (Zahl) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Wert der reservierte Wert `NaN` ist (keine Zahl).  
  
## <a name="syntax"></a>Syntax  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Parameter  
 `numValue`  
 Erforderlich. Der Wert, der mit `NaN` getestet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn der in den `Number`-Typ konvertierte Wert `NaN` lautet, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel verwenden Sie diese Methode zum Testen der Rückgabewerte von den Methoden `parseInt` und `parseFloat`.  
  
 `Number.isNaN` behebt Probleme mit der globalen `isNaN`-Funktion. `Number.isNaN` konvertiert das Argument erst nach dem Vergleich mit `NaN` in den Typ „Zahl“. Daher gibt es `true` nur dann zurück, wenn das übergebene Argument genau den gleichen Wert wie `NaN` aufweist. Die globale `isNaN`-Funktion konvertiert das Argument vor dem Vergleich in den Typ „Zahl“, was dazu führen kann, dass nicht-numerische Werte `true` zurückgeben, während sie `true` möglicherweise nicht für `Number.isNaN` zurückgeben.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```