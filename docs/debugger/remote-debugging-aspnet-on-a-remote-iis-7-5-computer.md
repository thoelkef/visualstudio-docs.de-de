---
title: Remote Debuggen von ASP.NET auf einem Remote-IIS-Computer | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: dddbe20c36aac6bc1c21cc2e29e59231c5b8feaf
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remote-IIS-Computer
Um eine ASP.NET-Anwendung debuggen, die in IIS bereitgestellt wurde, installieren Sie und führen Sie der Remotetools auf dem Computer aus, auf denen Sie Ihre app bereitgestellt haben, und fügen Sie an der ausgeführten app aus Visual Studio.

![Remotedebugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Dieses Handbuch erläutert das Einrichten eine Visual Studio 2017 ASP.NET MVC 4.5.2-Anwendung, für IIS bereitstellen und Konfigurieren von Visual Studio remote Debugger anfügen.

> [!NOTE]
> Zur Remote Debuggen von ASP.NET Core stattdessen, wie unter [Remote Debuggen ASP.NET Core auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Für Azure App Service, können Sie bereitstellen und Debuggen auf einer vorkonfigurierten Instanz von IIS mithilfe der [Momentaufnahme Debugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 erforderlich) oder durch [das Anfügen des Debuggers aus Server-Explorer](../debugger/remote-debugging-azure.md).

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2 Server die Schritte sind verschiedene)

## <a name="requirements"></a>Anforderungen

Der Remotedebugger wird unter Windows Server ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debuggen zwischen zwei Computern über einen Proxy verbunden wird nicht unterstützt. Remotedebuggen über eine hohe Latenz oder eine Verbindung mit geringer Bandbreite, z. B. DFÜ, Internet oder über das Internet Ländern wird nicht empfohlen und möglicherweise fehl oder sehr langsam sein.

## <a name="app-already-running-in-iis"></a>App, die bereits in IIS ausgeführt werden?

Dieser Artikel enthält die Schritte zum Einrichten einer Standardkonfiguration von IIS unter WindowsServer und zum Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass der Server installierte ist –, dass die app ordnungsgemäß ausgeführt werden kann, und Sie Remotedebuggen werden Komponenten erforderlich ist.

* Wenn Ihre app in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und starten Sie das Debuggen, wechseln zur möchten [herunterladen und installieren Sie die Remoteserver-Verwaltungstools für Windows Server](#BKMK_msvsmon).

* Wenn Sie Hilfe, um sicherzustellen, dass Ihre app bereitgestellt eingerichtet wird, und ordnungsgemäß in IIS ausgeführt, um Sie zu debuggen, führen Sie alle Schritte in diesem Thema.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen Sie die ASP.NET 4.5.2 Anwendung auf dem Visual Studio-Computer
  
1. Erstellen Sie eine neue MVC ASP.NET-Anwendung. (**Datei > Neu > Projekt**, und wählen Sie dann ** Visual c# > Web > ASP.NET-Webanwendung. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC**aus. Stellen Sie sicher, dass **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierung** festgelegt ist, um **keine Authentifizierung**. Nennen Sie das Projekt **MyASPApp**.)

2. Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()` -Methode fest.

## <a name="bkmk_configureIIS"></a> Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen hinzufügen, als vertrauenswürdigen Sites ermöglichen Ihnen, einige Web-Server-Komponenten herunterzuladen. Fügen Sie der vertrauenswürdigen Sites hinzu, durch das Aufrufen **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. Einige dieser Ressourcen sind nicht erforderlich, aber den Prozess zu vereinfachen, klicken Sie auf **hinzufügen** Aufforderung.

## <a name="BKMK_deploy_asp_net"></a> Installieren Sie ASP.NET 4.5 unter WindowsServer

Wenn Sie ausführlichere Informationen zur ASP.NET auf IIS installieren möchten, finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.

1. Verwenden Sie den Webplattform-Installer (WebPI), um ASP.NET 4.5 installieren (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

## <a name="choose-a-deployment-option"></a>Wählen Sie eine Bereitstellungsoption

Wenn Sie Hilfe benötigen, auf die app unter IIS bereitzustellen, sollten Sie diese Optionen:

* Erstellen eine Datei mit veröffentlichungseinstellungen in IIS, und Importieren der Einstellungen in Visual Studio bereitstellen. In einigen Szenarien ist dies eine schnelle Möglichkeit zum Bereitstellen Ihrer app. Wenn Sie die Datei mit veröffentlichungseinstellungen erstellen, werden Berechtigungen automatisch in IIS festgelegt.

* Veröffentlichen in einen lokalen Ordner, und kopieren die Ausgabe durch eine bevorzugte Methode auf eine vorbereitete Anwendungsordners auf IIS bereitstellen.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Die Bereitstellung über eine Datei mit veröffentlichungseinstellungen

Verwenden Sie diese Option können Sie eine Datei mit veröffentlichungseinstellungen zu erstellen und importieren Sie es in Visual Studio.

> [!NOTE]
> Diese Bereitstellungsmethode verwendet Web Deploy. Wenn Sie Web Deploy manuell in Visual Studio zu konfigurieren, anstatt die Einstellungen importieren möchten, können Sie Web bereitstellen 3.6 statt Web bereitstellen 3.6 für Hosting-Server installieren. Jedoch, wenn Sie Web Deploy manuell konfigurieren, Sie müssen sicherstellen, dass ein app-Ordners auf dem Server mit den richtigen Werten und die Berechtigungen konfiguriert ist (siehe [ASP.NET-Website konfigurieren](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hosting-Server unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt hat, sollte er automatisch gestartet. Wenn die app aus Visual Studio nicht gestartet wird, starten Sie die app in IIS.

1. In der **Einstellungen** (Dialogfeld), aktivieren Sie Debuggen, indem Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie dann **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie Debuggen in der *"Web.config"* beim Veröffentlichen der Datei.

1. Klicken Sie auf **speichern** und veröffentlichen Sie die app erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Durch die Veröffentlichung in einen lokalen Ordner bereitstellen

Sie können diese Option verwenden, zum Bereitstellen Ihrer app, wenn Sie so kopieren Sie die app in IIS mithilfe von Powershell RoboCopy, oder Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem ASP.NET-Projekt später bereitstellen möchten.

2. Wenn es nicht bereits geöffnet ist, öffnen Sie die **(Internet Information Services, IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** im linken Bereich, wechseln Sie zu **Sites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischen Pfad** auf **C:\Publish**.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardnamen Anwendungspool (**DefaultAppPool**), und legen Sie die **physischen Pfad** auf  **C:\Publish**.

7. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist keine Option für den Anwendungspool).

8. Mit den Standort im IIS-Manager ausgewählt haben, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie IUSR als ein Benutzer Berechtigungen für Lesen & ausführen.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der Anwendung in einen lokalen Ordner durch die Veröffentlichung aus Visual Studio

Sie können auch veröffentlichen und Bereitstellen der app mit dem Dateisystem oder anderen Tools.

1. (ASP.NET 4.5.2) Stellen Sie sicher, dass die Datei "Web.config" die richtige Version von .NET Framework aufgeführt.  Wenn Sie ASP.NET 4.5.2 abzielen, stellen Sie beispielsweise sicher, dass diese Version in der Datei "Web.config" aufgeführt ist.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Beispielsweise sollte die Version 4.0, bei der Installation von ASP.NET 4 statt 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools für Windows Server

In diesem Lernprogramm verwenden wir 2017 von Visual Studio.

Wenn Sie die Seite zu öffnen, mit dem Remotedebugger Download Probleme haben, finden Sie unter [entsperren den Dateidownload](../debugger/remote-debugging.md#unblock_msvsmon) um Hilfe zu erhalten.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten, führen Sie den Remotedebugger aus einer Dateifreigabe sein. Weitere Informationen finden Sie unter [führen Sie den Remotedebugger aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie benötigen Berechtigungen für zusätzliche Benutzer hinzufügen ändern den Authentifizierungsmodus oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Informationen zu den Remotedebugger als Dienst ausführen, finden Sie unter [den Remotedebugger als Dienst ausführen](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die **MyASPApp** Lösung.
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie erneut mit dem gleichen Prozess, die Sie zuvor angefügt mit **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse nicht angezeigt wird, versuchen Sie die IP-Adresse anstelle des remote-Computer (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse abzurufen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
6. Geben Sie den ersten Buchstaben des Namens eines Prozesses, schnell zu finden **w3wp.exe** für ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser auf **http://\<Remotecomputername >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="bkmk_openports"></a> Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Installationen werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Allerdings müssen Sie möglicherweise stellen Sie sicher, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 8172 – (Optional) erforderlich für Web Deploy zum Bereitstellen der app aus Visual Studio
- 4022 - erforderlich, für das Remotedebuggen aus Visual Studio 2017 (finden Sie unter [-Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) ausführliche Informationen.
- UDP 3702 - erkennungsport (Optional) ermöglicht es Ihnen, die **suchen** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

1. Um einen Port unter Windows Server zu öffnen, öffnen die **starten** Menü, suchen Sie nach **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **eingehende Regeln > neue Regel > Port**. Wählen Sie **Weiter** und wählen Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer an, klicken Sie auf **Weiter**, klicken Sie dann **Verbindung zulassen**, klicken Sie auf Weiter, und Fügen Sie den Namen (**IIS**, **Web Deploy**, oder **Msvsmon**) für die eingehende Regel.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.