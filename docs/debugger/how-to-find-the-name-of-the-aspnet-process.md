---
title: 'Vorgehensweise: herausfinden des ASP.NET-Prozessnamens | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 899860baf5461eb798341cebf775ccde488915b7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473818"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Gewusst wie: Herausfinden des ASP.NET-Prozessnamens
Für das Anhängen an eine ausgeführte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung müssen Sie den Namen des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozesses kennen.  

-   Wenn Sie ASP.NET Core unter IIS oder IIS Express ausgeführt werden, ist der Name des Prozesses dotnet.exe.

-   Wenn Sie ASP.NET auf IIS 6.0 später ausführen, ist der Name w3wp.exe.  
  
-   Wenn Sie ASP.NET unter einer früheren Version von IIS ausführen, lautet der Name aspnet_wp.exe.

-   Wenn Sie ASP.NET auf IIS Express ausgeführt werden, ist der Name iisexpress.exe.
  
Für Anwendungen, die mit Versionen von Visual Studio vor Visual Studio 2012 erstellt die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Code befinden sich auf das Dateisystem und unter dem Testserver WebDev.WebServer.exe oder WebDev.WebServer40.exe ausführen kann. In diesem Fall müssen Sie WebDev.WebServer.exe oder WebDev.WebServer40.exe anstelle von Anfügen der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Prozess. Dieses Szenario gilt nur für lokales Debuggen.
  
Ältere ASP-Anwendungen werden innerhalb des IIS-Prozesses inetinfo.exe ausgeführt, sobald sie prozessintern laufen.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>So stellen Sie die IIS-Version fest, unter der die Anwendung ausgeführt wird  

1.  Stellen Sie sicher, dass die Anwendung ausgeführt wird, und verwenden Sie dann in Visual Studio die [an den Prozess anhängen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) Befehl.

2.  Geben Sie den ersten Buchstaben des Namens eines Prozesses, wie w3wp.exe schnelle Auffinden von Prozessen in der **verfügbare Prozesse** Liste.

    In diesem Thema in der Liste der verfügbaren Prozesse werden angegeben, welche Versionen von IIS verfügbar sind und welcher Prozess die Anwendung ausgeführt wird.

    > [!NOTE]
    > Ab Visual Studio 2017 können können das Suchfeld Sie um den Namen des Prozesses zu suchen.
  
## <a name="see-also"></a>Siehe auch  
 [Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Voraussetzungen für das Remotedebuggen von ASP.NET-Webanwendungen](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)   
 [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)