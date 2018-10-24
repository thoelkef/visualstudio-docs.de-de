---
title: Remote Debuggen von ASP.NET auf einem Remotecomputer mit IIS-Computer | Microsoft-Dokumentation
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
ms.openlocfilehash: 1a13488f632e3cf1f244449b2a7a4dbfd7869428
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826505"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS-Computer
Um eine ASP.NET-Anwendung debuggen, die in IIS bereitgestellt wurde, installieren Sie und führen Sie die Remoteserver-Verwaltungstools auf dem Computer, in dem Sie Ihre app bereitgestellt haben, und fügen Sie dann auf der ausgeführten app in Visual Studio.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Dieses Handbuch wird erläutert, wie einrichten und konfigurieren Sie eine Visual Studio 2017 ASP.NET MVC 4.5.2-Anwendung, in IIS bereitstellen, und fügen Sie den Remotedebugger in Visual Studio.

> [!NOTE]
> Klicken Sie auf den Remotecomputer stattdessen Debuggen von ASP.NET Core, finden Sie unter [Remote Debuggen von ASP.NET Core auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Für Azure App Service Sie ganz einfach bereitstellen und Debuggen auf einer vorkonfigurierten Instanz von IIS entweder können die [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 erforderlich) oder durch [das Anfügen des Debuggers im Server-Explorer](../debugger/remote-debugging-azure.md).

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2, die Server Schritte unterscheiden sich)

## <a name="requirements"></a>Anforderungen

Der Remotedebugger wird auf Windows Server ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debuggen zwischen zwei Computern über einen Proxy verbunden sind, wird nicht unterstützt. Debuggen über eine hohe Latenz oder die Verbindung mit geringer Bandbreite, wie z. B. DFÜ, Internet oder über das Internet in Ländern wird nicht empfohlen und möglicherweise fehl oder unzumutbar langsam werden.

## <a name="app-already-running-in-iis"></a>App, die bereits in IIS ausgeführt werden?

Dieser Artikel enthält Schritte zum Einrichten einer Standardkonfiguration von IIS unter Windows Server und das Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass der Server, dass die app ordnungsgemäß ausgeführt werden kann und Sie bereit, remote zu debuggen sind installierte Komponenten erforderlich ist.

* Wenn Ihre app in IIS ausgeführt wird und Sie wollen den Remotedebugger herunterladen und mit dem Debuggen beginnen, navigieren zu [herunterladen und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie Hilfe, um sicherzustellen, dass Ihre app bereitgestellt eingerichtet wurde, anzeigen möchten und ordnungsgemäß in IIS ausgeführt, damit Sie debuggen können, befolgen alle Schritte in diesem Thema.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen von ASP.NET 4.5.2 auf Visual Studio-Computer
  
1. Erstellen Sie eine neue MVC ASP.NET-Anwendung. (**Datei > Neu > Projekt**, und wählen Sie dann <strong>Visual C# > Web > ASP.NET-Webanwendung. In der **ASP.NET 4.5.2</strong> -Vorlagenabschnitt wählen **MVC**. Stellen Sie sicher, dass **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierung** nastaven NA hodnotu **keine Authentifizierung**. Nennen Sie das Projekt **MyASPApp**.)

2. Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()` -Methode fest.

## <a name="bkmk_configureIIS"></a> Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Browser-Sicherheitseinstellungen auf Windows Server aktualisieren

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen als vertrauenswürdige Sites, um einige der Web-Server-Komponenten herunterladen können hinzufügen. Der vertrauenswürdigen Sites hinzufügen, indem Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Websites**. Fügen Sie den folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen zu erteilen. Einige dieser Ressourcen sind nicht erforderlich, jedoch zur Vereinfachung des Prozesses, klicken Sie auf **hinzufügen** Aufforderung.

## <a name="BKMK_deploy_asp_net"></a> Installieren Sie ASP.NET 4.5 auf WindowsServer

Weitere ausführliche Informationen zum Installieren von ASP.NET in IIS, finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.

1. Verwenden Sie den Webplattform-Installer (WebPI) installieren Sie ASP.NET 4.5 (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl aus:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Das System neu starten (oder führen Sie **net Stop was/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung an den Systempfad zu übernehmen).

## <a name="choose-a-deployment-option"></a>Wählen Sie eine Bereitstellungsoption

Wenn Sie Hilfe benötigen, um die app in IIS bereitzustellen, sollten Sie diese Optionen:

* Erstellen eine Datei mit veröffentlichungseinstellungen in IIS, und importieren die Einstellungen in Visual Studio bereitstellen. In einigen Szenarien ist dies eine schnelle Möglichkeit zum Bereitstellen Ihrer app. Wenn Sie die Datei mit veröffentlichungseinstellungen erstellen, werden Berechtigungen automatisch in IIS festgelegt.

* Veröffentlichen in einen lokalen Ordner, und Kopieren der Ausgabe von einer bevorzugten Methode in einem vorbereiteten app-Ordner auf IIS bereitstellen.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Bereitstellen Sie über eine Datei mit veröffentlichungseinstellungen

Verwenden Sie diese Option erstellen Sie eine Datei mit veröffentlichungseinstellungen aus, und klicken Sie in Visual Studio importieren.

> [!NOTE]
> Diese Methode der Bereitstellung wird die Web Deploy verwendet. Wenn Sie Web Deploy manuell in Visual Studio zu konfigurieren, anstatt die Einstellungen importieren möchten, können Sie Web bereitstellen 3.6 anstelle von Web-bereitstellen-3.6 für Hostserver installieren. Jedoch, wenn Sie Web Deploy manuell konfigurieren, Sie müssen sicherstellen, dass ein app-Ordner auf dem Server mit den richtigen Werten und die Berechtigungen konfiguriert ist (siehe [ASP.NET-Website konfigurieren](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hostserver unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen Sie die Datei mit veröffentlichungseinstellungen in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Die Einstellungen für die Veröffentlichung in Visual Studio importieren und bereitstellen

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die app erfolgreich bereitgestellt wurde, sollten sie automatisch gestartet. Wenn die app aus Visual Studio nicht gestartet wird, starten Sie die app in IIS.

1. In der **Einstellungen** (Dialogfeld), aktivieren Sie Debuggen, indem Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie dann **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie Debuggen in der *"Web.config"* -Datei, wenn Sie veröffentlichen.

1. Klicken Sie auf **speichern** , und klicken Sie dann die app erneut veröffentlichen.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Durch die Veröffentlichung in einen lokalen Ordner bereitstellen

Sie können diese Option verwenden, um Ihre app bereitzustellen, wenn Sie die app in IIS mithilfe von Powershell RoboCopy kopieren möchten, oder Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem Sie später das ASP.NET-Projekt bereitstellen.

2. Wenn sie nicht bereits geöffnet ist, öffnen Sie die **(Internet Information Services, IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** wechseln Sie im linken Bereich zu **Websites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischer Pfad** zu **C:\Publish**.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardwert-Anwendungspool (**DefaultAppPool**), und legen Sie die **physischer Pfad** zu  **C:\Publish**.

7. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist eine Option für den Anwendungspool nicht).

8. Wählen Sie den Standort ausgewählt im IIS-Manager, **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie als Benutzer mit Lesen & Ausführen an IUSR-Konto hinzu.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der app in einen lokalen Ordner durch die Veröffentlichung von Visual Studio

Sie können auch veröffentlichen und Bereitstellen der app, die über das Dateisystem oder andere Tools.

1. (ASP.NET 4.5.2) Stellen Sie sicher, dass die Datei "Web.config" die richtige Version von .NET Framework aufgeführt.  Wenn Sie ASP.NET 4.5.2 verwenden möchten, stellen Sie beispielsweise sicher, dass diese Version in der Datei "Web.config" aufgeführt ist.
  
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

## <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server

In diesem Tutorial verwenden wir Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a> Richten Sie den Remotedebugger unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie zum Hinzufügen von Berechtigungen für weitere Benutzer: des Authentifizierungsmodus ändern oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Weitere Informationen zu den Remotedebugger als Dienst ausführen, finden Sie unter [führen Sie den Remotedebugger als Dienst](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Computer Visual Studio die Projektmappe, die Sie debuggen möchten (**MyASPApp** , wenn Sie die Schritte in diesem Artikel folgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 können Sie an denselben Prozess, die Sie zuvor mit angefügte Anfügen **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P). 

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4022**.
4. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse, die nicht angezeigt wird, versuchen Sie den Namen des Remotecomputers (der Port ist erforderlich.) anstelle der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse zu erhalten.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
6. Geben Sie den ersten Buchstaben eines Prozessnamens schnell und problemlos suchen **w3wp.exe** für ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**

8. Öffnen Sie die Website des Remotecomputers. Wechseln Sie in einem Browser zu **http://\<Remotecomputernamen >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="bkmk_openports"></a> Problembehandlung: Erforderliche Ports für Windows Server öffnen

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Allerdings müssen Sie sicherstellen, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Erforderliche Ports:

- 80 - wird für IIS erforderlich.
- 8172 – (Optional) erforderlich für Web Deploy, um die app aus Visual Studio bereitstellen
- 4022 – erforderlich für das Remotedebuggen von Visual Studio 2017 (finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) ausführliche Informationen.
- UDP 3702 - erkennungsport (Optional) können Sie die **finden** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

1. Öffnen Sie zum Öffnen eines Ports in Windows Server die **starten** Menü, und suchen Sie **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **Eingangsregeln > neue Regel > Port**. Wählen Sie **Weiter** und wählen Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer, und klicken Sie auf **Weiter**, klicken Sie dann **Verbindung zulassen,**, klicken Sie auf Weiter, und Fügen Sie den Namen (**IIS**, **Web Deploy**, oder **"msvsmon"**) für die eingehende Regel.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports an.