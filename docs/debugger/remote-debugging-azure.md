---
title: Remote debugASP.net Core auf IIS und Azure | Microsoft-Dokumentation
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: c6a41a332e16f79673b475404af27e540689938d
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181135"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Remote Debuggen ASP.net Core auf IIS in Azure in Visual Studio

In diesem Handbuch wird erläutert, wie Sie eine Visual Studio ASP.net Core-App einrichten und konfigurieren, Sie in IIS mithilfe von Azure bereitstellen und den Remote Debugger aus Visual Studio anfügen.

Die empfohlene Vorgehensweise für das Remote Debuggen in Azure hängt von Ihrem Szenario ab:

* Informationen zum Debuggen von ASP.net Core auf Azure App Service finden [Momentaufnahmedebugger Sie unter Debuggen von Azure-apps mit](../debugger/debug-live-azure-applications.md) Dies ist die empfohlene Methode.
* Um ASP.net Core auf Azure App Service mithilfe von herkömmlichen Debuggingfunktionen zu debuggen, führen Sie die Schritte in diesem Thema aus (siehe Abschnitt [Remote Debuggen auf Azure App Service](#remote_debug_azure_app_service))

    In diesem Szenario müssen Sie die APP aus Visual Studio in Azure bereitstellen, aber Sie müssen IIS oder den Remote Debugger (diese Komponenten werden mit gepunkteten Linien dargestellt) nicht manuell installieren oder konfigurieren, wie in der folgenden Abbildung dargestellt.

    ![Remote Debugger-Komponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Führen Sie zum Debuggen von IIS auf einem virtuellen Azure-Computer die Schritte in diesem Thema aus (siehe Abschnitt [Remote Debuggen auf einem virtuellen Azure](#remote_debug_azure_vm)-Computer) Dies ermöglicht es Ihnen, eine angepasste Konfiguration von IIS zu verwenden, die Setup-und Bereitstellungs Schritte sind jedoch komplizierter.

    Für eine Azure-VM müssen Sie Ihre APP aus Visual Studio in Azure bereitstellen. Außerdem müssen Sie die IIS-Rolle und den Remote Debugger manuell installieren, wie in der folgenden Abbildung dargestellt.

    ![Remote Debugger-Komponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Informationen zum Debuggen von ASP.net Core in Azure Service Fabric finden Sie unter [Debuggen einer Remote Service Fabric Anwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

> [!WARNING]
> Stellen Sie sicher, dass Sie die Azure-Ressourcen löschen, die Sie erstellt haben, wenn Sie die Schritte in diesem Tutorial ausgeführt haben. Auf diese Weise können Sie unnötige Gebühren vermeiden.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

### <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei mit einem Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, wie z. b. ddas Internet oder über das Internet über das Internet hinweg, wird nicht empfohlen und schlägt möglicherweise fehl oder ist nicht akzeptabel. Eine umfassende Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.net Core Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.net Core Anwendung.

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **ASP.net**ein, wählen Sie **Vorlagen**aus, und klicken Sie dann auf **neue ASP.net Core Webanwendung erstellen**. Benennen Sie im angezeigten Dialogfeld das Projekt **myaspapp**, und wählen Sie dann **Erstellen**aus. Wählen Sie als nächstes **Webanwendung (Model-View-Controller)** aus, und wählen Sie dann **Erstellen**aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > neue > Projekt**aus, und wählen Sie dann  **C# Visual > web > ASP.net Core Webanwendung**aus. Wählen Sie im Abschnitt ASP.net Core Vorlagen die Option **Webanwendung (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.net Core 2,1 ausgewählt ist, dass die **docker-Unterstützung aktivieren** nicht ausgewählt ist und die **Authentifizierung** auf **keine Authentifizierung**festgelegt ist. Nennen Sie das Projekt **myaspapp**.
    ::: moniker-end

1. Öffnen Sie die Datei about.cshtml.cs, und legen Sie einen Haltepunkt in der `OnGet`-Methode fest (in älteren Vorlagen öffnen Sie stattdessen HomeController.cs, und legen Sie den Breakpoint in der `About()`-Methode fest).

## <a name="remote_debug_azure_app_service"></a>Remote debugASP.net Core auf einem Azure App Service

In Visual Studio können Sie Ihre APP schnell in einer vollständig bereitgestellten Instanz von IIS veröffentlichen und Debuggen. Allerdings ist die Konfiguration von IIS voreingestellt, und Sie können Sie nicht anpassen. Ausführlichere Anweisungen finden Sie unter Bereitstellen [einer ASP.net Core-Web-App in Azure mithilfe von Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie IIS anpassen möchten, versuchen Sie, auf einem virtuellen [Azure](#remote_debug_azure_vm)-Computer zu debuggen.)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>So stellen Sie die APP und das Remote Debuggen mit Server-Explorer bereit

1. Klicken Sie in Visual Studio mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **veröffentlichen**aus.

    Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil**.

1. Wählen Sie im Dialogfeld " **veröffentlichen** " **Azure App Service** aus, wählen Sie **neu erstellen**aus, und befolgen Sie die Anweisungen zum veröffentlichen.

    Ausführliche Anweisungen finden Sie unter [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Veröffentlichen in Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Öffnen Sie **Server-Explorer** ( > **Server-Explorer** **anzeigen** ), klicken Sie mit der rechten Maustaste auf die APP Service Instanz, und wählen Sie **Debugger anfügen**aus.

1. Klicken Sie in der Anwendung Running ASP.net **auf den Link zur Seite "** Info".

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für das Remote Debuggen auf einem virtuellen Azure-Computer.

## <a name="remote_debug_azure_vm"></a>Remote Debuggen ASP.net Core auf einer Azure-VM

Sie können eine Azure-VM für Windows Server erstellen und anschließend IIS und die anderen erforderlichen Softwarekomponenten installieren und konfigurieren. Dies erfordert mehr Zeit als die Bereitstellung für eine Azure App Service und erfordert, dass Sie die verbleibenden Schritte in diesem Tutorial ausführen.

Diese Prozeduren wurden auf diesen Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Die APP wird bereits in IIS auf der Azure-VM ausgeführt?

Dieser Artikel enthält die Schritte zum Einrichten einer grundlegenden Konfiguration von IIS unter Windows Server und zum Bereitstellen der APP aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server die erforderlichen Komponenten installiert sind, dass die APP ordnungsgemäß ausgeführt werden kann und dass Sie für das Remote Debuggen bereit sind.

* Wenn Ihre APP in IIS ausgeführt wird und Sie nur den Remote Debugger herunterladen und das Debuggen starten möchten, wechseln Sie zu [herunterladen und Installieren der Remote Tools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre APP in IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie Debuggen können, führen Sie alle Schritte in diesem Thema aus.

  * Bevor Sie beginnen, befolgen Sie alle Schritte, die unter [Installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal)beschrieben werden.

  * Wenn Sie Port 80 in der Netzwerk Sicherheitsgruppe öffnen, öffnen Sie auch den [korrekten Port](#bkmk_openports) für den Remote Debugger (4024 oder 4022). Auf diese Weise müssen Sie Sie später nicht mehr öffnen.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browser-Sicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserver Komponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internet Optionen > Sicherheits > vertrauenswürdige Sites > Websites**wechseln. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Website Skripts und Ressourcen. Einige dieser Ressourcen sind nicht erforderlich, um den Prozess zu vereinfachen, klicken Sie auf **Hinzufügen** , wenn Sie dazu aufgefordert werden.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.net Core unter Windows Server

1. Installieren Sie das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) auf dem Hostsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Ausführlichere Anweisungen finden [Sie unter Veröffentlichen in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* , bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

3. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

## <a name="choose-a-deployment-option"></a>Bereitstellungs Option auswählen

Wenn Sie Hilfe bei der Bereitstellung der app in IIS benötigen, beachten Sie die folgenden Optionen:

* Stellen Sie bereit, indem Sie eine Datei mit Veröffentlichungs Einstellungen in IIS erstellen und die Einstellungen in Visual Studio importieren. In einigen Szenarios ist dies eine schnelle Möglichkeit, Ihre APP bereitzustellen. Wenn Sie die Datei mit den Veröffentlichungs Einstellungen erstellen, werden Berechtigungen in IIS automatisch eingerichtet.

* Bereitstellung durch veröffentlichen in einem lokalen Ordner und Kopieren der Ausgabe durch eine bevorzugte Methode in einen vorbereiteten app-Ordner auf IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Optionale Bereitstellen mithilfe einer Datei mit Veröffentlichungs Einstellungen

Sie können diese Option verwenden, um eine Datei mit Veröffentlichungs Einstellungen zu erstellen und in Visual Studio zu importieren.

> [!NOTE]
> Bei dieser Bereitstellungs Methode wird Web deploy verwendet. Wenn Sie Web deploy manuell in Visual Studio konfigurieren möchten, anstatt die Einstellungen zu importieren, können Sie Web Deploy 3,6 anstelle von Web Deploy 3,6 für Host Server installieren. Wenn Sie Web deploy jedoch manuell konfigurieren, müssen Sie sicherstellen, dass ein app-Ordner auf dem Server mit den richtigen Werten und Berechtigungen konfiguriert ist (siehe [Konfigurieren der ASP.NET-Website](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web deploy für Host Server unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die APP nicht über Visual Studio gestartet wird, starten Sie die app in IIS. Für ASP.NET Core müssen Sie sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

1. Aktivieren Sie im Dialogfeld " **Einstellungen** " das Debuggen, indem Sie auf **weiter**klicken, eine **Debugkonfiguration** auswählen und dann unter den Optionen für die **Datei Veröffentlichung** **Weitere Dateien am Ziel entfernen** auswählen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie das Debuggen in der Datei " *Web. config* ", wenn Sie veröffentlichen.

1. Klicken Sie auf **Speichern** , und veröffentlichen Sie die APP erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Optionale Bereitstellen durch veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre APP bereitzustellen, wenn Sie die App mithilfe von PowerShell, Robocopy in IIS kopieren möchten, oder wenn Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a>Konfigurieren der ASP.net Core-Website auf dem Windows Server-Computer

Wenn Sie Veröffentlichungs Einstellungen importieren, können Sie diesen Abschnitt überspringen.

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie für das Feld **Alias** den Wert **myaspapp** und für das Feld Anwendungs Pool den Wert **kein verwalteter Code**fest. Legen Sie den **physischen Pfad** auf **c:\publish** fest (wo Sie später das ASP.net Core Projekt bereitstellen werden).

4. Wählen Sie bei ausgewählter Website im IIS-Manager die Option **Berechtigungen bearbeiten**aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der Benutzer, der für den Anwendungs Pool konfiguriert ist, ein autorisierter Benutzer mit Lese & Ausführungs rechten ist.

    Wenn einer dieser Benutzer keinen Zugriff hat, führen Sie die Schritte zum Hinzufügen von IUSR als Benutzer mit der Berechtigung Lesen & Execute aus.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Optionale Veröffentlichen und Bereitstellen der app durch veröffentlichen in einem lokalen Ordner in Visual Studio

Wenn Sie Web deploy nicht verwenden, müssen Sie die APP mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen. Sie können beginnen, indem Sie ein Paket mit dem Dateisystem erstellen und das Paket dann entweder manuell bereitstellen oder andere Tools wie PowerShell, Robocopy oder xcopy verwenden. In diesem Abschnitt wird davon ausgegangen, dass Sie das Paket manuell kopieren, wenn Sie Web deploy nicht verwenden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Herunterladen und Installieren der Remote Tools unter Windows Server

Laden Sie die Version der Remote Tools herunter, die Ihrer Version von Visual Studio entspricht.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a>Einrichten des Remote Debuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remote Debugger ändern müssen, finden Sie weitere Informationen unter [configure the Remote Debugger](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projekt Mappe, die Sie debuggen möchten (**myaspapp** , wenn Sie die Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (STRG + ALT + P).

    > [!TIP]
    > In Visual Studio 2017 und höheren Versionen können Sie an denselben Prozess, den Sie zuvor angefügt haben, erneut anfügen, indem Sie **Debuggen > erneut an den Prozess anfügen...** (UMSCHALT + ALT + P).

3. Legen Sie das Feld Qualifizierer auf **\<Remote Computername >** und drücken **Sie die Eingabe**Taste.

    Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im folgenden Format angezeigt wird: **\<Remote Computername >:p Ort** .

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 sollte **\<Remote Computername angezeigt werden >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 sollte **\<Remote Computername angezeigt werden >: 4022**
    ::: moniker-end
    Der Port ist erforderlich. Wenn die Portnummer nicht angezeigt wird, fügen Sie Sie manuell hinzu.

4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remote Computer namens zu verwenden (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile verwenden, um die IPv4-Adresse zu erhalten.

    Wenn Sie die Schaltfläche " **Suchen** " verwenden möchten, müssen Sie möglicherweise den [UDP-Port 3702](#bkmk_openports) auf dem Server öffnen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben Ihres Prozess namens ein, um Ihre APP schnell zu finden.

    * Wählen Sie " **dotnet. exe** " (für .net Core) aus.

      Wenn Sie mehrere Prozesse mit " **dotnet. exe**" haben, überprüfen Sie die Spalte " **Benutzer Name** ". In einigen Szenarien wird in der Spalte " **Benutzer Name** " der Name des App-Pools angezeigt, z. b. " **IIS apppool\defaultapppool**". Wenn Sie den App-Pool sehen, ist es einfach, den richtigen Prozess zu ermitteln, indem Sie einen neuen benannten App-Pool für die app-Instanz erstellen, die Sie debuggen möchten, und Sie können ihn dann problemlos in der Spalte **Benutzer Name** finden.

    * In einigen IIS-Szenarien finden Sie den Namen Ihrer APP möglicherweise in der Prozessliste, z. b. **myaspapp. exe**. Stattdessen können Sie diesen Prozess anfügen.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<Name_des_Remotecomputers>** .

    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der Anwendung Running ASP.net **auf den Link zur Seite "** Info".

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

In den meisten Setups werden erforderliche Ports durch die Installation von ASP.net und den Remote Debugger geöffnet. Wenn Sie jedoch Bereitstellungs Probleme behandeln und die APP hinter einer Firewall gehostet wird, müssen Sie möglicherweise überprüfen, ob die richtigen Ports geöffnet sind.

Auf einem virtuellen Azure-Computer müssen Sie Ports über die [Netzwerk Sicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal)öffnen.

Erforderliche Ports:

* 80-erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024-erforderlich für das Remote Debuggen von Visual Studio 2019 (Weitere Informationen finden Sie unter [Port Zuweisungen für Remote Debugger](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-erforderlich für das Remote Debuggen von Visual Studio 2017 (Weitere Informationen finden Sie unter [Port Zuweisungen für Remote Debugger](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(optional) der suchport ermöglicht Ihnen die Schaltfläche **Suchen** , wenn Sie an den Remote Debugger in Visual Studio anhängen.

Außerdem sollten diese Ports bereits von der ASP.net-Installation geöffnet werden:
- 8172 (optional) erforderlich, damit Web deploy die APP aus Visual Studio bereitstellen können
