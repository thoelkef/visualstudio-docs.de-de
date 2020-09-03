---
title: Remote Debuggen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300566"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde.  Dazu verwenden Sie den Visual Studio Remote Debugger.  
  
 Die hier bereitgestellten Informationen gelten für Windows Desktop- und ASP.NET-Anwendungen.  Weitere Informationen zum Remote Debuggen von Windows Store-Apps und Azure-apps finden Sie unter [Remote Debugging für Windows Store und Azure-apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Remote Tools  
Sie können die Remote Tools entweder direkt auf das Gerät oder den Server herunterladen, das Sie debuggen möchten, oder Sie können die Remote Tools von Ihrem Host Computer mit installierter Installation von Visual Studio herunterladen.

### <a name="to-download-and-install-the-remote-tools"></a>So laden Sie die Remote Tools herunter und installieren Sie
  
1. Holen Sie sich auf dem Gerät oder Server Computer, den Sie debuggen möchten (statt auf dem Computer, auf dem Visual Studio ausgeführt wird), die richtige Version der Remote Tools.

    |Version|Link|Hinweise|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, treten Sie der Gruppe Free Visual Studio dev Essentials bei, oder Sie können sich einfach mit einem gültigen Visual Studio-Abonnement anmelden. Öffnen Sie den Link ggf. erneut. Herunterladen der Version, die mit Ihrem Geräte Betriebssystem übereinstimmt (x86, x64 oder arm-Version)|
    |Visual Studio 2015 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, treten Sie der Gruppe Free Visual Studio dev Essentials bei, oder Sie können sich einfach mit einem gültigen Visual Studio-Abonnement anmelden. Öffnen Sie den Link ggf. erneut.|
    |Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Downloadseite in der Visual Studio 2013-Dokumentation|
    |Visual Studio 2012|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Downloadseite in der Visual Studio 2012-Dokumentation|
  
2. Wählen Sie auf der Downloadseite die Version der Tools aus, die Ihrem Betriebssystem entspricht (x86, x64 oder arm-Version), und laden Sie die Remote Tools herunter.
  
    > [!IMPORTANT]
    > Es wird empfohlen, die neueste Version der Remote Tools zu installieren, die Ihrer Version von Visual Studio entspricht. Nicht übereinstimmende Versionen werden nicht empfohlen.  
    >   
    >  Außerdem müssen Sie die Remote Tools installieren, die über die gleiche Architektur verfügen wie das Betriebssystem, auf dem Sie das Betriebssystem installieren möchten. Anders ausgedrückt: Wenn Sie eine 32-Bit-Anwendung auf einem Remote Computer debuggen möchten, auf dem ein 64-Bit-Betriebssystem ausgeführt wird, müssen Sie die 64-Bit-Version der Remote Tools auf dem Remote Computer installieren.  
  
3. Wenn Sie die ausführbare Datei heruntergeladen haben, folgen Sie den Anweisungen zum Installieren der Anwendung auf dem Remotecomputer. Siehe [Setup Anweisungen](#bkmk_setup)

Wenn Sie versuchen, den Remote Debugger (msvsmon.exe) auf den Remote Computer zu kopieren und ihn auszuführen, beachten Sie, dass der remotedebuggerkonfigurations- **Assistent** (**rdbgwiz.exe**) nur beim Herunterladen der Tools installiert ist. möglicherweise müssen Sie den Assistenten später für die Konfiguration verwenden, insbesondere dann, wenn der Remote Debugger als Dienst ausgeführt werden soll. Weitere Informationen finden Sie unter [(optional) konfigurieren Sie den Remote Debugger als Dienst](#bkmk_configureService) weiter unten.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>So führen Sie den Remote Debugger über eine Dateifreigabe aus

Sie können den Remote Debugger (**msvsmon.exe**) auf einem Computer finden, auf dem Visual Studio 2015 Community, Professional oder Enterprise bereits installiert ist. In vielen Szenarios ist die einfachste Möglichkeit zum Einrichten des Remote Debuggens das Ausführen des Remote Debuggers (msvsmon.exe) aus einer Dateifreigabe. Informationen zu den Nutzungsbeschränkungen finden Sie auf der Hilfeseite des Remote Debuggers (**Hilfe/Verwendung** im Remote Debugger).

1. Suchen Sie **msvsmon.exe** in dem Verzeichnis, das Ihrer Version von Visual Studio entspricht. Visual Studio 2015:

      **Programme\Microsoft Visual Studio 14,0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programme\Microsoft Visual Studio 14,0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Geben Sie den Ordner **Remote Debugger** auf dem Computer mit Visual Studio frei.

3. Führen Sie **msvsmon.exe**auf dem Remote Computer aus. Befolgen Sie die [Setupanweisungen](#bkmk_setup).

> [!TIP] 
> Informationen zur Befehlszeilen Installation und Befehlszeilen Referenz finden Sie auf der Hilfeseite für **msvsmon.exe** , indem ``msvsmon.exe /?`` Sie in der Befehlszeile auf dem Computer eingeben, auf dem Visual Studio installiert ist (oder zu " **Hilfe/Verwendung** " im Remote Debugger wechseln).

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme  
 Auf dem Remotecomputer muss eines der folgenden Betriebssysteme ausgeführt werden:  
  
- Windows 10  
  
- Windows 8 oder 8.1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 oder Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Unterstützte Hardwarekonfigurationen  
  
- 1,6-GHz-Prozessor oder schneller  
  
- 1 GB RAM (1,5 GB bei Ausführung auf einem virtuellen Computer)  
  
- 1 GB verfügbarer Festplattenspeicher  
  
- Festplatte mit 5.400 U/min  
  
- DirectX 9-kompatible Grafikkarte mit einer Auflösung von 1024 x 768 oder höher  
  
## <a name="network-configuration"></a>Netzwerkkonfiguration  
 Der Remotecomputer und der Visual Studio-Computer müssen über ein Netzwerk, eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden bzw. mit einem Ethernetkabel direkt verbunden werden. Das Debugging über das Internet wird nicht unterstützt.  
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Einrichten des Remote Debuggers  
 Sie müssen über Administratorberechtigungen auf dem Remotecomputer verfügen.  
  
1. Suchen Sie die Remotedebuggeranwendung. (Öffnen Sie das Startmenü, und suchen Sie nach **Remote Debugger**.)
  
    Wenn Sie den Remote Debugger auf einem Remote Server ausführen, können Sie mit der rechten Maustaste auf die remotedebuggerapp klicken und **als Administrator ausführen** auswählen (oder Sie können den Remote Debugger als Dienst ausführen). Wenn Sie Sie nicht auf einem Remote Server ausführen, starten Sie Sie einfach.
  
2. Wenn Sie die Remote Tools zum ersten Mal starten (oder bevor Sie Sie konfiguriert haben), wird das Feld **remotedebugkonfigurationskonfigurations** -dalog angezeigt.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Wenn die Windows-Dienst-API nicht installiert ist (Dies geschieht nur unter Windows Server 2008 R2), klicken Sie auf die Schaltfläche **Installieren** .  
  
4. Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
5. Wählen Sie **Remote Debugging konfigurieren** aus, um die Firewall zu konfigurieren und das Tool zu starten.  
  
6. Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger-Fenster angezeigt.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Der Remotedebugger wartet nun auf eine Verbindung. Notieren Sie sich den Servernamen und die Portnummer, die angezeigt werden, da Sie diese später für die Konfiguration in Visual Studio benötigen.  
  
   Wenn Sie das Debuggen abgeschlossen haben und den Remote Debugger beenden müssen, klicken Sie im-Fenster auf **Datei/beenden** . Sie können ihn über das **Startmenü** oder über die Befehlszeile neu starten:  
  
   ** \<Visual Studio installation directory> \Common7\ide\remotedebugger \\<x86, x64 oder Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurieren des Remotedebuggers  
 Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.
  
- Um anderen Benutzern das Herstellen einer Verbindung mit dem Remote Debugger zu ermöglichen, wählen Sie Extras > **Berechtigungen**aus. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

  > [!IMPORTANT]
  > Sie können den Remotedebugger unter einem anderen Benutzerkonto als dem auf dem Visual Studio-Computer verwendeten Benutzerkonto ausführen, allerdings müssen Sie das andere Benutzerkonto den Berechtigungen des Remotedebuggers hinzufügen. 

   Alternativ können Sie den Remote Debugger über die Befehlszeile mit dem **/Allow \<username> ** -Parameter starten: **msvsmon/Allow \<username@computer> **.
  
- Um den Authentifizierungsmodus oder die Portnummer zu ändern oder um einen Timeout Wert für die Remote Tools anzugeben, wählen Sie Extras > **Optionen**aus.  
  
   Eine Liste der standardmäßig verwendeten Portnummern finden Sie unter [Remotedebugger-Portzuweisungen](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Optional) Konfigurieren des Remotedebuggers als Dienst
 Zum Debuggen in ASP.NET und anderen Serverumgebungen müssen Sie den Remotedebugger als Administrator ausführen. Wenn Sie möchten, dass er immer ausgeführt wird, müssen Sie den Remotedebugger als Dienst ausführen.
  
 Wenn Sie den Remotedebugger als Dienst konfigurieren möchten, führen Sie die folgenden Schritte aus.  
  
1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (Dies ist eine vom Remotedebugger getrennte Anwendung.) Der Konfigurations-Assistent steht nur zur Verfügung, wenn Sie die Remotetools installieren, und wird nicht mit Visual Studio installiert.  
  
2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.  
  
3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .  
  
4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.  
  
    Sie müssen diesem Konto möglicherweise die Benutzerberechtigung zum **Anmelden als Dienst** hinzufügen. (Suchen Sie die **lokale Sicherheitsrichtlinie** (secpol.msc) auf der Seite bzw. im Fenster **Start** (oder geben Sie **secpol** an der Eingabeaufforderung ein). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Fügen Sie das Benutzerkonto zum Fenster **Eigenschaften** hinzu, und klicken Sie auf **OK**.) Klicken Sie auf **weiter**.  
  
5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.  
  
6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen**angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger**angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.  
  
7. Klicken Sie auf **Fertig stellen**.  
  
   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung/Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger**suchen.  
  
   Sie können den Remote Debugger-Dienst über die **Systemsteuerung/Dienste**starten und starten.  

## <a name="remote-debug-an-aspnet-application"></a>Remotedebuggen einer ASP.NET-Anwendung  
 Beim Bereitstellen einer ASP.NET-Anwendung auf einem Remotecomputer mit IIS sind verschiedene Schritte auszuführen, je nach Betriebssystem und IIS-Version. Für Remote Computer, auf denen Windows Server 2008 oder Windows Server 2012 mit IIS 7,5 oder höher ausgeführt wird, finden Sie weitere Informationen [unter Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Wenn Sie eine ASP.net Core-App Debuggen, finden Sie weitere Informationen unter [Veröffentlichen in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Zum Veröffentlichen einer ASP.net Core auf IIS sind verschiedene Schritte erforderlich. Nachdem Sie eine ASP.net Core-App erfolgreich veröffentlicht haben, können Sie Sie [wie andere ASP.net-apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)Remote Debuggen, mit dem Unterschied, dass der Prozess, an den Sie anhängen müssen, anstelle w3wp.exe dnx.exe ist.

## <a name="remote-debug-a-visual-c-project"></a>Remotedebuggen eines Visual C++-Projekts  
 Im folgenden Verfahren lautet der Name und der Pfad des Projekts „C:\remotetemp\MyMfc“ und der Name des Remotecomputers **MJO-DL**.  
  
1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.  
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Öffnen Sie die Registerkarte **Debuggen**.  
  
4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
   |Einstellung|Wert|
   |-|-|  
   |Remote-Befehl|C:\remotetemp\mymfc.exe|  
   |Arbeitsverzeichnis|C:\remotetemp|  
   |Remoteservername|MJO-DL:*Portnummer*|  
   |Verbindung|Remote mit Windows-Authentifizierung|  
   |Debuggertyp|Nur systemeigen|  
   |Bereitstellungsverzeichnis|C:\remotetemp.|  
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|  
  
    Wenn Sie zusätzliche Dateien bereitstellen (optional), muss der Ordner auf beiden Computern vorhanden sein.  
  
6. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Konfigurations-Manager** aus.  
  
7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Starten Sie das Debugging (**Debuggen/Debuggen starten**oder **F5**).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. Geben Sie Netzwerkanmeldeinformationen ein, wenn Sie dazu aufgefordert werden, um eine Verbindung mit dem Remotecomputer herzustellen.  
  
     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Beispielsweise können Sie auf einem Domänencomputer ein Sicherheitszertifikat auswählen oder den Domänennamen und das Kennwort eingeben. Auf einem Computer, der kein Domänencomputer ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen wie <strong>MJO-DL\name@something.com</strong> zusammen mit dem richtigen Kennwort eingeben.  
  
11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    > Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.  
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (Klicken Sie im **Projektmappen-Explorer**auf Hinzufügen > **neuer Ordner**.) Fügen Sie dann die Dateien dem Ordner hinzu (Klicken Sie im **Projektmappen-Explorer**auf Hinzufügen > **Vorhandenes Element**, und wählen Sie dann die Dateien aus.). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Remotedebugging eines Visual C#- oder Visual Basic-Projekts  
 Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Bei der folgenden Prozedur wird davon ausgegangen, dass Sie Sie auf einem Computer mit dem Namen **mjo-DL Debuggen**möchten, wie in der obigen Abbildung gezeigt.
  
1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.  
  
    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Öffnen Sie hierzu die Datei „MainWindow.xaml“, und fügen Sie ein Schaltflächensteuerelement aus der Toolbox hinzu. Doppelklicken Sie dann auf die Schaltfläche, um ihren Handler zu öffnen.
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**.  
  
4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.  
  
6. Wählen Sie **Remote Computer verwenden**aus, und geben Sie **mjo-DL: 4020** in das Textfeld ein. (4020 ist die im Remote Debugger-Fenster angezeigte Portnummer).  
  
7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.  
  
8. Erstellen Sie das Projekt.  
  
9. Erstellen Sie auf dem Remote Computer einen Ordner, bei dem es sich um den gleichen Pfad wie der **Debugordner** auf Ihrem Visual Studio-Computer handelt: ** \<source path> \mywpf\mywpf\bin\debug**.  
  
10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.
  
    > [!CAUTION]
    > Führen Sie keine Änderungen und keine Neuerstellung des Codes aus (andernfalls müssen Sie diesen Schritt wiederholen). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren oder XCopy, Robocopy, PowerShell oder andere Optionen verwenden.
  
11. Stellen Sie sicher, dass der Remote Debugger auf dem Zielcomputer ausgeführt wird. (Wenn dies nicht der Fall ist, suchen Sie im **Startmenü** nach **Remote Debugger** . ) Das Fenster Remote Debugger sieht wie folgt aus.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Starten Sie in Visual Studio das Debuggen (**Debuggen/Debuggen starten**oder **F5**).  
  
13. Geben Sie Netzwerkanmeldeinformationen ein, wenn Sie dazu aufgefordert werden, um eine Verbindung mit dem Remotecomputer herzustellen.  
  
     Die erforderlichen Anmeldeinformationen unterscheiden sich abhängig von der Sicherheitskonfiguration Ihres Netzwerks. Auf einem Domänencomputer können Sie z. B den Domänennamen und das Kennwort eingeben. Auf einem Computer, der kein Domänencomputer ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen wie <strong>MJO-DL\name@something.com</strong> zusammen mit dem richtigen Kennwort eingeben.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.
  
14. Nehmen Sie ggf. Maßnahmen zum Erreichen des Breakpoints vor. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die die Symbole für die Anwendung nicht geladen. Versuchen Sie es erneut, und wenn dies nicht funktioniert, erhalten Sie Informationen zum Laden von Symbolen und zur Problembehandlung in [den Symbol Dateien und in den Symbol Einstellungen von Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (Klicken Sie im **Projektmappen-Explorer**auf Hinzufügen > **neuer Ordner**.) Fügen Sie dann die Dateien dem Ordner hinzu (Klicken Sie im **Projektmappen-Explorer**auf Hinzufügen > **Vorhandenes Element**, und wählen Sie dann die Dateien aus.). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen  
 Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  
  
 Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Weitere Informationen finden Sie in der Hilfe zum Remote Debugging (drücken Sie **F1** im Remote Debugger-Fenster, oder klicken Sie auf **Hilfe/Verwendung**). Weitere Informationen finden Sie unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013 (Änderungen beim Laden von Symbolen in der .NET-Remoteinstanz in Visual Studio 2012 und 2013)](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Remote Debuggen in Windows Store und Azure-apps  
 Weitere Informationen zum Remote Debuggen mit Windows Store-Apps finden Sie unter [Debuggen und Testen von Windows Store-Apps auf einem Remote Gerät aus Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informationen zum Debuggen in Azure finden Sie in den folgenden Themen:  
  
- [Debuggen eines Clouddiensts oder eines virtuellen Computers in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debuggen des .NET-Backends in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Einführung in das Remote Debuggen auf Azure-Websites ([Teil 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Teil 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Teil 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurieren der Windows-Firewall für das Remote Debuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger-Port Zuweisungen](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
