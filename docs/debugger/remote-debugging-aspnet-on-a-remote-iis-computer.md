---
title: Remote-Debug-ASP.NET Core auf einem Remote-IIS-Computer | Microsoft Docs
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
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385477"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remotedebug ASP.NET Core auf einem Remote-IIS-Computer in Visual Studio

Um eine ASP.NET Core-Anwendung zu debuggen, die in IIS bereitgestellt wurde, installieren und führen Sie die Remotetools auf dem Computer aus, auf dem Sie Ihre App bereitgestellt haben, und fügen Sie dann an die ausgeführte App aus Visual Studio an.

![Remote-Debuggerkomponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In diesem Handbuch wird erläutert, wie Sie ein Visual Studio-ASP.NET Core einrichten und konfigurieren, es in IIS bereitstellen und den Remotedebugger aus Visual Studio anfügen. Informationen zum Remotedebuggen ASP.NET 4.5.2 finden Sie unter [Remotedebug-ASP.NET auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Sie können IIS auch mithilfe von Azure bereitstellen und debuggen. Für Azure App Service können Sie einfach auf einer vorkonfigurierten Instanz von IIS und dem Remotedebugger mithilfe des [Snapshot-Debuggers](../debugger/debug-live-azure-applications.md) oder durch [Anfügen des Debuggers aus dem Server-Explorer](../debugger/remote-debugging-azure.md)bereitstellen und debuggen.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 muss die in diesem Artikel beschriebenen Schritte ausführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 muss die in diesem Artikel beschriebenen Schritte ausführen.
::: moniker-end

Diese Verfahren wurden an diesen Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10

## <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei Computern, die über einen Proxy verbunden sind, wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder geringer Bandbreite, z. B. DFÜ-Internet, oder über das Internet zwischen Ländern wird nicht empfohlen und kann fehlschlagen oder unannehmbar langsam sein. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>App läuft bereits in IIS?

Dieser Artikel enthält Schritte zum Einrichten einer grundlegenden Konfiguration von IIS auf Windows-Server und zum Bereitstellen der App über Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server erforderliche Komponenten installiert sind, dass die App ordnungsgemäß ausgeführt werden kann und dass Sie zum Remotedebuggen bereit sind.

* Wenn Ihre App in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und mit dem Debuggen beginnen möchten, gehen Sie zu [Herunterladen und Installieren der Remotetools auf Windows Server](#BKMK_msvsmon).

* Wenn Sie helfen möchten, um sicherzustellen, dass Ihre App in IIS eingerichtet, bereitgestellt und ordnungsgemäß ausgeführt wird, damit Sie debuggen können, führen Sie alle Schritte in diesem Thema aus.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET Core-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.NET Core-Webanwendung. 

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **Strg + Q** ein, um das Suchfeld zu öffnen, geben Sie **asp.net**ein, wählen Sie **Vorlagen**aus, und wählen Sie dann neue ASP.NET Core Web **Application erstellen**. Benennen Sie im angezeigten Dialogfeld das Projekt **MyASPApp**, und wählen Sie dann **Erstellen**aus. Wählen Sie als Nächstes **Webapplication (Model-View-Controller)** aus, und wählen Sie dann **Erstellen**aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > Neues >-Projekt**aus, und wählen Sie dann **Visual C- > Web > ASP.NET Core Web Application aus.** Wählen Sie im Abschnitt ASP.NET Core-Vorlagen **Webapplication (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.NET Core 2.1 ausgewählt ist, dass **Docker-Support aktivieren** nicht ausgewählt ist und dass **die Authentifizierung** auf **Keine Authentifizierung**festgelegt ist. Benennen Sie das Projekt **MyASPApp**.
    ::: moniker-end

4. Öffnen Sie die About.cshtml.cs Datei, `OnGet` und legen Sie einen Haltepunkt in der Methode `About()` fest (in älteren Vorlagen öffnen Sie stattdessen HomeController.cs und legen Sie den Haltepunkt in der Methode fest).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installieren und Konfigurieren von IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren der Browsersicherheitseinstellungen auf Windows Server

Wenn die erweiterte Sicherheitskonfiguration in Internet Explorer aktiviert ist (standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserverkomponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internetoptionen > Sicherheit > vertrauenswürdige Sites > Sites**gehen. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen, die die Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen erteilen. Einige dieser Ressourcen sind nicht erforderlich, aber um den Prozess zu vereinfachen, klicken Sie auf **Hinzufügen,** wenn Sie dazu aufgefordert werden.

## <a name="install-aspnet-core-on-windows-server"></a>Installieren ASP.NET Core auf Windows Server

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

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner, **C:-Publish**, in dem Sie später das ASP.NET Core-Projekt bereitstellen.

2. Wenn es noch nicht geöffnet ist, öffnen Sie den **IIS-Manager (Internet Information Services).** (Wählen Sie im linken Bereich von Server Manager **IIS**aus. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Wechseln Sie unter **Verbindungen** im linken Bereich zu **Sites**.

4. Wählen Sie die **Standardwebsite**aus , wählen Sie **Grundlegende Einstellungen**aus, und legen Sie den **physischen Pfad** auf **C:'Publish**' fest.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Legen Sie das **Alias-Feld** auf **MyASPApp**fest, akzeptieren Sie den Standardanwendungspool (**DefaultAppPool**), und legen Sie den **physischen Pfad** auf **C:-Veröffentlichung**fest.

6. Wählen Sie unter **Verbindungen**die Option **Anwendungspools**aus. Öffnen Sie **DefaultAppPool,** und legen Sie das Feld Anwendungspool auf **Kein verwalteter Code**fest.

7. Klicken Sie im IIS-Manager mit der rechten Maustaste auf die neue Website, wählen Sie **Berechtigungen bearbeiten**aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der für den Zugriff auf die Web-App konfigurierte Benutzer ein autorisierter Benutzer mit Lese- & Ausführungsrechten ist.

    Wenn einer dieser Benutzer nicht mit Zugriff angezeigt wird, führen Sie Schritte durch, um IUSR als Benutzer mit Lese- & Ausführungsrechten hinzuzufügen.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichen und Bereitstellen der App durch Veröffentlichen in einem lokalen Ordner aus Visual Studio

Sie können die App auch mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Herunterladen und Installieren der Remotetools auf Windows Server

Laden Sie die Version der Remotetools herunter, die Ihrer Version von Visual Studio entsprechen.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Einrichten des Remotedebuggers auf Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen müssen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Informationen zum Ausführen des Remotedebuggers als Dienst finden Sie unter [Ausführen des Remotedebuggers als Dienst](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>An den ASP.NET Anwendung vom Visual Studio-Computer anfügen

1. Öffnen Sie auf dem Visual Studio-Computer die Lösung, die Sie debuggen möchten **(MyASPApp,** wenn Sie alle Schritte in diesem Artikel ausführen).
2. Klicken Sie in Visual Studio auf **Debuggen > an Den Prozess anfügen** (Strg + Alt + P).

    > [!TIP]
    > In Visual Studio 2017 und neueren Versionen können Sie denselben Prozess erneut anfügen, an den Sie zuvor angefügt haben, indem Sie **Debug > Anfügen an Prozess...** (Umschalt + Alt + P) verwenden.

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

    * Wenn Sie das [In-App-Hostingmodell](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) auf IIS verwenden, wählen Sie den richtigen **w3wp.exe-Prozess** aus. Ab .NET Core 3 ist dies die Standardeinstellung.

    * Andernfalls wählen Sie den **prozessiaus/dotnet.exe** aus. (Dies ist das out-of-Process-Hostingmodell.)

    Wenn mehrere Prozesse *an der Datei w3wp.exe* oder *dotnet.exe*angezeigt werden, überprüfen Sie die Spalte **Benutzername.** In einigen Szenarien zeigt die Spalte **Benutzername** Ihren App-Poolnamen an, z. B. **IIS APPPOOL-DefaultAppPool**. Wenn der App-Pool angezeigt wird, er jedoch nicht eindeutig ist, erstellen Sie einen neuen app-Pool mit dem Namen für die App-Instanz, die Sie debuggen möchten, und dann finden Sie ihn einfach in der Spalte **Benutzername.**

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Problembehandlung Öffnen Sie die erforderlichen Ports unter Windows Server

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und des Remote-Debuggers geöffnet. Möglicherweise müssen Sie jedoch überprüfen, ob Ports geöffnet sind.

> [!NOTE]
> Auf einer Azure-VM müssen Sie Ports über die [Netzwerksicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal)öffnen.

Erforderliche Ports:

* 80 - Erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024 - Erforderlich für Remote-Debugging aus Visual Studio 2019 (weitere Informationen finden Sie unter [Remotedebugger-Portzuweisungen).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Erforderlich für Remote-Debugging aus Visual Studio 2017 (weitere Informationen finden Sie unter [Remotedebugger-Portzuweisungen).](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* Mit dem UDP 3702 - (Optional) Discovery-Port können Sie die Schaltfläche **Suchen** verwenden, wenn Sie an den Remotedebugger in Visual Studio angefügt werden.

1. Um einen Port auf Windows Server zu öffnen, öffnen Sie das **Startmenü,** suchen Sie nach **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **eingehende Regeln > neue Regel > Port**aus, und klicken Sie dann auf **Weiter**. (Wählen Sie für UDP 3702 stattdessen **ausgehende Regeln** aus.)

3. Klicken Sie unter **Spezifische lokale Ports**auf die Portnummer, und klicken Sie auf **Weiter**.

4. Klicken Sie auf **Verbindung zulassen**, klicken Sie auf **Weiter**.

5. Wählen Sie einen oder mehrere Netzwerktypen aus, die für den Port aktiviert werden sollen, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
6. Fügen Sie den Namen (z. B. **IIS**, **Web Deploy**oder **msvsmon**) für die eingehende Regel hinzu, und klicken Sie auf **Fertig stellen**.

    Daraufhin sollte die neue Regel in der Liste „Eingangsregeln“ bzw. „Ausgangsregeln“ angezeigt werden.

    Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren der Windows-Firewall für Remotedebugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports.
