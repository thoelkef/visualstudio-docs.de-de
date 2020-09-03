---
title: 'Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185482"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie versuchen, eine ASP.NET-Anwendung auf einem Webserver zu debuggen, erhalten Sie möglicherweise folgende Fehlermeldung: „Das Debuggen kann auf dem Webserver nicht gestartet werden“.
  
In vielen Fällen tritt dieser Fehler auf, weil IIS nicht ordnungsgemäß konfiguriert ist.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Überprüfen der IIS-Konfiguration

Nachdem Sie die Schritte zum Beheben eines hier beschriebenen Problems und vor dem erneuten Debuggen ausgeführt haben, müssen Sie möglicherweise auch IIS zurücksetzen. Öffnen Sie hierzu eine Administrator Eingabeaufforderung `iisreset` , und geben Sie ein. Sie können dies auch im IIS-Manager tun. 

* Starten Sie die Anwendungs Pools, und starten Sie Sie neu.

    Der Anwendungs Pool wurde möglicherweise beendet, oder eine andere Konfigurationsänderung, die Sie vorgenommen haben, erfordert möglicherweise, dass Sie den Anwendungs Pool beenden und neu starten.
    
    > [!NOTE]
    > Wenn der Anwendungs Pool angehalten wird, müssen Sie möglicherweise das URL-Rewrite-Modul über die Systemsteuerung deinstallieren und dann mithilfe des Webplattform-Installers (WPI) neu installieren. Dies kann nach einer signifikanten Systemaktualisierung ein Problem sein.

* Überprüfen Sie die Konfiguration des Anwendungspools, korrigieren Sie sie gegebenenfalls, und versuchen Sie es dann noch mal.

    Wenn Kenn Wort Anmelde Informationen geändert wurden, müssen Sie Sie möglicherweise in Ihrem Anwendungs Pool aktualisieren. Wenn Sie vor kurzem ASP.NET installiert haben, ist der Anwendungs Pool möglicherweise für die falsche Version von ASP.NET konfiguriert. Beheben Sie das Problem, und starten Sie den Anwendungs Pool neu.
    
* Überprüfen Sie, ob Ihr Webanwendungsordner die erforderlichen Berechtigungen aufweist.

    Stellen Sie sicher, dass Sie für den Webanwendungs Ordner IIS_IUSRS oder IUSR (bzw. den bestimmten Benutzer, der dem Anwendungs Pool zugeordnet ist) die Lese-und Ausführungsrechte geben. Beheben Sie das Problem, und starten Sie Ihren Anwendungspool neu.

* Wenn Sie eine HOSTS-Datei mit lokalen Adressen verwenden, versuchen Sie es mit der Loopbackadresse anstelle der IP-Adresse des Computers.

* Rufen Sie die Seite "localhost" im Browser auf.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.
     
     Weitere Informationen zur Bereitstellung in IIS finden Sie unter [Remote Debugging ASP.net on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder, for ASP.net Core, [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Stellen Sie sicher, dass in den IIS die richtige ASP.NET-Version installiert ist.  Weitere Informationen finden Sie unter Bereitstellen [einer ASP.NET-Anwendung](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) oder ASP.net Core [Veröffentlichen in IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Erstellen Sie eine einfache ASP.NET-Anwendung auf dem Server.

     Wenn Sie es nicht ermöglichen können, dass die App mit dem Debugger verwendet werden kann, versuchen Sie, eine grundlegende ASP.NET-Anwendung lokal auf dem Server zu erstellen, und versuchen Sie, die grundlegende App zu debuggen. Wenn Sie eine einfache APP Debuggen können, können Sie dadurch leichter erkennen, worin sich die beiden Konfigurationen unterscheiden.
  
* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in IIS so konfiguriert ist, dass eine Authentifizierung erforderlich ist, tritt bei dieser Authentifizierung ein Fehler auf. Zur Behebung dieses Problems können Sie den Namen des Remotecomputers anstelle der IP-Adresse angeben.
     
## <a name="other-causes"></a>Weitere Ursachen

Wenn Sie eine ältere Version von Visual Studio verwenden:

- Starten Sie Visual Studio mit erhöhten Rechten neu, und versuchen Sie es erneut.

    Ein Fehler in älteren Versionen (später behoben) erforderte erweiterte Berechtigungen in einigen ASP.net-debuggingszenarien.
    
- Wenn mehrere Instanzen von Visual Studio ausgeführt werden, öffnen Sie das Projekt in einer Instanz von Visual Studio erneut, und wiederholen Sie den Vorgang.

## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
