---
title: "Die Anweisung kann nicht innerhalb des Schnittstellentexts verwendet werden (Visual Basic-Fehler). | Microsoft Docs"
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
  - "bc30604"
  - "vbc30604"
helpviewer_keywords: 
  - "BC30604"
ms.assetid: ce4759fe-5e49-43ad-8405-a3f46ed0a36f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Anweisung kann nicht innerhalb des Schnittstellentexts verwendet werden (Visual Basic-Fehler).
Es wurde ein unerwartetes Sprachkonstrukt gefunden. Es wird angenommen, dass ein `End Interface`\-Konstrukt fehlt und sich jeglicher Quellcode nach diesem Punkt außerhalb der Schnittstelle befindet.  
  
 **Fehler\-ID:** BC30604  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Syntax des innerhalb der Schnittstellendefinition verwendeten Codes.  
  
2.  Stellen Sie sicher, dass die Schnittstellendefinition mit einem `End Interface`\-Konstrukt endet.  
  
## Siehe auch  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)