---
title: "Delegaten k&#246;nnen keine Ereignisse verarbeiten. | Microsoft Docs"
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
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegaten k&#246;nnen keine Ereignisse verarbeiten.
Ein Delegat ist ein Verweistyp, der auf eine freigegebene Prozedur oder auf eine Instanzenprozedur eines Objekts verweist. Da die Prozedur, auf die der Delegat verweist, durch eine Zuweisung geändert werden kann, kann die `Delegate`\-Anweisung keine `Handles`\- oder `Implements`\-Klauseln unterstützen.  
  
 **Fehler\-ID:** BC30019  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Handles`\-Klausel aus der `Delegate`\-Anweisung.  
  
## Siehe auch  
 [NICHT IM BUILD: Delegaten und der AddressOf\-Operator](http://msdn.microsoft.com/de-de/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)