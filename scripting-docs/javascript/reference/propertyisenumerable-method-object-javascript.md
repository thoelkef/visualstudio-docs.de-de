---
title: PropertyIsEnumerable-Methode (Objekt) (JavaScript) | Microsoft Docs
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
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638850"
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable-Methode (Objekt) (JavaScript)
Bestimmt, ob eine angegebene Eigenschaft aufzählbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Instanz eines Objekts.  
  
 `proName`  
 Erforderlich. Zeichenfolgenwert eines Eigenschaftennamens.  
  
## <a name="remarks"></a>Hinweise  
 Die `propertyIsEnumerable` -Methode zurückkehrt `true` Wenn `proName` vorhanden ist, `object` und aufgelistet werden kann, mithilfe einer `For` Schleife. Die `propertyIsEnumerable` -Methode zurückkehrt `false` Wenn `object` verfügt nicht über eine Eigenschaft mit dem angegebenen Namen oder wenn die angegebene Eigenschaft nicht aufzählbar ist. Vordefinierte Eigenschaften sind nicht aufzählbare normalerweise benutzerdefinierten Eigenschaften sind immer aufzählbar.  
  
 Die `propertyIsEnumerable` Methode berücksichtigt nicht die Objekte in der Prototypenkette.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)