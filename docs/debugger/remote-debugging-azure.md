---
title: Remote-Debug-ASP.NET Core auf IIS und Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385499"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Remotedebug ASP.NET Core auf IIS in Azure in Visual Studio

In diesem Handbuch wird erläutert, wie Sie eine Visual Studio ASP.NET Core-App einrichten und konfigurieren, sie mithilfe von Azure in IIS bereitstellen und den Remotedebugger aus Visual Studio anfügen.

Die empfohlene Methode zum Remotedebuggen in Azure hängt von Ihrem Szenario ab:

* Informationen zum Debuggen ASP.NET Core in Azure App Service finden Sie unter Debuggen von [Azure-Apps mithilfe des Snapshot-Debuggers](../debugger/debug-live-azure-applications.md). Dies ist die empfohlene Methode.
* Um ASP.NET Core in Azure App Service mithilfe herkömmlicherer Debugfunktionen zu debuggen, führen Sie die Schritte in diesem Thema aus (siehe Abschnitt [Remotedebug in Azure App Service](#remote_debug_azure_app_service)).

    In diesem Szenario müssen Sie Ihre App von Visual Studio in Azure bereitstellen, müssen jedoch IIS oder den Remotedebugger (diese Komponenten werden mit gepunkteten Linien dargestellt) nicht manuell installieren oder konfigurieren (diese Komponenten werden mit gepunkteten Linien dargestellt), wie in der folgenden Abbildung dargestellt.

    ![Remote-Debuggerkomponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Um IIS auf einer Azure-VM zu debuggen, führen Sie die Schritte in diesem Thema aus (siehe Abschnitt [Remotedebug auf einer Azure-VM](#remote_debug_azure_vm)). Auf diese Weise können Sie eine benutzerdefinierte Konfiguration von IIS verwenden, aber die Setup- und Bereitstellungsschritte sind komplizierter.

    Für eine Azure-VM müssen Sie Ihre App von Visual Studio in Azure bereitstellen und auch die IIS-Rolle und den Remotedebugger manuell installieren, wie in der folgenden Abbildung dargestellt.

    ![Remote-Debuggerkomponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Informationen zum Debuggen ASP.NET Core in Azure Service Fabric finden Sie unter [Debuggen einer Remote-Service Fabric-Anwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Achten Sie darauf, die Azure-Ressourcen zu löschen, die Sie erstellen, wenn Sie die Schritte in diesem Tutorial abgeschlossen haben. Auf diese Weise können Sie unnötige Gebühren vermeiden.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 muss die in diesem Artikel beschriebenen Schritte ausführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 muss die in diesem Artikel beschriebenen Schritte ausführen.
::: moniker-end

### <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei Computern, die über einen Proxy verbunden sind, wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder geringer Bandbreite, z. B. DFÜ-Internet, oder über das Internet zwischen Ländern wird nicht empfohlen und kann fehlschlagen oder unannehmbar langsam sein. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET Core-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.NET Core-Anwendung.

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **Strg + Q** ein, um das Suchfeld zu öffnen, geben Sie **asp.net**ein, wählen Sie **Vorlagen**aus, und wählen Sie dann neue ASP.NET Core Web **Application erstellen**. Benennen Sie im angezeigten Dialogfeld das Projekt **MyASPApp**, und wählen Sie dann **Erstellen**aus. Wählen Sie als Nächstes **Webapplication (Model-View-Controller)** aus, und wählen Sie dann **Erstellen**aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > Neues >-Projekt**aus, und wählen Sie dann **Visual C- > Web > ASP.NET Core Web Application aus.** Wählen Sie im Abschnitt ASP.NET Core-Vorlagen **Webapplication (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.NET Core 2.1 ausgewählt ist, dass **Docker-Support aktivieren** nicht ausgewählt ist und dass **die Authentifizierung** auf **Keine Authentifizierung**festgelegt ist. Benennen Sie das Projekt **MyASPApp**.
    ::: moniker-end

1. Öffnen Sie die About.cshtml.cs Datei, `OnGet` und legen Sie einen Haltepunkt in der Methode `About()` fest (in älteren Vorlagen öffnen Sie stattdessen HomeController.cs und legen Sie den Haltepunkt in der Methode fest).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Remote-Debug-ASP.NET Core in einem Azure App Service

In Visual Studio können Sie Ihre App schnell veröffentlichen und auf einer vollständig bereitgestellten IIS-Instanz debuggen. Die Konfiguration von IIS ist jedoch voreingestellt und kann nicht angepasst werden. Ausführlichere Anweisungen finden Sie unter [Bereitstellen einer ASP.NET Core-Web-App in Azure mithilfe von Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie iIS anpassen können, versuchen Sie, auf einer [Azure-VM](#remote_debug_azure_vm)zu debuggen.)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>So stellen Sie die App und das Remote-Debugmit mithilfe von Cloud Explorer bereit

1. Klicken Sie in Visual Studio mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

    Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil**.

1. Wählen Sie **Azure App Service** im Dialogfeld **Veröffentlichen** aus, wählen Sie **Neu erstellen**aus, und folgen Sie den Anweisungen zum Erstellen eines Profils.

    Ausführliche Anweisungen finden Sie unter [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Veröffentlichen in Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Wählen Sie im Fenster Veröffentlichen die Option **Konfiguration bearbeiten** aus, wechseln Sie zu einer Debugkonfiguration, und wählen Sie dann **Veröffentlichen**aus.

   Zum Debuggen der App ist eine Debugkonfiguration erforderlich.

1. Öffnen Sie **Cloud Explorer** (**View** > **Cloud Explorer**), klicken Sie mit der rechten Maustaste auf die App Service-Instanz und wählen **Debugger anfügen**.

   Wenn Cloud Explorer nicht verfügbar ist, öffnen Sie stattdessen den Server-Explorer. Klicken Sie dann mit der rechten Maustaste auf die App Service-Instanz im Server-Explorer, und wählen Sie **Debugger anfügen**.

1. Klicken Sie in der ausgeführten ASP.NET Anwendung auf den Link zur Seite **Über.**

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für das Remotedebuggen auf einer Azure-VM.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Remotedebug-ASP.NET Core auf einer Azure-VM

Sie können eine Azure-VM für Windows Server erstellen und dann IIS und die anderen erforderlichen Softwarekomponenten installieren und konfigurieren. Dies nimmt mehr Zeit in Anspruch als die Bereitstellung in einem Azure App Service und erfordert, dass Sie die verbleibenden Schritte in diesem Tutorial ausführen.

Diese Verfahren wurden an diesen Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>App, die bereits in IIS auf der Azure-VM ausgeführt wird?

Dieser Artikel enthält Schritte zum Einrichten einer grundlegenden Konfiguration von IIS auf Windows-Server und zum Bereitstellen der App über Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server die erforderlichen Komponenten installiert sind, dass die App ordnungsgemäß ausgeführt werden kann und dass Sie zum Remotedebuggen bereit sind.

* Wenn Ihre App in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und mit dem Debuggen beginnen möchten, gehen Sie zu [Herunterladen und Installieren der Remotetools auf Windows Server](#BKMK_msvsmon).

* Wenn Sie helfen möchten, um sicherzustellen, dass Ihre App in IIS eingerichtet, bereitgestellt und ordnungsgemäß ausgeführt wird, damit Sie debuggen können, führen Sie alle Schritte in diesem Thema aus.

  * Bevor Sie beginnen, führen Sie alle unter Installieren beschriebenen Schritte [aus, und führen Sie IIS aus.](/azure/virtual-machines/windows/quick-create-portal)

  * Wenn Sie Port 80 in der Netzwerksicherheitsgruppe öffnen, öffnen Sie auch den [richtigen Port](#bkmk_openports) für den Remotedebugger (4024 oder 4022). Auf diese Weise müssen Sie es später nicht öffnen.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren der Browsersicherheitseinstellungen auf Windows Server

Wenn die erweiterte Sicherheitskonfiguration in Internet Explorer aktiviert ist (standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserverkomponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internetoptionen > Sicherheit > vertrauenswürdige Sites > Sites**gehen. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen, die die Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen erteilen. Einige dieser Ressourcen sind nicht erforderlich, aber um den Prozess zu vereinfachen, klicken Sie auf **Hinzufügen,** wenn Sie dazu aufgefordert werden.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren ASP.NET Core auf Windows Server

1. Installieren Sie das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) auf dem Hostsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Ausführlichere Anweisungen finden Sie unter [Veröffentlichen in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*, bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

3. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

## <a name="choose-a-deployment-option"></a>Auswählen einer Bereitstellungsoption

Wenn Sie Hilfe benötigen, um die App auf IIS bereitzustellen, sollten Sie die folgenden Optionen in Betracht ziehen:

* Bereitstellen, indem Sie eine Veröffentlichungseinstellungsdatei in IIS erstellen und die Einstellungen in Visual Studio importieren. In einigen Szenarien ist dies eine schnelle Möglichkeit, Ihre App bereitzustellen. Wenn Sie die Veröffentlichungseinstellungsdatei erstellen, werden Berechtigungen automatisch in IIS eingerichtet.

* Bereitstellen durch Veröffentlichen in einem lokalen Ordner und Kopieren der Ausgabe durch eine bevorzugte Methode in einen vorbereiteten App-Ordner auf IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Bereitstellen mithilfe einer Veröffentlichungseinstellungsdatei

Mit dieser Option können Sie eine Veröffentlichungseinstellungsdatei erstellen und in Visual Studio importieren.

> [!NOTE]
> Diese Bereitstellungsmethode verwendet Web Deploy. Wenn Sie Web Deploy manuell in Visual Studio konfigurieren möchten, anstatt die Einstellungen zu importieren, können Sie Web Deploy 3.6 anstelle von Web Deploy 3.6 für Hostingserver installieren. Wenn Sie Web Deploy jedoch manuell konfigurieren, müssen Sie sicherstellen, dass ein App-Ordner auf dem Server mit den richtigen Werten und Berechtigungen konfiguriert ist (siehe [Konfigurieren ASP.NET Website](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hostingserver auf Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die App nicht in Visual Studio gestartet wird, starten Sie die App in IIS. Für ASP.NET Core müssen Sie sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

1. Aktivieren Sie im Dialogfeld **Einstellungen** das Debuggen, indem Sie auf **Weiter**klicken , eine **Debugkonfiguration** auswählen, und wählen Sie dann unter den Optionen **Dateiveröffentlichung** **zusätzliche Dateien am Ziel entfernen** aus.

    > [!NOTE]
    > Wenn Sie eine Release-Konfiguration auswählen, deaktivieren Sie das Debuggen in der Datei *web.config,* wenn Sie veröffentlichen.

1. Klicken Sie auf **Speichern,** und veröffentlichen Sie die App erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Bereitstellen durch Veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre App bereitzustellen, wenn Sie die App mithilfe von PowerShell, RoboCopy oder manuell auf IIS kopieren möchten.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurieren der ASP.NET Core-Website auf dem Windows Server-Computer

Wenn Sie Veröffentlichungseinstellungen importieren, können Sie diesen Abschnitt überspringen.

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie das **Alias-Feld** auf **MyASPApp** und das Feld Anwendungspool auf **Kein verwalteter Code**fest. Legen Sie den **physischen Pfad** auf **C:-Veröffentlichung** fest (wo Sie später das ASP.NET Core-Projekt bereitstellen werden).

4. Wenn die im IIS-Manager ausgewählte Site ausgewählt ist, wählen Sie **Berechtigungen bearbeiten**aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der für den Anwendungspool konfigurierte Benutzer ein autorisierter Benutzer mit Lese-& Ausführungsrechten ist.

    Wenn einer dieser Benutzer nicht mit Zugriff angezeigt wird, führen Sie Schritte durch, um IUSR als Benutzer mit Lese- & Ausführungsrechten hinzuzufügen.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der App durch Veröffentlichen in einem lokalen Ordner aus Visual Studio

Wenn Sie Web Deploy nicht verwenden, müssen Sie die App mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen. Sie können zunächst ein Paket mit dem Dateisystem erstellen und dann das Paket entweder manuell bereitstellen oder andere Tools wie PowerShell, RoboCopy oder XCopy verwenden. In diesem Abschnitt gehen wir davon aus, dass Sie das Paket manuell kopieren, wenn Sie Web Deploy nicht verwenden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Herunterladen und Installieren der Remotetools auf Windows Server

Laden Sie die Version der Remotetools herunter, die Ihrer Version von Visual Studio entsprechen.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Einrichten des Remotedebuggers auf Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen müssen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>An den ASP.NET Anwendung vom Visual Studio-Computer anfügen

1. Öffnen Sie auf dem Visual Studio-Computer die Lösung, die Sie debuggen möchten **(MyASPApp,** wenn Sie die Schritte in diesem Artikel ausführen).
2. Klicken Sie in Visual Studio auf **Debuggen > an Den Prozess anfügen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 und neueren Versionen können Sie mit **Debug-> Neuattach-to-Process...** (Shift+Alt+P) erneut an denselben Prozess anfügen, an den Sie zuvor angefügt haben.

3. Legen Sie das Feld Qualifizierer auf ** \<den Namen des Remotecomputers>** fest, und drücken **Sie die Eingabetaste**.

    Stellen Sie sicher, dass Visual Studio dem Computernamen den erforderlichen Port hinzufügt, der im Format angezeigt wird: ** \<Remotecomputername>:Port**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 sollte der Name des ** \<Remotecomputers>:4024 angezeigt werden.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 sollte der ** \<Name des Remotecomputers>:4022 angezeigt werden.**
    ::: moniker-end
    Der Port ist erforderlich. Wenn die Portnummer nicht angezeigt wird, fügen Sie sie manuell hinzu.

4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remotecomputernamens zu verwenden (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile die IPv4-Adresse abrufen.

    Wenn Sie die **Schaltfläche Suchen** verwenden möchten, müssen Sie möglicherweise [udP-Port 3702](#bkmk_openports) auf dem Server öffnen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben Ihres Prozessnamens ein, um Ihre App schnell zu finden.

    * wählen Sie **dotnet.exe** (für .NET Core)

      Wenn mehrere Prozesse **an dotnet.exe**angezeigt werden, überprüfen Sie die Spalte **Benutzername.** In einigen Szenarien zeigt die Spalte **Benutzername** Ihren App-Poolnamen an, z. B. **IIS APPPOOL-DefaultAppPool**. Wenn der App-Pool angezeigt wird, können Sie den richtigen Prozess einfach identifizieren, wenn Sie einen neuen benannten App-Pool für die App-Instanz erstellen, die Sie debuggen möchten, und sie dann in der Spalte **Benutzername** leicht finden.

    * In einigen IIS-Szenarien finden Sie möglicherweise Ihren App-Namen in der Prozessliste, z. B. **MyASPApp.exe**. Sie können stattdessen an diesen Prozess anfügen.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie **auf Anfügen**.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<Name_des_Remotecomputers>**.

    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der ausgeführten ASP.NET Anwendung auf den Link zur Seite **Über.**

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und des Remote-Debuggers geöffnet. Wenn Sie jedoch Probleme mit der Bereitstellung beheben und die App hinter einer Firewall gehostet wird, müssen Sie möglicherweise überprüfen, ob die richtigen Ports geöffnet sind.

Auf einer Azure-VM müssen Sie Ports über die [Netzwerksicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal)öffnen.

Erforderliche Ports:

* 80 - Erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024 - Erforderlich für Remote-Debugging aus Visual Studio 2019 (weitere Informationen finden Sie unter [Remotedebugger-Portzuweisungen).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Erforderlich für Remote-Debugging aus Visual Studio 2017 (weitere Informationen finden Sie unter [Remotedebugger-Portzuweisungen).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* Mit dem UDP 3702 - (Optional) Discovery-Port können Sie die Schaltfläche **Suchen** verwenden, wenn Sie an den Remotedebugger in Visual Studio angefügt werden.

Darüber hinaus sollten diese Ports bereits durch die ASP.NET Installation geöffnet werden:
- 8172 - (Optional) Erforderlich für Web Deploy zur Bereitstellung der App aus Visual Studio
