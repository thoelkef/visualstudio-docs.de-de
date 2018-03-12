---
title: "Compile-Methode (regulärer Ausdruck) (JavaScript) | Microsoft Docs"
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
- compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>compile-Methode (regulärer Ausdruck) (JavaScript)
Kompiliert einen regulären Ausdruck in ein internes Format für die Ausführung beschleunigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Parameter  
 `rgExp`  
 Erforderlich. Eine Instanz von einem **reguläre** Objekt. Hierbei kann es sich um einen Variablennamen oder ein Literal sein.  
  
 *Muster*  
 Erforderlich. Ein Zeichenfolgenausdruck, enthält das Muster eines regulären Ausdrucks zu kompilierenden  
  
 `flags`  
 Dies ist optional. Folgende Flags, die miteinander kombinierbar sind, stehen zur Verfügung:  
  
-   g (globale Suche nach allen Vorkommen von *Muster*)  
  
-   i (Groß-/Kleinschreibung ignorieren)  
  
-   m (mehrzeilige Suche)  
  
## <a name="remarks"></a>Hinweise  
 Die **Kompilieren** -Methode konvertiert *Muster* in ein internes Format für die Ausführung beschleunigt wird. Dies ermöglicht eine effizientere Verwendung von regulären Ausdrücken in Schleifen, z. B.. Ein kompilierter regulärer Ausdruck beschleunigt Dinge Wenn den gleichen Ausdruck wiederholt wiederverwendet. Bietet keinen Vorteil ist jedoch erzielt, wenn der reguläre Ausdruck ändert.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Kompilieren** Methode:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)