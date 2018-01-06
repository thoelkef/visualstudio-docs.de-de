---
title: 'Fehler: Debuggen kann nicht auf dem Webserver | Microsoft Docs'
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7d09deda1aa2b24fba90f9d9d417917c5b284ad
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Fehler: Das Debuggen kann auf dem Webserver nicht gestartet werden

Wenn Sie versuchen, eine ASP.NET-Anwendung auf einem Webserver zu debuggen, erhalten Sie möglicherweise diese Fehlermeldung wird ausgegeben: `Unable to start debugging on the Web server`.

Häufig tritt dieser Fehler auf, da ein Fehler oder die Konfiguration geändert wurde, die ein Update auf Ihre Anwendungspools und/oder eine IIS-Rücksetzung erforderlich ist. Sie können IIS zurücksetzen, indem Sie eine Eingabeaufforderung mit erhöhten Rechten öffnen und Folgendes eingeben: `iisreset`. 

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to start debugging on the Web server` Nachricht ist generisch. In der Regel ist eine spezifische Nachricht in die Fehlerzeichenfolge enthalten, und, die können Sie die Ursache des Problems oder Suche für eine genauere Korrektur zu identifizieren. Hier sind einige der häufigsten Fehlermeldungen, die die wichtigsten Fehlermeldung angefügt sind:

- [Listet IIS eine Website, die den Start entspricht nicht Url](#IISlist)
- [Der Webserver ist nicht ordnungsgemäß konfiguriert.](#web_server_config)
- [Keine Verbindung mit dem Webserver herstellen](#unabletoconnect)
- [Der Webserver hat nicht rechtzeitig reagiert.](#webservertimeout)
- [Die Microsoft visual Studio Remotedebuggen monitor(msvsmon.exe) scheint nicht auf dem Remotecomputer ausgeführt werden](#msvsmon)
- [Der Remoteserver hat einen Fehler zurückgegeben.](#server_error)
- [Debuggen von ASP.NET konnte nicht gestartet](#aspnet)
- [Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen.](#cannot_connect)
- [Finden Sie Hilfe für häufige Konfigurationsfehler erläutert. Die Webseite außerhalb des Debuggers ausgeführt möglicherweise weitere Informationen bereit.](#see_help)

## <a name="IISlist"></a>Listet IIS eine Website, die den Start entspricht nicht Url

- Starten Sie Visual Studio als Administrator aus, und wiederholen Sie debuggen. (Einige Debugszenarien ASP.NET ist erhöhte Rechte erforderlich.)

    Sie können konfigurieren, dass Visual Studio mit der rechten Maustaste in der Visual Studio Symbol "Verknüpfung", immer als Administrator ausführen auswählen **Eigenschaften > erweitert**, und klicken Sie dann angeben, dass immer als Administrator ausführen.

## <a name="web_server_config"></a>Der Webserver ist nicht ordnungsgemäß konfiguriert.

- Finden Sie unter [Fehler: der Webserver ist nicht richtig konfiguriert](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>Keine Verbindung mit dem Webserver herstellen

- Sind Sie mit Visual Studio und den Webserver auf demselben Computer ausführen und Debuggen mit **F5** (anstelle von **an den Prozess anhängen**)? Öffnen Sie die Projekteigenschaften fest, und stellen Sie sicher, dass das Projekt zum Herstellen einer Verbindung mit dem richtigen Web-Server, und starten die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** Abhängigkeit vom Projekttyp. Für eine Web Forms-Projekt öffnen **Eigenschaftenseiten > Startoptionen > Server**.)

- Andernfalls starten Sie den Anwendungspool neu, und setzen Sie IIS zurück. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>Der Webserver hat nicht rechtzeitig reagiert.

- Setzen Sie IIS zurück, und wiederholen Sie dann debuggen. Mehrere Instanzen der Debugger möglicherweise an den IIS-Prozess angefügt werden; Zurücksetzen ein beendet werden. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a>Die Microsoft visual Studio Remotedebuggen monitor(msvsmon.exe) scheint nicht auf dem Remotecomputer ausgeführt werden

- Wenn Sie auf einem Remotecomputer debuggen, stellen Sie sicher, dass [installiert und den Remotedebugger ausführen](../debugger/remote-debugging.md). Wenn die Nachricht eine Firewall erwähnt, stellen Sie sicher, dass die [beheben Sie Ports in der Firewall](../debugger/remote-debugger-port-assignments.md) geöffnet sind, insbesondere dann, wenn Sie eine Drittanbieter-Firewall verwenden.
- Wenn Sie eine HOSTS-Datei verwenden, stellen Sie sicher, dass er ordnungsgemäß konfiguriert ist. Angenommen, Debuggen mit **F5** (anstelle von **an den Prozess anhängen**), die HOSTS-Datei muss die gleichen Projekt-URL wie in den Projekteigenschaften enthalten **Eigenschaften > Web > Server**  oder **Eigenschaften > Debuggen**vom Projekttyp abhängig.

## <a name="server_error"></a>Der Remoteserver hat einen Fehler zurückgegeben.

Überprüfen Sie den Fehlercode, der in der Nachricht, um die Ursache des Problems zu identifizieren zurückgegeben wird. Hier sind einige häufige Fehlercodes.
- ("403 Forbidden)". Stellen Sie sicher, dass Sie mit dem richtigen Server-Typ und URL herstellen (in **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**vom Projekttyp abhängig). Stellen Sie auch sicher, dass der Server "Web.config" enthält `debug=true` in das Compilation-Element. Wenn diese Einstellungen bereits korrekt sind, stellen Sie sicher, dass Ihr Web Application-Ordner die richtigen Berechtigungen verfügt. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).
- (503) Server nicht verfügbar. Der Anwendungspool möglicherweise aufgrund einer Änderung der Fehler oder die Konfiguration beendet. Starten Sie den Anwendungspool neu.
- (404) nicht gefunden. Stellen Sie sicher, dass der Anwendungspool für die richtige Version von ASP.NET konfiguriert ist.

## <a name="aspnet"></a>Debuggen von ASP.NET konnte nicht gestartet

- Starten Sie den Anwendungspool, und setzen Sie IIS zurück. Weitere Informationen finden Sie unter [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).
- Wenn Sie das URL-schreibt durchführen, testen Sie grundlegende "Web.config" mit keine URL ständig neu geschrieben. Finden Sie unter der **Hinweis** schreiben Sie zur URL-Modul im [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a>Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen.

Wenn Sie lokal debuggen, kann dieser Fehler auftreten, da Visual Studio eine 32-Bit-Anwendung ist, sodass sie die 64-Bit-Version des Remotedebuggers Debuggen von 64-Bit-Anwendungen verwendet. Öffnen Sie die Projekteigenschaften fest, und stellen Sie sicher, dass das Projekt für die Verbindung mit den richtigen Webserver und die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** Abhängigkeit vom Projekttyp.)

Wenn Sie eine HOSTS-Datei verwenden, stellen Sie außerdem sicher, dass er ordnungsgemäß konfiguriert ist. Angenommen, die HOSTS-Datei muss die gleichen Projekt-URL wie in den Projekteigenschaften enthalten **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**vom Projekttyp abhängig.

## <a name="see_help"></a>Finden Sie Hilfe für häufige Konfigurationsfehler erläutert. Die Webseite außerhalb des Debuggers ausgeführt möglicherweise weitere Informationen bereit.

- Sind Sie Visual Studio und dem Webserver auf demselben Computer ausgeführt? Öffnen Sie die Projekteigenschaften fest, und stellen Sie sicher, dass das Projekt zum Herstellen einer Verbindung mit dem richtigen Web-Server, und starten die URL konfiguriert ist. (Öffnen **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen** Abhängigkeit vom Projekttyp.)

- Wenn, die funktioniert nicht, oder Sie Remote Debuggen, führen Sie die Schritte [überprüfen Sie die IIS-Konfiguration](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a>Überprüfen Sie die IIS-Konfiguration

Nach der Schritte zur Behebung des Problems hier detailliert, und versuchen Sie es noch debuggen müssen Sie möglicherweise auch IIS zurücksetzen. Sie können dies vornehmen, indem Sie eine Eingabeaufforderung mit erhöhten Rechten öffnen und Folgendes eingeben: `iisreset`. 

* Beenden und starten Sie die IIS-Anwendungspools neu, und wiederholen Sie dann. 

    Der Anwendungspool möglicherweise aufgrund eines Fehlers beendet. Oder möglicherweise eine andere Konfiguration ändern, die Sie vorgenommen haben, zu beenden und starten Sie den Anwendungspool neu.
    
    > [!NOTE]
    > Wenn der Anwendungspool beenden, hält, müssen Sie möglicherweise das URL-Rewrite-Modul in der Systemsteuerung deinstallieren. Sie können ihn mit dem Webplattform-Installer (WebPI) installieren. Dieses Problem kann nach einem Systemupgrade erhebliche auftreten.

* Überprüfen Sie die Konfiguration des Anwendungspools, korrigieren Sie ihn bei Bedarf, und wiederholen Sie dann.

    Der Anwendungspool kann für eine Version von ASP.NET konfiguriert werden, die Visual Studio-Projekt nicht übereinstimmen. Aktualisieren Sie die Version von ASP.NET im Anwendungspool, und starten Sie ihn neu. Ausführliche Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Wenn Anmeldeinformationen geändert haben, müssen Sie auch diese in den Anwendungspool oder die Website zu aktualisieren.  In den Anwendungspool und Aktualisieren von Anmeldeinformationen in **Erweiterte Einstellungen > Prozessmodell > Identität**. Aktualisieren Sie für die Website-Anmeldeinformationen in **Grundeinstellungen > Verbinden als...** . Starten Sie den Anwendungspool neu.
    
* Überprüfen Sie, dass Ihr Web Application-Ordner die richtigen Berechtigungen verfügt.

    Stellen Sie sicher, dass Sie für den Web Application-Ordner Ausführungsrechte und geben IIS_IUSRS, IUSR-Konto oder den bestimmten Benutzer, die die schreibgeschützte Anwendungspool zugeordnet. Beheben Sie das Problem, und starten Sie den Anwendungspool neu.

* Stellen Sie sicher, dass die richtige Version von ASP.NET in IIS installiert ist.

    Nicht übereinstimmende Versionen von ASP.NET auf IIS und in Visual Studio-Projekt können dieses Problem verursachen. Sie müssen möglicherweise die Framework-Version in der Datei "Web.config" festlegen. Verwenden Sie zum Installieren von ASP.NET auf IIS die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Siehe auch [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Beheben Sie Authentifizierungsfehler, wenn Sie nur die IP-Adresse verwenden

     Standardmäßig wird davon ausgegangen, dass IP-Adressen dem Internet zuzuordnen sind, während die NTLM-Authentifizierung nicht über das Internet vorgenommen wird. Wenn Ihre Website in IIS eine Authentifizierung erforderlich konfiguriert ist, schlägt diese Authentifizierung fehl. Um dieses Problem zu beheben, können Sie den Namen des Remotecomputers anstelle der IP-Adresse angeben.
     
## <a name="other-causes"></a>Andere Ursachen

Wenn die IIS-Konfiguration nicht das Problem verursacht, probieren Sie diese Schritte aus:

- Starten Sie Visual Studio mit Administratorrechten, und versuchen Sie es erneut.

    Einige ASP.NET Debugszenarien z. B. mithilfe von Web Deploy erfordern erhöhten für Visual Studio.
    
- Wenn mehrere Instanzen von Visual Studio ausführen, öffnen Sie das Projekt in einer Instanz von Visual Studio (mit Administratorrechten), und wiederholen Sie den Vorgang.

- Bei Verwendung eine HOSTS-Datei mit lokalen Adressen versuchen Sie es mit der Loopback-Adresse anstelle des Computers die IP-Adresse.

    Wenn Sie lokale Adressen nicht verwenden, stellen Sie sicher, dass die HOSTS-Datei enthält die gleichen Projekt-URL wie in den Projekteigenschaften **Eigenschaften > Web > Server** oder **Eigenschaften > Debuggen**, abhängig von Ihrer Projekttyp.

## <a name="more-troubleshooting-steps"></a>Weitere Schritte zur Problembehandlung

* Schalten Sie die Seite "localhost" im Browser auf dem Server.

     Wenn IIS nicht ordnungsgemäß installiert wurde, sollten Fehler angezeigt werden, wenn Sie `http://localhost` in einem Browser eingeben.
     
     Weitere Informationen zum Bereitstellen von für IIS finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) und für ASP.NET Core, [Host unter Windows mit IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Erstellen Sie eine einfache ASP.NET-Anwendung auf dem Server (oder verwenden Sie eine grundlegende "Web.config"-Datei).

    Wenn Sie Ihre app mit dem Debugger funktioniert nicht, erstellen Sie eine einfache ASP.NET-Anwendung lokal auf dem Server, und versuchen Sie, die grundlegende app zu debuggen. (Sie können die Standardeinstellung ASP.NET MVC-Vorlage verwenden möchten.) Wenn Sie eine einfache app Debuggen können, möglicherweise, mit denen Sie ermitteln, was sich zwischen den beiden Konfigurationen unterscheidet. Suchen Sie nach Unterschiede in den Einstellungen in der Datei "Web.config" ein, z. B. URL-rewrite Regeln.

## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)