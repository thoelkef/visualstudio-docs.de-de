---
title: CharCodeAt-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt-Methode (String) (JavaScript)
Gibt den Unicode-Wert des Zeichens an der angegebenen Position zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Parameter  
 `strObj`  
 Erforderlich. Alle `String` -Objekt oder Zeichenfolgenliteral.  
  
 `index`  
 Erforderlich. Der nullbasierte Index des gewünschten Zeichens. Wenn es kein Zeichen am angegebenen Index ist `NaN` wird zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `charCodeAt`-Methode veranschaulicht.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [String.fromCharCode-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)