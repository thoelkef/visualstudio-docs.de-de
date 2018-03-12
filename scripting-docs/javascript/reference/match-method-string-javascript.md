---
title: Match-Methode (String) (JavaScript) | Microsoft Docs
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match-Methode (String) (JavaScript)
Vergleicht eine Zeichenfolge mit einem regulären Ausdruck und gibt ein Array mit den Ergebnissen dieses Vergleichs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das `String`-Objekt oder Zeichenfolgenliteral, in dem gesucht werden soll.  
  
 `rgExp`  
 Erforderlich. Ein Objekt eines regulären Ausdrucks, welches das Muster des regulären Ausdrucks und anwendbare Flags enthält. Dies kann auch ein Variablenname oder Zeichenfolgenliteral sein, worin das Muster des regulären Ausdrucks und die Flags enthalten sind.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `match`-Methode keine Übereinstimmung findet, gibt sie den Wert `null` zurück. Wenn sie eine Übereinstimmung findet, gibt `match` ein Array zurück, und die Eigenschaften des globalen `RegExp`-Objekts werden aktualisiert, um die Ergebnisse der Übereinstimmung anzuzeigen.  
  
 Wenn das globale Flag (`g`) nicht festgelegt ist, 0 (null) des Arrays enthält die vollständige Übereinstimmung und die Elemente 1 bis, Element  *n*  alle teilübereinstimmungen. Dieses Verhalten stimmt mit dem Verhalten der [Exec-Methode (regulärer Ausdruck)](../../javascript/reference/exec-method-regular-expression-javascript.md) Wenn das globale Flag nicht festgelegt ist. Wenn das globale Flag festgelegt ist, werden Elemente 0-  *n*  enthalten alle aufgetretenen Übereinstimmungen.  
  
 Wenn das globale Flag nicht festgelegt ist, weist das von der `match`-Methode zurückgegebene Array die beiden Eigenschaften, `input` und `index` auf. Die `input`-Eigenschaft enthält die gesamte durchsuchte Zeichenfolge. Die `index`-Eigenschaft enthält die Position der übereinstimmenden Teilzeichenfolge innerhalb der gesamten durchsuchten Zeichenfolge.  
  
 Wenn das Flag `i` festgelegt ist, wird bei der Suche nicht zwischen Groß- und Kleinschrift unterschieden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `match`-Methode veranschaulicht.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Exec-Methode (regulärer Ausdruck)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Replace-Methode (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Search-Methode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test-Methode (regulärer Ausdruck)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmieren mit regulären Ausdrücken (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternierung und Unterausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Rückverweise (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)