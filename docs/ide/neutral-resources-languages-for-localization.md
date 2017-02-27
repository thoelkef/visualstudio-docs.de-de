---
title: "Neutrale Ressourcensprachen f&#252;r die Lokalisierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Kultur, Suchen von Ressourcen"
  - "Globalisierung [Visual Studio], Ressourcen"
  - "Lokalisierung [Visual Studio], Ressourcen"
  - "Neutrale Ressourcen"
  - "NeutralResourcesLanguageAttribute-Klasse"
  - "Ressourcen [Visual Studio], Fallbacksystem"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Neutrale Ressourcensprachen f&#252;r die Lokalisierung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:System.Resources.NeutralResourcesLanguageAttribute>\-Klasse gibt die Kultur der in der Hauptassembly enthaltenen Ressourcen an.  Dieses Attribut zielt auf eine Leistungssteigerung ab, denn die Suche nach in der Hauptassembly enthaltenen Ressourcen durch das <xref:System.Resources.ResourceManager>\-Objekt wird dadurch vermieden.  
  
 Der folgende Code zeigt das Festlegen der neutralen Ressourcensprache.  Der Code kann entweder in ein Buildscript, in die Datei **AssemblyInfo.vb** oder die Datei **AssemblyInfo.cs** eingefügt werden.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## Siehe auch  
 <xref:System.Resources.ResourceManager>   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)