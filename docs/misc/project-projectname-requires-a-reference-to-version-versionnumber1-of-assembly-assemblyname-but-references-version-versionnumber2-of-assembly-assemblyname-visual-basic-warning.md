---
title: "Projekt &#39;&lt;Projektname&gt;&#39; erfordert einen Verweis auf die Version &#39;&lt;Versionsnummer1&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39;, aber verweist auf die Version &#39;&lt;Versionsnummer2&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39; (Visual Basic-Warnung) | Microsoft Docs"
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
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Projekt &#39;&lt;Projektname&gt;&#39; erfordert einen Verweis auf die Version &#39;&lt;Versionsnummer1&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39;, aber verweist auf die Version &#39;&lt;Versionsnummer2&gt;&#39; von Assembly &#39;&lt;Assemblyname&gt;&#39; (Visual Basic-Warnung)
Projekt '\<Projektname\>' erfordert einen Verweis auf die Version '\<Versionsnummer1\>' von Assembly '\<Assemblyname\>', aber verweist auf die Version '\<Versionsnummer2\>' von Assembly '\<Assemblyname\>'. Der Verweis auf die Version '\<Versionsnummer1\>' wurde ausgegeben.  
  
 Ein Projekt erstellt einen indirekten Verweis auf eine Assembly, die an anderer Stelle definiert ist, aber das Projekt verfügt auch über einen direkten Verweis auf eine frühere Version der Assembly.  
  
 Der Compiler verwendet den indirekten Verweis auf die neuere Version beim Auflösen von Zugriffen, um den Zugriff auf Typen und Programmierelemente zu unterstützen, die in der neueren, jedoch nicht in der früheren Version definiert sind.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42203  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den direkten Verweis auf die frühere Version der Assembly, oder ändern Sie den Verweis, damit er auf die neuere Version verweist.  
  
## Siehe auch  
 [Assemblys in der Common Language Runtime \(CLR\)](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Verwalten von Verweisen](http://msdn.microsoft.com/de-de/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)