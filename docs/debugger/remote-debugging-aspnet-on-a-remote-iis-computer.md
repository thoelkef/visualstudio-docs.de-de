---
title: Remote Debuggen ASP.net Core auf einem Remote-IIS-Computer | Microsoft-Dokumentation
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
ms.openlocfilehash: 3e11480949545781630dec0c533949dd200ecbc7
ms.sourcegitcommit: 7a9d5c10690c594dcdb414d88b20e070d43e7a4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82218885"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remote Debuggen ASP.net Core auf einem Remote-IIS-Computer in Visual Studio

Zum Debuggen einer ASP.net Core Anwendung, die in IIS bereitgestellt wurde, installieren und führen Sie die Remote Tools auf dem Computer aus, auf dem Sie die APP bereitgestellt haben, und fügen Sie dann in Visual Studio an ihre laufende APP an.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In diesem Handbuch wird erläutert, wie Sie eine Visual Studio-ASP.net Core einrichten und konfigurieren, Sie in IIS bereitstellen und den Remote Debugger aus Visual Studio anfügen. Informationen zum Remote Debuggen von ASP.NET 4.5.2 finden Sie unter [Remote Debug ASP.net auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Sie können auch unter IIS mithilfe von Azure bereitstellen und Debuggen. Für Azure App Service können Sie problemlos auf einer vorkonfigurierten Instanz von IIS und dem Remote Debugger bereitstellen und Debuggen, indem Sie entweder die [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) oder [den Debugger aus Server-Explorer](../debugger/remote-debugging-azure.md)anfügen.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

Diese Prozeduren wurden auf diesen Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10

## <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei mit einem Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, wie z. b. ddas Internet oder über das Internet über das Internet hinweg, wird nicht empfohlen und schlägt möglicherweise fehl oder ist nicht akzeptabel. Eine umfassende Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Die APP wird bereits in IIS ausgeführt?

Dieser Artikel enthält die Schritte zum Einrichten einer grundlegenden Konfiguration von IIS unter Windows Server und zum Bereitstellen der APP aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server erforderliche Komponenten installiert sind, dass die APP ordnungsgemäß ausgeführt werden kann und dass Sie für das Remote Debuggen bereit sind.

* Wenn Ihre APP in IIS ausgeführt wird und Sie nur den Remote Debugger herunterladen und das Debuggen starten möchten, wechseln Sie zu [herunterladen und Installieren der Remote Tools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre APP in IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie Debuggen können, führen Sie alle Schritte in diesem Thema aus.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.net Core Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.NET Core-Webanwendung. 

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **ASP.net**ein, wählen Sie **Vorlagen**aus, und klicken Sie dann auf **neue ASP.net Core Webanwendung erstellen**. Benennen Sie im angezeigten Dialogfeld das Projekt **myaspapp**, und wählen Sie dann **Erstellen**aus. Wählen Sie als nächstes **Webanwendung (Model-View-Controller)** aus, und wählen Sie dann **Erstellen**aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > neues > Projekt**aus, und wählen Sie dann **Visual c# > Web > ASP.net Core Webanwendung**aus. Wählen Sie im Abschnitt ASP.net Core Vorlagen die Option **Webanwendung (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.net Core 2,1 ausgewählt ist, dass die **docker-Unterstützung aktivieren** nicht ausgewählt ist und die **Authentifizierung** auf **keine Authentifizierung**festgelegt ist. Nennen Sie das Projekt **myaspapp**.
    ::: moniker-end

4. Öffnen Sie die Datei about.cshtml.cs, und legen Sie einen halte `OnGet` Punkt in der-Methode fest (in älteren Vorlagen, öffnen Sie stattdessen HomeController.cs, `About()` und legen Sie den Breakpoint in der-Methode fest).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installieren und Konfigurieren von IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browser-Sicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserver Komponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internet Optionen > Sicherheits > vertrauenswürdige Sites > Websites**wechseln. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Website Skripts und Ressourcen. Einige dieser Ressourcen sind nicht erforderlich, um den Prozess zu vereinfachen, klicken Sie auf **Hinzufügen** , wenn Sie dazu aufgefordert werden.

## <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.net Core unter Windows Server

1. Installieren Sie das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) auf dem Hostsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Ausführlichere Anweisungen finden [Sie unter Veröffentlichen in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*, bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

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

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurieren der ASP.net Core-Website auf dem Windows Server-Computer

1. Öffnen Sie Windows-Explorer, und erstellen Sie einen neuen Ordner ( **c:\publish**), in dem Sie später das ASP.net Core-Projekt bereitstellen.

2. Wenn Sie nicht bereits geöffnet ist, öffnen Sie den **Internetinformationsdienste (IIS)-Manager**. (Klicken Sie im linken Bereich Server-Manager auf **IIS**. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Wechseln Sie im linken Bereich unter **Verbindungen** zu **Websites**.

4. Wählen Sie die **Standard Website**aus, und wählen Sie **Grundeinstellungen**aus, und legen Sie den **physischen Pfad** auf **c:\publish**fest.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Legen Sie für das Feld **Alias** den Wert **myaspapp**fest, akzeptieren Sie den Standard Anwendungs Pool (**DefaultAppPool**), und legen Sie den **physischen Pfad** auf **c:\publish**fest.

6. Wählen Sie unter **Verbindungen**die Option **Anwendungs Pools**aus. Öffnen Sie **DefaultAppPool** , und legen Sie das Feld Anwendungs Pool auf **keinen verwalteten Code**fest.

7. Klicken Sie mit der rechten Maustaste auf die neue Website im IIS-Manager, wählen Sie **Berechtigungen bearbeiten**aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der Benutzer, der für den Zugriff auf die Web-App konfiguriert ist, ein autorisierter Benutzer mit Lese & Ausführungs rechten ist

    Wenn einer dieser Benutzer keinen Zugriff hat, führen Sie die Schritte zum Hinzufügen von IUSR als Benutzer mit der Berechtigung Lesen & Execute aus.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der app durch veröffentlichen in einem lokalen Ordner in Visual Studio

Sie können die APP auch mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Herunterladen und Installieren der Remote Tools unter Windows Server

Laden Sie die Version der Remote Tools herunter, die Ihrer Version von Visual Studio entspricht.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Einrichten des Remote Debuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remote Debugger ändern müssen, finden Sie weitere Informationen unter [configure the Remote Debugger](../debugger/remote-debugging.md#configure_msvsmon).

Weitere Informationen zum Ausführen des Remote Debuggers als Dienst finden Sie unter [Run the Remote Debugger as a Service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projekt Mappe, die Sie debuggen möchten (**myaspapp** , wenn Sie alle Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (STRG + ALT + P).

    > [!TIP]
    > In Visual Studio 2017 und höheren Versionen können Sie den Prozess, an den Sie zuvor angefügt haben, erneut an denselben Prozess anfügen, den Sie zuvor mit **Debuggen > an den Prozess anfügen...** (UMSCHALT + ALT + P).

3. Legen Sie das Feld Qualifizierer auf ** \<Remote Computername>** und drücken **Sie die Eingabe**Taste.

    Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im Format: ** \<Remote Computername>:p Ort angezeigt wird.**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 sollte der Name des ** \<Remote Computers angezeigt werden>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 sollte der Name des ** \<Remote Computers angezeigt werden>:4022**
    ::: moniker-end
    Der Port ist erforderlich. Wenn die Portnummer nicht angezeigt wird, fügen Sie Sie manuell hinzu.

4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remote Computer namens zu verwenden (der Port ist erforderlich). Sie können in `ipconfig` einer Befehlszeile verwenden, um die IPv4-Adresse zu erhalten.

    Wenn Sie die Schaltfläche " **Suchen** " verwenden möchten, müssen Sie möglicherweise den [UDP-Port 3702](#bkmk_openports) auf dem Server öffnen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben Ihres Prozess namens ein, um Ihre APP schnell zu finden.

    * Wenn Sie das [in-Process-Hostingmodell](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) auf IIS verwenden, wählen Sie den richtigen **w3wp. exe** -Prozess aus. Ab .net Core 3 ist dies die Standardeinstellung.

    * Wählen Sie andernfalls den Prozess " **dotnet. exe** " aus. (Hierbei handelt es sich um das Out-of-Process-Hostingmodell.)

    Wenn Sie über mehrere Prozesse verfügen, auf denen *w3wp. exe* oder *dotnet. exe*angezeigt wird, überprüfen Sie die Spalte **Benutzer Name** . In einigen Szenarien wird in der Spalte " **Benutzer Name** " der Name des App-Pools angezeigt, z. b. " **IIS apppool\defaultapppool**". Wenn Sie den App-Pool sehen, dies aber nicht eindeutig ist, erstellen Sie einen neuen benannten App-Pool für die app-Instanz, die Sie debuggen möchten, und Sie können ihn in der Spalte **Benutzer Name** leicht finden.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie auf **Anhängen**.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<Name_des_Remotecomputers>**.

    Es sollte die ASP.NET-Webseite angezeigt werden.

9. Klicken Sie in der Anwendung Running ASP.net **auf den Link zur Seite "** Info".

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

In den meisten Setups werden erforderliche Ports durch die Installation von ASP.net und den Remote Debugger geöffnet. Möglicherweise müssen Sie jedoch sicherstellen, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports über die [Netzwerk Sicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal)öffnen.

Erforderliche Ports:

* 80-erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024-erforderlich für das Remote Debuggen von Visual Studio 2019 (Weitere Informationen finden Sie unter [Port Zuweisungen für Remote Debugger](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-erforderlich für das Remote Debuggen von Visual Studio 2017 (Weitere Informationen finden Sie unter [Port Zuweisungen für Remote Debugger](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(optional) der suchport ermöglicht Ihnen die Schaltfläche **Suchen** , wenn Sie an den Remote Debugger in Visual Studio anhängen.

1. Öffnen Sie zum Öffnen eines Ports auf Windows Server das **Startmenü** , und suchen Sie nach **Windows-Firewall mit**erweiterter Sicherheit.

2. Wählen Sie dann **Eingehende Regeln > neue Regel > Port**aus, und klicken Sie dann auf **weiter**. (Wählen Sie für UDP 3702 stattdessen **ausgehende Regeln** aus.)

3. Geben Sie unter **bestimmte lokale Ports**die Portnummer ein, und klicken Sie auf **weiter**.

4. Klicken Sie auf **Verbindung zulassen**, und klicken Sie auf **weiter**.

5. Wählen Sie einen oder mehrere Netzwerktypen aus, die für den Port aktiviert werden, und klicken Sie auf **weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
6. Fügen Sie den Namen (z. b. **IIS**, **Web deploy**oder **msvsmon**) für die eingehende Regel hinzu, und klicken Sie auf **Fertig**stellen.

    Daraufhin sollte die neue Regel in der Liste „Eingangsregeln“ bzw. „Ausgangsregeln“ angezeigt werden.

    Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren der Windows-Firewall für das Remote Debuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.
