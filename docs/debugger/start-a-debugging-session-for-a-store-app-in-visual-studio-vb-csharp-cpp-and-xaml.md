---
title: Starten eine Debugsitzung für eine uwp-app in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: b298e2b17f1aa8805e0ab896c6978744c6c3bd53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481108"
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Starten einer Debugsitzung für eine uwp-app in Visual Studio
  
 In diesem Thema wird beschrieben, wie zum Starten einer Debugsitzung für uwp-apps in XAML und Visual C++, Visual c# oder Visual Basic geschrieben wurde, und für uwp-apps in HTML und JavaScript geschrieben wird. Das Debuggen einer Anwendung umfasst sowohl das Konfigurieren der Debugsitzung als auch die Auswahl der Methode für den Anwendungsstart.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Die einfache Methode zum Starten des Debuggings  
  
1.  Öffnen Sie in Visual Studio die Anwendungsprojektmappe.  
  
2.  Wählen Sie F5.  
  
 In Visual Studio wird die Anwendung mit dem angefügten Debugger erstellt und gestartet. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a> Wählen Sie die Buildkonfigurationsoptionen aus.  
  
1.   Aus der Dropdown-Liste neben den **Debuggen** Schaltfläche auf der Debugger **Standard** Symbolleiste auswählen **Debuggen**.  
  
2.  Wählen Sie in der Liste **Plattform** die Zielplattform aus, in der der Build erfolgen soll.  
  
##  <a name="BKMK_Choose_the_deployment_target"></a> Auswählen des Bereitstellungsziels  
  
Sie können bereitstellen und Debuggen eine uwp-app auf dem Visual Studio-Computer, einem angeschlossenen Gerät, Visual Studio-Simulator auf dem lokalen Computer, einem Remotegerät oder einen Emulator aus. Wählen Sie das Bereitstellungsziel aus der Dropdownliste rechts neben der **Plattform** Ziel auf der Debugger **Standard** Symbolleiste.
  
![Wählen Sie ein Bereitstellungsziel aus](../debugger/media/vsrun_select_target_device.png)  
  
Wählen Sie eine der folgenden Optionen aus:  
  
|||  
|-|-|  
|**Lokaler Computer**|Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer.|  
|**Simulator**|Debuggen Sie die Anwendung in Visual Studio-Simulator für uwp-apps. Der Simulator ist ein Desktopfenster mit dem Sie Gerät Debuggen kann, z. B. die Fingereingabe und geräterotation –, die möglicherweise nicht auf dem lokalen Computer verfügbar sein. Diese Option ist nur verfügbar wenn Ihre app **Mindestversion. Version** ist kleiner oder gleich dem Betriebssystem auf dem Entwicklungscomputer. Finden Sie unter [ausführen uwp-apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Remotecomputer**|Debuggen Sie die Anwendung auf einem Gerät, das mit dem lokalen Computer über ein Intranet oder direkt über ein Ethernetkabel verbunden ist. Zum Remotedebuggen müssen die Remotetools für Visual Studio installiert ist und auf dem Remotegerät ausgeführt werden. Finden Sie unter [ausführen uwp-apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Gerät**|Debuggen Sie die Anwendung auf einem über USB angeschlossenen Gerät. Das Gerät muss Developer entsperrt werden, und den Bildschirm entsperrt haben.|  
|**Mobile-Emulator**|Starten Sie einen Emulator mit der Konfiguration in der Emulator-Name angegeben, Bereitstellen Sie die app und Debuggen. Emulatoren sind nur auf Computern mit aktiviertem Hyper-V verfügbar.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Wählen Sie zusätzliche Optionen für das Debuggen  

Wenn Sie zusätzliche Debuggingoptionen konfigurieren möchten, öffnen Sie die Eigenschaftenseite für das Projekt.
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus. Wählen Sie im Kontextmenü **Eigenschaften**aus.  
  
2.  Führen Sie diese Option, um die Debugeigenschaftenseite für das Projekt zu öffnen:  
  
    -   Wählen Sie für Visual C#- und Visual Basic-Anwendungen **Debuggen**aus.  
  
         ![C&#35; &#47; Debugeigenschaftenseite des VB-Projekts](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   Erweitern Sie für Visual C++ und JavaScript-apps, die **Konfigurationseigenschaften** Knoten und wählen Sie dann **Debuggen**.  
  
         ![C&#43; &#43; uwp-app-debugging-Eigenschaftsseite](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Auswahl des zu verwendenden Debuggers  
In der Standardeinstellung erfolgt in Visual Studio ein Debuggen für verwalteten Code in C#- und Visual Basic-Anwendungen. Für C#- und Visual Basic-Anwendungen können Sie sowohl den verwalteten als auch den systemeigenen C/C++-Code der Anwendung debuggen. In C++-Anwendungen debuggt Visual Studio systemeigenen Code standardmäßig an. In JavaScript-apps erfolgt in Visual Studio Skript standardmäßig Debuggen. 
  
Für apps mit C++ und JavaScript können Sie auswählen, um bestimmte Codetypen debuggen, die in den Komponenten der app anstelle des oder zusätzlich zu den systemeigenen Code befinden. Sie geben den zu debuggenden Code in der Liste **Debuggertyp** auf der Eigenschaftenseite **Debuggen** des App-Projekts an.  
  
Wählen Sie einen dieser Debugger in der Liste **Anwendungsprozesse** aus:  
  
|||  
|-|-|  
|**Nur verwaltet**|Für das Debuggen des verwalteten Codes der Anwendung. JavaScript- und systemeigener C/C++-Code werden ignoriert.|  
|**Nur systemeigen**|Für das Debuggen des systemeigenen C/C++-Codes der Anwendung. Verwalteter und JavaScript-Code werden ignoriert.|  
|**Gemischt (verwaltet und systemeigen)**|Für das Debuggen des systemeigenen C/C++- und des verwalteten Codes der Anwendung. JavaScript-Code wird ignoriert. In C++-Projekten, diese Option heißt auch **(verwaltet und systemeigen)**.|  
|**Nur Skript**|Für das Debuggen des JavaScript-Codes der Anwendung. Verwalteter und systemeigener Code werden ignoriert.|  
|**Skript ' und ' Native**|Systemeigene C/C++-Code und JavaScript-Code in Ihrer app zu debuggen. Verwalteter Code wird ignoriert. In nur C++-Projekten verfügbar.|  
|**Nur GPU (C++-AMP)**|Debuggen von systemeigenem C++-Code, der auf einer Grafikverarbeitungseinheit (GPU) ausgeführt wird. In nur C++-Projekten verfügbar.|  

In c# und Visual Basic-apps, Sie können auch dieselben festlegen **Debuggertyp** Werte für alle Hintergrundaufgaben, die Teil des Projekts sind.
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Optional) Verzögertes Starten der Debugsitzung  
 In der Standardeinstellung wird die Anwendung in Visual Studio sofort gestartet, wenn Sie das Debuggen starten. Sie können zudem eine Debugsitzung starten, den Start der App jedoch verzögern. Wenn Sie diese Option auswählen, wird die Anwendung im Debugger gestartet, wenn diese über den Bildschirm, einen Aktivierungsvertrag oder von einem anderen Prozess oder eine Methode gestartet wird. Der Start einer App wird auch verzögert, wenn beim Debuggen einer Hintergrundaufgabe die App selbst nicht ausgeführt wird.  
  
 Um den Start der App zu verzögern, können Sie folgende Schritte durchführen:  
  
-   Wählen Sie für Visual C#- und Visual Basic-Apps auf der Eigenschaftenseite **Debuggen** die Option **Eigenen Code zunächst nicht starten sondern debuggen** aus.  
  
-   Wählen Sie für Visual C++ und JavaScript-apps **keine** aus der **Anwendung starten** auf in der Liste der **Debuggen** Eigenschaftenseite.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Optional) Netzwerkloopbacks deaktivieren  
  
 Aus Sicherheitsgründen wird eine im Standardverfahren installierten uwp-app nicht zulässig, Netzwerkaufrufe an das Gerät auszuführen, auf dem Sie installiert ist. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die app an Microsoft Store senden, sollten Sie die app ohne die Ausnahme testen.  
  
 So entfernen Sie die Netzwerkloopbackausnahme  
  
-   Bei Visual c# und Visual Basic-apps Deaktivieren der **lokales netzwerkloopback zulassen** Kontrollkästchen auf der **Debuggen** Eigenschaftenseite.  
  
-   Wählen Sie für Visual C++ und JavaScript-apps **keine** aus der **lokales Netzwerkloopback zulassen** auf in der Liste der **Debuggen** Eigenschaftenseite.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Optional) Installieren Sie die Anwendung neu, wenn Sie das Debuggen starten.  
 Um Probleme zu bestimmen, die mit der Installation und Erstkonfiguration der Visual C#- oder Visual Basic-App zusammenhängen, wählen Sie auf der Eigenschaftenseite **Debuggen** die Option **Paket deinstallieren und anschließend neu installieren**  aus, um eine ursprüngliche Installation beim Debugstart neu zu erstellen. Diese Option ist nicht für Visual C++ und JavaScript-Projekten verfügbar.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Optional) Deaktivieren Sie zum Starten des Remotedebuggers die Authentifizierungsanforderung.  
  
 Standardmäßig müssen Sie Anmeldeinformationen zum Ausführen des Remotedebuggers, bei der Auswahl angeben **Remotecomputer** als das Bereitstellungsziel.
  
> [!IMPORTANT]
>  Sie können auswählen, dass der Remotedebugger ohne Authentifizierung ausgeführt, in diesem Modus wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie die keine Authentifizierung, nur, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.  
  
 Um die Authentifizierungsanforderung zu entfernen, gehen Sie wie folgt vor:  
  
1.  Wählen Sie für Visual c# und Visual Basic-apps **Remotecomputer** als die **Zielgerät** auf die **Debuggen** Eigenschaftenseite, und legen Sie anschließend **Authentifizierungsmodus**  auf **keine** oder **Universal (unverschlüsselte Protocol)**.
  
2.  Wählen Sie für Visual C++ und JavaScript-apps **Remotecomputer** als die **Zielgerät** auf die **Debuggen** Eigenschaftenseite, und legen Sie anschließend **erfordern Authentifizierung** auf **keine** oder **Universal (unverschlüsselte Protocol)**.  

    **Universal (unverschlüsselte Protocol)** ist für die Verwendung, wenn Sie zu einem Remotegerät bereitstellen. Zurzeit ist dies für IoT-Geräten, Xbox-Geräte und HoloLens-Geräte als auch Ersteller Update oder neueren PCs. Universal (unverschlüsselte Protocol) sollte nur in vertrauenswürdigen Netzwerken verwendet werden. Die Debugverbindung ist anfällig für böswillige Benutzer, die abfangen und Ändern von Daten zwischen der Entwicklungs- und einen Remotecomputer übergeben werden konnte.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Starten der Debugsitzung  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Debuggen starten (F5)  
 Bei Auswahl **Debuggen** (Tastatur: F5) auf die **Debuggen** Menü, startet Visual Studio die app mit dem angefügten Debugger. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine Ausnahme auftritt, oder bis die Anwendung beendet ist.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Starten des Debuggens (F5) jedoch verzögerter Anwendungsstart  
 Sie können die App so einrichten, dass sie im Debugmodus ausgeführt wird, sie aber mit einer anderen Methode als dem Debugger starten. Beispielsweise sollten Sie so Debuggen Sie den Start der app über das Startmenü oder um einen Hintergrundprozess aus der app zu debuggen, ohne die app starten. Um den app-Start zu verzögern, tun Sie Folgendes aus:  
  
-   Auf der **Debuggen** Eigenschaftenseite der app (**Debuggen** in Visual C++ und JavaScript)  
  
    -   Wählen Sie für Visual C#- und Visual Basic-Anwendungen **Eigenen Code zunächst nicht starten sondern debuggen**aus.  
  
    -   Wählen Sie für Visual C++ und JavaScript-apps **Ja** aus der **Anwendung starten** Liste.  
  
-   Wählen Sie **Debuggen** auf die **Debuggen** Menü (Tastatur: F5).  
  
-   Starten Sie die Anwendung vom Startmenü aus, über einen Ausführungsvertrag oder von einer anderen Prozedur.  
  
 Die Anwendung wird im Debugmodus gestartet. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.  
  
 Weitere Informationen zum Debuggen von Hintergrundaufgaben finden Sie unter [Trigger anhalten, fortsetzen und hintergrundereignissen für uwp-apps)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Starten einer installierten App im Debugger  
Wenn Sie das Debugging mit F5 beginnen, erstellt Visual Studio die App, stellt sie bereit, aktiviert den Debugmodus für die App und startet sie. Um eine app starten, die bereits auf einem Gerät installiert ist, verwenden die **installiertes App-Paket Debuggen** (Dialogfeld). Dieses Verfahren eignet sich, wenn Sie zum Debuggen einer app, die von Microsoft Store installiert wurde, oder Sie haben die Quelldateien für die app, aber Sie verfügen nicht über die Visual Studio-Projekt für die app. So kann beispielsweise ein benutzerdefiniertes Buildsystem vorhanden sein, das keine Visual Studio-Projekte oder -Projektmappen verwendet.  
  
Die App kann auf dem lokalen Gerät oder einem Remotegerät installiert sein.  Sie können die App sofort starten oder festlegen, dass sie im Debugger ausgeführt wird, wenn ein anderer Prozess oder eine andere Methode sie startet, z. B. das Startmenü oder ein Aktivierungskontrakt. Auch um einen Hintergrundprozess zu debuggen, können Sie festlegen, dass die App im Debugmodus ausgeführt wird. Weitere Informationen finden Sie unter [Trigger anhalten, fortsetzen und hintergrundereignissen für uwp-apps)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Um eine installierte app im Debugger zu starten, wählen Sie **Debuggen**, klicken Sie dann **andere debugziele**, und klicken Sie dann **installiertes App-Paket Debuggen**. Zusätzliche Anleitungen finden Sie unter [eine installierte app-Paket Debuggen](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anfügen des Debuggers an eine ausgeführte uwp-app  

Um eine ausgeführte uwp-app zu debuggen, wählen Sie **Debuggen**, klicken Sie dann **andere debugziele**, und klicken Sie dann **installiertes App-Paket Debuggen**. Zusätzliche Anleitungen finden Sie unter [eine installierte app-Paket Debuggen](../debugger/debug-installed-app-package.md).
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anfügen des Debuggers an eine ausgeführte Windows 8.x-app
 Um den Debugger an eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -App anzufügen, müssen Sie im Manager für debugfähige Pakete festlegen, dass die App im Debugmodus ausgeführt wird. Der Manager für Debugfähige Pakete wird mit den Remotetools für Visual Studio installiert.  
  
 Das Anfügen des Debuggers an eine App ist nützlich zum Debuggen einer bereits installierten App, wie beispielsweise eine App, die aus dem [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]installiert wurde. Das Anfügen ist erforderlich, wenn Sie über die Quelldateien für die Anwendung, nicht jedoch über ein Visual Studio-Projekt für die Anwendung verfügen. So kann beispielsweise ein benutzerdefiniertes Buildsystem vorhanden sein, das keine Visual Studio-Projekte oder -Projektmappen verwendet.  
  
 Für das Anfügen des Debuggers an eine App sind folgende Schritte erforderlich:  
  
1.  Legen Sie die Ausführung der Anwendung im Debugmodus fest. Dies muss erfolgen, wenn die Anwendung nicht ausgeführt wird.  
  
2.  Starten Sie die Anwendung. Sie können die App über den Startbildschirm, einen Ausführungsvertrag oder eine andere Methode starten.  
  
3.  Fügen Sie den Debugger an die ausgeführte Anwendung an.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Festlegen der Ausführung der Anwendung im Debugmodus  
  
1.  Installieren der Remotetools für Visual Studio auf dem Gerät, auf dem die app installiert ist. Finden Sie unter [Installieren der Remotetools](../debugger/remote-debugging.md).  
  
2.  Suchen Sie auf dem Startbildschirm nach `Debuggable Package Manager` , und starten Sie diesen.  
  
     Es wird ein ordnungsgemäß für das AppxDebug-Cmdlet konfiguriertes PowerShell-Fenster angezeigt.  
  
3.  Um das Debuggen einer Anwendung zu aktivieren, müssen Sie den PackageFullName-Bezeichner der App angeben. Um eine Liste aller Apps anzuzeigen, die PackageFullName enthält, geben Sie an der PowerShell-Eingabeaufforderung `Get-AppxPackage` ein.  
  
4.  Geben Sie an der PowerShell-Eingabeaufforderung `Enable-AppxDebug` *PackageFullName* ein, wobei *PackageFullName* der PackageFullName-Bezeichner der App ist.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Fügen Sie den Debugger an.  
 So fügen Sie den Debugger an  
  
1.  Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**.  
  
     Das Dialogfeld **An den Prozess anhängen** wird angezeigt.  
  
2.  Um an eine Anwendung auf einem Remotegerät anzufügen, geben Sie das Remotegerät im Feld **Qualifizierer** an. Sie haben folgende Möglichkeiten:  
  
    -   Geben Sie im Feld **Qualifizierer** den gewünschten Anzeigenamen ein.  
  
    -   Wählen Sie den Pfeil nach unten im Feld **Qualifizierer** aus, und wählen Sie das Gerät aus einer Liste von Geräten aus, die Sie zu zuvor angefügt haben.  
  
    -   Wählen Sie **Suchen** aus, um das Gerät aus einer Liste von Geräten im lokalen Subnetz auszuwählen.  
  
3.  Geben Sie den Typ des Codes an, den Sie im Feld **Anfügen an** debuggen möchten.  
  
     Wählen Sie **Auswählen** aus, und gehen Sie folgendermaßen vor:  
  
    -   Wählen Sie **Zu debuggenden Codetyp automatisch bestimmen**aus.  
  
    -   Wählen Sie **Diese Codetypen debuggen** und anschließend mindestens einen Typ aus der Liste aus.  
  
4.  Wählen Sie in der Liste **Verfügbare Prozesse**  den App-Prozess aus.  

    > [!NOTE]
    >  Im Gegensatz zu anderen app-Typen führen JavaScript-apps in einer Instanz des wwahost.exe-Prozesses ausgeführt. Wenn andere JavaScript-Apps ausgeführt werden, während Sie an die App anfügen, müssen Sie die numerische Prozess-ID (PID) des wwahost.exe-Prozesses kennen, in dem die App ausgeführt wird.  
    >   
    >  Die einfachste Möglichkeit in dieser Situation besteht darin, alle anderen JavaScript-Apps zu schließen. Andernfalls können Sie vor dem Starten der App den Windows Task-Manager öffnen und sich die IDs der wwahost.exe-Prozesse notieren. Wenn Sie angeben, den Prozess zum Anfügen der **verfügbare Prozesse** (Dialogfeld), haben die wwahost.exe der app eine Id, die diejenigen unterscheidet, die Sie notiert haben.  
  
5.  Wählen Sie **Anfügen**aus.  
  
 Der Debugger wird in Visual Studio an den Prozess angefügt. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   