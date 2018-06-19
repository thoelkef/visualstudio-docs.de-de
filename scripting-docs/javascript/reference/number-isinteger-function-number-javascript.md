---
title: Number.isInteger-Funktion (Zahl) (JavaScript) | Microsoft Docs
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638800"
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger-Funktion (Zahl) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Wert eine ganze Zahl ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn der Wert eine Ganzzahl ist, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```