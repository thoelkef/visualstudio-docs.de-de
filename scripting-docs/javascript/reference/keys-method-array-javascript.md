---
title: Keys-Methode (Array) (JavaScript) | Microsoft Docs
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f600facc91dd10219196f580abd0f52537010dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="keys-method-array-javascript"></a>keys-Methode (Array) (JavaScript)
Gibt einen Iterator zurück, der die Indexwerte des Arrays zurückgibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
arrayObj.keys();  
```  
  
#### <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Das Arrayobjekt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die Schlüsselwerte eines Arrays abgerufen werden.  
  
```JavaScript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]