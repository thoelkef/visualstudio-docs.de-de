---
title: "Der f&#252;r die Case-Anweisung angegebene Bereich ist ung&#252;ltig. | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der f&#252;r die Case-Anweisung angegebene Bereich ist ung&#252;ltig.
Für eine `Case`\-Anweisung wurde ein ungültiger Bereich angegeben.  
  
 Wenn Sie den gleichen Ausdruck mit mehreren unterschiedlichen Werten vergleichen, können Sie die `Select...Case`\-Anweisungen als Alternative zu den `If...Then...Else`\-Anweisungen verwenden. Während die Anweisungen `If` und `ElseIf` in jeder Anweisung einen anderen Ausdruck auswerten können, wertet die `Select`\-Anweisung einen einzelnen Ausdruck nur einmal aus und verwendet ihn dann für jeden Vergleich. Jede `Case`\-Anweisung kann mehrere Werte, einen Wertebereich oder eine Kombination von Werten und Vergleichsoperatoren enthalten.  
  
 **Fehler\-ID:** BC40052  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Bereich, sodass er alle Werte enthält, oder verwenden Sie eine `Case Else`\-Anweisung, um einen nicht definierten Wert abzufangen.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Decision Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)