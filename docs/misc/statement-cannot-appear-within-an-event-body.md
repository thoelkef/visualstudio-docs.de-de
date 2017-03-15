---
title: "Eine Anweisung kann nicht innerhalb eines Ereignistexts verwendet werden. | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Anweisung kann nicht innerhalb eines Ereignistexts verwendet werden.
Eine Anweisung kann nicht innerhalb eines Ereignistexts verwendet werden. Das Ende des Ereignisses wird angenommen.  
  
 Eine Anweisung, die in einem Ereignistext ungültig ist, wird in einem Ereignistext angezeigt.  
  
 **Fehler\-ID:** BC31112  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie ein `End Event` vor der Anweisung hinzu.  
  
## Siehe auch  
 [Application Events Sample](http://msdn.microsoft.com/de-de/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)