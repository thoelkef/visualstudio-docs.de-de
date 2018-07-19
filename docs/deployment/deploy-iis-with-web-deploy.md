---
title: Bereitstellen von ASP.NET in IIS mit Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080849"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Bereitstellen von ASP.NET in einem IIS-Remotecomputer in Visual Studio mit Web Deploy

In diesem Artikel erläutert das Einrichten und konfigurieren eine Visual Studio 2017 ASP.NET MVC 4.5.2-Anwendung in IIS bereitstellen. Dieser Artikel enthält Schritte zum Einrichten einer Standardkonfiguration von IIS unter Windows Server und das Bereitstellen der app aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass es sich bei der Server installierte Komponenten erforderlich ist und Sie bereitstellen möchten. Wenn Sie eine ASP.NET Core-Anwendung bereitstellen, unterscheiden sich einige Schritte ausführen. Zum Bereitstellen einer ASP.NET Core-Apps finden Sie unter [Veröffentlichen einer Anwendung in IIS durch das Importieren der veröffentlichungseinstellungen](../deployment/tutorial-import-publish-settings-iis.md) Anweisungen. In einigen Szenarien ASP.NET- und ASP.NET Core wird schneller bereitstellen, IIS, durch das Importieren der veröffentlichungseinstellungen.

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2, die Server Schritte unterscheiden sich)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen von ASP.NET 4.5.2 auf Visual Studio-Computer
  
1. Wählen Sie auf dem Computer mit Visual Studio, **Datei** > **neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)**, und klicken Sie dann auf **OK**.

    Wenn die angegebene-Projektvorlagen nicht angezeigt wird, klicken Sie auf die **Visual Studio-Installer öffnen** Link im linken Bereich des der **neues Projekt** Dialogfeld. Der Visual Studio-Installer wird gestartet. Siehe die Voraussetzungen in diesem Artikel sind die erforderlichen Visual Studio-arbeitsauslastungen, die installiert werden muss.

1. Wählen Sie **MVC** ((.NET Framework) und stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen** > **Projektmappe** zum Erstellen des Projekts.

## <a name="install-and-configure-iis-on-windows-server"></a>Installieren und Konfigurieren von IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Browser-Sicherheitseinstellungen auf Windows Server aktualisieren

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (er ist standardmäßig aktiviert), müssen Sie einige Domänen als vertrauenswürdige Sites, um einige der Web-Server-Komponenten herunterladen können hinzufügen. Der vertrauenswürdigen Sites hinzufügen, indem Sie zu **Internetoptionen** > **Sicherheit** > **vertrauenswürdigen Sites** > **Websites** . Fügen Sie den folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- IIS.NET

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen an die Berechtigung zum Laden von verschiedenen Website-Skripts und Ressourcen zu erteilen. Einige dieser Ressourcen sind nicht erforderlich, jedoch zur Vereinfachung des Prozesses, klicken Sie auf **hinzufügen** Aufforderung.

## <a name="install-aspnet-45-on-windows-server"></a>Installieren Sie ASP.NET 4.5 auf WindowsServer

Weitere ausführliche Informationen zum Installieren von ASP.NET in IIS, finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.

1. Verwenden Sie den Webplattform-Installer (WebPI) installieren Sie ASP.NET 4.5 (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl aus:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Das System neu starten (oder führen Sie **net Stop was/y** gefolgt von **Net start w3svc** über eine Eingabeaufforderung, um eine Änderung an den Systempfad zu übernehmen).

## <a name="install-web-deploy-36-on-windows-server"></a>Installieren Sie Web Deploy-3.6 unter WindowsServer

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Konfigurieren von ASP.NET Web Site auf dem Windows Server-computer

1. Öffnen Sie Windows Explorer, und erstellen Sie einen neuen Ordner **C:\Publish**, in dem Sie später das ASP.NET-Projekt bereitstellen.

2. Wenn sie nicht bereits geöffnet ist, öffnen Sie die **(Internet Information Services, IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** wechseln Sie im linken Bereich zu **Websites**.

4. Wählen Sie die **Default Web Site**, wählen Sie **Grundeinstellungen**, und legen Sie die **physischer Pfad** zu **C:\Publish**.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

6. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardwert-Anwendungspool (**DefaultAppPool**), und legen Sie die **physischer Pfad** zu  **C:\Publish**.

7. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist eine Option für den Anwendungspool nicht).

8. Wählen Sie den Standort ausgewählt im IIS-Manager, **Berechtigungen bearbeiten**, und stellen Sie sicher, diese IUSR, IIS_IUSRS oder der Benutzer, die für den Anwendungspool ein autorisierter Benutzer mit Berechtigungen für Lesen & ausführen wird konfiguriert. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie als Benutzer mit Lesen & Ausführen an IUSR-Konto hinzu.

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>Veröffentlichen und Bereitstellen der app mithilfe von Web Deploy in Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Darüber hinaus müssen Sie möglicherweise im folgenden Abschnitt zur Problembehandlung von Ports zu lesen.

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Bei der Problembehandlung: Öffnen Sie erforderlichen Ports auf Windows Server

In den meisten Setups werden die erforderlichen Ports durch die Installation von ASP.NET und Web Deploy geöffnet. Allerdings müssen Sie sicherstellen, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einem virtuellen Azure-Computer müssen Sie Ports durch Öffnen der [Netzwerksicherheitsgruppe](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Erforderliche Ports:

* 80 - wird für IIS erforderlich.
* 8172 – erforderlich für Web Deploy, um die app aus Visual Studio bereitstellen

1. Öffnen Sie zum Öffnen eines Ports in Windows Server die **starten** Menü, und suchen Sie **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **Eingangsregeln** > **neue Regel** > **Port**. Wählen Sie **Weiter** und wählen Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer, und klicken Sie auf **Weiter**, klicken Sie dann **Verbindung zulassen,**, klicken Sie auf Weiter, und Fügen Sie den Namen (**IIS**, **Web Deploy**, oder **"msvsmon"**) für die eingehende Regel.

    Wenn Sie weitere Informationen zum Windows-Firewall konfigurieren möchten, finden Sie unter [konfigurieren Sie die Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie zusätzliche Regeln für die anderen erforderlichen Ports an.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erstellt eine Datei mit veröffentlichungseinstellungen importiert es in Visual Studio und eine ASP.NET-App in IIS bereitgestellt. Sie können auch bereitstellen, durch das Importieren der veröffentlichungseinstellungen.

> [!div class="nextstepaction"]
> [Bereitstellen in IIS durch das Importieren der veröffentlichungseinstellungen](../deployment/tutorial-import-publish-settings-iis.md)
