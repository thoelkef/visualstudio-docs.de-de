---
title: 'Fehler: Der Webserver ist nicht ordnungsgemäß konfiguriert | Microsoft Docs'
ms.custom: ''
ms.date: 09/20/2017
ms.technology:
- vs-ide-debug
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bf614f44ec4fedd0579f3c352e3046fa0c46e9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Fehler: Der Webserver ist nicht richtig konfiguriert.

Nach der Schritte zur Behebung des Problems hier detailliert, und versuchen Sie es noch debuggen müssen Sie möglicherweise auch IIS zurücksetzen. Sie können dies vornehmen, indem Sie eine Administrator-Eingabeaufforderung öffnen und Folgendes eingeben: `iisreset`.

Um dieses Problem zu beheben, gehen Sie wie folgt vor:

1. Wenn die Web-app auf dem Server gehosteten als konfiguriert ist ein Releasebuild kann als einen Debugbuild veröffentlichen, und stellen Sie sicher, dass die Datei "Web.config" enthält `debug=true` in das Compilation-Element. Zurücksetzen von IIS und versuchen Sie es erneut.

    Beispielsweise bei Verwendung von einem Veröffentlichungsprofil für einen Releasebuild debuggen zu ändern, und Sie erneut veröffentlichen. Andernfalls wird das Debug-Attribut festgelegt werden, um `false` beim Veröffentlichen.

2. (IIS) Stellen Sie sicher, dass der physische Pfad korrekt ist. In IIS finden Sie diese Einstellung in **Grundeinstellungen > physischen Pfad** (oder **Erweiterte Einstellungen** in älteren Versionen von IIS).

    Der physische Pfad möglicherweise fehlerhaft, wenn die Webanwendung in einem anderen Computer kopiert, manuell umbenannt oder verschoben wurde. Zurücksetzen von IIS und versuchen Sie es erneut.

3. Wenn Sie lokal in Visual Studio debuggen, stellen Sie sicher, dass der richtige Server, in den Eigenschaften ausgewählt wurde. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** Abhängigkeit vom Projekttyp. Für eine Web Forms-Projekt öffnen **Eigenschaftenseiten > Startoptionen > Server**).

    Wenn Sie einen externen (benutzerdefinierten) Server wie IIS verwenden, muss die URL richtig sein. Wählen Sie andernfalls, IIS Express, und versuchen Sie es erneut.

4. (IIS) Stellen Sie sicher, dass die richtige Version von ASP.NET auf dem Server installiert ist.

    Nicht übereinstimmende Versionen von ASP.NET auf IIS und in Visual Studio-Projekt können dieses Problem verursachen. Sie müssen möglicherweise die Framework-Version in der Datei "Web.config" festlegen. Verwenden Sie zum Installieren von ASP.NET auf IIS die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Siehe auch [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Wenn die `maxConnection` Begrenzung in IIS ist zu niedrig ist, und Sie haben zu viele Verbindungen, müssen Sie möglicherweise [erhöhen Sie das Verbindungslimit](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen von ASP.NET auf einem Remote-IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)