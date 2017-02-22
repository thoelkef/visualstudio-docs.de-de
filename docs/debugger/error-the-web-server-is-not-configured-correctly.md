---
title: "Fehler: Der Webserver ist nicht richtig konfiguriert. | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.projnotconfigured"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Webserver ist nicht richtig konfiguriert.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Fehler kann folgende Ursachen haben:  
  
-   Es wurde versucht, eine .NET\-Webanwendung zu debuggen, die auf einen anderen Computer kopiert, manuell umbenannt oder verschoben wurde.  
  
-   Es sind nicht genügend IIS\-Verbindungen vorhanden. Weitere Informationen zum Bereitstellen einer Website für IIS finden Sie unter [Erstellen einer Website](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Wenn Sie eine ASP.NET\-Anwendung debuggen, finden Sie unter [Veröffentlichen unter IIS](https://docs.asp.net/en/latest/publishing/iis.html) bzw. [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) weitere Informationen darüber, wie Sie bei der Bereitstellung auf einem Remotecomputer unter IIS 8 oder höher bzw. IIS 7.5 vorgehen.  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)