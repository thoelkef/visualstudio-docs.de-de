---
title: ToUpperCase-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toUpperCase method
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b84de440fc9e3cece3b831b57a90be394e819ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640660"
---
# <a name="touppercase-method-string-javascript"></a>toUpperCase-Methode (String) (JavaScript)
Konvertiert alle alphabetischen Zeichen in einer Zeichenfolge in Großbuchstaben konvertiert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## <a name="remarks"></a>Hinweise  
 Die `toUpperCase` Methode hat keine Auswirkung auf nicht alphabetische Zeichen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Auswirkungen der `toUpperCase` Methode:  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToLocaleUpperCase-Methode (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase-Methode](../../javascript/reference/tolowercase-method-javascript.md)