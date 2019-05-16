---
title: Voraussetzungen für das Remotedebuggen von Webanwendungen | Microsoft-Dokumentation
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c13cfdeb90fae554479c7dc8a68261f40bc4cfc6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690114"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Voraussetzungen für das Remotedebuggen von Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger können Sie Webanwendungen auf dem lokalen Computer oder einem Remoteserver transparent debuggen. Das bedeutet, dass der Debugger auf jedem Computer auf die gleiche Weise funktioniert und Ihnen dieselben Features zur Verfügung stehen. Damit das Remotedebuggen richtig funktioniert, müssen jedoch einige vorbereitende Maßnahmen getroffen werden.  
  
- Die Komponenten zum Remotedebuggen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] müssen auf dem Server, auf dem das Debuggen durchgeführt werden soll, installiert sein. Weitere Informationen finden Sie unter [Einrichten des Remotedebuggens](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Standardmäßig wird der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess als ASPNET-Benutzerprozess ausgeführt. Daher müssen Sie zum Debuggen auf dem Computer, auf dem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ausgeführt wird, über Administratorrechte verfügen. Der Name des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozesses ist je nach Debugszenario und IIS-Version unterschiedlich. Weitere Informationen finden Sie unter [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)
