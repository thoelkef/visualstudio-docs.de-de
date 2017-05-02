---
title: "Nummerkonstanten (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Konstanten [JavaScript], Nummer"
  - "MAX_VALUE-Konstante [JavaScript]"
  - "MIN_VALUE-Konstante [JavaScript]"
  - "NaN-Konstante [JavaScript]"
  - "NEGATIVE_INFINITY-Konstante [JavaScript]"
  - "Nummerkonstanten [JavaScript]"
  - "Number.MAX_VALUE-Konstante [JavaScript]"
  - "Number.MIN_VALUE-Konstante [JavaScript]"
  - "Number.NaN-Konstante [JavaScript]"
  - "Number.NEGATIVE_INFINITY-Konstante [JavaScript]"
  - "Number.POSITIVE_INFINITY-Konstante [JavaScript]"
  - "POSITIVE_INFINITY-Konstante [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Nummerkonstanten (JavaScript)
Die folgenden Zahlenkonstanten sind Eigenschaften des `Number`\-Objekts.  
  
## Konstanten des Number\-Objekts  
 Sie müssen kein `Number`\-Objekt erstellen, um auf diese Konstanten zuzugreifen.  
  
|Konstante|Zurückgegebener Wert|  
|---------------|--------------------------|  
|`Number.EPSILON`|Die kleinste Zahl, die in [!INCLUDE[javascript](../../includes/javascript-md.md)] dargestellt werden kann.  Ist ungefähr gleich 2,2204460492503130808472633361816E\-16.|  
|`Number.MAX_SAFE_INTEGER`|Die größte Zahl, die in JavaScript sicher dargestellt werden kann.  Gleich 9007199254740991.|  
|`Number.MAX_VALUE`|Die größte Zahl, die in [!INCLUDE[javascript](../../includes/javascript-md.md)] dargestellt werden kann.  Ist ungefähr gleich 1,79E\+308.|  
|`Number.MIN_SAFE_INTEGER`|Die kleinste Zahl, die in JavaScript sicher dargestellt werden kann.  Gleich −9007199254740991.|  
|`Number.MIN_VALUE`|Die Null am nächsten liegende Zahl, die in [!INCLUDE[javascript](../../includes/javascript-md.md)] dargestellt werden kann.  Ist ungefähr gleich 5,00E\-324.|  
|`Number.NaN`|Ein Wert, der keine Zahl ist.<br /><br /> In Gleichheitsvergleichen entspricht `NaN` keinem Wert, sich selbst eingeschlossen.  Um zu testen, ob ein Wert `NaN` entspricht, verwenden Sie die [isNaN\-Funktion](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Ein Wert, der kleiner als die größte negative Zahl ist, die in [!INCLUDE[javascript](../../includes/javascript-md.md)] dargestellt werden kann.<br /><br /> [!INCLUDE[javascript](../../includes/javascript-md.md)] zeigt `NEGATIVE_INFINITY`\-Werte als `-infinity` an.|  
|`Number.POSITIVE_INFINITY`|Ein Wert, der größer als die größte Zahl ist, die in [!INCLUDE[javascript](../../includes/javascript-md.md)] dargestellt werden kann.<br /><br /> [!INCLUDE[javascript](../../includes/javascript-md.md)] zeigt `POSITIVE_INFINITY`\-Werte als `infinity` an.|  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
 Für `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` und `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]  
  
 **Gilt für**: [Number\-Objekt](../../javascript/reference/number-object-javascript.md)  
  
## Siehe auch  
 [Math\-Konstanten](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript\-Konstanten](../../javascript/reference/javascript-constants.md)   
 [Infinity\-Konstante](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN\-Konstante](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN\-Funktion](../../javascript/reference/isnan-function-javascript.md)