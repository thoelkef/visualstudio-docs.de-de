---
title: 'Fehler: Debuggen kann nicht auf dem Webserver | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185482"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie versuchen, eine ASP.NET-Anwendung auf einem Webserver zu debuggen, erhalten Sie möglicherweise diese Fehlermeldung wird angezeigt: Debuggen kann nicht auf dem Webserver.
  
In vielen Fällen tritt dieser Fehler auf, da IIS nicht ordnungsgemäß konfiguriert ist.

## <a name="vxtbshttpservererrorsthingstocheck"></a> Überprüfen Sie die IIS-Konfiguration

Nach dem Maßnahmen zur Problembehebung detaillierte hier und vor dem erneuten Versuch zum Debuggen, müssen Sie auch IIS zurücksetzen. Sie können Sie dies, indem Sie eine Administrator-Eingabeaufforderung öffnen und Folgendes eingeben `iisreset`, oder Sie können dies im IIS-Manager. 

* Beenden Sie und neu starten Sie des Anwendungspools, und wiederholen Sie dann.

    Der Anwendungspool wurde beendet oder möglicherweise eine andere Änderung der Konfiguration, die Sie vorgenommen haben, beenden und starten Sie den Anwendungspool neu.
    
    > [!NOTE]
    > Wenn der Anwendungspool beendet wird, müssen Sie möglicherweise das URL-Rewrite-Modul in der Systemsteuerung deinstallieren und installieren Sie sie mit der Web Platform Installer (WPI). Dies kann ein Problem nach einem Upgrade beträchtliche Systemressourcen sein.

* Überprüfen Sie die Konfiguration des Anwendungspools, korrigieren Sie ihn bei Bedarf, und wiederholen Sie dann.

    Wenn Kennwörter geändert haben, müssen Sie sie in Ihrem Anwendungspool aktualisieren. Wenn Sie ASP.NET vor kurzem installiert haben, können auch den Anwendungspool für die falsche Version von ASP.NET konfiguriert werden. Beheben Sie das Problem, und starten Sie den Anwendungspool neu.
    
* Überprüfen Sie, dass Ihre Web Application-Ordner die richtigen Berechtigungen verfügt.

    Stellen Sie sicher, dass Sie IIS_IUSRS oder IUSR-Konto (oder den bestimmten Benutzer, die dem Anwendungspool zugeordnet) zum Lesen und Ausführen von Berechtigungen für Ordner der Web-Anwendung. Beheben Sie das Problem, und starten Sie den Anwendungspool neu.

* Wenn Sie eine Datei "HOSTS" mit lokalen Adressen verwenden, versuchen Sie, statt die Loopback-Adresse, die IP-Adresse des Computers.

* Fahren Sie die Localhost-Seite im Browser.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.
     
     Weitere Informationen zur Bereitstellung in IIS finden Sie unter [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder für ASP.NET Core, [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Stellen Sie sicher, dass die richtige Version von ASP.NET in IIS installiert ist.  Finden Sie unter [Bereitstellen einer ASP.NET-Anwendung](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) oder für ASP.NET Core [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Erstellen Sie eine einfache ASP.NET-Anwendung auf dem Server.

     Wenn Sie Ihre app mit dem Debugger funktioniert nicht, versuchen Sie es erstellen eine grundlegende ASP.NET-Anwendung lokal auf dem Server, und versuchen, die grundlegende app zu debuggen. Wenn Sie eine einfache app Debuggen können, kann, mit denen Sie bestimmen, welche Elemente sich zwischen den beiden Konfigurationen.
  
* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in IIS für die Authentifizierung konfiguriert ist, schlägt diese Authentifizierung fehl. Um dieses Problem zu beheben, können Sie den Namen des Remotecomputers anstelle der IP-Adresse angeben.
     
## <a name="other-causes"></a>Andere Ursachen

Wenn Sie eine ältere Version von Visual Studio verwenden:

- Starten Sie Visual Studio mit erhöhten Rechten, und versuchen Sie es erneut.

    Erhöhten in einigen Debugszenarien ASP.NET erforderlich, ein Fehler in älteren Versionen (später korrigiert).
    
- Wenn mehrere Instanzen von Visual Studio ausführen, öffnen Sie erneut Ihr Projekt in einer Instanz von Visual Studio, und versuchen Sie es erneut.

## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
