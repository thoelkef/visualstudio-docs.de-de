---
title: "Das Erben von &#39;System.&lt;Klassenname&gt;&#39; ist ung&#252;ltig. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30015"
  - "bc30015"
helpviewer_keywords: 
  - "BC30015"
ms.assetid: b4c005df-a510-47c7-b5cc-27f4514d32b6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Erben von &#39;System.&lt;Klassenname&gt;&#39; ist ung&#252;ltig.
Eine Klasse kann nicht von `System.Array`, `System.Delegate`, `System.Enum` oder `System.ValueType` erben.  
  
 **Fehler\-ID:** BC30015  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Inherits`\-Anweisung, oder ändern Sie sie, um von einer gültigen Basisklasse zu erben.  
  
## Siehe auch  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Object Variable Declaration](/dotnet/visual-basic/programming-guide/language-features/variables/object-variable-declaration)