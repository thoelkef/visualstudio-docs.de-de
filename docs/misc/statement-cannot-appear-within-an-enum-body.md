---
title: "Eine Anweisung kann nicht innerhalb eines Enumerationstexts angezeigt werden. | Microsoft Docs"
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
  - "vbc30619"
  - "bc30619"
helpviewer_keywords: 
  - "BC30619"
ms.assetid: 5d91d601-2a2d-418c-ae26-791d14a6f3cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Anweisung kann nicht innerhalb eines Enumerationstexts angezeigt werden.
Eine Anweisung kann nicht innerhalb eines Enumerationstexts auftreten. Das Ende der Enumeration wird angenommen.  
  
 Es wurde ein unerwartetes Sprachkonstrukt gefunden. Es wird angenommen, dass ein `End Enum`\-Konstrukt fehlt und sich jeglicher Quellcode nach diesem Punkt außerhalb der Enumeration befindet.  
  
 **Fehler\-ID:** BC30619  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Syntax des innerhalb der Enumeration verwendeten Codes.  
  
2.  Stellen Sie sicher, dass die Schnittstellendefinition mit einem `End Enum`\-Konstrukt endet.  
  
## Siehe auch  
 [Enum Statement](/dotnet/visual-basic/language-reference/statements/enum-statement)