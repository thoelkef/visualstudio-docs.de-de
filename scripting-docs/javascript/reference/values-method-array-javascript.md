---
title: Values-Methode (Array) (JavaScript) | Microsoft Docs
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1a90dfd81ae8baf6590f69f0126adc97d42c20e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640690"
---
# <a name="values-method-array-javascript"></a>values-Methode (Array) (JavaScript)
Gibt einen Iterator zurück, der die Werte des Arrays zurückgibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
arrayObj.values();  
```  
  
#### <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Das Arrayobjekt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die Werte eines Arrays abgerufen werden.  
  
```JavaScript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]