---
title: Substr-Methode (String) (JavaScript) | Microsoft Docs
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
- substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>substr-Methode (String) (JavaScript)
Ruft eine Teilzeichenfolge beginnt an der angegebenen Position und die angegebene Länge ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Parameter  
 `stringvar`  
 Erforderlich. Ein Zeichenfolgenliteral oder `String` -Objekt aus dem die Teilzeichenfolge extrahiert wird.  
  
 `start`  
 Erforderlich. Die Anfangsposition der gewünschten Teilzeichenfolge. Der Index des ersten Zeichens in der Zeichenfolge ist 0 (null).  
  
 `length`  
 Dies ist optional. Die Anzahl der Zeichen in der zurückgegebenen Teilzeichenfolge eingeschlossen werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `length` 0 (null) oder negativ ist, wird eine leere Zeichenfolge zurückgegeben. Wenn nicht angegeben wird, weiterhin die Teilzeichenfolge bis zum Ende des `stringvar`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `substr`-Methode veranschaulicht.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [substring-Methode (String)](../../javascript/reference/substring-method-string-javascript.md)