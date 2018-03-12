---
title: Math.Round-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Math.round-Funktion (JavaScript)
Gibt einen angegebenen numerischen Ausdruck, der auf die nächste ganze Zahl gerundet zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `number` Argument ist der Wert auf die nächste Ganzzahl gerundet werden soll.  
  
 Für positive Zahlen Wenn die Nachkommastellen des `number` 0,5 oder größer ist, ist der Rückgabewert ist die kleinste ganze Zahl größer gleich `number`. Wenn die Nachkommastellen kleiner als 0,5 ist, der Rückgabewert ist die größte ganze Zahl kleiner als oder gleich `number`.  
  
 Bei negativen Zahlen, wenn die Nachkommastellen exakt Verschiebung von -0,5, der Rückgabewert ist die kleinste ganze Zahl, die größer als die Anzahl ist.  
  
 Beispielsweise `Math.round(8.5)` gibt 9, aber `Math.round(-8.5)` gibt-8.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Math-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Math.random-Funktion](../../javascript/reference/math-random-function-javascript.md)