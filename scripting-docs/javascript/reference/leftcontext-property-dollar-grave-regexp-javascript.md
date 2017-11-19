---
title: LeftContext-Eigenschaft ($') (RegExp) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $`
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: leftContext property ($`)
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0234a547d2e26c6cf6b1d1a058a46135e577fdd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="leftcontext-property--regexp-javascript"></a>leftContext-Eigenschaft ($`) (RegExp) (JavaScript)
Gibt die Zeichen vom Anfang einer durchsuchten Zeichenfolge bis zu der Position zurück, an der die letzte Übereinstimmung beginnt. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RegExp.leftContext  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Objekt, das dieser Eigenschaft zugeordnet ist immer die globale `RegExp` Objekt.  
  
 Der Anfangswert von der `leftContext` Eigenschaft ist eine leere Zeichenfolge. Der Wert, der die `leftContext` Eigenschaft ändert, wenn eine Übereinstimmung gefunden wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `leftContext`-Eigenschaft.  
  
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
 [LastParen-Eigenschaft ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [rightContext-Eigenschaft ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)