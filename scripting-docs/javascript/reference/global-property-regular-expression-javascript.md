---
title: Global-Eigenschaft (regulärer Ausdruck) (JavaScript) | Microsoft Docs
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
- Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637430"
---
# <a name="global-property-regular-expression-javascript"></a>global-Eigenschaft (regulärer Ausdruck) (JavaScript)
Gibt einen booleschen Wert, der angibt, des Status der globalen Kennzeichnung (**g**) mit einem regulären Ausdruck verwendet. Standardmäßig wird **"false"**. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `rgExp` Verweis ist eine Instanz von einem **reguläre** Objekt.  
  
 Die `global` -Eigenschaft gibt **"true"** Wenn das globale Flag für einen regulären Ausdruck festgelegt ist, und gibt **"false"** wird jedoch nicht.  
  
 Wenn verwendet, das globale Flag gibt an, dass es sich bei einer Suche alle Vorkommen des Musters in der durchsuchten Zeichenfolge, nicht nur die erste Aktivität sollen. Dies ist auch bekannt als globale Suche.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `global` Eigenschaft. Wenn Sie übergeben **g** in an die Funktion, die weiter unten gezeigte alle Instanzen des Worts "the" sind durch ersetzt das Wort "a". Beachten Sie die "The" am Anfang der Zeichenfolge nicht wird ersetzt, da die **ich** (Groß-/Kleinschreibung ignorieren) Flag nicht an die Funktion übergeben wird.  
  
 Diese Funktion zeigt an, die Bedingung für die Eigenschaften für die zulässigen Flags für reguläre Ausdrücke sind **g**, **ich**, und **m**. Die Funktion zeigt auch die Zeichenfolge mit allen Ersetzungen vorgenommen.  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Beispiel  
 Folgendes ist die resultierende Ausgabe.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [IgnoreCase-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [MultiLine-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)