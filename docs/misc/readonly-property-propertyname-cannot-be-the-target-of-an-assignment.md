---
title: "Die ReadOnly-Eigenschaft &quot;&lt;Eigenschaftenname&gt;&quot; kann nicht das Ziel einer Zuweisung sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die ReadOnly-Eigenschaft &quot;&lt;Eigenschaftenname&gt;&quot; kann nicht das Ziel einer Zuweisung sein.
Ein `ReadOnly`\-Eigenschaft tritt in einem Kontext auf, der ihr einen Wert zuweist. Nur schreibbaren Variablen, Eigenschaften und Arrayelementen können während der Ausführung Werte zugewiesen werden.  
  
 **Fehler\-ID:** BC30098  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `ReadOnly`\-Schlüsselwort aus der `Property`\-Anweisung, die die Variable deklariert, oder entfernen Sie die Anweisung, die ihr einen Wert zuweist.  
  
## Siehe auch  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)