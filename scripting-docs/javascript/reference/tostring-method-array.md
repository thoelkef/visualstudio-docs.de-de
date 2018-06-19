---
title: ToString-Methode (Array) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640410"
---
# <a name="tostring-method-array"></a>toString-Methode (Array)
Gibt eine Zeichenfolgendarstellung eines Arrays zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Parameter  
 `array`  
 Erforderlich. Das Array, das als Zeichenfolge darzustellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Zeichenfolgendarstellung des Arrays.  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente einer `Array` in Zeichenfolgen konvertiert werden. Die resultierenden Zeichenfolgen werden verkettet und durch Kommas getrennt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ToString** Methode mit einem Array.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]