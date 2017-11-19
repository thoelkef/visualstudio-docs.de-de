---
title: 'ASP.NET-Debuggen: Systemanforderungen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30ac9c68104423c559ad3bfa8712426b67a4c734
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET-Debugging: Systemanforderungen
In diesem Thema werden die Software- und Sicherheitsanforderungen für die folgenden [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Debugszenarios beschrieben:  
  
-   Lokales Debuggen, bei dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die Webanwendung auf demselben Computer ausgeführt werden. Es gibt zwei Versionen dieses Szenarios:  
  
    -   Der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Code befindet sich im Dateisystem.  
  
    -   Der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Code befindet sich in einer IIS-Website.  
  
-   Remotedebuggen: [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird auf einem Clientcomputer und die debuggte Webanwendung auf einem Remoteservercomputer ausgeführt.  
  
## <a name="security-requirements"></a>Sicherheitsanforderungen  
 Lokale Computer und Remotecomputer müssen sich beim Remotedebuggen in einer Domänen- oder Arbeitsgruppenkonfiguration befinden.  
  
 So debuggen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Arbeitsprozess (nach einem Anwendungspool gehostet), Sie benötigen die Berechtigung zum Debuggen dieses Prozesses. Standardmäßig [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendungen vor IIS 6.0 ausgeführt wird, als die **ASPNET** Benutzer. In IIS 6.0 und IIS 7.0 die **Netzwerkdienst** Konto ist die Standardeinstellung. Wenn der Arbeitsprozess als **ASPNET**oder als **NETZWERKDIENST**ausgeführt wird, benötigen Sie zum Debuggen Administratorrechte.

 > [!IMPORTANT]
 > Ab Windows Server 2008 R2, wir empfehlen die Verwendung von der [ApplicationPoolIdentity](https://docs.microsoft.com/en-us/iis/manage/configuring-security/application-pool-identities) als Identität für jeden Anwendungspool.
  
 Der Name des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Arbeitsprozesses ist je nach Debugszenario und IIS-Version unterschiedlich. Weitere Informationen finden Sie unter [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Sie können das Benutzerkonto, unter dem der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Arbeitsprozess ausgeführt wird, ändern, indem Sie die Datei „machine.config“ auf dem Server ändern, auf dem IIS ausgeführt wird. Dazu verwenden Sie am besten den **Internet Information Services (IIS) Manager**. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen der Worker-Prozess unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Wenn Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Arbeitsprozess so ändern, dass er unter Ihrem eigenen Benutzerkonto ausgeführt wird, müssen Sie kein Administrator auf dem IIS-Servercomputer sein.  
  
> [!CAUTION]
>  Bevor Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Arbeitsprozess dahingehend ändern, dass er unter einem anderen Konto ausgeführt wird, sollten Sie mögliche Konsequenzen für den Fall bedenken, dass der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Arbeitsprozess beim Ausführen unter diesem Konto von Hackern angegriffen wird. Die ASPNET- und NETZWERKDIENST-Benutzerkonten werden mit minimalen Berechtigungen ausgeführt, was mögliche Schäden bei einem Hackerangriff auf den Prozess minimiert. Wenn Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Arbeitsprozess dahingehend ändern müssen, dass er unter einem Konto mit weiter reichenden Berechtigungen ausgeführt wird, kann der Schaden größer sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md)