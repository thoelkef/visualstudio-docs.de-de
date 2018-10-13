---
title: 'Fehler: Der Webserver ist nicht ordnungsgemäß konfiguriert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec803ea53dfa86c713b2287eb863efabc2351918
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171210"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler kann folgende Ursachen haben:  
  
-   Es wurde versucht, eine .NET-Webanwendung zu debuggen, die auf einen anderen Computer kopiert, manuell umbenannt oder verschoben wurde.  
  
-   Es sind nicht genügend IIS-Verbindungen vorhanden. Weitere Informationen zum Bereitstellen einer Website für IIS finden Sie unter [Erstellen einer Website](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Wenn Sie eine ASP.NET-Anwendung debuggen, finden Sie unter [Veröffentlichen unter IIS](https://docs.asp.net/en/latest/publishing/iis.html) bzw. [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) weitere Informationen darüber, wie Sie bei der Bereitstellung auf einem Remotecomputer unter IIS 8 oder höher bzw. IIS 7.5 vorgehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



