---
title: 'ASP.NET-Debugging: Systemanforderungen für | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 523764ae5cd787fd4b52650e894eb086ae4adb0c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097127"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET-Debugging: Systemanforderungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Software- und Sicherheitsanforderungen für die folgenden [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Debugszenarios beschrieben:  
  
- Lokales Debuggen, bei dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und die Webanwendung auf demselben Computer ausgeführt werden. Es gibt zwei Versionen dieses Szenarios:  
  
    - Der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Code befindet sich im Dateisystem.  
  
    - Der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Code befindet sich in einer IIS-Website.  
  
- Remotedebuggen: [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird auf einem Clientcomputer und die debuggte Webanwendung auf einem Remoteservercomputer ausgeführt.  
  
## <a name="security-requirements"></a>Sicherheitsanforderungen  
 Lokale Computer und Remotecomputer müssen sich beim Remotedebuggen in einer Domänen- oder Arbeitsgruppenkonfiguration befinden.  
  
 Zum Debuggen des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozesses müssen Sie hierfür über eine Berechtigung verfügen. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Anwendungen werden standardmäßig als **ASPNET** -Benutzer ausgeführt. Wenn der Arbeitsprozess als **ASPNET**oder als **NETZWERKDIENST**ausgeführt wird, benötigen Sie zum Debuggen Administratorrechte.  
  
 Der Name des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozesses ist je nach Debugszenario und IIS-Version unterschiedlich. Weitere Informationen finden Sie unter [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Sie können das Benutzerkonto, unter dem der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Arbeitsprozess ausgeführt wird, ändern, indem Sie die Datei „machine.config“ auf dem Server ändern, auf dem IIS ausgeführt wird. Dazu verwenden Sie am besten den **Internet Information Services (IIS) Manager**. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Wenn Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozess so ändern, dass er unter Ihrem eigenen Benutzerkonto ausgeführt wird, müssen Sie kein Administrator auf dem IIS-Servercomputer sein.  
  
> [!CAUTION]
>  Bevor Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozess dahingehend ändern, dass er unter einem anderen Konto ausgeführt wird, sollten Sie mögliche Konsequenzen für den Fall bedenken, dass der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozess beim Ausführen unter diesem Konto von Hackern angegriffen wird. Die ASPNET- und NETZWERKDIENST-Benutzerkonten werden mit minimalen Berechtigungen ausgeführt, was mögliche Schäden bei einem Hackerangriff auf den Prozess minimiert. Wenn Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Arbeitsprozess dahingehend ändern müssen, dass er unter einem Konto mit weiter reichenden Berechtigungen ausgeführt wird, kann der Schaden größer sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
