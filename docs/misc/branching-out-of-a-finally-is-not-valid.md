---
title: "Verzweigungen aus einem &quot;Finally&quot; sind ung&#252;ltig. | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Verzweigungen aus einem &quot;Finally&quot; sind ung&#252;ltig.
Eine `GoTo`\-Anweisung in einem `Finally`\-Block bewirkt einen Sprung aus dem Block. Es ist nicht zulässig, in einen oder aus einem `Catch`\- oder `Finally`\-Block zu springen.  
  
 **Fehler\-ID:** BC30101  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `GoTo`\-Anweisung, und implementieren Sie die Programmlogik mit Entscheidungs\- oder Schleifensteuerungsstrukturen.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Control Flow](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)