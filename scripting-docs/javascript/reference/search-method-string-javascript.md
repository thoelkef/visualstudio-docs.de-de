---
title: Search-Methode (String) (JavaScript) | Microsoft Docs
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
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>search-Methode (String) (JavaScript)
Sucht die erste teilzeichenfolgenübereinstimmung in einer Suche mit regulärem Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das `String`-Objekt oder Zeichenfolgenliteral, in dem gesucht werden soll.  
  
 `rgExp`  
 Erforderlich. Eine Instanz von einem **reguläre** Objekt, das das Muster eines regulären Ausdrucks sowie anwendbare Flags enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn eine Übereinstimmung gefunden wird, die **Suche** Methode gibt einen ganzzahligen-Wert, der den Offset vom Anfang der Zeichenfolge angibt, in dem die erste Übereinstimmung auftrat. Wenn keine Übereinstimmung gefunden wird, wird-1 zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Sie können auch Festlegen der `i` Flag, das bewirkt, dass die Suche Groß-/Kleinschreibung ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Suche** Methode.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Exec-Methode (regulärer Ausdruck)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match-Methode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Replace-Methode (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Test-Methode (regulärer Ausdruck)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmieren mit regulären Ausdrücken (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)