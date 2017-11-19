---
title: Number-Konstanten (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="number-constants-javascript"></a>Nummerkonstanten (JavaScript)
Die folgenden Zahlenkonstanten sind Eigenschaften des `Number`-Objekts.  
  
## <a name="number-object-constants"></a>Konstanten des Number-Objekts  
 Sie müssen kein `Number`-Objekt erstellen, um auf diese Konstanten zuzugreifen.  
  
|Konstante|Zurückgegebener Wert|  
|--------------|--------------------|  
|`Number.EPSILON`|Die kleinste Zahl, die in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dargestellt werden kann. Ist ungefähr gleich 2,2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Die größte Zahl, die in JavaScript sicher dargestellt werden kann. Gleich 9007199254740991.|  
|`Number.MAX_VALUE`|Die größte Zahl, die in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dargestellt werden kann. Ist ungefähr gleich 1,79E+308.|  
|`Number.MIN_SAFE_INTEGER`|Die kleinste Zahl, die in JavaScript sicher dargestellt werden kann. -9007199254740991 gleich.|  
|`Number.MIN_VALUE`|Die Null am nächsten liegende Zahl, die in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dargestellt werden kann. Ist ungefähr gleich 5,00E-324.|  
|`Number.NaN`|Ein Wert, der keine Zahl ist.<br /><br /> In Gleichheitsvergleichen entspricht `NaN` keinem Wert, sich selbst eingeschlossen. So testen Sie, ob ein Wert entspricht `NaN`, verwenden Sie die [IsNaN-Funktion](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Ein Wert, der kleiner als die größte negative Zahl ist, die in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dargestellt werden kann.<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zeigt `NEGATIVE_INFINITY`-Werte als `-infinity` an.|  
|`Number.POSITIVE_INFINITY`|Ein Wert, der größer als die größte Zahl ist, die in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dargestellt werden kann.<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zeigt `POSITIVE_INFINITY`-Werte als `infinity` an.|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Für `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` und `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Gilt für**: [Number-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Math-Konstanten](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript-Konstanten](../../javascript/reference/javascript-constants.md)   
 [Infinity-Konstante](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN-Konstante](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN-Funktion](../../javascript/reference/isnan-function-javascript.md)