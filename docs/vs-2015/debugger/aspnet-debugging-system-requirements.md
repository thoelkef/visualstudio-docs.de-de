---
title: 'ASP.NET-Debuggen: Systemanforderungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5386390261028fd635f93bc06d3a3fc8805ebdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509618"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET-Debugging: Systemanforderungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ASP.NET-Debuggen: Systemanforderungen](https://docs.microsoft.com/visualstudio/debugger/aspnet-debugging-system-requirements).  
  
In diesem Thema wird beschrieben, die Software- und sicherheitsanforderungen Anforderungen für [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Debugszenarios beschrieben:  
  
-   Lokales Debuggen, bei dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und die Webanwendung auf demselben Computer ausgeführt werden. Es gibt zwei Versionen dieses Szenarios:  
  
    -   Der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Code befindet sich im Dateisystem.  
  
    -   Der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Code befindet sich in einer IIS-Website.  
  
-   Remotedebuggen: [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird auf einem Clientcomputer und die debuggte Webanwendung auf einem Remoteservercomputer ausgeführt.  
  
## <a name="security-requirements"></a>Sicherheitsanforderungen  
 Lokale Computer und Remotecomputer müssen sich beim Remotedebuggen in einer Domänen- oder Arbeitsgruppenkonfiguration befinden.  
  
 Zum Debuggen des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozesses müssen Sie hierfür über eine Berechtigung verfügen. In der Standardeinstellung [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Anwendungen ausgeführt werden, als die **ASPNET** Benutzer. Wenn der Arbeitsprozess als **ASPNET**oder als **NETZWERKDIENST**ausgeführt wird, benötigen Sie zum Debuggen Administratorrechte.  
  
 Der Name des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozesses ist je nach Debugszenario und IIS-Version unterschiedlich. Weitere Informationen finden Sie unter [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Sie können das Benutzerkonto, unter dem der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Arbeitsprozess ausgeführt wird, ändern, indem Sie die Datei „machine.config“ auf dem Server ändern, auf dem IIS ausgeführt wird. Dazu verwenden Sie am besten den **Internet Information Services (IIS) Manager**. Weitere Informationen finden Sie unter [wie: Ausführen der Worker-Prozess unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Wenn Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess so ändern, dass er unter Ihrem eigenen Benutzerkonto ausgeführt wird, müssen Sie kein Administrator auf dem IIS-Servercomputer sein.  
  
> [!CAUTION]
>  Bevor Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess dahingehend ändern, dass er unter einem anderen Konto ausgeführt wird, sollten Sie mögliche Konsequenzen für den Fall bedenken, dass der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess beim Ausführen unter diesem Konto von Hackern angegriffen wird. Die ASPNET- und NETZWERKDIENST-Benutzerkonten werden mit minimalen Berechtigungen ausgeführt, was mögliche Schäden bei einem Hackerangriff auf den Prozess minimiert. Wenn Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess dahingehend ändern müssen, dass er unter einem Konto mit weiter reichenden Berechtigungen ausgeführt wird, kann der Schaden größer sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md)



