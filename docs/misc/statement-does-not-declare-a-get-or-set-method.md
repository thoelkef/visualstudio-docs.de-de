---
title: "Die Anweisung deklariert keine Get- oder Set-Methode. | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Anweisung deklariert keine Get- oder Set-Methode.
Die Anweisung gibt keine `Get`\- oder `Set`\-Deklarationsanweisung in Verbindung mit einer `Property`\-Prozedur an. Eine Eigenschaft wird als Codeblock definiert, der von den Anweisungen `Property` und `End Property` eingefasst wird. Innerhalb dieses Blocks erscheint jede `Property`\-Prozedur als interner Block, der von einer Deklarationsanweisung und einer End\-Anweisung eingefasst wird.  
  
 **Fehler\-ID:** BC30576  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie eine `Get`\- oder `Set`\-Deklarationsanweisung an.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)