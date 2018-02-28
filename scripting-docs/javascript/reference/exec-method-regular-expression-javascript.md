---
title: "Exec-Methode (regulärer Ausdruck) (JavaScript) | Microsoft Docs"
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>exec-Methode (regulärer Ausdruck) (JavaScript)
Führt eine Suche für eine Zeichenfolge, die mithilfe des Muster eines regulären Ausdrucks und gibt ein Array mit den Ergebnissen dieses Vergleichs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Parameter  
 `rgExp`  
 Erforderlich. Eine Instanz von einem **reguläre** Objekt, das das Muster eines regulären Ausdrucks sowie anwendbare Flags enthält.  
  
 `str`  
 Erforderlich. Das `String`-Objekt oder Zeichenfolgenliteral, in dem gesucht werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `exec`-Methode keine Übereinstimmung findet, gibt sie den Wert `null` zurück. Wenn sie eine Übereinstimmung findet, gibt `exec` ein Array zurück, und die Eigenschaften des globalen `RegExp`-Objekts werden aktualisiert, um die Ergebnisse der Übereinstimmung anzuzeigen. Element 0 (null) des Arrays enthält die gesamte Übereinstimmung, und die Elemente 1 -  *n*  alle teilübereinstimmungen, die innerhalb der Übereinstimmung aufgetreten sind. Dieses Verhalten entspricht dem Verhalten der `match` Methode ohne das globale Flag (**g**) festgelegt.  
  
 Wenn das globale Flag, auf einen regulären Ausdruck festgelegt ist `exec` durchsucht die Zeichenfolge beginnend an der durch den Wert der angegebenen Position `lastIndex`. Wenn das globale Flag nicht festgelegt ist, `exec` ignoriert den Wert der `lastIndex` und die Suche vom Anfang der Zeichenfolge.  
  
 Das zurückgegebene Array die `exec` Methode verfügt über drei Eigenschaften **input**, **Index** und **LastIndex.** Die **input** Eigenschaft enthält die gesamte durchsuchte Zeichenfolge. Die **Index** Eigenschaft enthält die Position der übereinstimmenden Teilzeichenfolge innerhalb der gesamten durchsuchten Zeichenfolge. Die `lastIndex` -Eigenschaft enthält die Position hinter dem letzten Zeichen in der Übereinstimmung.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `exec` Methode:  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Match-Methode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Search-Methode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test-Methode (regulärer Ausdruck)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmieren mit regulären Ausdrücken (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)