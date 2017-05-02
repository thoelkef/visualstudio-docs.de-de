---
title: "Math.round-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math-Objekt"
  - "Round-Methode"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round-Funktion (JavaScript)
Gibt den die nächste ganze Zahl gerundeten angegebenen numerischen Ausdruck zurück.  
  
## Syntax  
  
```  
  
Math.round(  
number  
)   
```  
  
## Hinweise  
 Das obligatorische `number`\-Argument bildet den Wert, der auf die nächste ganze Zahl gerundet werden soll.  
  
 Wenn bei positiven ganzen Zahlen der Nachkommateil von `number` 0,5 oder größer ist, wird als Rückgabewert die kleinste ganze Zahl größer als `number` verwendet.  Falls der Nachkommateil kleiner als 0,5 ist, wird als Rückgabewert die größte ganze Zahl kleiner oder gleich `number` verwendet.  
  
 Wenn bei negativen Zahlen der Nachkommateil genau \-0,5 beträgt, wird als Rückgabewert die kleinste ganze Zahl verwendet, die größer als die Zahl ist.  
  
 Beispielsweise gibt `Math.round(8.5)` 9, `Math.round(-8.5)` jedoch \-8 zurück.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Siehe auch  
 [Math.random\-Funktion](../../javascript/reference/math-random-function-javascript.md)