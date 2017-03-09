---
title: "F&#252;r das Ereignisprotokoll wurde ein ung&#252;ltiger Name angegeben. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r das Ereignisprotokoll wurde ein ung&#252;ltiger Name angegeben.
Für das Ereignisprotokoll wurde ein ungültiger Name angegeben. Dies liegt in der Regel an ungültigen Zeichen im Namen, an einem leeren Dateinamen oder an einem zu langen Dateinamen.  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der angegebene Name mehr als acht Zeichen lang ist, stellen Sie sicher, dass kein Konflikt mit den Namen anderer Ereignisprotokolle auftritt. Bei der Ermittlung, ob der Name eindeutig ist, werden nur die ersten acht Zeichen ausgewertet.  
  
-   Stellen Sie beim Angeben eines Pfads sicher, dass er ordnungsgemäß analysiert wird.  
  
-   Vergewissern Sie sich, dass sich keine ungültigen Zeichen im Namen befinden. Zu den Zeichen, die nicht in einem Dateinamen verwendet werden dürfen, zählen die Folgenden: `<`, `>`, `:`, `"`, `/`, `\` und `|`.  
  
## Siehe auch  
 [Gewusst wie: Analysieren von Dateipfaden](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)   
 [How to: Rename a File](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/de-de/af9b7da0-80c7-46ac-b7f7-897063ddd503)