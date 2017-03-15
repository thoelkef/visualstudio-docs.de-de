---
title: "Die Next-Steuervariable stimmt nicht mit der For-Schleifensteuerungsvariablen &#252;berein. | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Next-Steuervariable stimmt nicht mit der For-Schleifensteuerungsvariablen &#252;berein.
Die Steuervariable in der `Next`\-Anweisung einer `For...Next`\-Schleife muss mit der Variablen in der entsprechenden entsprechen `For`\-Anweisung übereinstimmen.  
  
 **Fehler\-ID:** BC30976  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Schreibweise der Variablen in der `Next`\-Anweisung und in der entsprechenden `For`\-Anweisung, um sicherzustellen, dass sie übereinstimmt.  
  
-   Vergewissern Sie sich, dass keine Teile der umschließenden Schleife versehentlich gelöscht wurden.  
  
-   Wenn diese Schleife Teil einer Reihe von geschachtelten Schleifen ist, müssen Sie sicherstellen, dass jede Schleife korrekt abgeschlossen ist.  
  
## Siehe auch  
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)