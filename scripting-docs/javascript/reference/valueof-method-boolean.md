---
title: "valueOf Method (Boolesch) | Microsoft Docs"
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
ms.assetid: ac6ad343-7663-406a-a2b7-4cc5025ca3d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf Method (Boolesch)
Gibt den primitiven Wert des angegebenen booleschen Werts zurück.  
  
## Syntax  
  
```  
  
boolean.valueOf()  
```  
  
## Rückgabewert  
 Der primitive Wert \(true oder false\) des booleschen Werts.  
  
## Hinweise  
 Im folgenden Code wird die Verwendung dieser Methode veranschaulicht.  
  
```javascript  
var bool = new Boolean("true");  
var s = bool.valueOf();  
document.write(s);  
  
// Output: true  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]