---
title: CharAt-Methode (String) (JavaScript) | Microsoft Docs
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="charat-method-string-javascript"></a>charAt-Methode (String) (JavaScript)
Gibt das Zeichen am angegebenen Index zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Parameter  
 `strObj`  
 Erforderlich. Alle `String` -Objekt oder Zeichenfolgenliteral.  
  
 `index`  
 Erforderlich. Der nullbasierte Index des gewünschten Zeichens.  
  
## <a name="remarks"></a>Hinweise  
 Die `charAt` Methodenrückgabe einen Zeichenwert das Zeichen an der angegebenen gleich `index`. Das erste Zeichen in eine Zeichenfolge ist bei Index 0, das zweite bei Index 1 usw. ist. Werte des `index` , sind außerhalb des gültigen Bereichs Rückgabewert eine leere Zeichenfolge.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `charAt` Methode:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [String-Objekt](../../javascript/reference/string-object-javascript.md)