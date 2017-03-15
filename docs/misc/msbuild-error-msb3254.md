---
title: "MSBuild-Fehler MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB3254
**MSB3254: Die Datei \<name \> kann nicht gelesen werden und wird ignoriert.  Diese Datei wurde entweder an InstalledAssemblySubsetTables übergeben oder wurde durch Suchen im Ordner \<name\> unter TargetFrameworkDirectories gefunden.**  
  
 Dieser Fehler tritt auf, wenn die [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]\-XML\-Datei \(client.xml\) nicht gelesen werden kann.  Die Datei kann wegen Beschädigung, einer Sperre oder eines anderen Problems nicht gelesen werden.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ist eine Teilmenge der vollständigen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5\-Laufzeitbibliothek.  Weitere Informationen zum [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Arbeitsschritte  
  
### So beheben Sie diesen Fehler  
  
-   Vergewissern Sie sich, dass Sie über vollständige Berechtigungen und uneingeschränkten Zugriff auf die Datei verfügen, oder installieren Sie die verteilbare [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]\-Laufzeitbibliothek neu, um die beschädigte Datei zu ersetzen.  
  
## Siehe auch  
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)