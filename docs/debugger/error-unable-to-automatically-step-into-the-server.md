---
title: "Fehler: Automatischer Einzelschritt auf dem Server nicht m&#246;glich | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Remotedebugging, Benachrichtigungsfehler"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Automatischer Einzelschritt auf dem Server nicht m&#246;glich
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Fehler lautet:  
  
 Automatischer Einzelschritt auf dem Server nicht möglich. Der Debugger wurde vor der Ausführung der Remoteprozedur nicht benachrichtigt.  
  
 Dieser Fehler wird angezeigt, wenn Sie versuchen, einen Webdienst in Einzelschritten auszuführen \(siehe [Schrittweises Ausführen eines XML\-Webdiensts](http://msdn.microsoft.com/de-de/8e67de38-bf5f-41cc-a457-1b88ce63d764)\). Er kann auftreten, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht ordnungsgemäß eingerichtet ist.  
  
 Mögliche Ursachen sind:  
  
-   In der Datei web.config der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung ist debug nicht auf "true" festgelegt \(siehe [Debugmodus in ASP.NET\-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Eine Version von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] wurde nach der Installation von Visual Studio installiert.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] muss vor Visual Studio installiert werden. Verwenden Sie zum Beheben dieses Problem in der Windows\-**Systemsteuerung** die Option **Programme und Funktionen**, um die Visual Studio\-Installation zu reparieren.  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)