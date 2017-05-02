---
title: "Math.sign-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Math.sign-Funktion (JavaScript)
Gibt das Vorzeichen einer Zahl zurück und gibt damit an, ob die Zahl positiv, negativ oder 0 ist.  
  
## Syntax  
  
```  
Math.sign(number)  
```  
  
## Hinweise  
 Das erforderliche `number`\-Argument ist ein numerischer Ausdruck, für den das Vorzeichen erforderlich ist.  
  
 Der Rückgabetyp ist einer der folgenden Werte:  
  
-   `NaN`, wenn `number` `NaN` ist.  
  
-   \-0, wenn `number` −0 ist.  
  
-   \+0, wenn `number` \+0 ist.  
  
-   \-1, wenn `number` negativ und nicht −0 ist.  
  
-   \+1, wenn `number` positiv und nicht \+0 ist.  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]