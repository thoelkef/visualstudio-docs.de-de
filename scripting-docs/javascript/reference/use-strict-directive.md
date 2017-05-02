---
title: "Use Strict-Direktive | Microsoft Docs"
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
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "strict-Modus"
  - "Use Strict-Direktive"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Use Strict-Direktive
Schränkt die Verwendung einiger Funktionen in JavaScript ein.  Wird in Internet Explorer 10 und nur in [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps unterstützt.  
  
## Syntax  
  
```javascript  
use strict  
```  
  
## Hinweise  
  
## Beispiel  
 Der folgende Code verursacht einen Syntaxfehler, da im strict\-Modus alle Variablen mit `var` deklariert werden müssen.  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## Siehe auch  
 [Strict\-Modus](../../javascript/advanced/strict-mode-javascript.md)