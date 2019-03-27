---
title: Remotedebuggen für ASP.NET Core auf einem Remotecomputer mit IIS-Computer | Microsoft-Dokumentation
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9d92ebc40fb61be5ddb6125799c07eee3d148551
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355499"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remotedebuggen von ASP.NET Core auf einem Remotecomputer mit IIS-Computer in Visual Studio
Um eine ASP.NET-Anwendung debuggen, die in IIS bereitgestellt wurde, installieren Sie und führen Sie die Remoteserver-Verwaltungstools auf dem Computer, in dem Sie Ihre app bereitgestellt haben, und fügen Sie dann auf der ausgeführten app in Visual Studio.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Dieses Handbuch wird erläutert, wie einrichten und konfigurieren eine Visual Studio ASP.NET Core, in IIS bereitstellen, und fügen Sie den Remotedebugger in Visual Studio. Remotedebuggen von ASP.NET 4.5.2, finden Sie unter [Remotedebuggen von ASP.NET auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Sie können auch bereitstellen und Debuggen in IIS mithilfe von Azure. Für Azure App Service Sie ganz einfach bereitstellen und Debuggen auf einer vorkonfigurierten Instanz von IIS und den Remotedebugger entweder können die [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) oder [das Anfügen des Debuggers im Server-Explorer](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

::: moniker range=">=vs-2019"
Visual Studio-2019 ist erforderlich, die in diesem Artikel gezeigten Schritte.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, die in diesem Artikel gezeigten Schritte ausführen.
::: moniker-end

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* WindowsServer 2016 und IIS 10

## <a name="network-requirements"></a>Netzwerkanforderungen

Debuggen zwischen zwei Computern über einen Proxy verbunden sind, wird nicht unterstützt. Debuggen über eine hohe Latenz oder die Verbindung mit geringer Bandbreite, wie z. B. DFÜ, Internet oder über das Internet in Ländern wird nicht empfohlen und möglicherweise fehl oder unzumutbar langsam werden. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>App, die bereits in IIS ausgeführt werden?

Dieser Artikel enthält Schritte zum Einrichten einer Standardkonfiguration von IIS unter Windows Server und das Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass der Server, dass die app ordnungsgemäß ausgeführt werden kann und Sie bereit, remote zu debuggen sind installierte Komponenten erforderlich ist.

* Wenn Ihre app in IIS ausgeführt wird und Sie wollen den Remotedebugger herunterladen und mit dem Debuggen beginnen, navigieren zu [herunterladen und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie Hilfe, um sicherzustellen, dass Ihre app bereitgestellt eingerichtet wurde, anzeigen möchten und ordnungsgemäß in IIS ausgeführt, damit Sie debuggen können, befolgen alle Schritte in diesem Thema.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen von ASP.NET Core-Anwendung auf dem Visual Studio-computer

1. Erstellen Sie eine neue ASP.NET Core-Webanwendung. 

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio-2019, **STRG + Q** Geben Sie zum Öffnen des Suchfelds **asp.net**, wählen Sie **Vorlagen**, wählen Sie dann **neue ASP.NET Core-Webanwendung erstellen** . Klicken Sie im Dialogfeld, das angezeigt wird, geben Sie dem Projekt **MyASPApp**, und wählen Sie dann **erstellen**. Wählen Sie als Nächstes **Webanwendung (Model-View-Controller)**, und wählen Sie dann **erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > Neu > Projekt**, und wählen Sie dann **Visual C# > Web > ASP.NET Core-Webanwendung**. Wählen Sie im Abschnitt ASP.NET Core-Vorlagen **Webanwendung (Model-View-Controller)**. Stellen Sie sicher, dass ASP.NET Core 2.1 ausgewählt ist, **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierung** nastaven NA hodnotu **keine Authentifizierung**. Nennen Sie das Projekt **MyASPApp**.
    ::: moniker-end

4. Öffnen Sie die Datei About.cshtml.cs und Festlegen eines Haltepunkts in der `OnGet` Methode (in älteren Vorlagen, stattdessen "HomeController.cs" öffnen, und legen Sie den Haltepunkt der `About()` Methode).

## <a name="bkmk_configureIIS"></a> Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Browser-Sicherheitseinstellungen auf Windows Server aktualisieren

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen als vertrauenswürdige Sites, um einige der Web-Server-Komponenten herunterladen können hinzufügen. Der vertrauenswürdigen Sites hinzufügen, indem Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Websites**. Fügen Sie den folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen zu erteilen. Einige dieser Ressourcen sind nicht erforderlich, jedoch zur Vereinfachung des Prozesses, klicken Sie auf **hinzufügen** Aufforderung.

## <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.NET Core unter WindowsServer

1. Installieren Sie das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) auf dem Hostsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Weitere ausführlichen Anweisungen finden Sie [Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*, bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

3. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

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

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die app aus Visual Studio nicht gestartet wird, starten Sie die app in IIS. Für ASP.NET Core müssen Sie sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

1. In der **Einstellungen** (Dialogfeld), aktivieren Sie Debuggen, indem Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie dann **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie Debuggen in der *"Web.config"* -Datei, wenn Sie veröffentlichen.

1. Klicken Sie auf **speichern** , und klicken Sie dann die app erneut veröffentlichen.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Durch die Veröffentlichung in einen lokalen Ordner bereitstellen

Sie können diese Option verwenden, um Ihre app bereitzustellen, wenn Sie die app in IIS mithilfe von Powershell RoboCopy kopieren möchten, oder Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem Sie später das ASP.NET-Projekt bereitstellen.

2. Wenn sie nicht bereits geöffnet ist, öffnen Sie die **(Internet Information Services, IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Klicken Sie unter **Verbindungen** wechseln Sie im linken Bereich zu **Websites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischer Pfad** zu **C:\Publish**.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardwert-Anwendungspool (**DefaultAppPool**), und legen Sie die **physischer Pfad** zu  **C:\Publish**.

6. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **kein verwalteter Code**.

7. Mit der rechten Maustaste in der neuen Website im IIS-Manager, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Zugriff auf die Web-app ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert.

    Wenn Sie einen dieser Benutzer mit Zugriff nicht angezeigt wird, wechseln Sie über die Schritte zum Hinzufügen des IUSR-Konto als Benutzer mit Berechtigungen für Lesen & ausführen.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der app in einen lokalen Ordner durch die Veröffentlichung von Visual Studio

Sie können auch veröffentlichen und Bereitstellen der app, die über das Dateisystem oder andere Tools.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools unter Windows Server

Laden Sie die Version der Remotetools, die Ihrer Version von Visual Studio entspricht.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Richten Sie den Remotedebugger unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie zum Hinzufügen von Berechtigungen für weitere Benutzer: des Authentifizierungsmodus ändern oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Weitere Informationen zu den Remotedebugger als Dienst ausführen, finden Sie unter [führen Sie den Remotedebugger als Dienst](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Computer Visual Studio die Projektmappe, die Sie debuggen möchten (**MyASPApp** , wenn Sie alle Schritte in diesem Artikel folgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 und höheren Versionen, Sie können erneut anfügen an denselben Prozess, die Sie zuvor mit angefügte **Debuggen > an Prozess anfügen...** (Umschalt + Alt + P).

3. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: Port**.

    ::: moniker range=">=vs-2019"
    **\<Name des Remotecomputers >: 4024** 2019 für Visual Studio
    ::: moniker-end
    ::: moniker range="vs-2017"
    **\<Name des Remotecomputers >: 4022** für Visual Studio 2017
    ::: moniker-end
4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse, die nicht angezeigt wird, versuchen Sie den Namen des Remotecomputers (der Port ist erforderlich.) anstelle der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile, um die IPv4-Adresse zu erhalten.

    Wenn Sie verwenden möchten die **finden** Schaltfläche müssen Sie möglicherweise [Öffnen von UDP-Port 3702](#bkmk_openports) auf dem Server.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
6. Geben Sie den ersten Buchstaben eines Prozessnamens schnell und problemlos suchen **dotnet.exe** (für ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<Name_des_Remotecomputers>**.

    Es sollte die ASP.NET-Webseite angezeigt werden.

9. Klicken Sie in der laufenden Anwendung ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und den Remotedebugger geöffnet. Allerdings müssen Sie sicherstellen, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal).

Erforderliche Ports:

* 80 - wird für IIS erforderlich.
::: moniker range=">=vs-2019"
* 4024: erforderlich für das Remotedebuggen von Visual Studio-2019 (finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) Informationen).
::: moniker-end
::: moniker range="vs-2017"
* 4022 – erforderlich für das Remotedebuggen von Visual Studio 2017 (finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md) Informationen).
::: moniker-end
* UDP 3702 - erkennungsport (Optional) können Sie die **finden** Schaltfläche beim Anfügen an den Remotedebugger in Visual Studio.

1. Öffnen Sie zum Öffnen eines Ports in Windows Server die **starten** Menü, und suchen Sie **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **Eingangsregeln > neue Regel > Port**, und klicken Sie dann auf **Weiter**. (Wählen Sie für UDP 3702, **Ausgangsregeln** stattdessen.)

3. Klicken Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer, und klicken Sie auf **Weiter**.

4. Klicken Sie auf **Verbindung zulassen,**, klicken Sie auf **Weiter**.

5. Wählen Sie eine oder mehrere Netzwerktypen für den Port zu aktivieren, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
6. Fügen Sie den Namen (z. B. **IIS**, **Web Deploy**, oder **"msvsmon"**) für die eingehende Regel und auf **Fertig stellen**.

    Daraufhin sollte die neue Regel in der Liste „Eingangsregeln“ bzw. „Ausgangsregeln“ angezeigt werden.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports an.
