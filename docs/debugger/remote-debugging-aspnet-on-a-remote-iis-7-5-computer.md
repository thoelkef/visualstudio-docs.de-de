---
title: Remotedebuggen von ASP.NET auf einem Computer mit IIS
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 86b035164c4d34f4ce0182ea51fdfe6381ad2d4f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536020"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS
Zum Debuggen einer ASP.NET-Anwendung, die in IIS bereitgestellt wurde, installieren und führen Sie die Remote Tools auf dem Computer aus, auf dem Sie die APP bereitgestellt haben, und fügen Sie dann in Visual Studio an ihre laufende APP an.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In diesem Handbuch wird erläutert, wie Sie eine Visual Studio ASP.NET MVC 4.5.2-Anwendung einrichten und konfigurieren, Sie in IIS bereitstellen und den Remote Debugger aus Visual Studio anfügen.

> [!NOTE]
> Informationen zum Remote Debuggen von ASP.net Core finden Sie unter [Remote Debug ASP.net Core auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Für Azure App Service können Sie problemlos auf einer vorkonfigurierten IIS-Instanz bereitstellen und Debuggen, indem Sie entweder die [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 erforderlich) oder [den Debugger aus Server-Explorer](../debugger/remote-debugging-azure.md)anfügen.

## <a name="prerequisites"></a>Erforderliche Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

Diese Prozeduren wurden auf diesen Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2 unterscheiden sich die Server Schritte)

## <a name="network-requirements"></a>Netzwerkanforderungen

Der Remote Debugger wird von Windows Server ab Windows Server 2008 Service Pack 2 unterstützt. Eine umfassende Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Das Debuggen zwischen zwei mit einem Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, wie z. b. ddas Internet oder über das Internet über das Internet hinweg, wird nicht empfohlen und schlägt möglicherweise fehl oder ist nicht akzeptabel.

## <a name="app-already-running-in-iis"></a>Die APP wird bereits in IIS ausgeführt?

Dieser Artikel enthält die Schritte zum Einrichten einer grundlegenden Konfiguration von IIS unter Windows Server und zum Bereitstellen der APP aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server erforderliche Komponenten installiert sind, dass die APP ordnungsgemäß ausgeführt werden kann und dass Sie für das Remote Debuggen bereit sind.

* Wenn Ihre APP in IIS ausgeführt wird und Sie nur den Remote Debugger herunterladen und das Debuggen starten möchten, wechseln Sie zu [herunterladen und Installieren der Remote Tools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre APP in IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie Debuggen können, führen Sie alle Schritte in diesem Thema aus.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET 4.5.2-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue MVC ASP.NET-Anwendung.

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **ASP.net**ein, wählen Sie **Vorlagen**aus, und wählen Sie dann **neue ASP.NET Webanwendung erstellen (.NET Framework)** aus. Benennen Sie im angezeigten Dialogfeld das Projekt **myaspapp**, und wählen Sie dann **Erstellen**aus. Wählen Sie **MVC** aus, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Um dies in Visual Studio 2017 zu tun, wählen Sie **Datei > Neues > Projekt**und **dann C# Visual > web > ASP.NET Webanwendung**aus. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC**aus. Stellen Sie sicher, dass **docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierung** auf **keine Authentifizierung**festgelegt ist. Nennen Sie das Projekt **myaspapp**.)
    ::: moniker-end

2. Öffnen Sie die Datei *HomeController.cs* , und legen Sie einen Haltepunkt in der `About()`-Methode fest.

## <a name="bkmk_configureIIS"></a>Installieren und Konfigurieren von IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browser-Sicherheitseinstellungen unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserver Komponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internet Optionen > Sicherheits > vertrauenswürdige Sites > Websites**wechseln. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Website Skripts und Ressourcen. Einige dieser Ressourcen sind nicht erforderlich, um den Prozess zu vereinfachen, klicken Sie auf **Hinzufügen** , wenn Sie dazu aufgefordert werden.

## <a name="BKMK_deploy_asp_net"></a>Installieren von ASP.NET 4,5 unter Windows Server

Ausführlichere Informationen zur Installation von ASP.net auf IIS finden Sie unter [IIS 8,0 Using ASP.NET 3,5 and ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Wählen Sie im linken Bereich Server-Manager **IIS**aus. Klicken sie zuerst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internet Information Services (IIS) Manager** (Internetinformationsdienste-Manager).

1. Verwenden Sie den Webplattform-Installer (webpi) zum Installieren von ASP.NET 4,5 (über den Server Knoten in Windows Server 2012 R2, wählen Sie **neue Webplattform-Komponenten erhalten** aus, und suchen Sie dann nach ASP.net).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie stattdessen ASP.NET 4 mit dem folgenden Befehl:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

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

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die APP nicht über Visual Studio gestartet wird, starten Sie die app in IIS.

1. Aktivieren Sie im Dialogfeld " **Einstellungen** " das Debuggen, indem Sie auf **weiter**klicken, eine **Debugkonfiguration** auswählen und dann unter den Optionen für die **Datei Veröffentlichung** **Weitere Dateien am Ziel entfernen** auswählen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie das Debuggen in der Datei " *Web. config* ", wenn Sie veröffentlichen.

1. Klicken Sie auf **Speichern** , und veröffentlichen Sie die APP erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Optionale Bereitstellen durch veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre APP bereitzustellen, wenn Sie die App mithilfe von PowerShell, Robocopy in IIS kopieren möchten, oder wenn Sie die Dateien manuell kopieren möchten.

### <a name="BKMK_deploy_asp_net"></a>Konfigurieren der ASP.NET-Website auf dem Windows Server-Computer

1. Öffnen Sie Windows-Explorer, und erstellen Sie einen neuen Ordner, **c:\publish**, in dem Sie später das ASP.net-Projekt bereitstellen.

2. Wenn Sie nicht bereits geöffnet ist, öffnen Sie den **Internetinformationsdienste (IIS)-Manager**. (Klicken Sie im linken Bereich Server-Manager auf **IIS**. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Wechseln Sie im linken Bereich unter **Verbindungen** zu **Websites**.

4. Wählen Sie die **Standard Website**aus, und wählen Sie **Grundeinstellungen**aus, und legen Sie den **physischen Pfad** auf **c:\publish**fest.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Legen Sie für das Feld **Alias** den Wert **myaspapp**fest, akzeptieren Sie den Standard Anwendungs Pool (**DefaultAppPool**), und legen Sie den **physischen Pfad** auf **c:\publish**fest.

7. Wählen Sie unter **Verbindungen**die Option **Anwendungs Pools**aus. Öffnen Sie **DefaultAppPool** , und legen Sie das Feld Anwendungs Pool auf **ASP.NET v 4.0** fest (ASP.NET 4,5 ist keine Option für den Anwendungs Pool).

8. Wählen Sie bei ausgewählter Website im IIS-Manager die Option **Berechtigungen bearbeiten**aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der für den Anwendungs Pool konfigurierte Benutzer ein autorisierter Benutzer mit Lese-& Ausführungsrechte ist. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie IUSR als Benutzer mit Lese-& Ausführungsrechte hinzu.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der app durch veröffentlichen in einem lokalen Ordner in Visual Studio

Sie können die APP auch mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen.

1. (ASP.NET 4.5.2) Stellen Sie sicher, dass in der Datei "Web. config" die richtige Version von .net aufgeführt ist.  Wenn Sie z. b. ASP.NET 4.5.2 als Ziel festlegen, stellen Sie sicher, dass diese Version in "Web. config" aufgeführt ist.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Beispielsweise sollte die Version 4,0 lauten, wenn Sie ASP.NET 4 anstelle von 4.5.2 installieren.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Herunterladen und Installieren der Remote Tools unter Windows Server

Laden Sie die Version der Remote Tools herunter, die Ihrer Version von Visual Studio entspricht.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a>Einrichten des Remote Debuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remote Debugger ändern müssen, finden Sie weitere Informationen unter [configure the Remote Debugger](../debugger/remote-debugging.md#configure_msvsmon).

Weitere Informationen zum Ausführen des Remote Debuggers als Dienst finden Sie unter [Run the Remote Debugger as a Service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projekt Mappe, die Sie debuggen möchten (**myaspapp** , wenn Sie die Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (STRG + ALT + P).

    > [!TIP]
    > In Visual Studio 2017 und höheren Versionen können Sie den Prozess, an den Sie zuvor angefügt haben, erneut an denselben Prozess anfügen, den Sie zuvor mit **Debuggen > an den Prozess anfügen...** (UMSCHALT + ALT + P).

3. Legen Sie das Feld Qualifizierer auf **\<remote Computername >** und drücken **Sie die Eingabe**Taste.

    Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im folgenden Format angezeigt wird: **\<remote Computername >:p Ort** .

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 sollte **\<remote Computername > angezeigt werden: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 sollte **\<remote Computername > angezeigt werden: 4022**
    ::: moniker-end
    Der Port ist erforderlich. Wenn die Portnummer nicht angezeigt wird, fügen Sie Sie manuell hinzu.

4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remote Computer namens zu verwenden (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile verwenden, um die IPv4-Adresse zu erhalten.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben eines Prozess namens ein, um **w3wp. exe** für ASP.NET 4,5 schnell zu finden.

    Wenn Sie über mehrere Prozesse verfügen, auf denen **w3wp. exe**angezeigt wird, überprüfen Sie die Spalte **Benutzer Name** . In einigen Szenarien wird in der Spalte " **Benutzer Name** " der Name des App-Pools angezeigt, z. b. " **IIS apppool\defaultapppool**". Wenn Sie den App-Pool sehen, ist es einfach, den richtigen Prozess zu ermitteln, indem Sie einen neuen benannten App-Pool für die app-Instanz erstellen, die Sie debuggen möchten, und Sie können ihn dann problemlos in der Spalte **Benutzer Name** finden.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie auf **Attach** (Anhängen).

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<Name_des_Remotecomputers>** .

    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der Anwendung Running ASP.net **auf den Link zur Seite "** Info".

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

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

2. Wählen Sie dann **Eingehende Regeln > neue Regel > Port**aus. Wählen **Sie weiter** aus, und geben Sie unter **bestimmte lokale Ports**die Portnummer ein. Klicken Sie dann auf **weiter**, **lassen Sie die Verbindung**zu, klicken Sie auf Weiter, und fügen Sie den Namen (**IIS**, **Web deploy**oder **msvsmon**) für die eingehende Regel hinzu.

    Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren der Windows-Firewall für das Remote Debuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.