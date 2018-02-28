---
title: LastIndexOf-Methode (String) (JavaScript) | Microsoft Docs
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf-Methode (String) (JavaScript)
Gibt das letzte Vorkommen einer Teilzeichenfolge in der Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Parameter  
 `strObj`  
 Erforderlich. Ein `String`-Objekt oder Zeichenfolgenliteral.  
  
 `substring`  
 Erforderlich. Die zu suchende Teilzeichenfolge.  
  
 `startindex`  
 Dies ist optional. Der Index, an dem die Suche beginnen soll. Wenn nicht angegeben ist, beginnt die Suche am Ende der Zeichenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Die **LastIndexOf** Methode gibt eine ganze Zahl für den Anfang der Teilzeichenfolge innerhalb der `String` Objekt. Wenn die Teilzeichenfolge nicht gefunden wird, wird-1 zurückgegeben.  
  
 Wenn `startindex` negativ ist, wird für `startindex` der Wert 0 (null) verwendet. Ist er größer als der größte Position Zeichenindex, wird er als der größtmögliche Index behandelt.  
  
 Die Suche erfolgt das letzte Zeichen in der Zeichenfolge ab. Diese Methode ist, andernfalls mit **IndexOf**.  
  
 Das folgende Beispiel veranschaulicht die Verwendung der **LastIndexOf** Methode.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [indexOf-Methode (String)](../../javascript/reference/indexof-method-string-javascript.md)