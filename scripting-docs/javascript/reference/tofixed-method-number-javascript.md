---
title: ToFixed-Methode (Zahl) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640400"
---
# <a name="tofixed-method-number-javascript"></a>toFixed-Methode (Zahl) (JavaScript)
Eine Zahl in Festkommanotation darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Parameter  
 `numObj`  
 Erforderlich, ein `Number` Objekt.  
  
 `fractionDigits`  
 Dies ist optional. Die Anzahl der Ziffern nach dem Dezimaltrennzeichen an. Muss im Bereich 0 - 20 liegen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine Zeichenfolgendarstellung einer Zahl in Festkommanotation, mit `fractionDigits` Ziffern nach dem Dezimaltrennzeichen an.  
  
 Wenn `fractionDigits` nicht angegeben wird oder **undefined**, der Standardwert ist 0 (null).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung von `toFixed` veranschaulicht.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ToExponential-Methode (Zahl)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision-Methode (Zahl)](../../javascript/reference/toprecision-method-number-javascript.md)