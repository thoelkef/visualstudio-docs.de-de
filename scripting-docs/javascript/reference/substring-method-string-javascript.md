---
title: substring-Methode (String) (JavaScript) | Microsoft Docs
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
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring-Methode (String) (JavaScript)
Gibt die Teilzeichenfolge an der angegebenen Position innerhalb einer `String` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Parameter  
 `start`  
 Erforderlich. Der nullbasierte Index ganze Zahl, die den Anfang der Teilzeichenfolge angibt.  
  
 `end`  
 Dies ist optional. Der nullbasierte Index ganze Zahl, die das Ende der Teilzeichenfolge. Die Teilzeichenfolge enthält die Zeichen bis zum, aber nicht einschließlich, das Zeichen, die durch angegeben `end`.  
  
 Wenn `end` weggelassen wird, die Zeichen von `start` bis zum Ende der ursprünglichen Zeichenfolge zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `substring` Methode gibt eine Zeichenfolge, enthält die Teilzeichenfolge aus `start` bis zur, aber nicht einschließlich `end`.  
  
 Die **Teilzeichenfolge** Methode verwendet den unteren Wert des `start` und `end` als Ausgangspunkt der Teilzeichenfolge. Beispielsweise strvar.substring (0, 3**)** und strvar.substring (3, 0) zurück, die gleiche Teilzeichenfolge.  
  
 Wenn entweder `start` oder `end` ist `NaN` oder negativ ist, es ersetzt wird mit 0 (null).  
  
 Die Länge der Teilzeichenfolge ist gleich dem absoluten Wert des Unterschieds zwischen `start` und `end`. Z. B. die Länge der Teilzeichenfolge in strvar.substring (0, 3) zurückgegeben und strvar.substring (3, 0) gleich 3.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Teilzeichenfolge** Methode.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [substr-Methode (String)](../../javascript/reference/substr-method-string-javascript.md)