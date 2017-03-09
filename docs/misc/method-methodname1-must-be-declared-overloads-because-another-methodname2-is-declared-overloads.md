---
title: "&lt;Methode&gt; &#39;&lt;Methodenname1&gt;&#39; muss als &#39;Overloads&#39; deklariert werden, da &#39;&lt;Methodenname2&gt;&#39; an anderer Stelle als &#39;Overloads&#39; deklariert wurde. | Microsoft Docs"
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
  - "vbc31409"
  - "bc31409"
helpviewer_keywords: 
  - "BC31409"
ms.assetid: 27813b4e-056d-45af-969e-76e8c1ee6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Methode&gt; &#39;&lt;Methodenname1&gt;&#39; muss als &#39;Overloads&#39; deklariert werden, da &#39;&lt;Methodenname2&gt;&#39; an anderer Stelle als &#39;Overloads&#39; deklariert wurde.
Eine andere Eigenschaft oder Methode mit demselben Namen wurde mit dem `Overloads`\-Modifizierer deklariert.  
  
 **Fehler\-ID:** BC31409  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie den `Overloads`\-Modifizierer zur Eigenschaft oder Methode hinzu.  
  
2.  Entfernen Sie den `Overloads`\-Modifizierer aus allen Eigenschaften oder Methoden mit demselben Namen.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)