---
title: Reverse-Methode (JavaScript) | Microsoft Docs
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
- reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639710"
---
# <a name="reverse-method-javascript"></a>reverse-Methode (JavaScript)
Kehrt die Elemente in einer `Array`.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Umgekehrten Arrays.  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `arrayObj` Verweis ist ein `Array` Objekt.  
  
 Die `reverse` Methode kehrt die Elemente einer `Array` -Objekts. Werden keine erstellt ein neues `Array` Objekts während der Ausführung.  
  
 Wenn das Array nicht zusammenhängend ist, ist die `reverse` Methode Elemente im Array, das Füllen der Lücken in das Array erstellt. Jedes dieser Elemente erstellt hat den Wert `undefined`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `reverse`-Methode veranschaulicht.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [concat-Methode (Array)](../../javascript/reference/concat-method-array-javascript.md)