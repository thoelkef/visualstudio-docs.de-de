---
title: Remotedebuggen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61b1bc7f81ca4d6c3f313c543be23b746d56d37e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812893"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde.  Dazu verwenden Sie den Visual Studio Remote Debugger.  
  
 Die hier bereitgestellten Informationen gelten für Windows Desktop- und ASP.NET-Anwendungen.  Informationen zum Remotedebuggen von Windows Store apps und Azure-apps finden Sie unter [Remotedebugging für Windows Store und Azure-Webanwendungen](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Remotetools beziehen  
Sie können entweder herunterladen, die die Remoteserver-Verwaltungstools direkt auf dem Gerät oder den Server, die Sie Debuggen, oder Sie möchten die Remoteserver-Verwaltungstools von Ihrem Hostcomputer mit Visual Studio installiert, abrufen können.

### <a name="to-download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools
  
1.  Erhalten Sie auf dem Gerät oder Server-Computer, die Sie debuggen möchten (statt der Computer mit Visual Studio) die richtige Version der Remotetools.

    |Version|Link|Hinweise|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, die kostenlose Visual Studio Dev Essentials-Gruppe beitreten, oder Sie können melden Sie sich ein gültiges Visual Studio-Abonnement. Klicken Sie dann erneut öffnen Sie den Link bei Bedarf. Immer herunterladen Sie die Version, die übereinstimmende Ihr Betriebssystems des Geräts (x 86, X64 oder ARM-Version)|
    |Visual Studio 2015 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, die kostenlose Visual Studio Dev Essentials-Gruppe beitreten, oder Sie können melden Sie sich ein gültiges Visual Studio-Abonnement. Klicken Sie dann erneut öffnen Sie den Link bei Bedarf.|
    |Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download-Seite in Visual Studio 2013-Dokumentation|
    |Visual Studio 2012|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download-Seite in Visual Studio 2012-Dokumentation|
  
2.  Wählen Sie auf der Downloadseite die Version der Tools, die das Betriebssystem (x 86, X64 oder ARM-Version) entspricht, und Laden Sie die Remoteserver-Verwaltungstools.
  
    > [!IMPORTANT]
    >  Es wird empfohlen, dass Sie die neueste Version der Remotetools installieren, die Ihrer Version von Visual Studio entspricht. Nicht übereinstimmende Versionen werden nicht empfohlen.  
    >   
    >  Darüber hinaus müssen Sie die Remotetools installieren, die die gleiche Architektur wie das Betriebssystem auf dem Sie sie installieren möchten. Das heißt, sollten Sie eine 32-Bit-Anwendung auf einem Remotecomputer unter einem 64-Bit-Betriebssystem zu debuggen, müssen Sie die 64-Bit-Version der Remotetools auf dem Remotecomputer installieren.  
  
3.  Wenn Sie die ausführbare Datei heruntergeladen haben, folgen Sie den Anweisungen zum Installieren der Anwendung auf dem Remotecomputer. Finden Sie unter [– Anweisungen zur Einrichtung](#bkmk_setup)

Wenn Sie versuchen, den Remotedebugger (msvsmon.exe) auf den Remotecomputer kopieren und ausführen, müssen Sie beachten, die die **Konfigurations-Assistent für Remote Debugger** (**rdbgwiz.exe**) wird nur installiert, wenn Sie Herunterladen der Tools, und Sie müssen zum Verwenden des Assistenten für die Konfiguration später, insbesondere, wenn den Remotedebugger als Dienst ausgeführt werden sollen. Weitere Informationen finden Sie unter [(Optional) Konfigurieren des Remotedebuggers als Dienst](#bkmk_configureService) unten.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Zum Ausführen des Remotedebuggers aus einer Dateifreigabe

Sie finden den Remotedebugger (**msvsmon.exe**) auf einem Computer mit Visual Studio 2015 Community, Professional oder Enterprise bereits installiert. Die einfachste Möglichkeit zum Einrichten des Remotedebuggens werden für viele Szenarien der Remotedebugger (msvsmon.exe) aus einer Dateifreigabe ausgeführt. Einschränkungen bezüglich der, finden Sie den Remotedebugger-Hilfeseite (**Hilfe / Verwendung** in den Remotedebugger).

1. Suchen **msvsmon.exe** in das Verzeichnis, das Ihrer Version von Visual Studio entspricht. Für Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Freigabe der **Remotedebugger** Ordner auf dem Visual Studio-Computer.

3. Führen Sie auf dem Remotecomputer **msvsmon.exe**. Führen Sie die [Anweisungen zur Einrichtung des](#bkmk_setup).

> [!TIP] 
> Installation über die Befehlszeile und Befehlszeilenreferenz-finden Sie auf die Hilfeseite für **msvsmon.exe** durch Eingabe ``msvsmon.exe /?`` in der Befehlszeile auf dem Computer mit Visual Studio installiert (oder wechseln Sie zu **Hilfe / Verwendung**in den Remotedebugger).

  
## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme  
 Auf dem Remotecomputer muss eines der folgenden Betriebssysteme ausgeführt werden:  
  
-   Windows 10  
  
-   Windows 8 oder 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 oder Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Unterstützte Hardwarekonfigurationen  
  
-   1,6-GHz-Prozessor oder schneller  
  
-   1 GB RAM (1,5 GB bei Ausführung auf einem virtuellen Computer)  
  
-   1 GB verfügbarer Festplattenspeicher  
  
-   Festplatte mit 5.400 U/min  
  
-   DirectX 9-kompatible Grafikkarte mit einer Auflösung von 1024 x 768 oder höher  
  
## <a name="network-configuration"></a>Netzwerkkonfiguration  
 Der Remotecomputer und der Visual Studio-Computer müssen über ein Netzwerk, eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden bzw. mit einem Ethernetkabel direkt verbunden werden. Das Debugging über das Internet wird nicht unterstützt.  
  
## <a name="bkmk_setup"></a>Einrichten des Remotedebuggers  
 Sie müssen über Administratorberechtigungen auf dem Remotecomputer verfügen.  
  
1. Suchen Sie die Remotedebuggeranwendung. (Öffnen Sie im Startmenü, und suchen Sie nach **Remotedebugger**.)
  
    Wenn Sie den Remotedebugger auf einem Remoteserver ausführen, können Sie mit der rechten Maustaste in der Remote Debugger-app und wählen Sie **als Administrator ausführen** (oder Sie können den Remotedebugger als Dienst ausführen). Wenn Sie Sie nicht auf einem Remoteserver ausgeführt werden, starten Sie es normalerweise.
  
2. Beim Starten von Remotetools zum ersten Mal (oder bevor Sie sie konfiguriert haben), wird die **Konfiguration für Remotedebugging** Dialogfenster angezeigt wird.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Wenn die Windows-Dienst-API nicht installiert ist (Dies geschieht nur bei Windows Server 2008 R2), wählen Sie die **installieren** Schaltfläche.  
  
4. Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
5. Wählen Sie **Konfigurieren des Remotedebuggings** zum Konfigurieren der Firewall, und starten Sie das Tool.  
  
6. Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger-Fenster angezeigt.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Der Remotedebugger wartet jetzt eine Verbindung. Notieren Sie sich den Namen des Servers und die Portnummer, die angezeigt wird, da Sie dies später für die Konfiguration in Visual Studio benötigen.  
  
   Wenn Sie das Debuggen und den Remotedebugger beendet werden muss abgeschlossen werden, klicken Sie auf **Datei / beenden** im Fenster. Sie können es von den Neustart der **starten** Menü oder über die Befehlszeile:  
  
   **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger\\< X86 X64 oder Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurieren des Remotedebuggers  
 Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.
  
- Um anderen Benutzern die Verbindung mit dem Remotedebugger zu aktivieren, wählen **Extras / Berechtigungen**. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

  > [!IMPORTANT]
  > Sie können den Remotedebugger unter einem Benutzerkonto, das unterscheidet sich über das Benutzerkonto auf dem Visual Studio-Computer verwendeten ausführen, jedoch müssen Sie das andere Benutzerkonto die Berechtigungen des Remotedebuggers hinzufügen. 

   Alternativ können Sie den Remotedebugger starten, über die Befehlszeile mit der **/ allow \<Benutzername >** Parameter: **Msvsmon / allow \< username@computer>**.
  
- So ändern Sie den Authentifizierungsmodus oder die Nummer des Ports oder einen Timeoutwert für die Remotetools anzugeben: Wählen Sie **Extras / Optionen**.  
  
   Eine Liste der standardmäßig verwendeten Portnummern, finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  >  Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

##  <a name="bkmk_configureService"></a> (Optional) Konfigurieren des Remotedebuggers als Dienst
 Für das Debuggen in ASP.NET und anderen serverumgebungen, müssen Sie den Remotedebugger als Administrator ausführen oder, soll es immer ausgeführt, den den Remotedebugger als Dienst ausführen.
  
 Wenn Sie den Remotedebugger als Dienst konfigurieren möchten, gehen Sie wie folgt vor.  
  
1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (Dies ist eine vom Remotedebugger getrennte Anwendung.) Der Konfigurations-Assistent steht nur zur Verfügung, wenn Sie die Remotetools installieren, und wird nicht mit Visual Studio installiert.  
  
2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.  
  
3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .  
  
4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.  
  
    Sie müssen diesem Konto möglicherweise die Benutzerberechtigung zum **Anmelden als Dienst** hinzufügen. (Suchen Sie die **lokale Sicherheitsrichtlinie** (secpol.msc) auf der Seite bzw. im Fenster **Start** (oder geben Sie **secpol** an der Eingabeaufforderung ein). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Hinzufügen des Benutzerkontos, das die **Eigenschaften** Fenster, und klicken Sie auf **OK**.) Klicken Sie auf **Weiter**.  
  
5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.  
  
6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen**angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger**angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.  
  
7. Klicken Sie auf **Fertig stellen**.  
  
   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung / Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger**suchen.  
  
   Sie können den Remotedebugger-Dienst über **Systemsteuerung / Dienste**beenden und starten.  

## <a name="remote-debug-an-aspnet-application"></a>Remotedebuggen einer ASP.NET-Anwendung  
 Beim Bereitstellen einer ASP.NET-Anwendung auf einem Remotecomputer mit IIS sind verschiedene Schritte auszuführen, je nach Betriebssystem und IIS-Version. Für Remotecomputer mit Windows Server 2008 oder Windows Server 2012, die IIS 7.5 oder höher installiert ist, finden Sie unter [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Wenn Sie eine ASP.NET Core-app Debuggen, finden Sie unter [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html). Verschiedene Schritte sind erforderlich, um eine ASP.NET Core in IIS veröffentlichen. Nachdem Sie erfolgreich eine ASP.NET Core-app veröffentlichen, können Sie remote Debuggen [genau wie andere ASP.NET-Apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), außer dass der Prozess zum Anfügen müssen dnx.exe anstelle von w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Remotedebuggen eines Visual C++-Projekts  
 In der folgenden Prozedur den Namen und Pfad des Projekts C:\remotetemp\MyMfc, und der Name des Remotecomputers ist **MJO-DL**.  
  
1. Erstellen eine MFC-Anwendung, die mit dem Namen **Mymfc.**  
  
2. Legen Sie einen Haltepunkt an einer beliebigen Stelle in der Anwendung, die leicht, z. B. in erreicht wird **"MainFrm.cpp"**, am Anfang des `CMainFrame::OnCreate`.  
  
3. Projektmappen-Explorer mit der Maustaste auf das Projekt, und wählen **Eigenschaften**. Öffnen der **Debuggen** Registerkarte.  
  
4. Legen Sie die **zu startender Debugger** zu **Remote-Windows-Debugger**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
   |Einstellung|Wert|
   |-|-|  
   |Remotebefehl|C:\remotetemp\mymfc.exe|  
   |Arbeitsverzeichnis|C:\remotetemp|  
   |Remoteservername|MJO-DL:*Portnumber*|  
   |Verbindung|Remote mit Windows-Authentifizierung|  
   |Debuggertyp|Nur systemeigen|  
   |Bereitstellungsverzeichnis|C:\remotetemp.|  
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|  
  
    Wenn Sie zusätzliche Dateien (optional) bereitstellen, muss der Ordner auf beiden Computern vorhanden sein.  
  
6. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in der Projektmappe, und wählen Sie **Configuration Manager**.  
  
7. Für die **Debuggen** Konfiguration der **bereitstellen** Kontrollkästchen.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Mit dem Debuggen beginnen (**Debuggen / Debugging starten**, oder **F5**).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Netzwerk eine Verbindung zum Remotecomputer herstellen.  
  
     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Sie können z. B. auf einem Computer, wählen Sie ein Sicherheitszertifikat oder geben Sie Ihren Domänennamen und Kennwort. Auf einem Computer nicht mit der Domäne möglicherweise eingegebenen Namen des Computers und einen gültigen Benutzerkontonamen an, wie z. B. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort.  
  
11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    >  Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. In der **Projektmappen-Explorer** mit der rechten Maustaste die **Mymfc** Knoten und wählen Sie dann **bereitstellen**.  
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen einen Projektordner für die zusätzlichen Dateien (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen / neue Ordner**.) Fügen Sie dann die Dateien in den Ordner hinzu (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen / vorhandenen Element**, wählen Sie die Dateien.). Auf der **Eigenschaften** Seite für jede Datei **in Ausgabeverzeichnis kopieren** zu **immer kopieren**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Remotedebugging eines Visual C#- oder Visual Basic-Projekts  
 Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Das folgende Verfahren wird davon ausgegangen, dass Sie auf dem Computer debuggen möchten **MJO-DL**, wie in der Abbildung oben gezeigt.
  
1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.  
  
    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Zu diesem Zweck öffnen Sie "MainWindow.xaml" aus der Toolbox fügen Sie ein Button-Steuerelement hinzu, und doppelklicken Sie auf die Schaltfläche, um deren Ereignishandler zu öffnen.
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.  
  
4. Auf der **Eigenschaften** Seite die **Debuggen** Registerkarte.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Stellen Sie sicher, dass die **Arbeitsverzeichnis** Textfeld leer ist.  
  
6. Wählen Sie **Remotecomputer**, und geben **MJO-DL:4020** in das Textfeld ein. (4020 ist die Portnummer im Remotedebugger-Fenster gezeigt).  
  
7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht ausgewählt ist.  
  
8. Erstellen Sie das Projekt.  
  
9. Erstellen Sie einen Ordner auf dem Remotecomputer, die den gleichen Pfad wie die **Debuggen** Ordner auf Ihrem Computer Visual Studio:  **\<Quellpfad > \MyWPF\MyWPF\bin\Debug**.  
  
10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.
  
    > [!CAUTION]
    >  Nehmen Sie keine Änderungen an den Code oder neu erstellen (oder Sie müssen diesen Schritt wiederholen). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren, verwenden von Xcopy, Robocopy, Powershell oder andere Optionen.
  
11. Stellen Sie sicher, dass der Remotedebugger auf dem Zielcomputer ausgeführt wird. (Wenn es nicht der Fall ist, suchen Sie nach **Remotedebugger** in die **starten** Menü. ) Das Remotedebugger-Fenster sieht wie folgt aus.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Debuggen in Visual Studio starten (**Debuggen / Debugging starten**, oder **F5**).  
  
13. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Netzwerk eine Verbindung zum Remotecomputer herstellen.  
  
     Die erforderlichen Anmeldeinformationen variieren je nach Sicherheitskonfiguration Ihres Netzwerks. Auf einem Computer, können Sie beispielsweise Ihren Domänennamen und ein Kennwort eingeben. Auf einem Computer nicht mit der Domäne möglicherweise eingegebenen Namen des Computers und einen gültigen Benutzerkontonamen an, wie z. B. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.
  
14. Führen Sie gegebenenfalls die Aktion, die der Haltepunkt erreicht. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die die Symbole für die Anwendung nicht geladen. Wiederholen Sie dann, und wenn dies nicht funktioniert, erhalten Sie Informationen zum Laden von Symbolen und wie sie auf Probleme bei [Grundlegendes zu Symboldateien und Visual Studio symboleinstellungen](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen einen Projektordner für die zusätzlichen Dateien (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen / neue Ordner**.) Fügen Sie dann die Dateien in den Ordner hinzu (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen / vorhandenen Element**, wählen Sie die Dateien.). Auf der **Eigenschaften** Seite für jede Datei **in Ausgabeverzeichnis kopieren** zu **immer kopieren**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen  
 Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  
  
 Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Weitere Informationen finden Sie in der Hilfe zum Remotedebugging (drücken Sie die **F1** im Remotedebugger-Fenster, oder klicken Sie auf **Hilfe / Verwendung**). Sie können weitere Informationen finden unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 und 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Remotedebugging in Windows Store und Azure-apps  
 Informationen zum Remotedebuggen mit Windows Store-apps finden Sie unter [Debuggen und Testen von Windows Store-apps auf einem Remotegerät in Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informationen zum Debuggen in Azure finden Sie in den folgenden Themen:  
  
-   [Debuggen eines Cloud-Diensts oder eines virtuellen Computers in Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Debuggen des .NET-Backends in Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Einführung in das Remotedebuggen auf Azure-Websites ([Teil 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Teil 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Teil 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurieren der Windows-Firewalls für Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)



