---
title: "Declare-Anweisungen in einem Modul d&#252;rfen nicht als &quot;&lt;Spezifizierer&gt;&quot; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30786"
  - "bc30786"
helpviewer_keywords: 
  - "BC30786"
ms.assetid: 488b855f-72ea-414b-bffc-a5b63e97d289
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declare-Anweisungen in einem Modul d&#252;rfen nicht als &quot;&lt;Spezifizierer&gt;&quot; deklariert werden.
Eine `Declare`\-Deklaration enthält einen Spezifizierer, der in einer `Module`\-Deklaration ungültig ist. Module können nie instanziiert werden, unterstützen keine Vererbung und können keine Schnittstellen implementieren.  
  
 **Fehler\-ID:** BC30786  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Spezifizierer.  
  
## Siehe auch  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)