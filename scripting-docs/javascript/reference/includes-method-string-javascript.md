---
title: Includes-Methode (String) (JavaScript) | Microsoft Docs
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>includes-Methode (String) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob die übergebene Zeichenfolge im string-Objekt enthalten ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das string-Objekt für den Test.  
  
 `substring`  
 Erforderlich. Die zu testende Zeichenfolge.  
  
 `position`  
 Dies ist optional. Die Position des ersten Zeichens für den Test im string-Objekt, beginnend mit 0.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die übergebene Zeichenfolge im string-Objekt enthalten ist, gibt die `includes`-Methode `true` zurück, andernfalls gibt sie `false` zurück.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]