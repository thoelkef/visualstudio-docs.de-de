---
title: "&quot;Assembly&quot; oder &quot;Module&quot; erwartet | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Assembly&quot; oder &quot;Module&quot; erwartet
Es wurde ein globales Attribut angegeben, ohne dass festgelegt wurde, ob es für die gesamte Assembly oder nur für das aktuelle Modul gilt. Globale Attribute müssen entweder `Assembly` oder `Module` angeben.  
  
 Ein globales Attribut steht allein auf einer Quellzeile und wird nicht auf die Deklaration eines bestimmten Programmierelements angewendet.  
  
 **Fehler\-ID:** BC32015  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn das Attribut global sein soll, fügen Sie am Anfang des Attributblocks das `Assembly`\-Schlüsselwort oder das `Module`\-Schlüsselwort gefolgt von einem Doppelpunkt \(:\) ein.  
  
2.  Wenn das Attribut nicht global sein soll, löschen Sie den Attributblock, oder verschieben Sie ihn in eine Deklaration für ein Programmierelement.  
  
## Siehe auch  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [NICHT IM BUILD: Globale Attribute in Visual Basic](http://msdn.microsoft.com/de-de/253a32d8-1531-4504-b687-088554ab71d2)