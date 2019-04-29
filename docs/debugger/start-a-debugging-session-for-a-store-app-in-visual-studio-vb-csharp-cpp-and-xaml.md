---
title: Starten einer Debugsitzung für UWP-Apps | Microsoft-Dokumentation
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
ms.openlocfilehash: 7c65662d054b8c3dd9e650fe088f7048cc3b4071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930034"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Starten einer Debugsitzung für eine UWP-App

Dieser Artikel beschreibt, wie Sie eine Visual Studio-Debugsitzung für eine universelle Windows-Plattform (UWP)-app zu starten. UWP-apps in XAML geschrieben werden können und C++, XAML und C#Nachrichtentexts. Klicken Sie zum Starten des Debuggens einer UWP-Apps Konfigurieren der Debugsitzung, und wählen Sie die Möglichkeit, die app zu starten.

::: moniker range=">=vs-2019"
> [!NOTE]
> Ab Visual Studio-2019 wird werden für HTML und JavaScript-UWP-apps nicht mehr unterstützt.
::: moniker-end
::: moniker range="vs-2017"
In Visual Studio 2017 gelten die meisten Befehle und Optionen, die in diesem Artikel gezeigten auch für UWP-apps für HTML und JavaScript. Verwaltete, in denen Befehle unterschiedlich sind und C++ apps JavaScript-apps in der Regel sind identisch mit Befehlen für C++ UWP-apps.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Starten des Debuggen von Visual Studio-Symbolleiste

Die einfachste Möglichkeit zum Konfigurieren und starten Sie das Debuggen wird der Visual Studio-Standardsymbolleiste.

![Über die Symbolleiste Debuggen](../debugger/media/vsrun_select_target_device.png)

1. Von der **Konfiguration** Dropdownliste auf der **Standard** Symbolleiste wählen **Debuggen**.

1. Aus der **Plattform** Dropdownliste, wählen Sie die Zielplattform für erstellen.

1. Wählen Sie in der Dropdownliste neben dem grünen Pfeil der Debug-Ziel. Sie können einen lokalen Computer, direkt verbundenen Gerät, lokalen Visual Studio-Simulator, Remoteneustart des Geräts oder -Emulator auswählen.

1. Wählen Sie zum Starten des Debuggens das grüne **starten** Pfeil auf der Symbolleiste, oder wählen Sie **Debuggen** > **Debuggen starten**, oder drücken Sie **F5**.

   In Visual Studio wird die Anwendung mit dem angefügten Debugger erstellt und gestartet.

Debuggen wird fortgesetzt, bis ein Haltepunkt erreicht wird, Sie manuell anhalten, eine nicht behandelte Ausnahme auftritt, oder die Anwendung beendet wird.

### <a name="BKMK_Choose_the_deployment_target"></a> Ziel-Bereitstellungsoptionen

Sie können das Debugziel in der Symbolleiste von Visual Studio festlegen oder Debuggen Eigenschaftenseite des Projekts. Wählen Sie einen der folgenden Optionen aus:

|||
|-|-|
|**Lokaler Computer**|Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer.|
|**Simulator**|Debuggen der app in Visual Studio-Simulator für UWP-apps. Der Simulator ist ein desktop-Fenster, das simuliert Gerätefunktionen, wie Fingereingabe und gerätedrehung, die möglicherweise nicht auf dem lokalen Computer vorhanden ist. Der Simulator-Option steht nur, wenn Ihrer app **Mindestversion. Version** ist kleiner als oder gleich der für das Betriebssystem auf dem lokalen Computer. Weitere Informationen finden Sie unter [Ausführen von UWP-apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Remotecomputer**|Debuggen der app auf einem Gerät, auf dem lokalen Computer über ein Netzwerk oder Ethernet-Kabel verbunden. Remotetools für Visual Studio muss installiert sein und auf dem Remotegerät ausgeführt. Weitere Informationen finden Sie unter [Ausführen von UWP-apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Gerät**|Debuggen der app auf einem USB-Gerät. Das Gerät muss Developer entsperrt und den Bildschirm nicht gesperrt.|
|**Mobile-Emulator**|Starten Sie den Emulator in den Namen des Emulators angegeben, Bereitstellen Sie die app und mit dem Debuggen beginnen. Emulatoren sind nur auf Computern mit aktiviertem Hyper-V verfügbar.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Konfigurieren des Debuggens auf der Seite der Projekteigenschaften

Verwenden Sie zum Konfigurieren zusätzlicher Optionen für das Debuggen des Projekts Debuggen-Eigenschaftenseite.

**So öffnen Sie die Debugeigenschaften:**

1. In **Projektmappen-Explorer**, wählen Sie das Projekt, und wählen Sie dann die **Eigenschaften** Symbol, oder mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.

1. Auf der linken Seite von der **Eigenschaften** Bereich:

   - Für C# und Visual Basic-Anwendungen, die Option **Debuggen**.

     ![C#und Visual Basic-Projekt Debuggen-Eigenschaftenseite](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Für C++ -apps wählen **Konfigurationseigenschaften** > **Debuggen**.

     ![C++Debugeigenschaftenseite von UWP-app](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> Auswahl des zu verwendenden Debuggers

Für C# und Visual Basic-Anwendungen, Visual Studio debuggt verwaltetem Code in der Standardeinstellung. Sie können auch andere oder zusätzliche Codetypen debuggen. Sie können auch festlegen **Debuggertyp** Werte für alle Hintergrundaufgaben, die Teil des Projekts sind.

In C++-Anwendungen debuggt Visual Studio systemeigenen Code standardmäßig an. Sie können auch bestimmte Codetypen anstelle von oder zusätzlich zu den systemeigenen Code Debuggen.

**So geben Sie Code, die zu debuggenden Codetypen an:**

- Für C# , und wählen Sie einen der folgenden Debugger in Visual Basic-Anwendungen, die **Anwendungstyp** und **Hintergrund Prozesstyp** Dropdownmenüs unter **Debuggertyp** auf die **Debuggen** Eigenschaftenseite.

- Für C++ -apps wählen Sie einen der folgenden Debugger in den **Debuggertyp** Dropdownliste auf der **Debuggen** Eigenschaftenseite.

|||
|-|-|
|**Nur verwaltet**|Für das Debuggen des verwalteten Codes der Anwendung. JavaScript- und systemeigener C/C++-Code werden ignoriert.|
|**Nur systemeigen**|Für das Debuggen des systemeigenen C/C++-Codes der Anwendung. Verwalteter und JavaScript-Code werden ignoriert.|
|**Gemischt (verwaltet und systemeigen)**|Für das Debuggen des systemeigenen C/C++- und des verwalteten Codes der Anwendung. JavaScript-Code wird ignoriert. In C++ Projekte, heißt diese Option **verwaltet und systemeigen**.|
|**Skript**|Für das Debuggen des JavaScript-Codes der Anwendung. Verwalteter und systemeigener Code werden ignoriert.|
|**Nativ mit Skript**|Debuggen des systemeigenen C/C++-Code und JavaScript-Code in Ihrer app. Verwalteter Code wird ignoriert. Verfügbar in C++ Projekte oder Hintergrund nur Vorgänge.|
|**Nur GPU (C++ AMP)**|Debuggen von systemeigenem C++-Code, der auf einer Grafikverarbeitungseinheit (GPU) ausgeführt wird. In der nur C++-Projekte verfügbar.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> Deaktivieren von netzwerkloopbacks (optional)

 Aus Sicherheitsgründen eine UWP-app, die in der Standardweise installiert ist Netzwerkaufrufe an das Gerät nicht möglich, die er installiert ist. Visual Studio-ausgenommene bereitgestellt apps, die von dieser Regel standardmäßig, damit Sie Kommunikationsverfahren auf einem einzelnen Computer testen können. Bevor Sie Ihre app freigeben, sollten Sie die app ohne die Ausnahme testen.

**So entfernen Sie die Netzwerkloopbackausnahme:**

- Für C# und Visual Basic-Anwendungen, deaktivieren Sie die **lokales netzwerkloopback zulassen** Kontrollkästchen unter **Startoptionen** auf die **Debuggen** Eigenschaftenseite.

- Für Visual C++ -apps wählen **keine** aus der **lokaler Netzwerkloopback zulassen** Dropdownliste auf der **Debuggen** Eigenschaftenseite.

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Installieren Sie die Anwendung neu, wenn Sie das Debuggen starten (optional)
 Diagnostizieren Sie Probleme bei der Installation eine C# oder Visual Basic-app, und wählen **deinstallieren und installieren Sie Mein Paket erneut** auf die **Debuggen** Eigenschaftenseite. Diese Option wird die ursprüngliche Installation neu erstellt, beim Starten des Debuggens. Diese Option ist nicht verfügbar für C++ Projekte.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Festlegen von Authentifizierungsoptionen für das Remotedebuggen

Standardmäßig müssen Sie Windows-Anmeldeinformationen zum Ausführen des Remotedebuggers, bei der Auswahl bereitstellen **Remotecomputer** als Bereitstellungsziel. Sie können die Authentifizierungsanforderung ändern.

Die **universell (unverschlüsseltes Protokoll)** Authentifizierungsmodus ist für IoT, Xbox und HoloLens-Geräte, und creators Update oder höher Windows 10-PCs.

**So ändern die Authentifizierungsmethode:**

- Für C# und Visual Basic-apps, auf die **Debuggen** auf der Seite wählen **Remotecomputer** als die **Zielgerät**. Wählen Sie dann **keine** oder **universell (unverschlüsseltes Protokoll)** für **Authentifizierungsmodus**.

- Für C++ -apps wählen **Remotecomputer** unter **zu startender Debugger** auf die **Debuggen** Eigenschaftenseite. Wählen Sie dann **keine Authentifizierung** oder **universell (unverschlüsseltes Protokoll)** für **Authentifizierungstyp**.

> [!CAUTION]
> Es gibt keine Netzwerksicherheit, beim Ausführen des Remotedebuggers in **keine** oder **universell (unverschlüsseltes Protokoll)** Modi. Wählen Sie diesen Modus nur in vertrauenswürdigen Netzwerken, die Sie nicht sicher durch bösartigen Code oder feindlichen Datenverkehr gefährdet sind.

## <a name="BKMK_Start_the_debugging_session"></a> Startoptionen für das Debuggen

Bei der Auswahl **Debuggen** > **Debuggen starten** , oder drücken Sie **F5**, Visual Studio die app mit dem angefügten Debugger gestartet. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Starten Sie das Debuggen aber Starten der Delay-app

Standardmäßig startet der Visual Studio die app sofort beim Starten des Debuggens. Sie können auch festlegen, dass die app im Debugmodus ausgeführt, aber die app außerhalb des Debuggers zu starten. Angenommen, Sie können aus der Windows-app starten debuggen möchten **starten** Menü oder zum Debuggen eines Prozesses Hintergrund in der app. Wenn Sie diese Option auswählen, wird die app im Debugger beim Start gestartet.

**So deaktivieren Sie die automatische app-Start**

- Für C# und Visual Basic-Anwendungen, die Option **nicht starten sondern Debuggen meinen Code** unter **Startoptionen** auf die **Debuggen** Eigenschaftenseite.

- Für C++ -apps wählen **keine** aus der **Anwendung starten** Dropdownliste auf der **Debuggen** Eigenschaftenseite.

Weitere Informationen zum Debuggen von Hintergrundaufgaben finden Sie unter [Trigger anhalten, fortsetzen und hintergrundereignissen für UWP-apps](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Debuggen einer UWP-app installierten oder ausgeführten

Sie können **Debuggen Installed App Package** eine UWP-app zu debuggen, die bereits installiert oder auf einem Gerät lokal oder remote ausgeführt wird. Die app kann aus dem Microsoft Store installiert wurden, oder er möglicherweise nicht über die Visual Studio-Projekt. Die app kann z. B. ein benutzerdefiniertes Buildsystem vorhanden sein, das Visual Studio nicht verwendet.

Sie können die installierte app sofort starten, oder Sie können festlegen, für die Ausführung im Debugger, wenn mit einer anderen Methode gestartet. Weitere Informationen finden Sie unter [Trigger anhalten, fortsetzen und hintergrundereignissen für UWP-apps)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Wählen Sie zum Starten einer installierten oder ausgeführten UWP-app im Debugger **Debuggen** > **andere Debugziele** > **Debuggen Installed App Package**. Weitere Informationen finden Sie unter [Debuggen eines installierten app-Pakets](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anfügen des Debuggers an eine ausgeführte Windows 8.x-app

Um den Debugger an eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -App anzufügen, müssen Sie im Manager für debugfähige Pakete festlegen, dass die App im Debugmodus ausgeführt wird. Manager für Debugfähige Pakete wird mit den Remotetools für Visual Studio installiert.

1. Installieren der Remotetools für Visual Studio auf dem Gerät, in dem die app installiert ist. Weitere Informationen finden Sie unter [Installieren der Remotetools](../debugger/remote-debugging.md).

1. In der Windows **starten** Startbildschirm, suchen und starten Sie **Manager für Debugfähige Pakete**.

   Es wird ein ordnungsgemäß für das AppxDebug-Cmdlet konfiguriertes PowerShell-Fenster angezeigt.

1. Geben Sie den PackageFullName-Bezeichner der app.

   1. Geben Sie zum Anzeigen einer Liste, die von allen apps PackageFullName enthält `Get-AppxPackage` an der PowerShell-Eingabeaufforderung.

   1. Geben Sie an der PowerShell-Eingabeaufforderung `Enable-AppxDebug <PackageFullName>`, wobei \<PackageFullName > ist der PackageFullName-Bezeichner der app.

1. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

1. In der **an den Prozess anhängen** Dialogfeld geben das Remotegerät im der **Verbindungsziel** Feld.

   Sie können Geben Sie den Gerätenamen ein, wählen Sie sie aus der Dropdownliste im der **Verbindungsziel** Feld, oder wählen Sie **finden** finden Sie das Gerät in die **Remoteverbindungen** im Dialogfeld.

1. An den Typ des Codes, zu debuggen, neben, der **Anfügen an** Kontrollkästchen **wählen**.

1. In der **Codetyp auswählen** Dialogfeld wählen:
   - **Den Typ der zu debuggenden Codetyp automatisch bestimmen**, oder
   - **Diese Codetypen debuggen**, und wählen Sie dann einen oder mehrere Codetypen aus der Liste.

1. In der **verfügbare Prozesse** wählen Sie die app-Prozess zu debuggen.

1. Wählen Sie **Anfügen**.

 Der Debugger wird in Visual Studio an den Prozess angefügt. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript-Apps werden in einer Instanz des Prozesses *wwahost.exe* ausgeführt. Wenn mehr als eine JavaScript-app ausgeführt wird, müssen Sie wissen, die numerische Prozess-Id (PID) Ihrer App *wwahost.exe* Prozess zum Anfügen.
>
> Die einfachste Möglichkeit zum Anfügen an Ihrer JavaScript-app werden alle anderen JavaScript-apps zu schließen. Oder Sie können die PIDs der Ausführung feststellen *wwahost.exe* Prozesse im Windows Task-Manager, bevor Sie Ihre app zu starten. Wenn Sie Ihre app zu starten, die *wwahost.exe* PID verkürzt werden kann, die sich von denen Sie zuvor notiert haben.
::: moniker-end

## <a name="see-also"></a>Siehe auch
- [Debuggen von Apps in Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)