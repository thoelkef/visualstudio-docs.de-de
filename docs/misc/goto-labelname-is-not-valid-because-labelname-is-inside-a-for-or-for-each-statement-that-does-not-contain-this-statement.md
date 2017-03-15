---
title: "&#39;GoTo &lt;Bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;Bezeichnungsname&gt;&#39; innerhalb einer &#39;For&#39;- oder &#39;For Each&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt. | Microsoft Docs"
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
  - "vbc30757"
  - "bc30757"
helpviewer_keywords: 
  - "BC30757"
ms.assetid: be28bec5-1bc4-4da1-ba0c-4e3faac81077
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;Bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;Bezeichnungsname&gt;&#39; innerhalb einer &#39;For&#39;- oder &#39;For Each&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt.
`GoTo`\-Anweisungen sind auf Sprünge innerhalb des aktuellen Codeblocks beschränkt.  
  
 **Fehler\-ID:** BC30757  
  
### So beheben Sie diesen Fehler  
  
-   Strukturieren Sie den Code um, sodass sich die `GoTo`\-Anweisung und die Bezeichnung innerhalb des `For`\-Blocks befinden.  
  
## Siehe auch  
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [For \(Visual Basic\)](http://msdn.microsoft.com/de-de/c470a263-9b49-4308-8fd6-8592b84a7980)