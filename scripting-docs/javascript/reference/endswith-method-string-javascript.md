---
title: EndsWith-Methode (String) (JavaScript) | Microsoft Docs
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="endswith-method-string-javascript"></a>endsWith-Methode (String) (JavaScript)
Gibt einen Wert zurück, der angibt, ob eine Zeichenfolge oder Teilzeichenfolge mit einer anderen angegebenen Zeichenfolge endet.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das String-Objekt, nach dem gesucht werden soll.  
  
 `str`  
 Erforderlich. Die Suchzeichenfolge.  
  
 `position`  
 Dies ist optional. Die Position des ersten Zeichens für die Suche im String-Objekt, beginnend mit 0.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die bei `position` beginnende Zeichenfolge mit der Suchzeichenfolge endet, gibt die `endsWith`-Methode `true` zurück; andernfalls gibt sie `false` zurück.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn `str` ein `RegExp` ist, wird ein `TypeError` ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]