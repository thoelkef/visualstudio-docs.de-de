---
title: "MSBuild Error MSB3256 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3256"
ms.assetid: 809ccd0a-78cd-4bf5-83a8-2fb51815ea27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3256
**MSB3256: Aus den redist\-Listen wurden keine Assemblys gelesen.  Es konnte keine Ausschlussliste für die TargetFramework\-Teilmenge generiert werden.**  
  
 Es wurde keine Liste verteilbarer Elemente \(REDIST\-Liste\) gefunden.  
  
 Zum Generieren einer Liste der Assemblys, die aus der .NET Framework\-Teilmenge auszuschließen sind, werden zwei Dateien benötigt: eine "REDIST\-Liste" mit dem Namen "FrameworkList.xml", die die Namen der verteilbaren Elemente in .NET Framework enthält, und eine "Teilmengenliste" mit dem Namen "client.xml", die die Namen der Elemente in .NET Framework enthält.  Da die Teilmengendefinition beide Listen erfordert, kann die .NET Framework\-Teilmenge nicht aufgerufen werden, wenn die REDIST\-Liste fehlt.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ist eine Teilmenge der vollständigen [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)]\-Laufzeitbibliothek.  Weitere Informationen zum [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie entweder eine gültige REDIST\-Liste mit dem Namen \<legacyBold\>FrameworkList.xml\<\/legacyBold\> zur Verfügung, oder geben Sie die vollständige verteilbare [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)]\-Bibliothek als Ziel an.  Weitere Informationen darüber, wie Sie die vollständige [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als Ziel angeben, finden Sie unter [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Siehe auch  
 [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)