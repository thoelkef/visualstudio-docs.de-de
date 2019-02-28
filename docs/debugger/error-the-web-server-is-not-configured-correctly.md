---
title: 'Fehler: Der Webserver ist nicht ordnungsgemäß konfiguriert | Microsoft-Dokumentation'
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc0c61b766b6f93fd1321b15861000d7c628f124
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711604"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert.

Unter Berücksichtigung der hier angegebenen Schritte zur Behebung des Problems und vor dem erneuten Versuch zum Debuggen müssen Sie auch IIS zurücksetzen. Sie können Sie dies, indem Sie eine Administrator-Eingabeaufforderung öffnen und Folgendes eingeben `iisreset`.

Führen Sie diese Schritte, um dieses Problem zu beheben:

1. Wenn auf dem Server gehostete Web-app als konfiguriert ist ein Releasebuild erstellt, als ein Debugbuild erneut veröffentlichen, und stellen Sie sicher, dass die Datei "Web.config" enthält `debug=true` in das Compilation-Element. Zurücksetzen von IIS, und wiederholen Sie.

    Z. B., wenn Sie ein Veröffentlichungsprofil für einen Releasebuild verwenden, ändern Sie ihn in Debug und erneut veröffentlichen. Andernfalls wird das Debug-Attribut festgelegt werden, um `false` beim Veröffentlichen.

2. (IIS) Stellen Sie sicher, dass der physische Pfad richtig ist. In IIS finden Sie diese Einstellung im **Grundeinstellungen > physischen Pfad** (oder **Erweiterte Einstellungen** in älteren Versionen von IIS).

    Der physische Pfad kann falsch sein, wenn die Webanwendung in einem anderen Computer kopiert, manuell umbenannt oder verschoben wurde. Zurücksetzen von IIS, und wiederholen Sie.

3. Wenn Sie lokal in Visual Studio debuggen, stellen Sie sicher, dass in den Eigenschaften der richtige Server ausgewählt ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** je nach Projekttyp. Öffnen Sie für eine Web Forms-Projekt **Eigenschaftenseiten > Startoptionen > Server**).

    Wenn Sie einen externen (benutzerdefinierten)-Server wie IIS verwenden, muss die URL richtig sein. Wählen Sie andernfalls IIS Express, und wiederholen Sie.

4. (IIS) Stellen Sie sicher, dass die richtige Version von ASP.NET auf dem Server installiert ist.

    Nicht übereinstimmende Versionen von ASP.NET auf IIS und in Visual Studio-Projekts können dazu führen, dass dieses Problem. Sie müssen möglicherweise die Framework-Version in der Datei "Web.config" festgelegt. Verwenden Sie zum Installieren von ASP.NET in IIS die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Siehe auch [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Wenn die `maxConnection` Begrenzung in IIS ist zu niedrig ist, und Sie zu viele Verbindungen haben, müssen Sie möglicherweise [erhöhen Sie das Verbindungslimit](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)