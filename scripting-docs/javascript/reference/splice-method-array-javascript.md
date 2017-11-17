---
title: splice-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>splice-Methode (Array) (JavaScript)
Entfernt Elemente aus einem Array und fügt ggf. an ihrer Stelle neue Elemente ein, wobei die gelöschten Elemente zurückgegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `start`  
 Erforderlich. Die nullbasierte Position im Array, ab dem Entfernen von Elementen beginnen.  
  
 `deleteCount`  
 Erforderlich. Die Anzahl der zu entfernenden Elemente.  
  
 `item1, item2,. . ., itemN`  
 Dies ist optional. Elemente, die in das Array anstelle der gelöschten Elemente eingefügt.  
  
## <a name="remarks"></a>Hinweise  
 Die `splice` Methode ändert `arrayObj` durch das Entfernen der angegebenen Anzahl von Elementen aus Position `start` und das Einfügen von neuen Elementen. Die gelöschten Elemente werden zurückgegeben, als neue `Array` Objekt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `splice`-Methode veranschaulicht.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [slice-Methode (Array)](../../javascript/reference/slice-method-array-javascript.md)