---
title: "MSBuild-Fehler MSB3252 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB3252
**MSB3252: Das Projekt enthält einen Verweis auf Assembly \<name\>.  Diese Assembly ist kein Teil von .NET Framework Client Profile.  Durch diesen fehlerhaften Verweis können Kompilierungs\- oder Laufzeitfehler auftreten.**  
  
 Es wurde ein Member in einer Assembly oder einer abhängigen Assembly aufgerufen, die kein Teil von [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ist.  Deshalb kann der Aufruf nicht aufgelöst und die Anwendung nicht kompiliert werden.  
  
 Weitere Informationen zum [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie entweder die angegebene Assembly aus dem Projekt, oder legen Sie die gesamte [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anstelle der [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]\-Teilmengenbibliothek als Ziel fest.  Weitere Informationen darüber, wie Sie die vollständige [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als Ziel angeben, finden Sie unter [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Siehe auch  
 [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)