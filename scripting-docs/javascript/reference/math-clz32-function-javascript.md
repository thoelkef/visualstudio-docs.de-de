---
title: Math. clz32-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Math.clz32-Funktion (JavaScript)
Gibt die Anzahl führender Nullbits in der 32-Bit-Binärdarstellung einer Zahl zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn `number` 0 ist, lautet das Ergebnis 32. Wenn das wichtigste Bit der 32-Bit-Binärverschlüsselung von `number` 1 ist, lautet das Ergebnis 0.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)