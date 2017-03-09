---
title: "Voraussetzungen f&#252;r das Remotedebuggen von Webanwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen von ASP.NET-Webanwendungen, Remoteserver"
  - "Remotedebuggen, Voraussetzungen"
  - "Remoteserver, Debuggen von Webanwendungen"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Voraussetzungen f&#252;r das Remotedebuggen von Webanwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debugger können Sie Webanwendungen auf dem lokalen Computer oder einem Remoteserver transparent debuggen.  Das bedeutet, dass der Debugger auf jedem Computer auf die gleiche Weise funktioniert und Ihnen dieselben Features zur Verfügung stehen.  Damit das Remotedebuggen richtig funktioniert, müssen jedoch einige vorbereitende Maßnahmen getroffen werden.  
  
-   Die Komponenten zum Remotedebuggen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] müssen auf dem Server, auf dem das Debuggen durchgeführt werden soll, installiert sein.  Weitere Informationen finden Sie unter [Einrichten des Remotedebuggens](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   Standardmäßig wird der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess als ASPNET\-Benutzerprozess ausgeführt.  Daher müssen Sie zum Debuggen auf dem Computer, auf dem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ausgeführt wird, über Administratorrechte verfügen.  Der Name des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozesses ist je nach Debugszenario und IIS\-Version unterschiedlich.  Weitere Informationen finden Sie unter [Gewusst wie: Herausfinden des ASP.NET\-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## Siehe auch  
 [Debuggen von ASP.NET\- und AJAX\-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)