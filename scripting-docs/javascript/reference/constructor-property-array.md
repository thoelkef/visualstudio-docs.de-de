---
title: Constructor-Eigenschaft (Array) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca779a2fa2356c1f3e1ca816f16531c0930459a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-array"></a>constructor-Eigenschaft (Array)
Gibt die Funktion an, mit der ein Array erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array.constructor  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `array` ist der Name eines Arrays.  
  
 Die `constructor`-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt. Dies schließt alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte mit Ausnahme der `Global` und `Math` Objekte. Die `constructor`-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der Constructor-Eigenschaft.  
  
```JavaScript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]