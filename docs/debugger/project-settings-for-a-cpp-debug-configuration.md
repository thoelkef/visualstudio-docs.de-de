---
title: Projekteinstellungen für eine C++-Debugkonfiguration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.openlocfilehash: 6b323ab51f4be02faaddc1df7ab2dd6902323d63
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Projekteinstellungen für eine C++-Debugkonfiguration
Sie können die projekteinstellungen für eine C#- oder Visual C++-Debugkonfiguration im Ändern der **Eigenschaftenseiten** (Dialogfeld), wie in beschrieben [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo die debuggerspezifischen Einstellungen im Suchen der **Eigenschaftenseiten** (Dialogfeld).  
  
> [!WARNING]
>  Die debugprojekteinstellungen in der **Konfigurationseigenschaften/Debugging** Kategorie für uwp-apps und Komponenten, die in C++ geschrieben sind, sind unterschiedlich. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Geben Sie die Debugger verwendet den **zu startender Debugger** Listenfeld. Die Auswahl beeinflusst, welche Eigenschaften angezeigt werden.  
  
 Jede Debugeigenschafteneinstellung wird automatisch in die "Pro Benutzer"-Datei (.vcxproj.user) der Projektmappe geschrieben und dort gespeichert, sobald Sie die Projektmappe speichern.  
  
## <a name="configuration-properties-folder-debugging-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen")  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Zu startender Debugger**|Gibt den auszuführenden Debugger mit den folgenden Auswahlmöglichkeiten an:<br /><br /> -   **Lokaler Windows-Debugger**<br />-   **Remote-Windows-Debugger**<br />-   **Webbrowserdebugger**<br />-   **Webdienst-Debugger**|  
|**Befehl** (lokaler Windows-Debugger)|Gibt den Startbefehl für das auf dem lokalen Computer zu debuggende Programm an.|  
|**Remotebefehl** (Remote-Windows-Debugger)|Der Pfad für die EXE-Datei auf dem Remotecomputer. Geben Sie den Pfad wie auf dem Remotecomputer ein.|  
|**Befehlsargumente** (lokaler Windows-Debugger und Remote-Windows-Debugger)|-Gibt Argumente für den oben aufgeführten Befehl an.<br /><br /> In diesem Feld können die folgenden Umleitungsoperatoren verwendet werden:<br /><br /> < `file`<br /> Liest "stdin" aus der Datei.<br /><br /> > `file`<br /> Schreibt "stdout" in die Datei.<br /><br /> >> `file`<br /> Fügt "stdout" an die Datei an.<br /><br /> 2> `file`<br /> Schreibt "stderr" in die Datei.<br /><br /> 2>> `file`<br /> Fügt "stderr" an die Datei an.<br /><br /> 2> &1<br /> Sendet "stderr (2)"-Ausgaben an denselben Speicherort wie "stdout (1)".<br /><br /> 1> &2<br /> Sendet "stdout (1)"-Ausgaben an denselben Speicherort wie "stderr (2)".<br /><br /> In den meisten Fällen sind diese Operatoren nur auf Konsolenanwendungen anwendbar.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des zu debuggenden Programms bezogen auf das Projektverzeichnis an, in dem sich die EXE-Datei befindet. Wenn Sie kein Arbeitsverzeichnis festlegen, wird das Projektverzeichnis verwendet. Beim Remotedebuggen befindet sich das Projektverzeichnis auf dem Remoteserver.|  
|**Fügen Sie** (lokaler Windows-Debugger und Remote-Windows-Debugger)|Gibt an, ob die Anwendung gestartet oder angefügt werden soll. Die Standardeinstellung ist "Nein".|  
|**Remoteservername** (Remote-Windows-Debugger)|Gibt den Namen eines anderen Remotecomputers an, auf dem Sie eine Anwendung debuggen möchten.<br /><br /> Das RemoteMachine-Buildmakro wird auf den Wert dieser Eigenschaft festgelegt. Weitere Informationen finden Sie unter [Makros für Buildbefehle und-Eigenschaften](/cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Verbindung** (Remote-Windows-Debugger)|Ermöglicht es Ihnen, für das Remotedebugging zwischen den Verbindungstypen "Standard" und "Ohne Authentifizierung" zu wechseln. Geben Sie den Namen eines Remotecomputers in der **Remoteservername** Feld. Folgende Verbindungstypen stehen zur Verfügung:<br /><br /> -   **Remote mit Windows-Authentifizierung**<br />-   **Remote ohne Authentifizierung**<br /><br /> **Hinweis** Remotedebuggen ohne Authentifizierung möglicherweise anfällig für den Remotecomputer sicherheitsverletzungen. Der Windows-Authentifizierungsmodus ist sicherer.<br /><br /> Weitere Informationen finden Sie unter [Remote Debugging – Setup](../debugger/remote-debugging.md).|  
|**HTTP-URL** (Webdienst- und Webbrowserdebugger)|Gibt die URL zu dem Projekt an, das Sie debuggen.|  
|**Debuggertyp**|Gibt den Typ des zu verwendenden Debuggers an: **nur systemeigen**, **nur verwaltet**, **nur GPU**, **gemischt**, **automatisch**(Standard), oder **Skript**.<br /><br /> -   **Nur systemeigen** für nicht verwalteten C++-Code ist.<br />-   **Nur verwaltet** ist für Code, der unter der common Language Runtime (verwalteter Code) ausgeführt wird.<br />-   **Gemischte** Debugger für verwalteten und nicht Code verwaltetem aufgerufen.<br />-   **Automatische** legt den Debuggertyp anhand von Compilerdaten und EXE-Daten.<br />-   **Skript** Ruft einen Debugger für Skripts.<br />-   **Nur GPU** ist für C++ AMP-Code, der auf einem GPU-Gerät oder auf die DirectX-Referenzrasterprogramm ausgeführt wird. Finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).|  
|**Umgebung** (lokaler Windows-Debugger und Remote-Windows-Debugger)|Gibt die Umgebungsvariablen für das Programm an, das Sie debuggen. Verwenden Sie die standardmäßige Umgebungsvariablensyntax (z. B. `PATH="%SystemRoot%\..."`). Diese Variablen überschreiben die Systemumgebungsvariablen oder werden zusammengeführt, mit den Systemumgebungsvariablen, abhängig von der **Mergeumgebung** Einstellung. Wenn Sie in der Spalte Einstellungen klicken Sie auf "Bearbeiten..." angezeigt wird. Klicken Sie auf diesen Link, um die Umgebungsvariablen zu bearbeiten.|  
|**Mergeumgebung** (lokaler Windows-Debugger)|Bestimmt, ob die Variablen, sind im angegebenen der **Umgebung** Feld zusammengeführt werden mit der Umgebung, die vom Betriebssystem definiert ist. Die Standardeinstellung ist "Ja".|  
|**SQL-Debuggen** (alle außer MPI-Clusterdebugger)|Ermöglicht das Debuggen von SQL-Prozeduren über die [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Anwendung. Die Standardeinstellung ist "Nein".|  
|**Debuggingbeschleunigungstyp** (nur GPU-debugging)|Gibt das für das Debugging zu verwendende GPU-Gerät an. Durch die Installation von Gerätetreibern für kompatible GPU-Geräte werden zusätzliche Optionen hinzugefügt. Die Standardeinstellung lautet "GPU – Softwareemulator".|  
|**GPU-Standardhaltepunktverhalten** (nur GPU-debugging)|Gibt an, ob für jeden Thread in einer SIMD-Verzerrung ein Haltepunktereignis ausgelöst werden soll. Die Standardeinstellung gibt an, das Haltepunktereignis nur einmal pro Verzerrung auszulösen.|  
|**Standard-Ampaccelerator**|Gibt den Standard-AMPAccelerator beim Debuggen von GPU-Code an. Wählen Sie **WARP-softwarebeschleuniger** untersuchen, ob ein Problem von der Hardware oder eines Treibers nicht vom Code verursacht wird.|  
|**Bereitstellungsverzeichnis** (Remote-Windows-Debugger)|Gibt den Pfad auf dem Remotecomputer an, in den die Projektausgabe vor dem Start kopiert wird. Der Pfad kann eine Netzwerkfreigabe auf dem Remotecomputer sein oder ein Pfad zu einem Ordner auf dem Remotecomputer. Die Standardeinstellung ist leer, was bedeutet, dass die Projektausgabe nicht in eine Netzwerkfreigabe kopiert wird. Sie müssen auch auswählen, um die Bereitstellung der Dateien zu ermöglichen, die **bereitstellen** Kontrollkästchen in der Configuration Manager-Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Zusätzliche bereitzustellende Dateien** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, handelt es sich hierbei um eine durch Semikolons getrennte Liste zusätzlicher Dateien, die in das Bereitstellungsverzeichnis kopieren werden sollen. Die Standardeinstellung ist leer, was bedeutet, dass keine zusätzlichen Dateien in den Bereitstellungsordner kopiert werden. Sie müssen auch auswählen, um die Bereitstellung der Dateien zu ermöglichen, die **bereitstellen** Kontrollkästchen in der Configuration Manager-Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Bereitstellen von Visual C++ Debugging-Laufzeitbibliotheken** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, wird hierdurch angegeben, ob die Visual C++ Debugging-Laufzeitbibliotheken für die aktuelle Plattform in die Netzwerkfreigabe kopiert werden sollen. Die Standardeinstellung ist "Ja".|  
  
## <a name="cc-folder-general-category"></a>Ordner "C/C++" (Kategorie "Allgemein")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Debuginformationsformat** (["/ Z7", / Zd, Zi, / Zi](/cpp/build/reference/z7-zi-zi-debug-information-format))|Gibt den Typ der Debuginformationen an, die für das Projekt erstellt werden sollen.<br /><br /> Mit der Standardoption (/ZI) wird eine Programmdatenbank (.pdb) in einem Format erstellt, das mit "Bearbeiten und Fortfahren" kompatibel ist. Weitere Informationen finden Sie unter ["/ Z7", / Zd, / Zi, / Zi (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Ordner "C/C++" (Kategorie "Optimierung")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Optimization**|Gibt an, ob der Compiler den erstellten Code optimieren soll. Durch die Optimierung wird der auszuführende Code geändert. Optimierter Code entspricht nicht mehr dem Quellcode. Dadurch wird das Debuggen erschwert.<br /><br /> Option "Default" (**deaktiviert (/ 0d**) Optimierung unterdrückt wird. Sie können mit unterdrückter Optimierung entwickeln und sie anschließend bei der Erstellung der Code-Produktionsversion aktivieren.|  
  
## <a name="linker-folder-debugging-category"></a>Ordner "Linker" (Kategorie "Debuggen")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Debuginfo generieren** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Weist den Linker an, Debuginformationen in dem durch /Z7, /Zd, Zi oder /ZI festgelegten Format einzulesen.|  
|**Programmdatenbankdatei** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|In diesem Feld geben Sie den Namen einer PDB-Datei an. Sie müssen ZI oder /Zi als Debuginformationsformat auswählen.|  
|**Private Symbole entfernen** ([/PDBSTRIPPED: Dateiname](/cpp/build/reference/pdbstripped-strip-private-symbols))|Wenn die PDB-Datei keine privaten Symbole enthalten soll, geben Sie in diesem Feld den Namen einer PDB-Datei ein. Mit dieser Option wird eine zweite Programmdatenbank-Datei (PDB) generiert, wenn das Programmabbild mit einer der Compiler- oder Linkeroptionen erstellt wurde, mit denen eine PDB-Datei generiert wird, wie "/DEBUG", "/Z7" oder "/Zd". Oder "/Zi". Die zweite PDB-Datei enthält keine Symbole, die nicht an Kunden weitergegeben werden. Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Zuordnungsdatei generieren** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Weist den Linker an, während der Verknüpfung eine Zuordnungsdatei zu generieren. Die Standardeinstellung ist "Nein". Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/cpp/build/reference/map-generate-mapfile).|  
|**Zuordnen von Dateinamen** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*Namen*)|Bei Auswahl von "Zuordnungsdatei generieren" können Sie in diesem Feld die Zuordnungsdatei angeben. Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/cpp/build/reference/map-generate-mapfile).|  
|**Zuordnungsexporte** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Fügt exportierte Funktionen in die Zuordnungsdatei ein. Die Standardeinstellung ist "Nein". Weitere Informationen finden Sie unter [/MapInfo (umfassen Informationen in der Zuordnungsdatei)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Debugfähige Assembly** ([des Linkers an](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Gibt die Einstellungen für die /ASSEMBLYDEBUG-Option des Linkers an. Folgende Werte sind möglich:<br /><br /> -   **Kein Attribut "Debuggable" ausgegeben,**.<br />-   **Laufzeit nachverfolgen oder deaktivieren Sie Optimierungen (/ ASSEMBLYDEBUG)**. Dies ist die Standardeinstellung.<br />-   **Keine Common Language Runtime und optimizations(/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<erben von der übergeordneten oder Projekt Projektstandard >**.<br />-Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Sie können diese Einstellungen im Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen") programmgesteuert über die Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings-Schnittstelle ändern. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Andere Einstellungen für Projektdateien

Um Projekttypen, z. B. statische Bibliotheken und DLLs zu debuggen, muss Visual Studio-Projekt die richtigen Dateien gefunden werden. Wenn Quellcode verfügbar ist, können Sie statische Bibliotheken und DLLs als separate Projekte derselben Projektmappe hinzufügen (Dadurch wird leicht Debuggen). Informationen zum Erstellen von diesen Projekttypen finden Sie unter [erstellen und Verwenden einer Dynamic Link Library (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) und [erstellen, Verwenden einer statischen Bibliothek](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Mit der Quellcode ist verfügbar, können Sie auch ein neues Visual Studio-Projekt erstellen, indem Sie auswählen **Datei > Neu > Projekt aus vorhandenem Code**.

Zum Debuggen von DLLs, die außerhalb des Projekts sind, finden Sie unter [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Wenn Sie müssen ein eigene DLL-Projekt debuggen, aber nicht Zugriff auf das Projekt für die aufrufende Anwendung finden Sie in [aus einem DLL-Projekt Debuggen von](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Erstellen und Verwalten von Visual C++-Projekten](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Gängige Makros für Buildbefehle und -eigenschaften.](/cpp/ide/common-macros-for-build-commands-and-properties)