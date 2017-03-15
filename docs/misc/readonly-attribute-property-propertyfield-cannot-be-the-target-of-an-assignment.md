---
title: "Die ReadOnly-Attributeigenschaft &quot;&lt;Eigenschaftenfeld&gt;&quot; kann nicht das Ziel einer Zuweisung sein. | Microsoft Docs"
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
  - "bc31501"
  - "vbc31501"
helpviewer_keywords: 
  - "BC31501"
ms.assetid: 41c3f979-6b24-4595-9503-9c80a4d6d762
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die ReadOnly-Attributeigenschaft &quot;&lt;Eigenschaftenfeld&gt;&quot; kann nicht das Ziel einer Zuweisung sein.
Es wurde versucht, einer `ReadOnly`\-Eigenschaft in einem Attribut einen Wert zuzuweisen.  
  
 **Fehler\-ID:** BC31501  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Anweisung zur Zuweisung der Eigenschaft.  
  
2.  Wenn Sie Eigenschaften verwenden, die Sie entwickelt haben, entfernen Sie den `ReadOnly`\- oder `Shared`\-Modifizierer aus der Attributeigenschaft.  
  
## Siehe auch  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)