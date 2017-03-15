---
title: "Der Preserve-Operand &#39;ReDim&#39; kann nicht &#39;Nothing&#39; sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Preserve-Operand &#39;ReDim&#39; kann nicht &#39;Nothing&#39; sein
Eine `ReDim`\-Anweisung hat versucht, mithilfe des `Preserve`\-Schlüsselworts eine Dimension eines Arrays zu ändern, die nicht die letzte Dimension ist, aber es wurde keine gültiger Wert für den Operanden bereitgestellt.  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den `Preserve`\-Operanden in einen gültigen Wert.  
  
## Siehe auch  
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD: Mehrdimensionale Arrays in Visual Basic](http://msdn.microsoft.com/de-de/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Beibehalten – Löschen](http://msdn.microsoft.com/de-de/91badeab-b4e0-48b6-92c9-9f0c8f995d81)