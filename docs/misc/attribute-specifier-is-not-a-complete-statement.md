---
title: "Der Attributspezifizierer ist keine vollst&#228;ndige Anweisung | Microsoft Docs"
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
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Attributspezifizierer ist keine vollst&#228;ndige Anweisung
Der Attributspezifizierer ist keine vollständige Anweisung. Verwenden Sie eine Zeilenfortsetzung, um das Attribut auf die folgende Anweisung anzuwenden.  
  
 Auf einer Quellcodezeile wird ein Attributblock allein angezeigt. Attribute müssen am Beginn einer Deklarationsanweisung angegeben werden, und sie müssen Teil dieser Anweisung sein.  
  
 **Fehler\-ID:** BC32035  
  
### So beheben Sie diesen Fehler  
  
-   Wenn sich die Deklarationsanweisung auf der nächsten Zeile befindet, fügen Sie ein Leerzeichen und einen Unterstrich \(`_`\) nach dem Attributblock hinzu, um die Quellcodezeilen zu verbinden.  
  
-   Wenn keine Deklarationsanweisung dem Attributblock zugeordnet ist, geben Sie diese an, oder entfernen Sie den Attributblock.  
  
-   Wenn das Attribut für die gesamte Assembly oder das aktuelle Assemblymodul gilt, bleibt der Attributblock auf einer separaten Quellcodezeile. Stellen Sie dem Attributnamen in den eckigen Klammern \(`< >`\) `Assembly:` oder `Module:` voran, und fügen Sie nach dem Attributblock kein Leerzeichen und keinen Unterstrich hinzu. Vergewissern Sie sich zudem, dass sich dieser Attributblock am Beginn der Quelldatei befindet.  
  
## Siehe auch  
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Gewusst wie: Umbrechen und Zusammenfassen von Anweisungen in Code](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)