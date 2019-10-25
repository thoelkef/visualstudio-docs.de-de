---
title: 'Fehler: der Webserver ist nicht ordnungsgemäß konfiguriert | Microsoft-Dokumentation'
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
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736931"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert.

Nachdem Sie die hier beschriebenen Schritte ausgeführt haben, um das Problem zu beheben, und bevor Sie versuchen, das Debugging erneut auszuführen, müssen Sie möglicherweise auch IIS zurücksetzen. Öffnen Sie hierzu eine Administrator Eingabeaufforderung, und geben Sie `iisreset` ein.

Gehen Sie folgendermaßen vor, um dieses Problem zu beheben:

1. Wenn die auf dem Server gehostete Web-App als Releasebuild konfiguriert ist, veröffentlichen Sie Sie als Debugbuild erneut, und überprüfen Sie, ob die Datei Web. config `debug=true` im Kompilierungs Element enthält. IIS zurücksetzen und wiederholen.

    Wenn Sie z. b. ein Veröffentlichungs Profil für einen Releasebuild verwenden, ändern Sie es in Debuggen und erneut veröffentlichen. Andernfalls wird das debug-Attribut auf `false` festgelegt, wenn Sie veröffentlichen.

2. Ausschalten Überprüfen Sie, ob der physische Pfad richtig ist. In IIS finden Sie diese Einstellung unter **Grundeinstellungen > physischen Pfad** (oder **Erweiterte Einstellungen** in älteren Versionen von IIS).

    Der physische Pfad ist möglicherweise falsch, wenn die Webanwendung auf einen anderen Computer kopiert, manuell umbenannt oder verschoben wurde. IIS zurücksetzen und wiederholen.

3. Wenn Sie lokal in Visual Studio debuggen, vergewissern Sie sich, dass in den Eigenschaften der richtige Server ausgewählt ist. (Öffnen Sie die **Eigenschaften > web > Server** oder Eigenschaften, die je nach Projekttyp **> Debuggen** . Öffnen Sie für ein Web Forms Projekt die **Eigenschaften Seiten > Start Optionen > Server**).

    Wenn Sie einen externen (benutzerdefinierten) Server (z. b. IIS) verwenden, muss die URL richtig sein. Wählen Sie andernfalls IIS Express aus, und versuchen Sie es erneut.

4. Ausschalten Stellen Sie sicher, dass die richtige Version von ASP.net auf dem Server installiert ist.

    Das Problem kann durch nicht übereinstimmende Versionen von ASP.net auf IIS und in Ihrem Visual Studio-Projekt verursacht werden. Möglicherweise müssen Sie die Frameworkversion in der Datei "Web. config" festlegen. Verwenden Sie zum Installieren von ASP.net auf IIS den [Webplattform-Installer (webpi)](https://www.microsoft.com/web/downloads/platform.aspx). Weitere Informationen finden [Sie unter IIS 8,0 mithilfe von ASP.NET 3,5 und ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder ASP.net Core unter [Windows mit IIS hosten](https://docs.asp.net/en/latest/publishing/iis.html).

4. Wenn das `maxConnection` Limit in IIS zu niedrig ist, und Sie über zu viele Verbindungen verfügen, müssen Sie möglicherweise [das Verbindungs Limit erhöhen](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)