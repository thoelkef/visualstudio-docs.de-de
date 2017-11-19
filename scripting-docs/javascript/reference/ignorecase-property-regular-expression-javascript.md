---
title: "IgnoreCase-Eigenschaft (regulärer Ausdruck) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase-Eigenschaft (regulärer Ausdruck) (JavaScript)
Gibt einen booleschen Wert, der angibt, des Status der IgnoreCase-Flags (**ich**) mit einem regulären Ausdruck verwendet. Standardmäßig wird **"false"**. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `rgExp` Verweis ist eine Instanz der `RegExp` Objekt.  
  
 Die **IgnoreCase** -Eigenschaft gibt **"true"** Wenn IgnoreCase-Flags für einen regulären Ausdruck festgelegt ist, und gibt **"false"** wird jedoch nicht.  
  
 IgnoreCase-Flags, wenn verwendet, gibt an, dass eine Suche Groß-/Kleinschreibung ignorieren soll, wenn das Muster in der durchsuchten Zeichenfolge.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **IgnoreCase** Eigenschaft. Wenn Sie "gi" in der unten gezeigten Funktion übergeben, alle Instanzen des Worts "the" sind durch ersetzt das Wort "a", einschließlich des ersten "The". Dies ist, da die IgnoreCase-Flags festgelegt ist, die Suche Groß-/Kleinschreibung ignoriert. Daher entspricht "T" "t" für die Zwecke der Übereinstimmung.  
  
 Diese Funktion gibt die boolesche Werte, die den Status der Flags für zulässige reguläre Ausdrücke an, der sind **g**, **ich**, und **m**. Die Funktion gibt die Zeichenfolge auch mit allen Ersetzungen vorgenommen.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Beispiel  
 Folgendes ist die resultierende Ausgabe.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Global-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [MultiLine-Eigenschaft (regulärer Ausdruck)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)