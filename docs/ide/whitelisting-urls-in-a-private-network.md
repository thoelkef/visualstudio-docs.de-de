---
title: Erstellen von URL-Whitelists in einem privaten Netzwerk | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2018
---
# <a name="whitelisting-urls-in-a-private-network"></a>Erstellen von URL-Whitelists in einem privaten Netzwerk

Wenn Sie Visual Studio in einem privaten Netzwerk verwenden, in dem eine Sicherheitsappliance wie z.B. eine Firewall genutzt wird, kann Visual Studio möglicherweise keine Verbindung mit einigen Netzwerkressourcen herstellen. Zu diesen Ressourcen zählen Visual Studio Team Services (VSTS) für die Anmeldung und Lizenzierung, NuGet und Azure-Dienste. Wenn Visual Studio keine Verbindung mit einer dieser Ressourcen herstellen kann, wird die folgende Fehlermeldung angezeigt:

  **The underlying connection was closed: An unexpected error occurred on send** (Die zugrunde liegende Verbindung wurde geschlossen: Beim Senden ist ein unerwarteter Fehler aufgetreten.)

Visual Studio verwendet das Protokoll Transport Layer Security (TLS) 1.2 für die Verbindung mit Netzwerkressourcen. Sicherheitsappliances blockieren in einigen privaten Netzwerken bestimmte Serververbindungen, wenn Visual Studio TLS 1.2 verwendet. Um den Fehler zu beheben, lassen Sie Verbindungen mit den folgenden URLs zu:

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (für Azure-Verbindungen)

- *.nuget.org (für NuGet-Verbindungen)

- *.visualstudio.com

- cdn.vsassets.io (Hosting von CDN-Inhalten (Content Delivery Network))

- *.gallerycdn.vsassets.io (Hosting von VSTS-Erweiterungen)

- static2.sharepointonline.com (Hosting von Ressourcen wie beispielsweise Schriftarten, die Visual Studio im Zusammenhang mit dem Office Fabric UI-Kit verwendet)

> [!NOTE]
> URLs von privaten NuGet-Servern sind in der oben aufgeführten Liste möglicherweise nicht enthalten. Sie können überprüfen, welche NuGet-Server Sie verwenden, indem Sie „%APPData%\Nuget\NuGet.Config“ öffnen.

## <a name="see-also"></a>Siehe auch

[Fehler: Proxyautorisierung erforderlich](../ide/reference/proxy-authorization-required.md)  
[Installieren von Visual Studio hinter einer Firewall oder einem Proxyserver](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
