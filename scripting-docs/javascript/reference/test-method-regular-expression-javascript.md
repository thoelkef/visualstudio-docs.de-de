---
title: Test-Methode (regulärer Ausdruck) (JavaScript) | Microsoft Docs
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
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640750"
---
# <a name="test-method-regular-expression-javascript"></a>test-Methode (regulärer Ausdruck) (JavaScript)
Gibt einen booleschen Wert, der angibt, ob ein Muster in einer durchsuchten Zeichenfolge vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Parameter  
 `rgExp`  
 Erforderlich. Eine Instanz von einem **reguläre** Objekt, das das Muster eines regulären Ausdrucks sowie anwendbare Flags enthält.  
  
 `str`  
 Erforderlich. Die Zeichenfolge, für die Suche durchführen.  
  
## <a name="remarks"></a>Hinweise  
 Die **testen** Methode überprüft, um festzustellen, ob ein Muster in einer Zeichenfolge vorhanden ist und gibt **"true"** Wenn dies der Fall ist, und **"false"** andernfalls.  
  
 Die Eigenschaften des globalen `RegExp` Objekt nicht geändert werden die **testen** Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **testen** Methode. Um dieses Codebeispiel verwenden möchten, übergeben Sie der Funktion Muster eines regulären Ausdrucks und eine Zeichenfolge. Die Funktion wird für das Vorkommen der Muster für reguläre Ausdrücke in der Zeichenfolge zu testen und geben eine Zeichenfolge, der angibt, die Ergebnisse dieses Vergleichs zurück:  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)