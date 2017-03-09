---
title: "Ung&#252;ltige Musterzeichenfolge | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ung&#252;ltige Musterzeichenfolge
Die angegebene Musterzeichenfolge in der `Like`\-Operation einer Suche ist ungültig.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die zulässigen Zeichen für Listenausdrücke.  
  
2.  Stellen Sie im Musterbereich sicher, dass das Zeichen für den Startbereich kleiner als das Zeichen für den Endbereich ist, wie in `[a-z]`.  
  
3.  Stellen Sie im Musterbereich sicher, dass nicht mehrere Bindestriche nebeneinander verwendet werden, wie in `[a--z]`.  
  
4.  Beenden Sie die Musterbereiche mit einer schließenden eckigen Klammer.  
  
## Siehe auch  
 [Like Operator](/dotnet/visual-basic/language-reference/operators/like-operator)