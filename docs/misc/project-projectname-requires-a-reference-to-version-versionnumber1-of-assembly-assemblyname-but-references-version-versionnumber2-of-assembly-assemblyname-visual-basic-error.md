---
title: "Projekt &#39;&lt;Projektname&gt;&#39; erfordert einen Verweis auf die Version &#39;&lt;Versionsnummer1&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39;, aber verweist auf die Version &#39;&lt;Versionsnummer2&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39; (Visual Basic-Fehler) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32209"
  - "bc32209"
helpviewer_keywords: 
  - "BC32209"
ms.assetid: fe50736b-444f-4e40-8f80-9760ff13a153
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Projekt &#39;&lt;Projektname&gt;&#39; erfordert einen Verweis auf die Version &#39;&lt;Versionsnummer1&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39;, aber verweist auf die Version &#39;&lt;Versionsnummer2&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39; (Visual Basic-Fehler)
Ein Projekt erstellt einen indirekten Verweis auf eine Assembly, die an anderer Stelle definiert ist, aber das Projekt verfügt auch über einen direkten Verweis auf eine spätere Version der Assembly.  
  
 Wenn der Compiler dem Code die Verwendung des indirekten Verweises gestattet hat, können Sie möglicherweise nicht auf Typen und Programmierelemente zugreifen, die in der späteren Version, jedoch nicht in der früheren Version definiert sind.  
  
 **Fehler\-ID:** BC32209  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den indirekten Verweis auf die frühere Version der Assembly, und verwenden Sie den direkten Verweis für die spätere Version.  
  
## Siehe auch  
 [Assemblys in der Common Language Runtime \(CLR\)](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Verwalten von Verweisen](http://msdn.microsoft.com/de-de/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)