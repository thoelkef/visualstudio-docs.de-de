---
title: Math.Acosh-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Math.acosh-Funktion (JavaScript)
Gibt den hyperbolischen Arkuskosinus (oder den umgekehrten hyperbolischen Kosinus) einer Zahl zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Parameter  
 Das erforderliche `number`-Argument ist ein numerischer Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Der umgekehrte hyperbolische Kosinus des `number`-Arguments im Bogenmaß.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung der `acosh`-Funktion veranschaulicht.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Hinweise  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Math.acos-Funktion](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.ASIN-Funktion](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.ATAN-Funktion](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.Cos-Funktion](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.Sin-Funktion](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan-Funktion](../../javascript/reference/math-tan-function-javascript.md)   
 [Math-Objekt](../../javascript/reference/math-object-javascript.md)