---
title: Starten einer Debugsitzung für eine UWP-App | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/20/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436008"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Starten einer Debugsitzung für eine UWP-App

In diesem Artikel wird beschrieben, wie eine Visual Studio-Debugsitzung für eine universelle Windows-Plattform-app (UWP) gestartet wird. UWP-Apps können in XAML und C++, XAML und C#/Visual Basic geschrieben werden. Zum Starten des Debuggens einer UWP-App konfigurieren Sie die Debugsitzung, und wählen Sie die Methode zum Starten der APP aus.

::: moniker range=">=vs-2019"
> [!NOTE]
> Ab Visual Studio 2019 werden UWP-Apps für HTML und JavaScript nicht mehr unterstützt.
::: moniker-end
::: moniker range="vs-2017"
In Visual Studio 2017 gelten die meisten Befehle und Optionen in diesem Artikel auch für UWP-Apps für HTML und JavaScript. Wenn sich die Befehle zwischen verwalteten apps C++ und apps unterscheiden, entsprechen JavaScript-apps in der C++ Regel den Befehlen für UWP-apps.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Starten des Debuggens über die Visual Studio-Symbolleiste

Die einfachste Möglichkeit zum Konfigurieren und Starten des Debuggens ist die Standard Symbolleiste von Visual Studio.

![Debuggen über die Symbolleiste](../debugger/media/vsrun_select_target_device.png)

1. Wählen Sie in der Dropdown Liste **Konfiguration** auf der Symbolleiste **Standard** die Option **Debuggen**.

1. Wählen Sie in der Dropdown Liste **Plattform** die Zielplattform aus, die erstellt werden soll.

1. Wählen Sie in der Dropdown Liste neben dem grünen Pfeil das Debugziel aus. Sie können einen lokalen Computer, ein direkt verbundenes Gerät, einen lokalen Visual Studio-Simulator, ein Remote Gerät oder einen Emulator auswählen.

1. Wählen Sie zum Starten des Debuggens den grünen **Start** Pfeil auf der Symbolleiste aus, oder wählen Sie **Debuggen**  > **Debugging starten**, oder drücken Sie **F5**.

   In Visual Studio wird die Anwendung mit dem angefügten Debugger erstellt und gestartet.

Das Debuggen wird fortgesetzt, bis ein Haltepunkt erreicht wird, Sie die Ausführung manuell aussetzen, eine nicht behandelte Ausnahme auftritt oder die APP beendet wird.

### <a name="BKMK_Choose_the_deployment_target"></a>Optionen für Bereitstellungs Ziel

Sie können das Debugziel auf der Visual Studio-Symbolleiste oder auf der Eigenschaften Seite Debuggen des Projekts festlegen. Wählen Sie einen der folgenden Optionen aus:

|||
|-|-|
|**Lokaler Computer**|Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer.|
|**Simulator**|Debuggen Sie die APP im Visual Studio-Simulator für UWP-apps. Der Simulator ist ein Desktop Fenster, das Gerätefunktionen simuliert, wie z. b. Touchgesten und Geräte Drehung, die auf dem lokalen Computer möglicherweise nicht vorhanden sind. Die Option Simulator ist nur verfügbar, wenn die **Zielplattform min. Version** Ihrer APP kleiner als oder gleich dem Betriebssystem auf dem lokalen Computer ist. Weitere Informationen finden Sie unter [Ausführen von UWP-apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Remotecomputer**|Debuggen Sie die APP auf einem Gerät, das über ein Netzwerk oder Ethernet-Kabel mit dem lokalen Computer verbunden ist. Der Remotetools für Visual Studio muss auf dem Remote Gerät installiert sein und ausgeführt werden. Weitere Informationen finden Sie unter [Ausführen von UWP-apps auf einem Remote Computer](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Gerät**|Debuggen Sie die APP auf einem USB-Gerät. Das Gerät muss von einem Entwickler entsperrt sein, und der Bildschirm ist entsperrt.|
|**Mobiler Emulator**|Starten Sie den im Emulatornamen angegebenen Emulator, stellen Sie die APP bereit, und starten Sie das Debuggen. Emulatoren sind nur auf Hyper-V-fähigen Computern verfügbar.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Konfigurieren des Debuggens auf der Eigenschaften Seite des Projekts

Um zusätzliche Debugoptionen zu konfigurieren, verwenden Sie die Seite debuggingeigenschaften des Projekts.

**So öffnen Sie die Debugeigenschaften:**

1. Wählen Sie in **Projektmappen-Explorer**das Projekt aus, und wählen Sie dann das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**

1. Auf der linken Seite des **Eigenschaften** Bereichs:

   - Wählen C# Sie für und Visual Basic-apps **Debuggen**aus.

     ![C#und Visual Basic Project Debug-Eigenschaften Seite](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Wählen C++ Sie für apps die Option **Konfigurations Eigenschaften**  > **Debuggen**aus.

     ![C++UWP-App-Debugging (Eigenschaften Seite)](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> Auswahl des zu verwendenden Debuggers

Bei C# -und-Visual Basic-apps wird verwalteter Code von Visual Studio standardmäßig debuggt. Sie können auch andere oder zusätzliche Codetypen debuggen. Sie können auch die Werte für den **Debuggertyp** für alle Hintergrundaufgaben festlegen, die Teil des Projekts sind.

In C++ -apps debuggt Visual Studio standardmäßig systemeigenen Code. Sie können auswählen, dass bestimmte Codetypen anstelle von oder zusätzlich zu nativem Code debuggt werden.

**So geben Sie die zu debuggenden Codetypen an:**

- Wählen C# Sie für-und-Visual Basic-apps einen der folgenden **Debugger** aus den Dropdown Listen **Anwendungstyp** und **Hintergrund Prozesstyp** unter Debuggertyp auf der Eigenschaften Seite **Debuggen** aus.

- Wählen C++ Sie für apps einen der folgenden **Debugger** aus der Dropdown Liste Debuggertyp auf der Eigenschaften Seite **Debuggen** aus.

|||
|-|-|
|**Nur verwaltet**|Für das Debuggen des verwalteten Codes der Anwendung. JavaScript- und systemeigener C/C++-Code werden ignoriert.|
|**Nur systemeigen**|Für das Debuggen des systemeigenen C/C++-Codes der Anwendung. Verwalteter und JavaScript-Code werden ignoriert.|
|**Gemischt (verwaltet und systemeigen)**|Für das Debuggen des systemeigenen C/C++- und des verwalteten Codes der Anwendung. JavaScript-Code wird ignoriert. In C++ -Projekten heißt diese Option **verwaltet und nativ**.|
|**Skript**|Für das Debuggen des JavaScript-Codes der Anwendung. Verwalteter und systemeigener Code werden ignoriert.|
|**Nativ mit Skript**|Debuggen SieC++ systemeigenen C/Code-und JavaScript-Code in Ihrer APP. Verwalteter Code wird ignoriert. Nur in C++ Projekten oder Hintergrundaufgaben verfügbar.|
|**Nur GPU (C++ AMP)**|Debuggen von systemeigenem C++-Code, der auf einer Grafikverarbeitungseinheit (GPU) ausgeführt wird. Nur in C++ -Projekten verfügbar.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Netzwerk Loop Backs deaktivieren deaktivieren (optional)

 Aus Sicherheitsgründen kann eine UWP-APP, die auf Standard Art installiert wird, keine Netzwerk Aufrufe an das Gerät vornehmen, auf dem Sie installiert ist. In Visual Studio werden bereitgestellte apps standardmäßig von dieser Regel ausgenommen, sodass Sie Kommunikationsverfahren auf einem einzelnen Computer testen können. Bevor Sie Ihre APP freigeben, sollten Sie die APP ohne die Ausnahme testen.

**So entfernen Sie die Netzwerkloopbackausnahme:**

- Deaktivieren C# Sie für und Visual Basic-apps auf der Eigenschaften Seite **Debuggen** unter **Start Optionen** das Kontrollkästchen **Lokales Netzwerk Loopback zulassen** .

- Wählen C++ Sie für apps auf der Eigenschaften Seite **Debuggen** aus der Dropdown Liste **Lokales Netzwerk Loopback zulassen** die Option **Nein** aus.

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Installieren Sie die APP neu, wenn Sie das Debuggen starten (optional)
 Um Installationsprobleme mit einer C# oder Visual Basic-APP zu diagnostizieren, wählen Sie deinstallieren aus, **und installieren Sie dann das Paket erneut** auf der Eigenschaften Seite **Debuggen** . Mit dieser Option wird die ursprüngliche Installation neu erstellt, wenn Sie das Debuggen starten. Diese Option ist für C++ -Projekte nicht verfügbar.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Festlegen der Authentifizierungs Optionen für das Remote Debuggen

Standardmäßig müssen Sie Windows-Anmelde Informationen angeben, um den Remote Debugger auszuführen, wenn Sie als Bereitstellungs Ziel **Remote Computer** auswählen. Sie können die Authentifizierungsanforderung ändern.

Der Authentifizierungsmodus für **universelle (unverschlüsselte Protokolle)** ist für IOT-, Xbox-und hololens-Geräte sowie für Windows 10-PCs von Creator und höher vorgesehen.

**So ändern Sie die Authentifizierungsmethode:**

- Wählen C# Sie für und Visual Basic-apps auf der Eigenschaften Seite **Debuggen** die Option **Remote Computer** als **Zielgerät**aus. Wählen Sie dann **keine** oder **Universelles (unverschlüsseltes Protokoll)** für den **Authentifizierungsmodus**aus.

- Wählen C++ Sie für apps unter Debugger die Option **Remote Computer** aus, um auf der Eigenschaften Seite **Debuggen** **zu starten** . Wählen Sie dann **keine Authentifizierung** oder **Universelles (unverschlüsseltes Protokoll)** für den **Authentifizierungstyp**aus.

> [!CAUTION]
> Wenn Sie den Remote Debugger im Modus " **keine** " oder "universell" **(unverschlüsseltes Protokoll)** ausführen, gibt es keine Netzwerksicherheit. Wählen Sie diese Modi nur in vertrauenswürdigen Netzwerken aus, für die Sie sicher sind, dass Sie nicht durch schädlichen Code oder feindlichen Datenverkehr gefährdet sind

## <a name="BKMK_Start_the_debugging_session"></a>Startoptionen Debuggen

Wenn Sie **Debuggen**  > **Debuggen starten** auswählen oder **F5**drücken, startet Visual Studio die APP mit dem angefügten Debugger. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Debuggen starten, App-Start verzögern

Standardmäßig startet Visual Studio die APP sofort, wenn Sie mit dem Debuggen beginnen. Sie können auch festlegen, dass die APP im Debugmodus ausgeführt wird. Starten Sie die APP jedoch außerhalb des Debuggers. Beispielsweise möchten Sie möglicherweise den App-Start über das Windows- **Startmenü** Debuggen oder einen Hintergrundprozess in der APP Debuggen. Wenn Sie diese Option auswählen, wird die APP beim Start im Debugger gestartet.

**So deaktivieren Sie den automatischen App-Start:**

- Wählen C# Sie für und Visual Basic-apps auf der Eigenschaften Seite **Debuggen** die Option eigenen Code beim **Start unter Start Optionen** **nicht starten, sondern Debuggen** aus.

- Wählen C++ Sie für apps auf der Eigenschaften Seite **Debuggen** in der Dropdown Liste **Anwendung starten** die Option **Nein** aus.

Weitere Informationen zum Debuggen von Hintergrundaufgaben finden Sie unter [aussetzen von Suspend-, Fortsetzungs-und Hintergrund Ereignissen für UWP-apps](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Debuggen einer installierten oder laufenden UWP-App

Sie können **installiertes App-Paket Debuggen** verwenden, um eine UWP-APP zu debuggen, die bereits auf einem lokalen oder Remote Gerät ausgeführt wird. Möglicherweise wurde die APP aus dem Microsoft Store installiert, oder es handelt sich nicht um ein Visual Studio-Projekt. Beispielsweise verfügt die APP möglicherweise über ein benutzerdefiniertes Buildsystem, das Visual Studio nicht verwendet.

Sie können die installierte App sofort starten, oder Sie können Sie so festlegen, dass Sie im Debugger ausgeführt wird, wenn Sie mit einer anderen Methode gestartet wird. Weitere Informationen finden Sie unter [aussetzen von Suspend-, Resume-und Background-Ereignissen für UWP-apps](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Zum Starten einer installierten oder ausgelaufenden UWP-App im Debugger wählen Sie **Debuggen**  > **andere debugziele**  > **installiertes App-Paket Debuggen**. Weitere Anweisungen finden Sie unter [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anfügen des Debuggers an eine laufende Windows 8. x-APP

Um den Debugger an eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -App anzufügen, müssen Sie im Manager für debugfähige Pakete festlegen, dass die App im Debugmodus ausgeführt wird. Der Manager für debugfähige Pakete wird mit dem-Remotetools für Visual Studio installiert.

1. Installieren Sie die Remotetools für Visual Studio auf dem Gerät, auf dem die APP installiert ist. Weitere Informationen finden Sie unter [Installieren der Remote Tools](../debugger/remote-debugging.md).

1. Suchen Sie im Windows- **Start** Bildschirm nach dem **debugfähigen Paket-Manager**, und starten Sie ihn.

   Es wird ein ordnungsgemäß für das AppxDebug-Cmdlet konfiguriertes PowerShell-Fenster angezeigt.

1. Geben Sie den packagefullname-Bezeichner der APP an.

   1. Geben Sie `Get-AppxPackage` an der PowerShell-Eingabeaufforderung ein, um eine Liste anzuzeigen, die packagefullname aller apps enthält.

   1. Geben Sie an der PowerShell-Eingabeaufforderung `Enable-AppxDebug <PackageFullName>` ein, wobei \<PackageFullName > der packagefullname-Bezeichner der APP ist.

1. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

1. Geben Sie im Dialogfeld **an den Prozess anhängen** im Feld **Verbindungs Ziel** das Remote Gerät an.

   Sie können den Gerätenamen eingeben, ihn aus der Dropdown Liste im Feld **Verbindungs Ziel** auswählen oder auf **Suchen** klicken, um das Gerät im Dialogfeld " **Remote Verbindungen** " zu suchen.

1. Wenn Sie den Typ des zu debuggenden Codes angeben möchten, wählen Sie neben dem Feld **Anfügen an** die Option **auswählen**aus.

1. Wählen Sie im Dialogfeld **Codetyp auswählen** eine der folgenden Optionen aus:
   - **Bestimmen Sie automatisch den zu debuggenden Codetyp**, oder
   - **Debuggen Sie diese Codetypen**, und wählen Sie dann einen oder mehrere Codetypen aus der Liste aus.

1. Wählen Sie in der Liste **Verfügbare Prozesse** den zu debuggenden App-Prozess aus.

1. Wählen Sie **Anfügen**.

 Der Debugger wird in Visual Studio an den Prozess angefügt. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript-Apps werden in einer Instanz des Prozesses *wwahost.exe* ausgeführt. Wenn mehr als eine JavaScript-app ausgeführt wird, müssen Sie die numerische Prozess-ID (PID) des *wwahost. exe* -Prozesses Ihrer APP kennen, um sie anzufügen.
>
> Die einfachste Möglichkeit zum Anfügen an Ihre JavaScript-App besteht darin, alle anderen JavaScript-apps zu schließen. Sie können auch die PIDs der Ausführung von *wwahost. exe* -Prozessen im Windows Task-Manager notieren, bevor Sie die app starten. Wenn Sie die app starten, ist die *wwahost. exe* -PID die ID, die sich von den zuvor notierten Namen unterscheidet.
::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Debuggen von Apps in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)