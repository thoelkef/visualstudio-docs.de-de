---
title: "toString-Methode (Zahl) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString-Methode (Zahl)
Gibt eine Zeichenfolgendarstellung einer Zahl zurück.  
  
## Syntax  
  
```  
  
number.toString()  
```  
  
## Parameter  
 `number`  
 Erforderlich.  Die Zahl, die als Zeichenfolge dargestellt werden soll.  
  
## Rückgabewert  
 Die Zeichenfolgendarstellung der Zahl.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **toString**\-Methode mit einer Zahl.  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]