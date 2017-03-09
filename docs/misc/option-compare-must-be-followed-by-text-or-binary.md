---
title: "Auf &#39;Option Compare&#39; muss &#39;Text&#39; oder &#39;Binary&#39; folgen. | Microsoft Docs"
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
  - "vbc30207"
  - "bc30207"
helpviewer_keywords: 
  - "BC30207"
ms.assetid: e59cf10d-47ce-401d-8474-3b69a3a5f5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf &#39;Option Compare&#39; muss &#39;Text&#39; oder &#39;Binary&#39; folgen.
Eine `Option Compare`\-Anweisung enthält eine falsche oder keine Einstellung. Die einzige Einstellungen, die in `Option Compare` zulässig ist, sind `Text` und `Binary`.  
  
 **Fehler\-ID:** BC30207  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob der Einstellungsspezifizierer falsch geschrieben wurde.  
  
2.  Fügen Sie entweder `Text` oder `Binary` zur `Option Compare`\-Anweisung hinzu, z. B. `Option Compare Text`.  
  
## Siehe auch  
 [Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement)