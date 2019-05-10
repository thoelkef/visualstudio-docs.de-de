---
title: 'Fehler: Die Webserver nicht ordnungsgemäß konfiguriert ist | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 643be465aab889b1f31e8fa75dba68261444bc31
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061007"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler kann folgende Ursachen haben:  
  
- Es wurde versucht, eine .NET-Webanwendung zu debuggen, die auf einen anderen Computer kopiert, manuell umbenannt oder verschoben wurde.  
  
- Es sind nicht genügend IIS-Verbindungen vorhanden. Weitere Informationen zum Bereitstellen einer Website für IIS finden Sie unter [Erstellen einer Website](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
- Wenn Sie eine ASP.NET-Anwendung debuggen, finden Sie unter [Veröffentlichen unter IIS](https://docs.asp.net/en/latest/publishing/iis.html) bzw. [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) weitere Informationen darüber, wie Sie bei der Bereitstellung auf einem Remotecomputer unter IIS 8 oder höher bzw. IIS 7.5 vorgehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
