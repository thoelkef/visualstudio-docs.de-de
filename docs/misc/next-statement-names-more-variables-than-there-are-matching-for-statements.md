---
title: "Die Next-Anweisung benennt mehr Variablen, als entsprechende For-Anweisungen vorhanden sind. | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Next-Anweisung benennt mehr Variablen, als entsprechende For-Anweisungen vorhanden sind.
Geschachtelte Schleifen enden mit einer einzelnen `Next`\-Anweisung, die mehr Schleifenvariablen angibt, als sich Schleifen in der Schachtelung befinden, wie im folgenden Beispiel gezeigt:  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **Fehler\-ID:** BC32037  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass die `Next`\-Anweisung alle geschachtelten Schleifenvariablen in der umgekehrten Reihenfolge der Schleifeninitiierung angibt.  
  
2.  Entfernen Sie alle überflüssigen Variablen aus der `Next`\-Anweisung.  
  
## Siehe auch  
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)