---
title: "Die Shared-Attributeigenschaft &#39;&lt;eigenschaftsfeld&gt;&#39; kann nicht das Ziel einer Zuweisung sein. | Microsoft Docs"
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
  - "bc31500"
  - "vbc31500"
helpviewer_keywords: 
  - "BC31500"
ms.assetid: dffa2b07-9609-4aa3-ae58-c0804d8a05d6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Shared-Attributeigenschaft &#39;&lt;eigenschaftsfeld&gt;&#39; kann nicht das Ziel einer Zuweisung sein.
Es wurde versucht, einer `ReadOnly`\- oder `Shared`\-Eigenschaft in einem Attribut einen Wert zuzuweisen.  
  
 **Fehler\-ID:** BC31500  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Anweisung zur Zuweisung der Eigenschaft.  
  
2.  Wenn Sie Eigenschaften verwenden, die Sie entwickelt haben, entfernen Sie den `ReadOnly`\- oder `Shared`\-Modifizierer aus der Attributeigenschaft.  
  
## Siehe auch  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)