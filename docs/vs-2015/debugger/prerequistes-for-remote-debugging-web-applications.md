---
title: Voraussetzungen für das Remotedebuggen von Webanwendungen | Microsoft-Dokumentation
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514207"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Voraussetzungen für das Remotedebuggen von Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Voraussetzungen für das Debuggen von ASP.NET-Webanwendungen](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
Mit dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger können Sie Webanwendungen auf dem lokalen Computer oder einem Remoteserver transparent debuggen. Das bedeutet, dass der Debugger auf jedem Computer auf die gleiche Weise funktioniert und Ihnen dieselben Features zur Verfügung stehen. Damit das Remotedebuggen richtig funktioniert, müssen jedoch einige vorbereitende Maßnahmen getroffen werden.  
  
-   Die Komponenten zum Remotedebuggen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] müssen auf dem Server, auf dem das Debuggen durchgeführt werden soll, installiert sein. Weitere Informationen finden Sie unter [Einrichten des Remotedebuggens](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Standardmäßig wird der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess als ASPNET-Benutzerprozess ausgeführt. Daher müssen Sie zum Debuggen auf dem Computer, auf dem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ausgeführt wird, über Administratorrechte verfügen. Der Name des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozesses ist je nach Debugszenario und IIS-Version unterschiedlich. Weitere Informationen finden Sie unter [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)



