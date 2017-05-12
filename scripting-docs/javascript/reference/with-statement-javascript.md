---
title: "with-Anweisung (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With-Anweisung"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with-Anweisung (JavaScript)
Legt das Standardobjekt für eine Anweisung fest.  
  
## Syntax  
  
```  
with (object) {  
    statements  
}   
```  
  
## Parameter  
 `object`  
 Das Standardobjekt.  
  
 `statements`  
 Eine oder mehrere Anweisungen, für die `object` das Standardobjekt ist.  
  
## Hinweise  
 Die `with`\-Anweisung wird vielfach zur Verkürzung von Programmcode verwendet.  
  
> [!WARNING]
>  Die Verwendung von `with` ist im Strict\-Modus nicht zugelassen.  Durch die Verwendung von `with` kann Code schwieriger lesbar und zu debuggen sein und sollte im Allgemeinen vermieden werden.  
  
## Beispiel  
 In diesem Beispiel wird das `Math`\-Objekt wiederholt verwendet.  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## Beispiel  
 Wenn Sie das Beispiel ändern, um die `with`\-Anweisung zu verwenden, wird der Code kürzer:  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [this\-Anweisung](../../javascript/reference/this-statement-javascript.md)