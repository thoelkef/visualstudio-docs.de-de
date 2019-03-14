---
title: 'Fehler: Debuggen kann nicht auf dem Webserver | Microsoft-Dokumentation'
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
ms.openlocfilehash: 908500a333303857ac88d27c76b285464913ff1c
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526294"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden

Wenn Sie versuchen, eine ASP.NET-Anwendung auf einem Webserver zu debuggen, erhalten Sie möglicherweise folgende Fehlermeldung: `Unable to start debugging on the Web server`.

Häufig tritt dieser Fehler auf, da ein Fehler oder die Konfiguration geändert wurde, die ein Update des Anwendungspools, eine IIS-Rücksetzung oder beides erforderlich ist. Sie können IIS zurücksetzen, indem Sie eine Eingabeaufforderung mit erhöhten Rechten öffnen und eingeben `iisreset`.

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to start debugging on the Web server` Nachricht ist generisch. In der Regel eine spezifische Nachricht ist in die Zeichenfolge enthalten, und kann, mit denen Sie die Ursache des Problems oder Suche für eine genauere Problembehebung zu identifizieren. Hier sind einige der häufigeren Fehlermeldungen, die die wichtigsten Fehlermeldung angefügt sind:

- [IIS führt eine Website, die den Start entspricht nicht Url](#IISlist)
- [Der Webserver ist nicht richtig konfiguriert](#web_server_config)
- [Es konnte keine Verbindung zum webserver](#unabletoconnect)
- [Der Webserver hat nicht rechtzeitig reagiert.](#webservertimeout)
- [Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt](#msvsmon)
- [Der Remoteserver hat einen Fehler zurückgegeben.](#server_error)
- [Debuggen von ASP.NET konnte nicht gestartet](#aspnet)
- [Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen.](#cannot_connect)
- [ In der Hilfe werden häufige Konfigurationsfehler erläutert. Die Webseite außerhalb des Debuggers ausgeführt, kann weitere Informationen bereitstellen.](#see_help)

## <a name="IISlist"></a> IIS führt eine Website, die den Start entspricht nicht Url

- Starten Sie Visual Studio als Administrator aus, und wiederholen Sie die Debuggen. (Einige Debugszenarien ASP.NET erfordern erhöhten.)

    Sie können konfigurieren, dass Visual Studio immer als Administrator ausführen, durch Rechtsklick auf das Verknüpfungssymbol Visual Studio auswählen **Eigenschaften > erweitert**, und wählen Sie anschließend zu immer als Administrator ausführen.

## <a name="web_server_config"></a> Der Webserver ist nicht richtig konfiguriert

- Finden Sie unter [Fehler: der Webserver ist nicht ordnungsgemäß konfiguriert](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Es konnte keine Verbindung zum webserver

- Sind Sie mit Visual Studio und dem Webserver auf demselben Computer ausführen und Debuggen mit **F5** (anstelle von **an den Prozess anhängen**)? Öffnen Sie die Projekteigenschaften, und stellen Sie sicher, dass das Projekt zum Verbinden mit dem richtigen Webserver, und starten die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** je nach Projekttyp. Öffnen Sie für eine Web Forms-Projekt **Eigenschaftenseiten > Startoptionen > Server**.)

- Andernfalls starten Sie den Anwendungspool neu, und klicken Sie dann IIS zurücksetzen. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Der Webserver hat nicht rechtzeitig reagiert.

- Setzen Sie IIS zurück, und wiederholen Sie die Debuggen. Mehrere Instanzen der Debugger können an den IIS-Prozess angefügt werden; Zurücksetzen ein beendet diese. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon">Der Microsoft Visual Studio-Remotedebugmonitor (msvsmon.exe) wird auf dem Remotecomputer nicht ausgeführt</a>

- Wenn Sie auf einem Remotecomputer debuggen, stellen Sie sicher, dass [installiert haben und Ausführen des Remotedebuggers](../debugger/remote-debugging.md). Wenn die Nachricht über eine Firewall erwähnt, stellen Sie sicher die [Ports in der Firewall beheben](../debugger/remote-debugger-port-assignments.md) geöffnet sind, insbesondere dann, wenn Sie eine Drittanbieter-Firewall verwenden.
- Wenn Sie eine Datei "HOSTS" verwenden, stellen Sie sicher, dass er richtig konfiguriert ist. Angenommen, Debuggen mit **F5** (anstelle von **an den Prozess anhängen**), die HOSTS-Datei muss die gleiche URL wie in den Projekteigenschaften enthalten **Eigenschaften > Web > Server**  oder **Eigenschaften > Debuggen**, je nach Art Ihres Projekts.

## <a name="server_error"></a> Der Remoteserver hat einen Fehler zurückgegeben.

Überprüfen Sie Ihre [IIS-Protokolldatei](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) Fehler Untercodes und Weitere Informationen und dieses IIS 7 [Blogbeitrag](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Darüber hinaus sind hier einige der allgemeinen Fehlercodes und einige Vorschläge.
- (403) Unzulässig. Es gibt viele mögliche Ursachen für diesen Fehler, überprüfen Sie daher Ihre Protokolldatei und die IIS-Sicherheitseinstellungen für die Website. Stellen Sie sicher, dass der Server die Datei "Web.config" enthält `debug=true` in das Compilation-Element. Stellen Sie sicher, dass Ihre Web Application-Ordner die richtigen Berechtigungen verfügt und die Anwendungspool-Konfiguration richtig ist (ein Kennwort möglicherweise geändert haben). Finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck). Wenn diese Einstellungen bereits korrekt sind, und Sie lokal debuggen, auch überprüfen, ob Sie mit dem richtigen Server-Typ und URL herstellen (in **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**, Je nach Projekttyp).
- (503) Server nicht verfügbar. Der Anwendungspool möglicherweise aufgrund einer Änderung Fehler oder die Konfiguration beendet. Starten Sie den Anwendungspool neu.
- (404) Nicht gefunden. Stellen Sie sicher, dass der Anwendungspool für die richtige Version von ASP.NET konfiguriert ist.

## <a name="aspnet"></a> Debuggen von ASP.NET konnte nicht gestartet

- Starten Sie den Anwendungspool, und setzen Sie IIS zurück. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).
- Wenn Sie URL-Umschreibungen durchführen, testen Sie eine einfache Web.config-Datei mit den Umschreibungen keine URL. Finden Sie unter den **Hinweis** über die URL-Rewrite-Modul in [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen.

Wenn Sie lokal debuggen, kann dieser Fehler auftreten, da Visual Studio eine 32-Bit-Anwendung ist, und die 64-Bit-Version des Remotedebuggers zum Debuggen von 64-Bit-Anwendungen verwendet. Öffnen Sie die Projekteigenschaften, und stellen Sie sicher, dass das Projekt für die Verbindung mit den richtigen Webserver und die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** je nach Projekttyp.)

Wenn Sie eine Datei "HOSTS" verwenden, stellen Sie außerdem sicher, dass er richtig konfiguriert ist. Z. B. die HOSTS-Datei muss die gleiche URL wie in den Projekteigenschaften enthalten **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**, je nach Art Ihres Projekts.

## <a name="see_help"></a> In der Hilfe werden häufige Konfigurationsfehler erläutert. Die Webseite außerhalb des Debuggers ausgeführt, kann weitere Informationen bereitstellen.

- Führen Sie Visual Studio und dem Webserver auf demselben Computer aus? Öffnen Sie die Projekteigenschaften, und stellen Sie sicher, dass das Projekt zum Verbinden mit dem richtigen Webserver, und starten die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** je nach Projekttyp.)

- Wenn, das funktioniert nicht, oder Sie Remote Debuggen, führen Sie die Schritte [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Überprüfen Sie die IIS-Konfiguration

Unter Berücksichtigung der hier angegebenen Schritte zur Behebung des Problems und vor dem erneuten Versuch zum Debuggen müssen Sie auch IIS zurücksetzen. Sie können dies durch eine Eingabeaufforderung mit erhöhten Rechten öffnen und eingeben `iisreset`.

* Beenden und starten Sie Ihre IIS-Anwendungspools neu, und wiederholen Sie dann.

    Der Anwendungspool möglicherweise aufgrund eines Fehlers beendet. Oder möglicherweise eine andere Änderung der Konfiguration, die Sie vorgenommen haben, beenden und starten Sie den Anwendungspool neu.

    > [!NOTE]
    > Wenn der Anwendungspool beendet wird, müssen Sie möglicherweise das URL-Rewrite-Modul in der Systemsteuerung deinstallieren. Sie können es mit dem Webplattform-Installer (WebPI) installieren. Dieses Problem kann nach einem Upgrade beträchtliche Systemressourcen auftreten.

* Überprüfen Sie die Konfiguration des Anwendungspools, korrigieren Sie ihn bei Bedarf, und wiederholen Sie dann.

    Der Anwendungspool kann für eine Version von ASP.NET konfiguriert werden, die nicht mit Visual Studio-Projekts übereinstimmt. Aktualisieren Sie die ASP.NET-Version im Anwendungspool, und starten Sie ihn neu. Ausführliche Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Auch wenn Kennwortanmeldeinformationen geändert haben, müssen Sie sie in Ihrem Anwendungspool oder die Website zu aktualisieren.  In den Anwendungspool Aktualisieren von Anmeldeinformationen in **Advanced Settings > Prozessmodell > Identität**. Für die Website aktualisieren von Anmeldeinformationen in **Grundeinstellungen > Verbinden als...** . Starten Sie den Anwendungspool neu.

* Überprüfen Sie, dass Ihre Web Application-Ordner die richtigen Berechtigungen verfügt.

    Stellen Sie sicher, dass Sie IIS_IUSRS, IUSR-Konto, oder den bestimmte Benutzer zugeordneten der [Anwendungspool](/iis/manage/configuring-security/application-pool-identities) Read- und execute-Berechtigungen für Ordner der Web-Anwendung. Beheben Sie das Problem, und starten Sie den Anwendungspool neu.

* Stellen Sie sicher, dass die richtige Version von ASP.NET in IIS installiert ist.

    Nicht übereinstimmende Versionen von ASP.NET auf IIS und in Visual Studio-Projekts können dazu führen, dass dieses Problem. Sie müssen möglicherweise die Framework-Version in der Datei "Web.config" festgelegt. Verwenden Sie zum Installieren von ASP.NET in IIS die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Siehe auch [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in IIS für die Authentifizierung konfiguriert ist, schlägt diese Authentifizierung fehl. Um dieses Problem zu beheben, können Sie den Namen des Remotecomputers anstelle der IP-Adresse angeben.

## <a name="other-causes"></a>Andere Ursachen

Wenn die IIS-Konfiguration nicht das Problem verursacht hat, versuchen Sie diese Schritte aus:

- Starten Sie Visual Studio mit Administratorrechten aus, und versuchen Sie es noch mal.

    Einige ASP.NET Debugszenarien wie die Verwendung von Web Deploy sind erhöhte Rechte für Visual Studio erforderlich.

- Wenn mehrere Instanzen von Visual Studio ausführen, öffnen Sie Ihr Projekt in einer Instanz von Visual Studio (mit Administratorrechten), und versuchen Sie es erneut.

- Wenn Sie eine Datei "HOSTS" mit lokalen Adressen verwenden, versuchen Sie, statt die Loopback-Adresse, die IP-Adresse des Computers.

    Wenn Sie lokale Adressen nicht verwenden, stellen Sie sicher, dass die Datei "HOSTS" enthält die gleiche URL wie in den Projekteigenschaften **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**, je nach Ihrer der Projekttyp.

## <a name="more-troubleshooting-steps"></a>Weitere Schritte

* Fahren Sie die Localhost-Seite im Browser auf dem Server.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.

     Weitere Informationen zum Bereitstellen in IIS finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) und für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Erstellen Sie eine einfache ASP.NET-Anwendung auf dem Server (oder verwenden Sie eine einfache web.config-Datei).

    Wenn Sie Ihre app mit dem Debugger funktioniert nicht, versuchen Sie es erstellen eine grundlegende ASP.NET-Anwendung lokal auf dem Server, und versuchen, die grundlegende app zu debuggen. (Sie können die standardmäßige ASP.NET MVC-Vorlage verwenden möchten.) Wenn Sie eine einfache app Debuggen können, kann, mit denen Sie bestimmen, welche Elemente sich zwischen den beiden Konfigurationen. Suchen Sie nach der Unterschiede in den Einstellungen in der Datei "Web.config" ein, z. B. URL rewrite-Regeln gelten.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)