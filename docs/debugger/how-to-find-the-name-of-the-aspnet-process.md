---
title: Suchen des laufenden ASP.NET-Prozesses | Microsoft-Dokumentation
ms.date: 11/04/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: c14067d58289dd0b41fa526937a0553c10934ea7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349606"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Herausfinden des ASP.NET-Prozessnamens

Der Visual Studio-Debugger muss nach Namen an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess angehängt werden, um eine ausgeführte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-App zu debuggen.

**Ermitteln eines Prozesses, der eine ASP.NET-App ausführt:**

1. Klicken Sie auf **Debuggen** > **An Prozess anhängen**, wenn die App in Visual Studio ausgeführt wird.

1. Geben Sie die ersten Buchstaben der Prozessnamen aus der folgenden Liste ein im Dialogfeld **An Prozess anhängen** oder im Suchfeld ein. Bei dem ausgeführten Prozess handelt es sich um den Prozess, der die ASP.NET-App ausführt. Hängen Sie den Debugger an diesen Prozess an, um die App zu debuggen.

    - *w3wp.exe* entspricht IIS 6.0 und höher.
    - *aspnet_wp.exe* entspricht früheren Versionen von IIS.
    - *iisexpress.exe* entspricht IISExpress.
    - *dotnet.exe* entspricht ASP.NET Core.
    - *inetinfo.exe* entspricht älteren ASP-Anwendungen, die im Prozess ausgeführt werden.

>[!NOTE]
>Visual Studio 2012 und älterer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Code kann sich im Dateisystem befinden und auf den Testservern *WebDev.WebServer.exe* oder *WebDev.WebServer40.exe* ausgeführt werden. Hängen Sie den Debugger für das lokale Debuggen in diesem Fall an die Testserver *WebDev.WebServer.exe* oder *WebDev.WebServer40.exe* anstatt an den Prozess [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] an.

**Weitere Informationen finden Sie in den folgenden Artikeln:**

- [Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Voraussetzungen für das Remotedebuggen von Webanwendungen](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)
- [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)