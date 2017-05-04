---
title: "Nicht definierter Bezeichner | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5009"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8c8000d9-dd14-487e-922d-98430024a0f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Nicht definierter Bezeichner
Sie haben versucht, einen Bezeichner zu verwenden, den der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Compiler nicht erkennt.  Der Wert "nicht definiert" wird in folgenden Fällen zurückgegeben:  
  
-   Es wird eine Variable verwendet, die nicht vorhanden ist.  
  
-   Eine deklarierte Variable wird verwendet, der jedoch niemals ein Wert zugewiesen wurde.  
  
-   Es wird eine nicht vorhandene Objekteigenschaft verwendet.  
  
### So beheben Sie diesen Fehler  
  
-   Deklarieren Sie die Variable mit einer **var** \-Anweisung \(wie in `var` x;\).  
  
## Siehe auch  
 [Variablen](../../javascript/variables-javascript.md)   
 [Variablenbereich](../../javascript/advanced/variable-scope-javascript.md)