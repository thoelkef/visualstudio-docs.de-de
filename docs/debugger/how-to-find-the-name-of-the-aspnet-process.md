---
title: Suchen Sie den ausgeführten Prozess für ASP.NET | Microsoft-Dokumentation
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 4a65269f9fd99b31ee797be0d5e27559daa1f25a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836165"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Herausfinden des ASP.NET-Prozessnamens

So debuggen Sie eine laufende [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -app, an dem Visual Studio-Debugger Anfügen muss die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] verarbeiten anhand des Namens.

**Um herauszufinden, welcher Prozess eine ASP.NET-Anwendung ausgeführt wird:**

1. Wählen Sie die app ausgeführt wird, in Visual Studio **Debuggen** > **an den Prozess anhängen**. 
   
1. In der **an den Prozess anhängen** Dialogfelds die erste Buchstaben des Prozesses in der folgenden Liste nennt, oder geben Sie sie in das Suchfeld. Diejenige, die ausgeführt wird wird die ASP.NET-App ausgeführt wird. Fügen Sie für den jeweiligen Prozess Debuggen die app. 
   
    - *w3wp.exe* wird von IIS 6.0 und höher. 
    - *aspnet_wp.exe* wird von frühere Versionen von IIS.
    - *iisexpress.exe* IISExpress ist.
    - *dotnet.exe* ist ASP.NET Core.
    - *Inetinfo.exe* ältere ASP-Anwendungen, die in-Process-Ausführung ist. 

>[!NOTE]
>Visual Studio 2012 und früher [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Code im Dateisystem werden kann, und führen Sie auf dem Testserver *WebDev.WebServer.exe* oder *WebDev.WebServer40.exe*. In diesem Fall für das lokale Debuggen, Anfügen an *WebDev.WebServer.exe* oder *WebDev.WebServer40.exe* statt der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Prozess. 

**Weitere Informationen finden Sie in den folgenden Artikeln:**

 [Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Voraussetzungen für das Remotedebuggen von Webanwendungen](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)   
 [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)