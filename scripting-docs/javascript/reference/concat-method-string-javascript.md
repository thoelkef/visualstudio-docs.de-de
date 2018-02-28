---
title: Concat-Methode (String) (JavaScript) | Microsoft Docs
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>concat-Methode (String) (JavaScript)
Gibt eine Zeichenfolge, die die Verkettung von zwei oder mehr Zeichenfolgen enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `string1`  
 Erforderlich. Die `String` -Objekt oder Zeichenfolgenliteral, alle anderen angegebenen Zeichenfolgen verkettet werden.  
  
 `string2,. . ., stringN`  
 Dies ist optional. Der Zeichenfolgen, die am Ende anfügen `string1`.  
  
## <a name="remarks"></a>Hinweise  
 Das Ergebnis der `concat` Methode entspricht: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Eine Änderung des Werts in einer Quelle oder das Ergebnis Zeichenfolge wirkt sich nicht auf den Wert in die andere Zeichenfolge aus. Wenn die Argumente, die keine Zeichenfolgen darstellen, werden zunächst konvertiert in Zeichenfolgen verkettet werden, um `string1`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `concat` Methode, wenn mit einer Zeichenfolge verwendet:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Additionsoperator (+)](../../javascript/reference/addition-operator-decrement-javascript.md)