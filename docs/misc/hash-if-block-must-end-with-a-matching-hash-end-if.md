---
title: "#If-Block muss mit einem entsprechenden &quot;#End If&quot; abgeschlossen werden | Microsoft Docs"
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
  - "vbc30012"
  - "bc30012"
helpviewer_keywords: 
  - "BC30012"
ms.assetid: 9d51f3be-d2c3-4918-a36d-0d9e9763e47b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #If-Block muss mit einem entsprechenden &quot;#End If&quot; abgeschlossen werden
`#If` ist eine Direktive für die bedingte Kompilierung. Ein `#If`\-Block wird nicht durch eine `#End If`\-Direktive beendet.  
  
 **Fehler\-ID:** BC30012  
  
### So beheben Sie diesen Fehler  
  
-   Hinzufügen eine `#End If`\-Direktive am Ende des Blocks für die bedingte Kompilierung hinzu.  
  
## Siehe auch  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)