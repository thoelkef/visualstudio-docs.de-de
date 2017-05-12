---
title: "toString-Methode (Array) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString-Methode (Array)
Gibt eine Zeichenfolgendarstellung eines Arrays zurück.  
  
## Syntax  
  
```  
  
array.toString()  
```  
  
## Parameter  
 `array`  
 Erforderlich.  Das Array, das als Zeichenfolge dargestellt werden soll.  
  
## Rückgabewert  
 Die Zeichenfolgendarstellung des Arrays.  
  
## Hinweise  
 Die Elemente eines `Array` werden in Zeichenfolgen konvertiert.  Die resultierenden Zeichenfolgen werden durch Kommas getrennt miteinander verkettet.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **toString**\-Methode mit einem Array.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]