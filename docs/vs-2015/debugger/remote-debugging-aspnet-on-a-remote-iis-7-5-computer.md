---
title: Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5 Computer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de51ed1cda2116b1f3b8b698be6e4653a1b648fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513969"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS-Computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](https://docs.microsoft.com/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer).  
  
Sie können eine ASP.NET-Webanwendung auf einem Windows Server-Computer mit IIS bereitstellen und für das Remotedebuggen einrichten. Dieses Handbuch wird erläutert, wie einrichten und konfigurieren Sie eine Visual Studio 2015 MVC 4.5.2-Anwendung, in IIS bereitstellen, und fügen Sie den Remotedebugger in Visual Studio.

Diese Prozeduren haben auf diese Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 10
* Windows Server 2008 R2 und IIS 7.5

Die meisten der Informationen in diesem Artikel gilt auch für das Remotedebuggen einer ASP.NET Core-Anwendung, außer dass die Bereitstellung von ASP.NET Core-apps unterscheidet sich und sind zusätzliche Schritte erforderlich. Zum Bereitstellen einer ASP.NET Core-Apps in IIS müssen Sie alle Abschnitte des Abschließens [in diesem Artikel](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Voraussetzungen: Installieren des Remotedebuggers auf dem Windows Server-computer

Anweisungen dazu, wie Sie den Remotedebugger auf dem Windows Server-Computer herunterladen, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

Zum Remotedebuggen von ASP.NET-Anwendungen, können Sie die remotedebuggeranwendung als Administrator ausführen oder den Remotedebugger als Dienst gestartet. Ausführliche Informationen zum auszuführen des Remotedebuggers als Dienst Sie unter finden [Remotedebuggen](../debugger/remote-debugging.md).

Nachdem sie installiert ist, stellen Sie sicher, dass der Remotedebugger auf dem Zielcomputer ausgeführt wird. (Wenn es nicht der Fall ist, suchen Sie nach **Remotedebugger** in die **starten** Menü. ) Das Remotedebugger-Fenster sieht wie folgt aus. (4020 ist die Standardportnummer)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Erstellen der Anwendung auf dem Visual Studio-Computer  
  
1. Erstellen Sie eine neue MVC ASP.NET-Anwendung. (Wählen Sie**Datei / Neu / Projekt**und dann **Visual C# / Web / ASP.NET-Webanwendung** aus. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC**aus. Stellen Sie sicher, dass **Host in der Cloud** nicht unter dem Abschnitt "Azure" ausgewählt ist. Nennen Sie das Projekt **Meinmvc**.)
1. Öffnen Sie die Datei „HomeController.cs“, und legen Sie einen Haltepunkt in der `About()` -Methode fest.
1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.
1. Wählen Sie für **Veröffentlichungsziel auswählen**die Option **Benutzerdefiniert** aus, und nennen Sie das Profil **MeinMVC**. Klicken Sie auf **Weiter**.
1. Legen Sie auf der Registerkarte **Verbindung** das Feld **Veröffentlichungsmethode** auf **Dateisystem** und das Feld **Zielspeicherort** auf ein lokales Verzeichnis fest. Klicken Sie auf **Weiter**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Legen Sie die Konfiguration auf **Debuggen**fest. Klicken Sie auf **Veröffentlichen**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Die Anwendung sollte in das lokale Verzeichnis veröffentlicht werden.

## <a name="BKMK_deploy_asp_net"></a> Bereitstellen der ASP.NET-Anwendung auf dem Windows Server-Remotecomputer

 In diesem Abschnitt wird davon ausgegangen, dass die Windows Server-Computer IIS bereits aktiviert ist. Unter Windows Server 2012 R2, finden Sie unter [IIS-Konfiguration](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) um IIS zu aktivieren. (Sie können anderen Abschnitten dieses Artikels überspringen, es sei denn, Sie versuchen, eine ASP.NET Core-app bereitzustellen. Führen Sie für ASP.NET Core die Schritte im Artikel zum Bereitstellen der app anstelle der hier beschriebenen Schritte.)
1. Installieren Sie ASP.NET verwenden die Webkomponenten für die Plattform zum Installieren von ASP.NET 4.5 (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Auf Windows Server 2008 R2, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl: **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe - Ir**
1. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer in ein lokales Verzeichnis (das wir **C:\Publish**nennen) auf dem Windows Server-Computer. Sie können das Projekt manuell kopieren, verwenden von Xcopy, Web Deploy, Robocopy, Powershell oder andere Optionen.

    > [!CAUTION]
    >  Wenn Sie den Code oder die Neuerstellung ändern möchten, müssen Sie erneut veröffentlichen und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.
1. Stellen Sie sicher, dass in der Datei „web.config“ die richtige Version von .NET Framework aufgeführt ist.  Beispielsweise wird standardmäßig auf Windows Server 2008 R2 installierte .NET Framework-Version ist 4.0.30319, aber wir haben eine ASP.NET 4.5.2 erstellt Version. Wenn eine app für ASP.NET 4.0 auf dem Windows Server-Computer ausgeführt wird, müssen Sie die Version zu ändern:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.
1. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.
1. Legen Sie die **Alias** Feld **Meinmvc** und das Feld "Anwendungspool" auf **ASP.NET v4. 0** (ASP.NET 4.5 ist eine Option für den Anwendungspool nicht). Legen Sie den **physischen Pfad** auf **C:\Publish** fest (in den Sie das ASP.NET-Projektverzeichnis kopiert haben).

    >[!NOTE] 
    > Legen Sie für ASP.NET Core-apps, auf das Feld "Anwendungspool" **kein verwalteter Code**.
1. Testen der Bereitstellung mit der rechten Maustaste **Default Web Site** , und wählen Sie **Durchsuchen**.
    Wenn Sie die app erfolgreich bereitgestellt haben, sehen Sie die Webseite.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projektmappe **MeinMVC** .
1. Klicken Sie in Visual Studio auf **Debuggen / an den Prozess anhängen** (**Strg + Alt + P**).
1. Legen Sie auf das Feld "Qualifizierer"  **\<Name des Remotecomputers >: 4020**.
1. Klicken Sie auf **aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn alle Prozesse, die nicht angezeigt wird, versuchen Sie den Namen des Remotecomputers (der Port ist erforderlich.) anstelle der IP-Adresse. Verwendung `ipconfig` in einer Befehlszeile, um die IPv4-Adresse zu erhalten.
1. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.
1. Suchen Sie nach **w3wp.exe** , und klicken Sie auf **Anfügen**.

     Um schnell den Prozessnamen zu suchen, geben Sie den ersten Buchstaben des Prozesses.
     
    >[!NOTE]
    > Wählen Sie für eine ASP.NET Core-app den dnx.exe-Prozess statt w3wp.exe. (Dieser Prozessname kann in einer zukünftigen Version ändern.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Öffnen Sie die Website des Remotecomputers. Wechseln Sie in einem Browser zu **http://\<Remotecomputernamen >**.
    
    Es sollte die ASP.NET-Webseite angezeigt werden.
1. Klicken Sie auf der Webseite von ASP.NET auf den Link, um die **zu** Seite.

    Der Haltepunkt sollte in Visual Studio erreicht werden.



