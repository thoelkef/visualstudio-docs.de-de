---
title: LastParen-Eigenschaft ($ +) (RegExp) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $+
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastParen property ($+)
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 059cfc6556873d770798eff59bf7415426526626
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="lastparen-property--regexp-javascript"></a>lastParen-Eigenschaft ($+) (RegExp) (JavaScript)
Gibt die letzte in Klammern gesetzte Teilübereinstimmung einer die oft ausgegebene Befehlszeilen  Suche mit regulärem Ausdruck zurück, sofern vorhanden. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RegExp.lastParen  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Objekt, das dieser Eigenschaft zugeordnet ist immer die globale `RegExp` Objekt.  
  
 Der Anfangswert von der `lastParen` Eigenschaft ist eine leere Zeichenfolge. Der Wert, der die `lastParen` Eigenschaft ändert, wenn eine Übereinstimmung gefunden wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `lastParen`-Eigenschaft.  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [$1... $9-Eigenschaften (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Index-Eigenschaft (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Input-Eigenschaft ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [LastIndex-Eigenschaft (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [LastMatch-Eigenschaft ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [LeftContext-Eigenschaft ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext-Eigenschaft ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)