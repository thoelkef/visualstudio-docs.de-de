---
title: unshift-Methode (Array) (JavaScript) | Microsoft Docs
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
- unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>unshift-Methode (Array) (JavaScript)
Fügt am Anfang eines Arrays neue Elemente ein.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `item1, item2,. . ., itemN`  
 Dies ist optional. Elemente zum Einfügen am Anfang der `Array`.  
  
## <a name="remarks"></a>Hinweise  
 Die `unshift` -Methode fügt Elemente am Anfang eines Arrays, damit sie in der gleichen Reihenfolge angezeigt werden, in dem sie in der Argumentliste angezeigt werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `unshift`-Methode veranschaulicht.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [shift-Methode (Array)](../../javascript/reference/shift-method-array-javascript.md)