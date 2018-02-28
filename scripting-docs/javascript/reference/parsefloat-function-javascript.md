---
title: ParseFloat-Funktion (JavaScript) | Microsoft Docs
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
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat-Funktion (JavaScript)
Konvertiert eine Zeichenfolge in eine Gleitkommazahl.  
  
## <a name="syntax"></a>Syntax  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `numString` Argument ist eine Zeichenfolge, die eine Gleitkommazahl enthält.  
  
 Die `parseFloat` idatabasebackupreadstream einen numerischen Wert der Zahl `numString`. Wenn kein Präfix des `numString` erfolgreich in eine Gleitkommazahl analysiert werden `NaN` (not a Number) zurückgegeben wird.  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Sie können testen, für `NaN` mithilfe der `isNaN` Funktion.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [IsNaN-Funktion](../../javascript/reference/isnan-function-javascript.md)   
 [ParseInt-Funktion](../../javascript/reference/parseint-function-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)