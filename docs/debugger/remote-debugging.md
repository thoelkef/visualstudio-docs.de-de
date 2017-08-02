---
title: "Remotedebugging | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.remote.overview"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "JScript"
  - "VB"
helpviewer_keywords: 
  - "Remotedebugging, Setup"
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 76
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Remotedebugging
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Visual Studio\-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde.  Dazu verwenden Sie den Visual Studio Remote Debugger.  
  
 Die hier bereitgestellten Informationen gelten für Windows Desktop\- und ASP.NET\-Anwendungen.  Informationen zum Remotedebugging von Windows Store\-Apps und Azure\-Apps finden Sie unter [Remotedebugging in Windows Store und Azure-Apps](#bkmk_winstoreAzure).  
  
## Herunterladen und Installieren der Remotetools  
 Sie können die Remotetools für das Debuggen unter [Remotetools für Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48155) herunterladen. Wählen Sie zwischen den x86\-, x64\- und ARM\-Versionen der Tools aus. Wenn Sie die ausführbare Datei heruntergeladen haben, folgen Sie den Anweisungen zum Installieren der Anwendung auf dem Remotecomputer.  
  
 Sie können die Version „Update 1“ der Remotetools unter [Remotetools für Visual Studio 2015 Update 1](https://www.microsoft.com/en-us/download/details.aspx?id=49986&44F86079-8679-400C-BFF2-9CA5F2BCBDFC=1) herunterladen.  
  
> [!IMPORTANT]
>  Sie müssen die Version der Remotetools installieren, die der Version Ihrer Visual Studio\-Installation entspricht. Nicht übereinstimmende Versionen werden nicht unterstützt. Darüber hinaus müssen Sie die Remotetools installieren, die die gleiche Architektur wie die Anwendung aufweisen, die Sie debuggen möchten. Mit anderen Worten, wenn Sie eine 64\-Bit\-Anwendung debuggen möchten, müssen Sie die 64\-Bit\-Version der Remotetools installieren.  
  
 Ist auf dem Remotecomputer bereits Visual Studio 2015 Community, Professional oder Enterprise installiert, ist auch der Remotedebugger \(**msvsmon.exe**\) bereits installiert, und Sie können ihn aus dem folgenden Verzeichnis starten:  
  
 **\<Visual Studio\-Installationsverzeichnis\>\\Common7\\IDE\\Remote Debugger\\\(x64, x86, Appx\)\\msvsmon.exe**  
  
 Der **Konfigurations\-Assistent für Remote Debugger** \(**rdbgwiz.exe**\) wird allerdings nur installiert, wenn Sie die Tools herunterladen und installieren, und Sie müssen ihn möglicherweise später für die Konfiguration verwenden, insbesondere, wenn der Remotedebugger als Dienst ausgeführt werden soll. Weitere Informationen finden Sie weiter unten unter [Konfigurieren des Remotedebuggers als Dienst](#bkmk_configureService).  
  
## Unterstützte Betriebssysteme  
 Auf dem Remotecomputer muss eines der folgenden Betriebssysteme ausgeführt werden:  
  
-   Windows 10  
  
-   Windows 8 oder 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 oder Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## Unterstützte Hardwarekonfigurationen  
  
-   1,6\-GHz\-Prozessor oder schneller  
  
-   1 GB RAM \(1,5 GB bei Ausführung auf einem virtuellen Computer\)  
  
-   1 GB verfügbarer Festplattenspeicher  
  
-   Festplatte mit 5.400 U\/min  
  
-   DirectX 9\-kompatible Grafikkarte mit einer Auflösung von 1024 x 768 oder höher  
  
## Netzwerkkonfiguration  
 Der Remotecomputer und der Visual Studio\-Computer müssen über ein Netzwerk, eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden bzw. mit einem Ethernetkabel direkt verbunden werden. Das Debugging über das Internet wird nicht unterstützt.  
  
## Einrichten des Remotedebuggers  
 Sie müssen über Administratorberechtigungen auf dem Remotecomputer verfügen.  
  
1.  Suchen Sie die Remotedebuggeranwendung. Sie können im Menü **Start**  nach **Remotedebugger** suchen.  
  
2.  Wenn Sie die Remotetools zum ersten Mal starten \(oder bevor Sie sie konfiguriert haben\), wird das Dialogfenster **Konfiguration für Remotedebugging** angezeigt.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3.  Wenn die Windows\-Dienst\-API nicht installiert ist \(geschieht nur auf Windows Server 2008 R2\), klicken Sie auf die Schaltfläche **Installieren**.  
  
4.  Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
5.  Wählen Sie **Remotedebugging konfigurieren** aus, um die Firewall zu konfigurieren und das Tool zu starten.  
  
6.  Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger\-Fenster angezeigt.  
  
     ![RemoteDebuggerWindow](~/docs/debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
 Sie können den Remotedebugger beenden, indem Sie in diesem Fenster auf **Datei \/ Beenden**. Sie können ihn über das Menü **Start** oder über die Befehlszeile neu starten:  
  
 **\<Visual Studio\-Installationsverzeichnis\>\\Common7\\IDE\\Remote Debugger\\\<x86, x64 oder Appx\>\\msvsmon.exe**.  
  
## Konfigurieren des Remotedebuggers  
 Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.  
  
-   Um anderen Benutzern zu ermöglichen, eine Verbindung mit dem Remotedebugger herzustellen, wählen Sie **Extras \> Berechtigungen** aus. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.  
  
-   Um den Authentifizierungsmodus oder die Portnummer zu ändern oder einen Timeoutwert für die Remotetools anzugeben, wählen Sie „Extras \> Optionen“ aus.  
  
     Eine Liste der standardmäßig verwendeten Portnummern finden Sie unter [Remotedebugger \- Portzuweisungen](../debugger/remote-debugger-port-assignments.md).  
  
> [!WARNING]
>  Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.  
  
##  <a name="bkmk_configureService"></a> Konfigurieren des Remotedebuggers als Dienst  
 Zum Debuggen in ASP.NET und anderen Serverumgebungen muss der Remotedebugger als Dienst ausgeführt werden.  
  
1.  Suchen Sie den **Konfigurations\-Assistenten für Remote Debugger** \(rdbgwiz.exe\). \(Dies ist eine vom Remotedebugger getrennte Anwendung.\) Der Konfigurations\-Assistent steht nur zur Verfügung, wenn Sie die Remotetools installieren, und wird nicht mit Visual Studio installiert.  
  
2.  Starten Sie den Konfigurations\-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen**.  
  
4.  Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.  
  
     Sie müssen diesem Konto möglicherweise die Benutzerberechtigung zum **Anmelden als Dienst** hinzufügen. \(Suchen Sie die **lokale Sicherheitsrichtlinie** \(secpol.msc\) auf der Seite bzw. im Fenster **Start** \(oder geben Sie **secpol** an der Eingabeaufforderung ein\). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Fügen Sie das Benutzerkonto zum Fenster **Eigenschaften** hinzu, und klicken Sie auf **OK**.\) Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.  
  
6.  Wenn der Dienst gestartet werden kann, wird **Der Konfigurations\-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen** angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger** angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
 An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung \/ Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger** suchen.  
  
 Sie können den Remotedebugger\-Dienst über **Systemsteuerung \/ Dienste** beenden und starten.  
  
## Ausführen des Remotedebuggers unter anderen Benutzerkonten  
 Es ist möglich, den Remotedebugger unter einem anderen Benutzerkonto als dem auf dem Visual Studio\-Computer verwendeten Benutzerkonto auszuführen, allerdings müssen Sie das andere Benutzerkonto zu den Berechtigungen des Remotedebuggers hinzufügen.  
  
-   Sie können den Remotedebugger über die Befehlszeile mit dem **\/allow \<Benutzername\>**\-Parameter erneut starten: **msvsmon \/allow \<Benutzername@Computer\>**.  
  
-   Sie können den Benutzer den Remotedebuggerberechtigungen \(im Remotedebugger\-Fenster \(**Extras \> Berechtigungen**\) hinzufügen.  
  
## Remotedebuggen eines Visual C\+\+\-Projekts  
 Im folgenden Verfahren lautet der Name und der Pfad des Projekts „C:\\remotetemp\\MyMfc“ und der Name des Remotecomputers **remote1**.  
  
1.  Erstellen Sie eine MFC\-Anwendung mit dem Namen **mymfc**.  
  
2.  Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z. B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.  
  
3.  Wählen Sie in Visual Studio im Menü **Projekt**die Option **Eigenschaften** aus. Öffnen Sie die Registerkarte **Debuggen**.  
  
4.  Legen Sie **Zu startender Debugger** auf **Remote\-Windows\-Debugger** fest.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
    |||  
    |-|-|  
    |**Einstellung**|**Wert**|  
    |Remotebefehl|C:\\remotetemp\\mymfc.exe|  
    |Arbeitsverzeichnis|C:\\remotetemp|  
    |Remoteservername|remote1|  
    |Verbindung|Remote mit Windows\-Authentifizierung|  
    |Debuggertyp|Nur systemeigen|  
    |Bereitstellungsverzeichnis|C:\\remotetemp.|  
    |Zusätzliche bereitzustellende Dateien|C:\\data\\mymfcdata.txt.|  
  
6.  Öffnen Sie auf der Symbolleiste das Dropdownmenü **Projektmappenkonfiguration**, und wählen Sie **Konfigurations\-Manager** aus.  
  
7.  Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Starten Sie das Debuggen \(wählen Sie **Debuggen \> Debuggen starten** aus, oder drücken Sie **F5**\).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. Auf dem Visual Studio\-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    >  Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.  
  
 Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio\-Projekt hinzufügen. Erstellen eines Projektordners für die zusätzlichen Dateien \(klicken Sie im **Projektmappen\-Explorer** auf **Hinzufügen \> Neuen Ordner**.\) Fügen Sie die Dateien dann zum Ordner hinzu \(klicken Sie im **Projektmappen\-Explorer** auf **Hinzufügen \> Vorhandenes Element**, und wählen Sie dann die Dateien aus\). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.  
  
## Remotedebugging eines Visual C\#\- oder Visual Basic\-Projekts  
 Der Debugger kann Visual C\#\- oder Visual Basic\-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Im folgenden Verfahren wird davon ausgegangen, dass Sie die Anwendung auf einem Computer mit dem Namen **remote1** debuggen möchten.  
  
1.  Erstellen Sie ein WPF\-Projekt mit dem Namen **MyWpf**.  
  
2.  Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest. Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen.  
  
3.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
4.  Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.  
  
6.  Wählen Sie **Remotecomputer verwenden** aus, und geben Sie **remote1** in das Textfeld ein.  
  
7.  Stellen Sie sicher, dass **Debuggen von systemeigenem Code aktivieren** nicht aktiviert ist.  
  
8.  Erstellen Sie das Projekt.  
  
9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**\-Ordner auf Ihrem Visual Studio\-Computer: **\<Quellpfad\>\\MyWPF\\MyWPF\\bin\\Debug**.  
  
10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio\-Computer in den neu erstellten Ordner auf dem Remotecomputer.  
  
    > [!CAUTION]
    >  Führen Sie vor diesem Schritt keine Änderungen und keine Neuerstellung des Codes aus. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.  
  
11. Starten Sie das Debuggen in Visual Studio \(wählen Sie **Debuggen \> Debuggen starten** aus, oder drücken Sie **F5**\).  
  
12. Überprüfen Sie den Haltepunkt. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die die Symbole für die Anwendung nicht geladen. Informationen zum Laden und zur Fehlerbehandlung von Symbolen finden Sie unter [Understanding symbol files and Visual Studio’s symbol settings](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).  
  
13. Das Hauptfenster der WPF\-Anwendung sollte auf dem Remotecomputer geöffnet sein. Führen Sie die Aktion aus, die bewirkt, dass der Haltepunkt erreicht wird.  
  
14. Auf dem Visual Studio\-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.  
  
 Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio\-Projekt hinzufügen. Erstellen eines Projektordners für die zusätzlichen Dateien \(klicken Sie im **Projektmappen\-Explorer** auf **Hinzufügen \> Neuen Ordner**.\) Fügen Sie die Dateien dann zum Ordner hinzu \(klicken Sie im **Projektmappen\-Explorer** auf **Hinzufügen \> Vorhandenes Element**, und wählen Sie dann die Dateien aus\). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.  
  
## Remotedebuggen einer ASP.NET\-Anwendung  
 Beim Bereitstellen einer ASP.NET\-Anwendung auf einem Remotecomputer mit IIS sind verschiedene Schritte auszuführen, je nach Betriebssystem und IIS\-Version. Für Remotecomputer mit den Betriebssystemen Windows 8 oder höher bzw. Windows Server 2012, auf denen IIS 8 \(oder höher\) installiert ist, lesen Sie [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Für Remotecomputer mit Windows 7 oder Windows Server 2008, auf denen IIS 7.5 installiert ist, lesen Sie [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
## Einrichten des Debuggings mit Remotesymbolen  
 Sie sollten Ihren Code mit den auf dem Visual Studio\-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden. Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  
  
 Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon\-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Weitere Informationen finden Sie in der Hilfe zum Remotedebugging \(drücken Sie **F1** im Remotedebuggerfenster, oder klicken Sie auf **Hilfe \> Verwendung**\). Weitere Informationen finden Sie unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Remotedebugging in Windows Store und Azure\-Apps  
 Weitere Informationen zum Remotedebuggen mit Windows Store\-Apps finden Sie unter [Debuggen und Testen von Windows Store\-Apps auf einem Remotegerät in Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informationen zum Debuggen in Azure finden Sie in den folgenden Themen:  
  
-   [Debuggen eines Cloud\-Diensts oder virtuellen Computers in Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Debuggen des .NET\-Backends in Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Einführung in das Remotedebuggen auf Azure\-Websites \([Teil 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Teil 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Teil 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)\).  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurieren der Windows\-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remotedebugger \- Portzuweisungen](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)