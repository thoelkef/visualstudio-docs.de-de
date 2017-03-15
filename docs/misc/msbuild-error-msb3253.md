---
title: "MSBuild-Fehler MSB3253 | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB3253
**MSB3254: Die Assembly \<name\>, auf die im Projekt verwiesen wird, ist abhängig von \<name2\>. \<name2\> ist jedoch nicht im .NET Framework Client Profile enthalten.**  
  
 Eine der Assemblys oder abhängigen Assemblys, auf die im Projekt verwiesen wird, ist von einer anderen, nicht in [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] enthaltenen Assembly abhängig.  
  
 Diese Meldung wird in der Regel angezeigt, wenn ein Projekt auf Steuerelemente eines Drittanbieters oder auf eine DLL verweist, die ihrerseits auf eine externe Assembly verweist.  So verwendet ein Projekt beispielsweise ein Steuerelement, das selbst Funktionen verwendet, die im vollständigen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] enthalten sind.  Wenn die Anwendung neu auf [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ausgerichtet und auf einem System installiert wird, das nicht über [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)] verfügt, wird die Anwendung möglicherweise nicht ordnungsgemäß ausgeführt, wenn diese versucht, auf eine Funktion zuzugreifen, die in der [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]\-Teilmenge nicht enthalten ist.  
  
 Bei dieser "Fehler"\-Meldung handelt es sich lediglich um eine Warnung. Die Anwendung kompiliert trotzdem.  Es kann jedoch zu einem späteren Zeitpunkt ein Fehler auftreten, wenn das Steuerelement oder die DLL auf eine Funktion verweist, die sich in einer fehlenden Assembly befindet.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] ist eine Teilmenge der vollständigen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5\-Laufzeitbibliothek.  Weitere Informationen zum [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie entweder die angegebene Assembly aus dem Projekt, oder legen Sie als Ziel die gesamte [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anstelle der [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]\-Teilmengenbibliothek fest.  Weitere Informationen darüber, wie Sie die vollständige [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als Ziel angeben, finden Sie unter [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Siehe auch  
 [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)