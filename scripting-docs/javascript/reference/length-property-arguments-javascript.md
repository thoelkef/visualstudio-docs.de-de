---
title: Length-Eigenschaft (Arguments) (JavaScript) | Microsoft Docs
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637910"
---
# <a name="length-property-arguments-javascript"></a>length-Eigenschaft (arguments) (JavaScript)
Gibt die tatsächliche Anzahl der Argumente zurück, die von der aufrufenden Routine an eine Funktion übergeben wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Hinweise  
 Das optionale *Funktion* -Argument ist der Name der derzeit ausgeführten `Function` Objekt.  
  
 Die **Länge** Eigenschaft von der **Argumente** Objekt wird initialisiert, indem dem Skriptmodul in die tatsächliche Anzahl der Argumente an eine `Function` Objekt, wenn die Ausführung in dieser Funktion beginnt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung von der **Länge** Eigenschaft von der **Argumente** Objekt. Um das Beispiel vollständig zu verstehen, übergeben Sie mehrere Argumente an die Funktion als 2 Argumente erwartet:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Arguments-Objekt](../../javascript/reference/arguments-object-javascript.md)&#124; [Objekt-Funktion](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Arguments-Eigenschaft (Funktion)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length-Eigenschaft (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length-Eigenschaft (String)](../../javascript/reference/length-property-string-javascript.md)