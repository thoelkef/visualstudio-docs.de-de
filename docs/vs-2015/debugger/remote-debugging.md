---
title: Remote Debugging | Microsoft Docs
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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300566"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde.  Dazu verwenden Sie den Visual Studio Remote Debugger.  
  
 Die hier bereitgestellten Informationen gelten für Windows Desktop- und ASP.NET-Anwendungen.  For information about remote debugging Windows Store apps and Azure apps, see [Remote Debugging on Windows Store and Azure apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Get the remote tools  
You can either download the remote tools directly on the device or server that you want to debug, or you can get the remote tools from your host machine with Visual Studio installed.

### <a name="to-download-and-install-the-remote-tools"></a>To download and install the remote tools
  
1. On the device or server machine that you want to debug (rather than the machine running Visual Studio), get the correct version of the remote tools.

    |Version|Link|Notizen|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary. Always download the version matching your device operating system (x86, x64, or  ARM version)|
    |Visual Studio 2015 (older)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary.|
    |Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2013 documentation|
    |Visual Studio 2012|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2012 documentation|
  
2. On the download page, choose the version of the tools that matches your operating system (x86, x64, or  ARM version) and download the remote tools.
  
    > [!IMPORTANT]
    > We recommend you install the most recent version of the remote tools that matches your version of Visual Studio. Mismatched versions are not recommended.  
    >   
    >  In addition, you must install the remote tools that have the same architecture as the operating system on which you want to install it. In other words, if you want to debug a 32-bit application on a remote computer running a 64-bit operating system, you must install the 64-bit version of the remote tools on the remote computer.  
  
3. Wenn Sie die ausführbare Datei heruntergeladen haben, folgen Sie den Anweisungen zum Installieren der Anwendung auf dem Remotecomputer. See [setup instructions](#bkmk_setup)

If you try to copy the remote debugger (msvsmon.exe) to the remote computer and run it, be aware that the **Remote Debugger Configuration Wizard** (**rdbgwiz.exe**) is installed only when you download the tools, and you may need to use the wizard for configuration later, especially if you want the remote debugger to run as a service. For more information, see [(Optional) Configure the remote debugger as a service](#bkmk_configureService) below.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>To run the remote debugger from a file share

You can find the remote debugger (**msvsmon.exe**) on a computer with Visual Studio 2015 Community, Professional, or Enterprise already installed. For many scenarios, the easiest way to set up remote debugging is to run the remote debugger (msvsmon.exe) from a file share. For usage limitations, see the remote debugger's Help page (**Help / Usage** in the remote debugger).

1. Find **msvsmon.exe** in the directory matching your version of Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Share the **Remote Debugger** folder on the Visual Studio computer.

3. On the remote computer, run **msvsmon.exe**. Follow the [setup instructions](#bkmk_setup).

> [!TIP] 
> For command line installation and command line reference, see the Help page for **msvsmon.exe** by typing ``msvsmon.exe /?`` in the command line on the computer with Visual Studio installed (or go to **Help / Usage** in the remote debugger).

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme  
 Auf dem Remotecomputer muss eines der folgenden Betriebssysteme ausgeführt werden:  
  
- Windows 10  
  
- Windows 8 oder 8.1  
  
- Windows 7 Service Pack 1  
  
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
  
## <a name="bkmk_setup"></a>Set up the remote debugger  
 Sie müssen über Administratorberechtigungen auf dem Remotecomputer verfügen.  
  
1. Suchen Sie die Remotedebuggeranwendung. (Open the Start menu and search for **Remote Debugger**.)
  
    If you are running the remote debugger on a  remote server, you can right-click the Remote Debugger app and choose **Run as administrator** (Or, you can run the remote debugger as a service).If you are not running it on a remote server, just start it normally.
  
2. When you start the remote tools for the first time (or before you have configured it), the **Remote Debugging Configuration** dalog box appears.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. If the Windows Service API is not installed (which happens only on Windows Server 2008 R2), choose the **Install** button.  
  
4. Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
5. Choose **Configure remote debugging** to configure the firewall and start the tool.  
  
6. Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger-Fenster angezeigt.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    The remote debugger is now waiting for a connection. Make a note of the server name and port number that is displayed, because you will need this later for configuration in Visual Studio.  
  
   When you are finished debugging and need to stop the remote debugger, click **File / Exit** on the window. You can restart it from the **Start** menu or from the command line:  
  
   **\<Visual Studio installation directory>\Common7\IDE\Remote Debugger\\<x86, x64, or Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurieren des Remotedebuggers  
 Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.
  
- To enable other users to connect to the remote debugger, choose **Tools / Permissions**. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

  > [!IMPORTANT]
  > You can run the remote debugger under a user account that differs from the user account you are using on the Visual Studio computer, but you must add the different user account to the remote debugger's permissions. 

   Alternatively, you can start the remote debugger from the command line with the **/allow \<username>** parameter: **msvsmon /allow \<username@computer** .
  
- To change the Authentication mode or the port number, or to specify a timeout value for the remote tools: choose **Tools / Options**.  
  
   For a listing of the port numbers used by default, see [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

## <a name="bkmk_configureService"></a> (Optional) Configure the remote debugger as a service
 For debugging in ASP.NET and other server environments, you must either run the remote debugger as an Administrator or, if you want it always running,  run the remote debugger as a service.
  
 If you want to configure the remote debugger as a service, follow these steps.  
  
1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (This is a separate application from the Remote Debugger.) It is available only when you install the remote tools. und wird nicht mit Visual Studio installiert.  
  
2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.  
  
3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .  
  
4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.  
  
    Sie müssen diesem Konto möglicherweise die Benutzerberechtigung zum **Anmelden als Dienst** hinzufügen. (Suchen Sie die **lokale Sicherheitsrichtlinie** (secpol.msc) auf der Seite bzw. im Fenster **Start** (oder geben Sie **secpol** an der Eingabeaufforderung ein). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Add the user account to the **Properties** window and click **OK**.) Click **Next**.  
  
5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.  
  
6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen**angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger**angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.  
  
7. Klicken Sie auf **Fertig stellen**.  
  
   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung / Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger**suchen.  
  
   Sie können den Remotedebugger-Dienst über **Systemsteuerung / Dienste**beenden und starten.  

## <a name="remote-debug-an-aspnet-application"></a>Remotedebuggen einer ASP.NET-Anwendung  
 Beim Bereitstellen einer ASP.NET-Anwendung auf einem Remotecomputer mit IIS sind verschiedene Schritte auszuführen, je nach Betriebssystem und IIS-Version. For remote computers running Windows Server 2008 or Windows Server 2012 that have IIS 7.5 or later installed, please see [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 If you are debugging an ASP.NET Core app, please see [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html). Different steps are required to publish an ASP.NET Core on IIS. Once you publish an ASP.NET Core app successfully, you can remote debug it [just like other ASP.NET apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), except that the process you need to attach to is dnx.exe instead of w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Remotedebuggen eines Visual C++-Projekts  
 In the following procedure, the name and path of the project is C:\remotetemp\MyMfc, and the name of the remote computer is **MJO-DL**.  
  
1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.  
  
3. In Solution Explorer, right-click on the project and select **Properties**. Öffnen Sie die Registerkarte **Debuggen**.  
  
4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
   |Einstellung|Wert|
   |-|-|  
   |Remote-Befehl|C:\remotetemp\mymfc.exe|  
   |Arbeitsverzeichnis|C:\remotetemp|  
   |Remoteservername|MJO-DL:*portnumber*|  
   |Verbindung|Remote mit Windows-Authentifizierung|  
   |Debuggertyp|Nur systemeigen|  
   |Bereitstellungsverzeichnis|C:\remotetemp.|  
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|  
  
    If you deploy additional files (optional), the folder must exist on both machines.  
  
6. In Solution Explorer, right-click the solution and choose **Configuration Manager**.  
  
7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Start debugging (**Debug / Start Debugging**, or **F5**).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials are specific to your network's security configuration. For example, on a domain computer, you might choose a security certificate or enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.  
  
11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    > Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.  
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Remotedebugging eines Visual C#- oder Visual Basic-Projekts  
 Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. The following procedure assumes that you want to debug it on a computer named **MJO-DL**, as shown in the earlier illustration.
  
1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.  
  
    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. To do this, open MainWindow.xaml, and add a Button control from the Toolbox, then double-click the button to open it's handler.
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**.  
  
4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.  
  
6. Choose **Use remote machine**, and type **MJO-DL:4020** in the text box. (4020 is the port number shown in the remote debugger window).  
  
7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.  
  
8. Erstellen Sie das Projekt.  
  
9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**-Ordner auf Ihrem Visual Studio-Computer: **\<Quellpfad>\MyWPF\MyWPF\bin\Debug**.  
  
10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.
  
    > [!CAUTION]
    > Do not make changes to the code or rebuild (or you must repeat this step). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    You can copy the project manually, use Xcopy, Robocopy, Powershell, or other options.
  
11. Make sure the remote debugger is running on the target machine. (If it's not, search for **Remote Debugger** in the **Start** menu. ) The remote debugger window looks like this.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, start debugging (**Debug / Start Debugging**, or **F5**).  
  
13. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials vary depending on your network's security configuration. For example, on a domain computer, you can  enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.
  
14. If necessary, take action to hit the breakpoint. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die die Symbole für die Anwendung nicht geladen. Retry, and if that doesn't work, get information about loading symbols and how troubleshoot them at [Understanding symbol files and Visual Studio’s symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen  
 Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  
  
 Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 For more information, please see the remote debugging help (press **F1** in the remote debugger window, or click **Help / Usage**). Weitere Informationen finden Sie unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013 (Änderungen beim Laden von Symbolen in der .NET-Remoteinstanz in Visual Studio 2012 und 2013)](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="bkmk_winstoreAzure"></a> Remote Debugging on Windows Store and Azure apps  
 For information about remote debugging with Windows Store apps, see [Debug and test Windows Store apps on a remote device from Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Informationen zum Debuggen in Azure finden Sie in den folgenden Themen:  
  
- [Debugging a Cloud Service or Virtual Machine in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debugging the .NET Backend in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introduction to Remote Debugging on Azure Web Sites ([Part 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Part 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Part 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
