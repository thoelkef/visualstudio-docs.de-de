---
title: "Es ist ein Verweis auf das Modul &quot;&lt;Modulname&gt;&quot; erforderlich, das die Definition f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; enth&#228;lt.  | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es ist ein Verweis auf das Modul &quot;&lt;Modulname&gt;&quot; erforderlich, das die Definition f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; enth&#228;lt. 
Es ist ein Verweis auf das Modul "\<`modulename`\>" erforderlich, das die Definition für das Ereignis "\<`eventname`\>" enthält. Fügen Sie dem Projekt einen Verweis hinzu.  
  
 Das Ereignis ist in einem Modul definiert, auf das Ihr Projekt nicht direkt verweist. Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler benötigt einen Verweis, um Mehrdeutigkeiten zu vermeiden, falls das Ereignis in mehr als einem Modul definiert ist.  
  
 **Fehler\-ID:** BC30006  
  
### So beheben Sie diesen Fehler  
  
-   Nehmen Sie den Namen des nicht referenzierten Moduls in Ihre Projektverweise auf.  
  
## Siehe auch  
 [NICHT IM BUILD: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)