---
title: Slice-Methode (String) (JavaScript) | Microsoft Docs
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice-Methode (String) (JavaScript)
Gibt einen Abschnitt einer Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Ein `String`-Objekt oder Zeichenfolgenliteral.  
  
 `start`  
 Erforderlich. Der Index auf den Anfang des angegebenen Teils `stringObj`.  
  
 `end`  
 Dies ist optional. Der Index bis zum Ende des angegebenen Bereichs des `stringObj`. Die Teilzeichenfolge enthält die Zeichen bis zum, aber nicht einschließlich, das Zeichen, die durch angegeben `end`. Wenn dieser Wert nicht angegeben wird, weiterhin die Teilzeichenfolge bis zum Ende des `stringObj`.  
  
## <a name="remarks"></a>Hinweise  
 Die `slice` Methode gibt ein `String` Objekt, das den angegebenen Teil enthält `stringObj`.  
  
 Die `slice` -Methode kopiert bis zur, aber nicht einschließlich, die durch angegebene Zeichen `end`.  
  
 Wenn `start` ist negativ ist, wird dies als behandelt *Länge*  +  `start` , in denen *Länge* ist die Länge der Zeichenfolge. Wenn `end` ist negativ ist, wird dies als behandelt *Länge* + `end`. Wenn `end` wird weggelassen, bis zum Ende weiterhin kopieren `stringObj`. Wenn `end` tritt ein, bevor `start`, keine Zeichen in der neuen Zeichenfolge kopiert werden.  
  
## <a name="example"></a>Beispiel  
 Im ersten Beispiel das `slice` Methode die gesamte Zeichenfolge zurückgegeben. Im zweiten Beispiel die `slice` Methode gibt die gesamte Zeichenfolge, mit Ausnahme der letzten Zeichen zurück.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [slice-Methode (Array)](../../javascript/reference/slice-method-array-javascript.md)