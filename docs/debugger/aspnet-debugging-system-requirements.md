---
title: "ASP.NET-Debugging: Systemanforderungen | Microsoft Docs"
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
  - "Debuggen von ASP.NET-Webanwendungen, Systemanforderungen"
  - "Debuggen von ASP.NET-Webanwendungen, Sicherheitsanforderungen"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ASP.NET-Debugging: Systemanforderungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden die Software\- und Sicherheitsanforderungen für die folgenden [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Debugszenarios beschrieben:  
  
-   Lokales Debuggen, bei dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die Webanwendung auf demselben Computer ausgeführt werden. Es gibt zwei Versionen dieses Szenarios:  
  
    -   Der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code befindet sich im Dateisystem.  
  
    -   Der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code befindet sich in einer IIS\-Website.  
  
-   Remotedebuggen: [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird auf einem Clientcomputer und die debuggte Webanwendung auf einem Remoteservercomputer ausgeführt.  
  
## Sicherheitsanforderungen  
 Lokale Computer und Remotecomputer müssen sich beim Remotedebuggen in einer Domänen\- oder Arbeitsgruppenkonfiguration befinden.  
  
 Zum Debuggen des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozesses müssen Sie hierfür über eine Berechtigung verfügen.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendungen werden standardmäßig als **ASPNET**\-Benutzer ausgeführt. Wenn der Arbeitsprozess als **ASPNET** oder als **NETZWERKDIENST** ausgeführt wird, benötigen Sie zum Debuggen Administratorrechte.  
  
 Der Name des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozesses ist je nach Debugszenario und IIS\-Version unterschiedlich. Weitere Informationen finden Sie unter [Gewusst wie: Herausfinden des ASP.NET\-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Sie können das Benutzerkonto, unter dem der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Arbeitsprozess ausgeführt wird, ändern, indem Sie die Datei „machine.config“ auf dem Server ändern, auf dem IIS ausgeführt wird. Dazu verwenden Sie am besten den **Internet Information Services \(IIS\) Manager**. Weitere Informationen finden Sie unter [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Wenn Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess so ändern, dass er unter Ihrem eigenen Benutzerkonto ausgeführt wird, müssen Sie kein Administrator auf dem IIS\-Servercomputer sein.  
  
> [!CAUTION]
>  Bevor Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess dahingehend ändern, dass er unter einem anderen Konto ausgeführt wird, sollten Sie mögliche Konsequenzen für den Fall bedenken, dass der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess beim Ausführen unter diesem Konto von Hackern angegriffen wird. Die ASPNET\- und NETZWERKDIENST\-Benutzerkonten werden mit minimalen Berechtigungen ausgeführt, was mögliche Schäden bei einem Hackerangriff auf den Prozess minimiert. Wenn Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess dahingehend ändern müssen, dass er unter einem Konto mit weiter reichenden Berechtigungen ausgeführt wird, kann der Schaden größer sein.  
  
## Siehe auch  
 [Debuggen von ASP.NET\- und AJAX\-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md)