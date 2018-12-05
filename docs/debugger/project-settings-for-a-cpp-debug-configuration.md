---
title: Projekteinstellungen für eine C++-Debugkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: b333dca8f717cbd8e1172ed00b4a044aafeed857
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389655"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Projekteinstellungen für eine C++-Debugkonfiguration
Sie können die projekteinstellungen für eine C- oder Visual C++-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Dialogfeld wie in beschrieben [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Dialogfeld **Eigenschaftenseiten** zu finden sind.  
  
> [!NOTE]
>  Die debugprojekteinstellungen in der **Konfigurationseigenschaften/Debugging** Kategorie unterscheiden sich für UWP-apps und Komponenten, die in C++ geschrieben sind. Finden Sie unter [Starten einer Debugsitzung (VB, C#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Jede Debugeigenschafteneinstellung wird automatisch geschrieben und in der Datei "pro Benutzer" gespeichert (. vcxproj.user) für Ihre Lösung, wenn Sie die Projektmappe speichern.  

 Geben Sie an der Debugger für die Verwendung in der **zu startender Debugger** Listenfeld, wie in der folgenden Tabelle beschrieben. Die Auswahl beeinflusst, welche Eigenschaften angezeigt werden.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen")  
  
| **Einstellung** | **Beschreibung** |
| - | - |
| **Debugger to launch** (Zu startender Debugger) | Gibt den auszuführenden Debugger mit den folgenden Auswahlmöglichkeiten an:<br /><br /> -   **Lokaler Windows-Debugger**<br />-   **Remote-Windows-Debugger**<br />-   **Webbrowserdebugger**<br />-   **Webdienst-Debugger** |
| **Befehl** (Lokaler Windows-Debugger) | Gibt den Startbefehl für das auf dem lokalen Computer zu debuggende Programm an. |
| **Remotebefehl** (Remote-Windows-Debugger) | Der Pfad für die EXE-Datei auf dem Remotecomputer. Geben Sie den Pfad wie auf dem Remotecomputer ein. |
| **Befehlsargumente** (lokaler Windows-Debugger)<br /><br /> **Remotebefehlsargumente** (Remote-Windows-Debugger) | Gibt Argumente für den oben aufgeführten Befehl an.<br /><br /> In diesem Feld können die folgenden Umleitungsoperatoren verwendet werden:<br /><br /> < `file`<br /> Liest "stdin" aus der Datei.<br /><br /> > `file`<br /> Schreibt "stdout" in die Datei.<br /><br /> >> `file`<br /> Fügt "stdout" an die Datei an.<br /><br /> 2> `file`<br /> Schreibt "stderr" in die Datei.<br /><br /> 2>> `file`<br /> Fügt "stderr" an die Datei an.<br /><br /> 2> &1<br /> Sendet "stderr (2)"-Ausgaben an denselben Speicherort wie "stdout (1)".<br /><br /> 1> &2<br /> Sendet "stdout (1)"-Ausgaben an denselben Speicherort wie "stderr (2)".<br /><br /> In den meisten Fällen sind diese Operatoren nur auf Konsolenanwendungen anwendbar. |
| **Arbeitsverzeichnis** | Gibt das Arbeitsverzeichnis des zu debuggenden Programms bezogen auf das Projektverzeichnis an, in dem sich die EXE-Datei befindet. Wenn Sie kein Arbeitsverzeichnis festlegen, wird das Projektverzeichnis verwendet. Für das Remotedebuggen ist das Projektverzeichnis auf dem Remoteserver aus. |
| **Anfügen** (Lokaler Windows-Debugger und Remote-Windows-Debugger) | Gibt an, ob die Anwendung gestartet oder angefügt werden soll. Die Standardeinstellung ist "Nein". |
| **Remoteservername** (Remote-Windows-Debugger) | Gibt den Namen eines anderen Remotecomputers an, auf dem Sie eine Anwendung debuggen möchten.<br /><br /> Das RemoteMachine-Buildmakro wird auf den Wert dieser Eigenschaft festgelegt. Weitere Informationen hierzu finden Sie unter [Makros für Buildbefehle und -eigenschaften](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Verbindung** (Remote-Windows-Debugger) | Ermöglicht es Ihnen, für das Remotedebugging zwischen den Verbindungstypen "Standard" und "Ohne Authentifizierung" zu wechseln. Geben Sie im Feld **Remoteservername** den Namen des Remotecomputers an. Folgende Verbindungstypen stehen zur Verfügung:<br /><br /> -   **Remote mit Windows-Authentifizierung**<br />-   **Remote ohne Authentifizierung**<br /><br /> **Hinweis:** Der Remotecomputer ist durch das Remotedebuggen ohne Authentifizierung möglicherweise anfällig für Sicherheitsverletzungen. Der Windows-Authentifizierungsmodus ist sicherer.<br /><br /> Weitere Informationen finden Sie unter [Remote Debugging setup (Einrichten des Remotedebuggens)](../debugger/remote-debugging.md). |
| **HTTP-URL** (Webdienst- und Webbrowserdebugger) | Gibt die URL zu dem Projekt an, das Sie debuggen. |
| **Debuggertyp** | Gibt den Typ des zu verwendenden Debuggers an: **Nur nativ**, **Nur verwaltet**, **Nur GPU**, **Gemischt**, **Automatisch** (Standard) oder **Skript**.<br /><br /> Die Einstellung **Nur nativ** eignet sich für nicht verwalteten C++-Code.<br />Die Einstellung **Nur verwaltet** ist für Code konzipiert, der in der Common Language Runtime ausgeführt wird (verwalteter Code).<br />Mit **Gemischt** werden Debugger sowohl für verwalteten als auch für nicht verwalteten Code aufgerufen.<br />Die Einstellung **Automatisch** legt den Debuggertyp anhand von Compilerdaten und EXE-Daten fest.<br />**Skript** ruft einen Debugger für Skripts auf.<br />Die Einstellung **Nur GPU** ist für C++ AMP-Code vorgesehen, der auf einem GPU-Gerät oder im DirectX-Referenzraster ausgeführt wird. Finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md). |
| **Umgebung** (lokaler Windows-Debugger und Remote Windows-Debugger) | Gibt die Umgebungsvariablen für das Programm an, das Sie debuggen. Verwenden Sie die standardmäßige Umgebungsvariablensyntax (z. B. `PATH="%SystemRoot%\..."`). Je nach Einstellung der **Zusammenführungsumgebung** überschreiben diese Variablen die Systemumgebung oder werden mit der Systemumgebung zusammengeführt. Wenn Sie in der Spalte "Einstellungen" klicken, wird "Bearbeiten...". Wählen Sie diesen Link, um Umgebungsvariablen zu bearbeiten. |
| **Zusammenführungsumgebung** (Lokaler Windows-Debugger) | Legt fest, ob die in dem Feld **Umgebung** angegebenen Variablen mit der vom verwendeten Betriebssystem definierten Umgebung zusammengeführt werden. Die Standardeinstellung ist "Ja". |
| **SQL-Debugging** (alle außer MPI-Clusterdebugger) | Ermöglicht das Debuggen von SQL-Prozeduren über die [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Anwendung. Die Standardeinstellung ist "Nein". |
| **Debuggingbeschleunigungstyp** (nur GPU-Debugging) | Gibt das für das Debugging zu verwendende GPU-Gerät an. Durch die Installation von Gerätetreibern für kompatible GPU-Geräte werden zusätzliche Optionen hinzugefügt. Die Standardeinstellung lautet **GPU – Softwareemulator**. |
| **GPU-Standardhaltepunktverhalten** (nur GPU-Debugging) | Gibt an, ob für jeden Thread in einer SIMD-Verzerrung ein Haltepunktereignis ausgelöst werden soll. Die Standardeinstellung gibt an, das Haltepunktereignis nur einmal pro Verzerrung auszulösen. |
| **AMP-Standardbeschleunigung** | Gibt den Standard-AMPAccelerator beim Debuggen von GPU-Code an. Wählen Sie **WARP-Softwarebeschleunigung** aus, um zu untersuchen, ob ein Problem von der Hardware oder einem Treibers verursacht wird und nicht vom Code. |
| **Bereitstellungsverzeichnis** (Remote-Windows-Debugger) | Gibt den Pfad auf dem Remotecomputer an, in den die Projektausgabe vor dem Start kopiert wird. Der Pfad kann eine Netzwerkfreigabe auf dem Remotecomputer sein oder ein Pfad zu einem Ordner auf dem Remotecomputer. Die Standardeinstellung ist leer, was bedeutet, dass die Projektausgabe nicht in eine Netzwerkfreigabe kopiert wird. Sie müssen im Dialogfeld „Konfigurations-Manager“ auch das Kontrollkästchen **Bereitstellen** aktivieren, um die Bereitstellung der Dateien zu ermöglichen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md). |
| **Zusätzliche bereitzustellende Dateien** (Remote-Windows-Debugger) | Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt ist, ist dies eine durch Semikolons getrennte Liste zusätzlicher Dateien in das Bereitstellungsverzeichnis kopiert. Die Standardeinstellung ist leer, was bedeutet, dass keine zusätzlichen Dateien in den Bereitstellungsordner kopiert werden. Sie müssen im Dialogfeld „Konfigurations-Manager“ auch das Kontrollkästchen **Bereitstellen** aktivieren, um die Bereitstellung der Dateien zu ermöglichen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md). |
| **Visual C++-Debug-Laufzeitbibliotheken bereitstellen** (Remote-Windows-Debugger) | Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, wird hierdurch angegeben, ob die Visual C++ Debugging-Laufzeitbibliotheken für die aktuelle Plattform in die Netzwerkfreigabe kopiert werden sollen. Die Standardeinstellung ist "Ja". |
  
## <a name="cc-folder-general-category"></a>Ordner "C/C++" (Kategorie "Allgemein")  
  
|Einstellung|Beschreibung |  
|-------------|-----------------|  
|**Debuginformationsformat** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Gibt den Typ der Debuginformationen an, die für das Projekt erstellt werden sollen.<br /><br /> Mit der Standardoption (/ZI) wird eine Programmdatenbank (.pdb) in einem Format erstellt, das mit "Bearbeiten und Fortfahren" kompatibel ist. Weitere Informationen hierzu finden Sie unter [/Z7, /Zd, /Zi, /ZI (Debug information format) (/Z7, /Zd, /Zi, /ZI (Debuginformationsformat))](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Ordner "C/C++" (Kategorie "Optimierung")  
  
|Einstellung|Beschreibung |  
|-------------|-----------------|  
|**Optimization**|Gibt an, ob der Compiler den erstellten Code optimieren soll. Durch die Optimierung wird der auszuführende Code geändert. Optimierter Code entspricht nicht mehr den Quellcode, der Debuggen erschwert.<br /><br /> Die Standardoption (**Deaktiviert (/0d)**) dient zum Unterdrücken der Optimierung. Sie können mit unterdrückter Optimierung entwickeln und sie anschließend bei der Erstellung der Code-Produktionsversion aktivieren.|  
  
## <a name="linker-folder-debugging-category"></a>Ordner "Linker" (Kategorie "Debuggen")  
  
|Einstellung|Beschreibung |  
|-------------|-----------------|  
|**Debuginfo generieren** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Weist den Linker an, Debuginformationen in dem durch [/Z7, /Zd, Zi oder /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format) festgelegten Format einzulesen.|  
|**Programmdatenbankdatei erstellen** ([/PDB:Name](/cpp/build/reference/pdb-use-program-database))|Geben Sie den Namen der Programmdatenbankdatei (PDB) in diesem Feld ein. Sie müssen ZI oder /Zi als Debuginformationsformat auswählen.|  
|**Private Symbole entfernen** ([/PDBSTRIPPED:Dateiname](/cpp/build/reference/pdbstripped-strip-private-symbols))|Wenn die PDB-Datei keine privaten Symbole enthalten soll, geben Sie in diesem Feld den Namen einer PDB-Datei ein. Diese Option wird eine zweite PDB-Datei erstellt, wenn das Programmabbild mit einer der Compiler- oder Linkeroptionen erstellt wurde, die eine PDB-Datei, z. B. "/ Debug", "/ Z7", "/ Zd" zu generieren. Oder "/Zi". Die zweite PDB-Datei enthält keine Symbole, die nicht an Kunden weitergegeben werden. Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Zuordnungsdatei generieren** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Weist den Linker an, während der Verknüpfung eine Zuordnungsdatei zu generieren. Die Standardeinstellung ist "Nein". Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/cpp/build/reference/map-generate-mapfile).|  
|**Name der Zuordnungsdatei** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*Namen*)|Bei Auswahl von "Zuordnungsdatei generieren" können Sie in diesem Feld die Zuordnungsdatei angeben. Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/cpp/build/reference/map-generate-mapfile).|  
|**Zuordnungsexporte** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Fügt exportierte Funktionen in die Zuordnungsdatei ein. Die Standardeinstellung ist "Nein". Weitere Informationen finden Sie unter [/MapInfo (Daten in Zuordnungsdatei einfügen)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Debugfähige Assembly** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Gibt die Einstellungen für die /ASSEMBLYDEBUG-Option des Linkers an. Dabei sind folgende Werte möglich:<br /><br /> -   **Das Attribut „Debuggable“ wurde nicht ausgegeben**.<br />-   **Problemnachverfolgung zur Laufzeit und deaktivierte Optimierungen (/ASSEMBLYDEBUG)**. Dies ist die Standardeinstellung.<br />-   **Keine Problemnachverfolgung zur Laufzeit und aktivierte Optimierungen (/ASSEMBLYDEBUG)**.<br />-   **\<Vom übergeordneten Projekt erben oder Projektstandard>**<br />Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (Add DebuggableAttribute) (/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen))](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Sie können diese Einstellungen im Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen") programmgesteuert über die Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings-Schnittstelle ändern. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Andere projekteinstellungen

Um Projekttypen, z. B. statische Bibliotheken und DLLs zu debuggen, muss Visual Studio-Projekt die richtigen Dateien gefunden werden. Wenn Quellcode verfügbar ist, können Sie statische Bibliotheken und DLLs der gleichen Projektmappe, um das Debugging zu erleichtern als separate Projekte hinzufügen. Informationen zum Erstellen dieser Projekttypen, finden Sie unter [erstellen und Verwenden einer Dynamic Link Library (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) und [Erstellen einer mit einer statischen Bibliothek](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Der Quellcode ist verfügbar, können Sie auch ein neues Visual Studio-Projekt erstellen, durch Auswahl **Datei** > **neu** > **Projekt aus vorhandenem Code**.

Zum Debuggen von DLLs, die außerhalb des Projekts sind, finden Sie unter [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Wenn Sie müssen zum Debuggen Ihres eigenen DLL-Projekts, jedoch nicht haben Zugriff auf das Projekt für die aufrufende Anwendung finden Sie unter [aus einem DLL-Projekt Debuggen](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Siehe auch  
 [Debugging native code (Debuggen von nativem Code)](../debugger/debugging-native-code.md)   
 [Debugger settings and preparation (Einstellungen und Vorbereitung des Debuggers)](../debugger/debugger-settings-and-preparation.md)   
 [Erstellen und Verwalten von Visual C++-Projekten](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (Add DebuggableAttribute) (/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen))](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Gängige Makros für Buildbefehle und -eigenschaften](/cpp/ide/common-macros-for-build-commands-and-properties)