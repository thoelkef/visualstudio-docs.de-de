---
title: Repeat-Methode (String) (JavaScript) | Microsoft Docs
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="repeat-method-string-javascript"></a>repeat-Methode (String) (JavaScript)
Gibt ein neues String-Objekt mit einem Wert zurück, der gleich der ursprünglichen Zeichenfolge in der angegebenen Anzahl von Wiederholungen ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das String-Objekt.  
  
 `count`  
 Erforderlich. Die Anzahl der Wiederholungen der ursprünglichen Zeichenfolge in der zurückgegebenen Zeichenfolge.  
  
## <a name="exceptions"></a>Ausnahmen  
 Diese Methode löst einen RangeError aus, wenn und nur wenn das Argument negativ oder plus unendlich ist.  
  
## <a name="remarks"></a>Hinweise  
 Die `repeat`-Methode verkettet die ursprüngliche Zeichenfolge mit der neuen Zeichenfolge, und zwar so oft, wie von `count` angegeben.  
  
 Diese Methode löst einen Fehler aus, wenn `count` keine positive Zahl kleiner als `Infinity` ist.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]