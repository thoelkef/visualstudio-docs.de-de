---
title: ParseInt-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt-Funktion (JavaScript)
Konvertiert eine Zeichenfolge in eine ganze Zahl.  
  
## <a name="syntax"></a>Syntax  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Parameter  
 `numString`  
 Erforderlich. Eine Zeichenfolge, die in eine Zahl zu konvertieren.  
  
 `radix`  
 Dies ist optional. Ein Wert zwischen 2 und 36 liegt, der angibt, der Basis der Zahl in `numString`. Wenn dieses Argument nicht angegeben ist, sind Zeichenfolgen mit dem Präfix "0 X" als hexadezimale betrachtet. Alle anderen Zeichenfolgen werden als Dezimal betrachtet.  
  
## <a name="remarks"></a>Hinweise  
 Die `parseInt` Funktion gibt einen ganzzahligen Wert gleich der Zahl in `numString`. Wenn kein Präfix des `numString` erfolgreich in eine ganze Zahl analysiert werden `NaN` (not a Number) zurückgegeben wird.  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Sie können testen, für `NaN` mithilfe der `isNaN` Funktion.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  Ab [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]die `parseInt` Funktion ist eine Zeichenfolge, die das Präfix "0" als oktale hat nicht behandeln. Wenn Sie nicht mithilfe der `parseInt` -Funktion, allerdings Zeichenfolgen mit dem Präfix "0" weiterhin als in oktalen Zahlen ist interpretiert werden können. Finden Sie unter [Datentypen](../../javascript/data-types-javascript.md) Informationen oktale ganze Zahlen.  
  
## <a name="see-also"></a>Siehe auch  
 [IsNaN-Funktion](../../javascript/reference/isnan-function-javascript.md)   
 [ParseFloat-Funktion](../../javascript/reference/parsefloat-function-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)   
 [valueOf-Methode (Objekt)](../../javascript/reference/valueof-method-object-javascript.md)