---
title: ToPrecision-Methode (Zahl) (JavaScript) | Microsoft Docs
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
- toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>toPrecision-Methode (Zahl) (JavaScript)
Eine Zahl darstellt, entweder in Exponentialnotation oder in Festkommanotation Notation mit einer angegebenen Anzahl von Ziffern.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Parameter  
 `numObj`  
 Erforderlich. Ein `Number`-Objekt.  
  
 `precision`  
 Dies ist optional. Die Anzahl der signifikanten Stellen. Muss im Bereich 1-21 liegen.  
  
## <a name="return-value"></a>Rückgabewert  
 Für Zahlen in Exponentialschreibweise `precision` - 1 Ziffern nach dem Dezimaltrennzeichen zurückgegeben werden. Für Zahlen in Festkommanotation `precision` signifikante Ziffern zurückgegeben werden.  
  
 Wenn `precision` nicht angegeben oder ist **undefined**, die **ToString** -Methode erfolgt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung von `toPrecision` veranschaulicht.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToFixed-Methode (Zahl)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential-Methode (Zahl)](../../javascript/reference/toexponential-method-number-javascript.md)