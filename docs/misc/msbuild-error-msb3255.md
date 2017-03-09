---
title: "MSBuild-Fehler MSB3255 | Microsoft Docs"
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
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB3255
**MSB3255: Es wurden keine Dateien der Zielframeworkuntermenge in den Zielframeworkverzeichnissen oder an den in InstalledAssemblySubsetTables angegebenen Speicherorten gefunden.**  
  
 Dieser Fehler tritt auf, wenn ein Name an die <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A>\-Eigenschaft übergeben wird, jedoch keine Teilmenge mit diesem Namen gefunden werden kann.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ist eine Teilmenge der vollständigen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5\-Laufzeitbibliothek.  Weitere Informationen zum [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Arbeitsschritte  
  
### So beheben Sie diesen Fehler  
  
-   Platzieren Sie eine Kopie der Teilmengendatei in den Zielframeworkordner oder in eines der Verzeichnisse, die in <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A> angegeben sind.  
  
## Siehe auch  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)