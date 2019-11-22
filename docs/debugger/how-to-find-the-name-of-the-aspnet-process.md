---
title: Suchen des laufenden ASP.NET-Prozesses | Microsoft-Dokumentation
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187654"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Herausfinden des ASP.NET-Prozessnamens

Zum Debuggen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-APP, die ausgeführt wird, muss der Visual Studio-Debugger mithilfe des Namens an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Prozess angehängt werden

**So ermitteln Sie, welcher Prozess eine ASP.net-app ausgeführt hat:**

1. Wenn die app ausgeführt wird, wählen Sie in Visual Studio **Debuggen** > **an den Prozess anhängen**.

1. Geben Sie im Dialogfeld **an den Prozess anhängen** in der folgenden Liste die ersten Buchstaben der Prozessnamen ein, oder geben Sie Sie in das Suchfeld ein. Der einzige, der ausgeführt wird, ist der, der die ASP.net-app ausgeführt wird. Fügen Sie diesen Prozess an, um die APP zu debuggen.

    - *w3wp. exe* ist IIS 6,0 und höher.
    - *Aspnet_wp. exe* ist eine frühere Version von IIS.
    - *iisexpress. exe* ist iisexpress.
    - " *dotnet. exe* " ist ASP.net Core.
    - *inetinfo. exe* ist ältere ASP-Anwendungen, die innerhalb des Prozesses ausgeführt werden.

>[!NOTE]
>Visual Studio 2012 und frühere [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Code kann sich im Dateisystem befinden und auf dem Testserver " *WebDev. Webserver. exe* " oder " *WebDev. WebServer40. exe*" ausgeführt werden. Fügen Sie in diesem Fall für das lokale Debuggen an *WebDev. Webserver. exe* oder *WebDev. WebServer40. exe* statt an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Prozess an.

**Weitere Informationen finden Sie in den folgenden Artikeln:**

- [Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Voraussetzungen für das Remote Debugging von Webanwendungen](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)
- [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)