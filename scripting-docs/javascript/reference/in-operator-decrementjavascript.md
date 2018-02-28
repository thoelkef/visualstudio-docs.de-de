---
title: in-Operator (JavaScript) | Microsoft Docs
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="in-operator-javascript"></a>in-Operator (JavaScript)
Überprüft, ob eine Eigenschaft in einem Objekt vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Erforderlich. Beliebige Variable.  
  
 `property`  
 Erforderlich. Ein Ausdruck, der auf einen Zeichenfolgenausdruck ausgewertet wird.  
  
 `object`  
 Erforderlich. Jedes Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Die `in` Operator bestimmt, ob ein Objekt über eine Eigenschaft namens verfügt `property`. Es bestimmt außerdem, ob die Eigenschaft Teil der Prototypenkette des Objekts. Weitere Informationen zum Objekt-Prototypen, finden Sie unter [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die `in` Operator:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)