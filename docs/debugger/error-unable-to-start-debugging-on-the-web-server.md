---
title: 'Fehler: das Debuggen kann auf dem Webserver nicht gestartet werden | Microsoft-Dokumentation'
ms.date: 05/23/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c976f14a4250741d166c189c53a1b8cae8ea891a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736703"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden

Wenn Sie versuchen, eine ASP.NET-Anwendung zu debuggen, die auf einem Webserver ausgeführt wird, wird möglicherweise die folgende Fehlermeldung angezeigt: `Unable to start debugging on the Web server`.

Dieser Fehler tritt häufig auf, weil eine Fehler-oder Konfigurationsänderung aufgetreten ist, die ein Update Ihrer Anwendungs Pools, eine IIS-zurück setzung oder beides erfordert. Sie können IIS zurücksetzen, indem Sie eine Eingabeaufforderung mit erhöhten Rechten öffnen und `iisreset` eingeben.

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to start debugging on the Web server` Nachricht ist generisch. In der Regel ist eine spezifischere Nachricht in der Fehler Zeichenfolge enthalten, die Ihnen helfen kann, die Ursache des Problems zu identifizieren oder nach einer genaueren Korrektur zu suchen. Im folgenden finden Sie einige der häufigsten Fehlermeldungen, die an die Haupt Fehlermeldung angehängt werden:

- [IIS listet keine Websites auf, die mit der Start-URL übereinstimmen.](#IISlist)
- [Der Webserver ist nicht richtig konfiguriert](#web_server_config)
- [Es kann keine Verbindung mit dem Webserver hergestellt werden.](#unabletoconnect)
- [Der Webserver hat nicht rechtzeitig reagiert.](#webservertimeout)
- [Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt](#msvsmon)
- [Der Remote Server hat einen Fehler zurückgegeben.](#server_error)
- [ASP.NET-Debugging konnte nicht gestartet werden.](#aspnet)
- [Der Debugger kann keine Verbindung mit dem Remote Computer herstellen.](#cannot_connect)
- [Weitere Informationen finden Sie in der Hilfe zu häufigen Konfigurationsfehlern. Wenn Sie die Webseite außerhalb des Debuggers ausführen, werden möglicherweise weitere Informationen bereitgestellt.](#see_help)

## <a name="IISlist"></a>IIS listet keine Websites auf, die mit der Start-URL übereinstimmen.

- Starten Sie Visual Studio als Administrator neu, und wiederholen Sie das Debugging. (Einige ASP.net-debuggingszenarien erfordern erhöhte Rechte.)

    Sie können Visual Studio so konfigurieren, dass Sie immer als Administrator ausgeführt werden, indem Sie mit der rechten Maustaste auf das Visual Studio-Verknüpfungs Symbol klicken, **Eigenschaften > erweitert**auswählen und dann auswählen, dass Sie immer als Administrator ausgeführt werden.

## <a name="web_server_config"></a> Der Webserver ist nicht richtig konfiguriert

- Siehe [Fehler: der Webserver ist nicht ordnungsgemäß konfiguriert](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>Es kann keine Verbindung mit dem Webserver hergestellt werden.

- Führen Sie Visual Studio und den Webserver auf demselben Computer aus und Debuggen mit **F5** (statt **an den Prozess anhängen**)? Öffnen Sie die Projekteigenschaften, und stellen Sie sicher, dass das Projekt für die Verbindung mit dem richtigen Webserver und der Start-URL konfiguriert ist. (Öffnen Sie die **Eigenschaften > web > Server** oder Eigenschaften, die je nach Projekttyp **> Debuggen** . Öffnen Sie für ein Web Forms Projekt die **Eigenschaften Seiten > Start Optionen > Server**.)

- Starten Sie andernfalls den Anwendungs Pool neu, und setzen Sie IIS zurück. Weitere Informationen finden Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>Der Webserver hat nicht rechtzeitig reagiert.

- Setzen Sie IIS zurück, und wiederholen Sie das Debugging. An den IIS-Prozess können mehrere Debugger-Instanzen angefügt werden. beim Zurücksetzen werden Sie beendet. Weitere Informationen finden Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt

- Wenn Sie auf einem Remote Computer Debuggen, müssen Sie sicherstellen, dass [der Remote Debugger installiert ist und ausgeführt](../debugger/remote-debugging.md)wird. Wenn in der Meldung eine Firewall erwähnt wird, stellen Sie sicher, dass die [richtigen Ports in der Firewall](../debugger/remote-debugger-port-assignments.md) geöffnet sind. Dies gilt insbesondere, wenn Sie eine Firewall eines Drittanbieters verwenden.
- Wenn Sie eine Hosts-Datei verwenden, stellen Sie sicher, dass Sie ordnungsgemäß konfiguriert ist. Wenn Sie z. b. mit **F5** Debuggen (statt **an den Prozess anhängen**), muss die Datei "Hosts" dieselbe Projekt-URL wie in den Projekteigenschaften, **Eigenschaften > web > Server** oder **Eigenschaften > Debuggen**, abhängig von Ihr Projekttyp.

## <a name="server_error"></a>Der Remote Server hat einen Fehler zurückgegeben.

Überprüfen Sie die [IIS-Protokolldatei](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) auf Fehler-und zusätzliche Informationen sowie den IIS 7- [Blogbeitrag](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Außerdem finden Sie hier einige der allgemeinen Fehlercodes und einige Vorschläge.
- (403) Unzulässig. Es gibt viele mögliche Ursachen für diesen Fehler. Überprüfen Sie daher die Protokolldatei und die IIS-Sicherheitseinstellungen für die Website. Stellen Sie sicher, dass die Datei "Web. config" des Servers `debug=true` im Kompilierungs Element enthält. Stellen Sie sicher, dass Ihr Webanwendungs Ordner über die richtigen Berechtigungen verfügt und dass die Anwendungs Pool Konfiguration korrekt ist (ein Kennwort wurde möglicherweise geändert). Siehe [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck). Wenn diese Einstellungen bereits richtig sind und Sie lokal debuggen, vergewissern Sie sich auch, dass Sie eine Verbindung mit dem richtigen Servertyp und der richtigen URL (in **Eigenschaften > web > Server** oder **Eigenschaften > Debuggen**, je nach Projekttyp) herstellen.
- (503) Server nicht verfügbar. Der Anwendungs Pool wurde aufgrund eines Fehlers oder einer Konfigurationsänderung möglicherweise beendet. Starten Sie den Anwendungs Pool neu.
- (404) Nicht gefunden. Stellen Sie sicher, dass der Anwendungs Pool für die richtige Version von ASP.NET konfiguriert ist.

## <a name="aspnet"></a>ASP.NET-Debugging konnte nicht gestartet werden.

- Starten Sie den Anwendungs Pool neu und setzen Sie IIS zurück. Weitere Informationen finden Sie unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).
- Wenn Sie URL-Neuschreibungen ausführen, testen Sie eine einfache Web. config-Datei ohne URL-Neuschreibungen. Weitere Informationen finden **Sie im Hinweis** zum URL-Rewrite-Modul unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a>Der Debugger kann keine Verbindung mit dem Remote Computer herstellen.

Wenn Sie lokal debuggen, öffnen Sie die Projekteigenschaften in Visual Studio, und stellen Sie sicher, dass das Projekt für die Verbindung mit dem richtigen Webserver und der richtigen URL konfiguriert ist. (Öffnen Sie die **Eigenschaften > web > Server** oder Eigenschaften, die je nach Projekttyp **> Debuggen** .)

Dieser Fehler kann auftreten, wenn Sie lokal debuggen, da Visual Studio eine 32-Bit-Anwendung ist. Daher wird die 64-Bit-Version des Remote Debuggers verwendet, um 64-Bit-Anwendungen zu debuggen. Überprüfen Sie Ihren app-Pool auf IIS, um sicherzustellen, dass **32-Bit-Anwendungen aktivieren** auf `true` festgelegt ist, starten Sie IIS neu, und versuchen Sie es

Wenn Sie eine Hostdatei verwenden, stellen Sie außerdem sicher, dass Sie ordnungsgemäß konfiguriert ist. Beispielsweise muss die Datei "Hosts" die gleiche Projekt-URL wie in den Projekteigenschaften, **Eigenschaften > web > Server** oder **Eigenschaften > Debuggen**, abhängig vom Projekttyp, einschließen.

## <a name="see_help"></a> In der Hilfe werden häufige Konfigurationsfehler erläutert. Wenn Sie die Webseite außerhalb des Debuggers ausführen, werden möglicherweise weitere Informationen bereitgestellt.

- Führen Sie Visual Studio und den Webserver auf demselben Computer aus? Öffnen Sie die Projekteigenschaften, und stellen Sie sicher, dass das Projekt für die Verbindung mit dem richtigen Webserver und der Start-URL konfiguriert ist. (Öffnen Sie die **Eigenschaften > web > Server** oder Eigenschaften, die je nach Projekttyp **> Debuggen** .)

- Wenn dies nicht funktioniert oder Sie Remote Debuggen, führen Sie die Schritte unter [Überprüfen der IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck)aus.

## <a name="vxtbshttpservererrorsthingstocheck"></a>Überprüfen der IIS-Konfiguration

Nachdem Sie die hier beschriebenen Schritte ausgeführt haben, um das Problem zu beheben, und bevor Sie versuchen, das Debugging erneut auszuführen, müssen Sie möglicherweise auch IIS zurücksetzen. Öffnen Sie hierzu eine Eingabeaufforderung mit erhöhten Rechten, und geben Sie `iisreset` ein.

* Starten Sie die IIS-Anwendungs Pools, und starten Sie Sie neu.

    Der Anwendungs Pool wurde möglicherweise aufgrund eines Fehlers angehalten. Oder eine andere Konfigurationsänderung, die Sie vorgenommen haben, erfordert möglicherweise, dass Sie den Anwendungs Pool abbrechen und neu starten.

    > [!NOTE]
    > Wenn der Anwendungs Pool angehalten wird, müssen Sie möglicherweise das URL-Rewrite-Modul über die Systemsteuerung deinstallieren. Sie können Sie mithilfe des Webplattform-Installers (webpi) neu installieren. Dieses Problem tritt möglicherweise nach einer signifikanten Systemaktualisierung auf.

* Überprüfen Sie die Anwendungs Pool Konfiguration, korrigieren Sie Sie bei Bedarf, und versuchen Sie es dann erneut.

    Der Anwendungs Pool kann für eine Version von ASP.NET konfiguriert werden, die nicht dem Visual Studio-Projekt entspricht. Aktualisieren Sie die ASP.NET-Version im Anwendungs Pool, und starten Sie Sie neu. Ausführliche Informationen finden Sie unter [IIS 8,0 mit ASP.NET 3,5 und ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Wenn sich Kenn Wort Anmelde Informationen geändert haben, müssen Sie Sie möglicherweise auch in Ihrem Anwendungs Pool oder auf der Website aktualisieren.  Aktualisieren Sie im Anwendungs Pool die Anmelde Informationen in **Erweiterte Einstellungen > Prozessmodell > Identität**. Aktualisieren Sie die Anmelde Informationen für die-Website in den **grundlegenden Einstellungen, > Connect als...** Starten Sie den Anwendungs Pool neu.

* Überprüfen Sie, ob Ihr Webanwendungs Ordner die richtigen Berechtigungen besitzt.

    Stellen Sie sicher, dass Sie IIS_IUSRS, IUSR oder der bestimmte Benutzer, die dem [Anwendungs Pool](/iis/manage/configuring-security/application-pool-identities) zugeordnet sind, über die Berechtigungen Lesen und Ausführen für den Webanwendungs Ordner verfügen. Beheben Sie das Problem, und starten Sie den Anwendungs Pool neu.

* Stellen Sie sicher, dass die richtige Version von ASP.net auf IIS installiert ist.

    Das Problem kann durch nicht übereinstimmende Versionen von ASP.net auf IIS und in Ihrem Visual Studio-Projekt verursacht werden. Möglicherweise müssen Sie die Frameworkversion in der Datei "Web. config" festlegen. Verwenden Sie zum Installieren von ASP.net auf IIS den [Webplattform-Installer (webpi)](https://www.microsoft.com/web/downloads/platform.aspx). Weitere Informationen finden [Sie unter IIS 8,0 mithilfe von ASP.NET 3,5 und ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder ASP.net Core unter [Windows mit IIS hosten](https://docs.asp.net/en/latest/publishing/iis.html).

* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in IIS so konfiguriert ist, dass eine Authentifizierung erforderlich ist, tritt bei dieser Authentifizierung ein Fehler auf. Um dieses Problem zu beheben, können Sie den Namen des Remote Computers anstelle der IP-Adresse angeben.

## <a name="other-causes"></a>Weitere Gründe

Wenn die IIS-Konfiguration das Problem nicht verursacht, führen Sie die folgenden Schritte aus:

- Starten Sie Visual Studio mit Administrator Rechten neu, und versuchen Sie es erneut.

    Einige ASP.net-debuggingszenarien wie die Verwendung von Web deploy erfordern erweiterte Berechtigungen für Visual Studio.

- Wenn mehrere Instanzen von Visual Studio ausgeführt werden, öffnen Sie das Projekt in einer Instanz von Visual Studio (mit Administrator Rechten) erneut, und versuchen Sie es noch mal.

- Wenn Sie eine Hosts-Datei mit lokalen Adressen verwenden, versuchen Sie, anstelle der IP-Adresse des Computers die Loopback Adresse zu verwenden.

    Wenn Sie keine lokalen Adressen verwenden, stellen Sie sicher, dass die Hostdatei die gleiche Projekt-URL wie in den Projekteigenschaften, **Eigenschaften > web > Server** oder **Eigenschaften > debug**, abhängig vom Projekttyp enthält.

## <a name="more-troubleshooting-steps"></a>Weitere Schritte zur Problembehandlung

* Rufen Sie die localhost-Seite im Browser auf dem Server auf.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.

     Weitere Informationen zur Bereitstellung in IIS finden [Sie unter IIS 8,0 mit ASP.NET 3,5 und ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) und unter [Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html)für ASP.net Core.

* Erstellen Sie eine einfache ASP.NET-Anwendung auf dem Server (oder verwenden Sie eine einfache Web. config-Datei).

    Wenn Sie nicht möchten, dass Ihre APP mit dem Debugger funktioniert, versuchen Sie, eine einfache ASP.NET-Anwendung lokal auf dem Server zu erstellen, und versuchen Sie, die grundlegende APP zu debuggen. (Möglicherweise möchten Sie die standardmäßige ASP.NET-MVC-Vorlage verwenden.) Wenn Sie eine einfache APP Debuggen können, können Sie dadurch leichter erkennen, worin sich die beiden Konfigurationen unterscheiden. Suchen Sie Unterschiede in den Einstellungen in der Datei "Web. config", z.b. URL-Rewrite-Regeln.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)