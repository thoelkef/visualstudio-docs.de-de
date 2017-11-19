---
title: ToExponential-Methode (Zahl) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>toExponential-Methode (Zahl) (JavaScript)
Stellt eine Zahl in Exponentialschreibweise dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Parameter  
 `numObj`  
 Erforderlich. Ein **Anzahl** Objekt.  
  
 `fractionDigits`  
 Dies ist optional. Die Anzahl der Ziffern nach dem Dezimaltrennzeichen an. Muss im Bereich 0 - 20 liegen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine Zeichenfolgendarstellung einer Zahl in Exponentialschreibweise zurück. Die Zeichenfolge enthält eine Ziffer vor dem Dezimaltrennzeichen und enthalten möglicherweise `fractionDigits` Ziffern nach.  
  
 Wenn `fractionDigits` nicht angegeben wird, die `toExponential` Methodenrückgabe so viele Ziffern erforderlich, um die Anzahl eindeutig anzugeben.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToFixed-Methode (Zahl)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision-Methode (Zahl)](../../javascript/reference/toprecision-method-number-javascript.md)