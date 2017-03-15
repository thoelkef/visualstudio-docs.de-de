---
title: "Es ist ein Verweis auf die Assembly &quot;&lt;Assemblyname&gt;&quot; erforderlich, die die Definition f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; enth&#228;lt. | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es ist ein Verweis auf die Assembly &quot;&lt;Assemblyname&gt;&quot; erforderlich, die die Definition f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; enth&#228;lt.
Es ist ein Verweis auf die Assembly "\<`assemblyname`\>" erforderlich, die die Definition für das Ereignis "\<`eventname`\>" enthält. Fügen Sie Ihrem Projekt einen Verweis hinzu.  
  
 Das Ereignis ist in einer Dynamic Link Library \(DLL\) definiert, auf die in Ihrem Projekt nicht direkt verwiesen wird. Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler benötigt einen Verweis, um Mehrdeutigkeiten zu vermeiden, falls das Ereignis in mehreren DLLs oder Assemblys definiert ist.  
  
 **Fehler\-ID:** BC30005  
  
### So beheben Sie diesen Fehler  
  
-   Nehmen Sie den Namen der nicht referenzierten DLL oder Assembly in Ihre Projektverweise auf.  
  
## Siehe auch  
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)