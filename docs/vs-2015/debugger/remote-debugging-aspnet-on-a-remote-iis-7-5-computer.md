---
title: Remote Debuggen ASP.net auf einem Remote Computer mit IIS 7,5 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841061"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem IIS-Remotecomputer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine ASP.NET-Webanwendung auf einem Windows Server-Computer mit IIS bereitstellen und für das Remote Debuggen einrichten. In diesem Handbuch wird erläutert, wie Sie eine Visual Studio 2015 MVC 4.5.2-Anwendung einrichten und konfigurieren, Sie in IIS bereitstellen und den Remote Debugger aus Visual Studio anfügen.

Diese Verfahren wurden für die folgenden Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 10
* Windows Server 2008 R2 und IIS 7,5

Die meisten Informationen in diesem Artikel gelten auch für das Remote Debuggen einer ASP.net Core Anwendung, mit der Ausnahme, dass die Bereitstellung von ASP.net Core-apps anders ist und zusätzliche Schritte erforderlich sind. Zum Bereitstellen einer ASP.net Core-app in IIS müssen Sie alle Abschnitte in [diesem Artikel](https://docs.asp.net/en/latest/publishing/iis.html)ausführen.

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Voraussetzungen: Installieren Sie den Remote Debugger auf dem Windows Server-Computer.

Anweisungen dazu, wie Sie den Remote Debugger auf den Windows Server-Computer herunterladen, finden Sie unter [Remote Debugging](../debugger/remote-debugging.md).

Zum Remote Debuggen von ASP.NET-Anwendungen können Sie entweder die Remote Debugger-Anwendung als Administrator ausführen oder den Remote Debugger als Dienst starten. Ausführliche Informationen zum Ausführen des Remotedebuggers als Dienst finden Sie unter [Remote Debugging](../debugger/remote-debugging.md).

Stellen Sie nach der Installation sicher, dass der Remote Debugger auf dem Zielcomputer ausgeführt wird. (Wenn dies nicht der Fall ist, suchen Sie im **Startmenü** nach **Remote Debugger** . ) Das Fenster Remote Debugger sieht wie folgt aus. (4020 ist die Standard Portnummer)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Erstellen der Anwendung auf dem Visual Studio-Computer  
  
1. Erstellen Sie eine neue MVC ASP.NET-Anwendung. (Wählen Sie**Datei / Neu / Projekt**und dann **Visual C# / Web / ASP.NET-Webanwendung** aus. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC**aus. Stellen Sie sicher, dass der **Host in der Cloud** im Azure-Abschnitt nicht ausgewählt ist. Nennen Sie das Projekt " **mymvc**".)
1. Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()` -Methode fest.
1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.
1. Wählen Sie für **Veröffentlichungsziel auswählen**die Option **Benutzerdefiniert** aus, und nennen Sie das Profil **MeinMVC**. Klicken Sie auf **Weiter**.
1. Legen Sie auf der Registerkarte **Verbindung** das Feld **Veröffentlichungsmethode** auf **Dateisystem** und das Feld **Zielspeicherort** auf ein lokales Verzeichnis fest. Klicken Sie auf **Weiter**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Legen Sie die Konfiguration auf **Debuggen**fest. Klicken Sie auf **Veröffentlichen**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Die Anwendung sollte in das lokale Verzeichnis veröffentlicht werden.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Bereitstellen der ASP.NET-Anwendung auf dem Windows Server-Remote Computer

 In diesem Abschnitt wird davon ausgegangen, dass IIS bereits auf dem Windows Server-Computer aktiviert ist. Informationen zu Windows Server 2012 R2 finden Sie unter [IIS-Konfiguration](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) zum Aktivieren von IIS. (Sie können auch andere Abschnitte dieses Artikels überspringen, es sei denn, Sie versuchen, eine ASP.net Core-App bereitzustellen. Führen Sie für ASP.net Core die Schritte im Artikel zum Bereitstellen der APP anstelle der hier beschriebenen Schritte aus.)
1. Installieren ASP.NET verwenden Sie die Webplattform-Komponenten zum Installieren von ASP.NET 4,5 (über den Server Knoten in Windows Server 2012 R2, wählen Sie **neue Webplattform-Komponenten erhalten** aus, und suchen Sie dann nach ASP.net).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Installieren Sie unter Windows Server 2008 R2 stattdessen ASP.NET 4 mit dem folgenden Befehl:   **c:\WINDOWS\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-IR**
1. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer in ein lokales Verzeichnis (das wir **C:\Publish**nennen) auf dem Windows Server-Computer. Sie können das Projekt manuell kopieren und xcopy, Web deploy, Robocopy, PowerShell oder andere Optionen verwenden.

    > [!CAUTION]
    > Wenn Sie Änderungen am Code vornehmen müssen, müssen Sie die Veröffentlichung erneut ausführen und diesen Schritt wiederholen. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.
1. Stellen Sie sicher, dass in der Datei „web.config“ die richtige Version von .NET Framework aufgeführt ist.  Beispielsweise ist die .NET Framework Version, die standardmäßig unter Windows Server 2008 R2 installiert ist, 4.0.30319, aber wir haben eine ASP.NET 4.5.2-Version erstellt. Wenn eine ASP.NET 4,0-App auf dem Windows Server-Computer ausgeführt wird, müssen Sie die Version ändern:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.
1. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.
1. Legen Sie das Feld **Alias** auf **mymvc** und das Feld Anwendungs Pool auf **ASP.NET v 4.0** fest (ASP.NET 4,5 ist keine Option für den Anwendungs Pool). Legen Sie den **physischen Pfad** auf **C:\Publish** fest (in den Sie das ASP.NET-Projektverzeichnis kopiert haben).

    >[!NOTE] 
    > Legen Sie für ASP.net Core-apps das Feld Anwendungs Pool auf **keinen verwalteten Code**fest.
1. Testen Sie die Bereitstellung, indem Sie mit der rechten Maustaste auf **Standard Website** klicken und **Durchsuchen**auswählen
    Wenn Sie die APP erfolgreich bereitgestellt haben, wird die Webseite angezeigt.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projektmappe **MeinMVC** .
1. Klicken Sie in Visual Studio auf **Debuggen > an den Prozess anhängen** (**STRG + ALT + P**).
1. Legen Sie das Feld Qualifizierer auf ** \<remote computer name> : 4020**fest.
1. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remotecomputernamens zu verwenden (der Port ist erforderlich). Verwenden Sie `ipconfig` in der Befehlszeile, um die IPv4-Adresse zu erhalten.
1. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
1. Suchen Sie nach **w3wp.exe** , und klicken Sie auf **Anfügen**.

     Um den Prozessnamen schnell zu ermitteln, geben Sie den ersten Buchstaben des Prozesses ein.
     
    >[!NOTE]
    > Wählen Sie für eine ASP.net Core-App den dnx.exe Prozess anstelle w3wp.exe aus. (Dieser Prozess Name kann sich in einer zukünftigen Version ändern.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<remote computer name>** .
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
1. Klicken Sie auf der ASP.NET-Webseite **auf den Link zur Seite "** Info".

    Der Haltepunkt sollte in Visual Studio erreicht werden.
