---
title: Remote Debuggen von ASP.NET auf einem Remote-IIS-Computer | Microsoft Docs
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 6f11ec81c740a6930ce4eaef16d4e4e389aaca47
ms.sourcegitcommit: 65f85389047c5a1938b6d5243ccba8d4f14362ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remote-IIS-Computer
Um eine ASP.NET-Anwendung debuggen, die in IIS bereitgestellt wurde, installieren Sie und führen Sie der Remotetools auf dem Computer aus, auf denen Sie Ihre app bereitgestellt haben, und fügen Sie an der ausgeführten app aus Visual Studio.

![Remotedebugger-Komponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Dieses Handbuch erläutert das Einrichten eine Visual Studio 2017 ASP.NET MVC 4.5.2-Anwendung, für IIS bereitstellen und Konfigurieren von Visual Studio remote Debugger anfügen. Zum Remotedebuggen ASP.NET Core finden Sie unter [Remote Debuggen ASP.NET Core auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Für Azure App Service, können Sie bereitstellen und Debuggen auf einer vorkonfigurierten Instanz von IIS mithilfe der [Momentaufnahme Debugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 erforderlich) oder durch [das Anfügen des Debuggers aus Server-Explorer](../debugger/remote-debugging-azure.md).

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2 Server die Schritte sind verschiedene)

## <a name="requirements"></a>Anforderungen

Der Remotedebugger wird unter Windows Server ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debuggen zwischen zwei Computern über einen Proxy verbunden wird nicht unterstützt. Remotedebuggen über eine hohe Latenz oder eine Verbindung mit geringer Bandbreite, z. B. DFÜ, Internet oder über das Internet Ländern wird nicht empfohlen und möglicherweise fehl oder sehr langsam sein.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen Sie die ASP.NET 4.5.2 Anwendung auf dem Visual Studio-Computer
  
1. Erstellen Sie eine neue MVC ASP.NET-Anwendung. (**Datei > Neu > Projekt**, und wählen Sie dann ** Visual c# > Web > ASP.NET-Webanwendung. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC**aus. Stellen Sie sicher, dass **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierung** festgelegt ist, um **keine Authentifizierung**. Nennen Sie das Projekt **MyASPApp**.)

2. Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()` -Methode fest.

## <a name="bkmk_configureIIS"></a>Installieren und Konfigurieren von IIS unter WindowsServer

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren von Browsersicherheitseinstellungen unter Windows Server

Je nach Ihren Sicherheitseinstellungen kann es Speicherzeit Sie Ihren Browser die folgenden vertrauenswürdigen Sites hinzugefügt werden, damit Sie problemlos in diesem Lernprogramm beschriebene Software herunterladen können. Möglicherweise müssen Sie den Zugriff auf diese Websites:

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- visualstudio.com

Wenn Sie Internet Explorer verwenden, können Sie den vertrauenswürdigen Sites hinzufügen, navigieren Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**. Diese Schritte sind für andere Browser unterschiedlich. (Wenn Sie eine ältere Version des Remotedebuggers von my.visualstudio.com herunterladen müssen, sind einige zusätzliche vertrauenswürdige Websites erforderlich, sich anzumelden.)

Wenn Sie die Software heruntergeladen haben, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen gewähren. In den meisten Fällen sind die folgenden zusätzlichen Ressourcen beim Installieren der Clientsoftware nicht erforderlich.

## <a name="BKMK_deploy_asp_net"></a>Installieren Sie ASP.NET 4.5 unter WindowsServer

Wenn Sie ausführlichere Informationen zur ASP.NET auf IIS installieren möchten, finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Verwenden Sie den Webplattform-Installer (WebPI), um ASP.NET 4.5 installieren (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Das System neu starten (oder führen Sie **net Stop wurde/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung am System Pfad übernehmen).

## <a name="BKMK_install_webdeploy"></a>(Optional) Installieren Sie Web Deploy 3.6 unter WindowsServer

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>Konfigurieren Sie ASP.NET-Website, auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem ASP.NET-Projekt später bereitstellen möchten.

2. Öffnen der **Internetinformationsdienste (IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** im linken Bereich, wechseln Sie zu **Sites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischen Pfad** auf **C:\Publish**.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardnamen Anwendungspool (**DefaultAppPool**), und legen Sie die **physischen Pfad** auf  **C:\Publish**.

7. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist keine Option für den Anwendungspool).

8. Mit den Standort im IIS-Manager ausgewählt haben, wählen Sie **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie IUSR als ein Benutzer Berechtigungen für Lesen & ausführen.

## <a name="bkmk_webdeploy"></a>(Optional) Veröffentlichen und Bereitstellen der app mithilfe von Web Deploy von Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

Darüber hinaus möglicherweise auf den Abschnitt lesen [Problembehandlung Ports](#bkmk_openports).

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichen und Bereitstellen der Anwendung in einen lokalen Ordner durch die Veröffentlichung aus Visual Studio

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

## <a name="BKMK_msvsmon"></a>Herunterladen Sie und installieren Sie die Remoteserver-Verwaltungstools für Windows Server

In diesem Lernprogramm verwenden wir 2017 von Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten, führen Sie den Remotedebugger aus einer Dateifreigabe sein. Weitere Informationen finden Sie unter [führen Sie den Remotedebugger aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a>Einrichten des Remotedebuggers unter Windows Server

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

## <a name="bkmk_openports"></a>Zur Fehlerbehebung: Öffnen Sie erforderlichen Ports auf Windows Server

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