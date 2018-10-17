---
title: Projekteinstellungen für eine C++-Debugkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05667c982daa35910bb1d4e1d895fb2bef50fb78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193465"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Projekteinstellungen für eine C++-Debugkonfiguration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die projekteinstellungen für eine C- oder Visual C++-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Dialogfeld wie in beschrieben [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo Sie debuggerspezifischen Einstellungen im finden die **Eigenschaftenseiten** Dialogfeld.  
  
> [!WARNING]
>  Die debugprojekteinstellungen in der **Konfigurationseigenschaften/Debugging** unterscheiden sich die Kategorie für Windows Store-apps und Komponenten, die in C++ geschrieben sind. Finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) im Windows Developer Center.  
  
 Geben Sie an der Debugger für die Verwendung in der **zu startender Debugger** Listenfeld. Die Auswahl beeinflusst, welche Eigenschaften angezeigt werden.  
  
 Jede Debugeigenschafteneinstellung wird automatisch in die "Pro Benutzer"-Datei (.vcxproj.user) der Projektmappe geschrieben und dort gespeichert, sobald Sie die Projektmappe speichern.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen")  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Zu startender Debugger**|Gibt den auszuführenden Debugger mit den folgenden Auswahlmöglichkeiten an:<br /><br /> -   **Lokale Windows-Debugger**<br />-   **Remote-Windows-Debugger**<br />-   **Webbrowserdebugger**<br />-   **Webdienst-Debugger**|  
|**Befehl** (lokaler Windows-Debugger)|Gibt den Startbefehl für das auf dem lokalen Computer zu debuggende Programm an.|  
|**Remotebefehl** (Remote-Windows-Debugger)|Der Pfad für die EXE-Datei auf dem Remotecomputer. Geben Sie den Pfad wie auf dem Remotecomputer ein.|  
|**Befehlsargumente** (lokaler Windows-Debugger und Remote Windows-Debugger)|-Gibt Argumente für den oben aufgeführten Befehl.<br /><br /> In diesem Feld können die folgenden Umleitungsoperatoren verwendet werden:<br /><br /> < `file`<br /> Liest "stdin" aus der Datei.<br /><br /> > `file`<br /> Schreibt "stdout" in die Datei.<br /><br /> >> `file`<br /> Fügt "stdout" an die Datei an.<br /><br /> 2> `file`<br /> Schreibt "stderr" in die Datei.<br /><br /> 2>> `file`<br /> Fügt "stderr" an die Datei an.<br /><br /> 2> &1<br /> Sendet "stderr (2)"-Ausgaben an denselben Speicherort wie "stdout (1)".<br /><br /> 1> &2<br /> Sendet "stdout (1)"-Ausgaben an denselben Speicherort wie "stderr (2)".<br /><br /> In den meisten Fällen sind diese Operatoren nur auf Konsolenanwendungen anwendbar.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des zu debuggenden Programms bezogen auf das Projektverzeichnis an, in dem sich die EXE-Datei befindet. Wenn Sie kein Arbeitsverzeichnis festlegen, wird das Projektverzeichnis verwendet. Beim Remotedebuggen befindet sich das Projektverzeichnis auf dem Remoteserver.|  
|**Fügen Sie** (lokaler Windows-Debugger und Remote Windows-Debugger)|Gibt an, ob die Anwendung gestartet oder angefügt werden soll. Die Standardeinstellung ist "Nein".|  
|**Remoteservername** (Remote-Windows-Debugger)|Gibt den Namen eines anderen Remotecomputers an, auf dem Sie eine Anwendung debuggen möchten.<br /><br /> Das RemoteMachine-Buildmakro wird auf den Wert dieser Eigenschaft festgelegt. Weitere Informationen finden Sie unter [Makros für Buildbefehle und-Eigenschaften](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Verbindung** (Remote-Windows-Debugger)|Ermöglicht es Ihnen, für das Remotedebugging zwischen den Verbindungstypen "Standard" und "Ohne Authentifizierung" zu wechseln. Geben Sie den Namen eines Remotecomputers in der **Remoteservername** Feld. Folgende Verbindungstypen stehen zur Verfügung:<br /><br /> -   **Remote mit Windows-Authentifizierung**<br />-   **Remote ohne Authentifizierung (nur systemeigen)**<br /><br /> **Beachten Sie** Remotedebuggen ohne Authentifizierung möglicherweise anfällig für den Remotecomputer sicherheitsverletzungen. Der Windows-Authentifizierungsmodus ist sicherer.<br /><br /> Weitere Informationen finden Sie unter [Remote Debugging – Setup](../debugger/remote-debugging.md).|  
|**HTTP-URL** (Webdienst- und Webbrowserdebugger)|Gibt die URL zu dem Projekt an, das Sie debuggen.|  
|**Debuggertyp**|Gibt den Typ des zu verwendenden Debuggers: **nur systemeigen**, **nur verwaltet**, **nur GPU**, **gemischt**, **automatisch**(Standard), oder **Skript**.<br /><br /> -   **Nur systemeigen** für nicht verwalteten C++-Code ist.<br />-   **Nur verwaltet** ist für Code, der unter der common Language Runtime (verwalteter Code) ausgeführt wird.<br />-   **Gemischte** Debugger für verwaltete und nicht Code verwaltetem aufgerufen.<br />-   **Automatische** legt den Debuggertyp anhand von Compilerdaten und EXE-Daten.<br />-   **Skript** einen Debugger für Skripts aufruft.<br />-   **Nur GPU** ist für C++ AMP-Code, der auf einem GPU-Gerät oder die DirectX-Referenzrasterprogramm ausgeführt wird. Finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).|  
|**Umgebung** (lokaler Windows-Debugger)|Gibt die Umgebungsvariablen für das Programm an, das Sie debuggen. Verwenden Sie die standardmäßige Umgebungsvariablensyntax (z. B. `PATH="%SystemRoot%\..."`). Diese Variablen überschreiben die Systemumgebungsvariablen oder werden zusammengeführt, mit der Umgebung, je nach den **Mergeumgebung** festlegen. Wenn Sie auf die Spalte "Einstellungen" klicken, wird "Bearbeiten..." angezeigt. Klicken Sie auf diesen Link, um die Umgebungsvariablen zu bearbeiten.|  
|**Zusammenführungsumgebung** (lokaler Windows-Debugger)|Bestimmt, ob die Variablen, die im angegebenen die **Umgebung** Feld wird zusammengeführt werden, mit der Umgebung, die vom Betriebssystem definiert ist. Die Standardeinstellung ist "Ja".|  
|**SQL-Debugging** (alle außer MPI-Clusterdebugger)|Ermöglicht das Debuggen von SQL-Prozeduren über die [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Anwendung. Die Standardeinstellung ist "Nein".|  
|**Debuggingbeschleunigungstyp** (nur GPU-debugging)|Gibt das für das Debugging zu verwendende GPU-Gerät an. Durch die Installation von Gerätetreibern für kompatible GPU-Geräte werden zusätzliche Optionen hinzugefügt. Die Standardeinstellung lautet "GPU – Softwareemulator".|  
|**GPU-Standardhaltepunktverhalten** (nur GPU-debugging)|Gibt an, ob für jeden Thread in einer SIMD-Verzerrung ein Haltepunktereignis ausgelöst werden soll. Die Standardeinstellung gibt an, das Haltepunktereignis nur einmal pro Verzerrung auszulösen.|  
|**Standard-Ampaccelerator** (nur GPU-debugging)|Gibt den Standard-AMPAccelerator beim Debuggen von GPU-Code an. Wählen Sie **WARP-softwarebeschleuniger** untersuchen, ob ein Problem durch die Hardware oder einen Treiber, statt den Code verursacht wird.|  
|**Bereitstellungsverzeichnis** (Remote-Windows-Debugger)|Gibt den Pfad auf dem Remotecomputer an, in den die Projektausgabe vor dem Start kopiert wird. Der Pfad kann eine Netzwerkfreigabe auf dem Remotecomputer sein oder ein Pfad zu einem Ordner auf dem Remotecomputer. Die Standardeinstellung ist leer, was bedeutet, dass die Projektausgabe nicht in eine Netzwerkfreigabe kopiert wird. Sie müssen auch auswählen, um die Bereitstellung der Dateien zu ermöglichen, die **bereitstellen** Kontrollkästchen in der Configuration Manager-Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Zusätzliche bereitzustellende Dateien** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, handelt es sich hierbei um eine durch Semikolons getrennte Liste zusätzlicher Dateien, die in das Bereitstellungsverzeichnis kopieren werden sollen. Die Standardeinstellung ist leer, was bedeutet, dass keine zusätzlichen Dateien in den Bereitstellungsordner kopiert werden. Sie müssen auch auswählen, um die Bereitstellung der Dateien zu ermöglichen, die **bereitstellen** Kontrollkästchen in der Configuration Manager-Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Visual C++ Debugging-Laufzeitbibliotheken bereitstellen** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, wird hierdurch angegeben, ob die Visual C++ Debugging-Laufzeitbibliotheken für die aktuelle Plattform in die Netzwerkfreigabe kopiert werden sollen. Die Standardeinstellung ist "Ja".|  
  
### <a name="cc-folder-general-category"></a>Ordner "C/C++" (Kategorie "Allgemein")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Debuginformationsformat** ([/Z7, / Zd, Zi, / Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Gibt den Typ der Debuginformationen an, die für das Projekt erstellt werden sollen.<br /><br /> Mit der Standardoption (/ZI) wird eine Programmdatenbank (.pdb) in einem Format erstellt, das mit "Bearbeiten und Fortfahren" kompatibel ist. Weitere Informationen finden Sie unter [/Z7, / Zd, / Zi, / Zi (Debuginformationsformat)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Ordner "C/C++" (Kategorie "Optimierung")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Optimization**|Gibt an, ob der Compiler den erstellten Code optimieren soll. Durch die Optimierung wird der auszuführende Code geändert. Optimierter Code entspricht nicht mehr dem Quellcode. Dadurch wird das Debuggen erschwert.<br /><br /> Die Standardoption (**deaktiviert (/ 0d**) wird die Optimierung unterdrückt. Sie können mit unterdrückter Optimierung entwickeln und sie anschließend bei der Erstellung der Code-Produktionsversion aktivieren.|  
  
### <a name="linker-folder-debugging-category"></a>Ordner "Linker" (Kategorie "Debuggen")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Generieren von Debuginformationen** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Weist den Linker an, Debuginformationen in dem durch /Z7, /Zd, Zi oder /ZI festgelegten Format einzulesen.|  
|**Programmdatenbankdatei erstellen** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|In diesem Feld geben Sie den Namen einer PDB-Datei an. Sie müssen ZI oder /Zi als Debuginformationsformat auswählen.|  
|**Private Symbole entfernen** ([/PDBSTRIPPED: Dateiname](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Wenn die PDB-Datei keine privaten Symbole enthalten soll, geben Sie in diesem Feld den Namen einer PDB-Datei ein. Mit dieser Option wird eine zweite Programmdatenbank-Datei (PDB) generiert, wenn das Programmabbild mit einer der Compiler- oder Linkeroptionen erstellt wurde, mit denen eine PDB-Datei generiert wird, wie "/DEBUG", "/Z7" oder "/Zd". Oder "/Zi". Die zweite PDB-Datei enthält keine Symbole, die nicht an Kunden weitergegeben werden. Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Zuordnungsdatei generieren** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Weist den Linker an, während der Verknüpfung eine Zuordnungsdatei zu generieren. Die Standardeinstellung ist "Nein". Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Name der Zuordnungsdatei** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*Namen*)|Bei Auswahl von "Zuordnungsdatei generieren" können Sie in diesem Feld die Zuordnungsdatei angeben. Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Zuordnungsexporte** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Fügt exportierte Funktionen in die Zuordnungsdatei ein. Die Standardeinstellung ist "Nein". Weitere Informationen finden Sie unter [/MapInfo (Daten in Zuordnungsdatei einfügen)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Debugfähige Assembly** ([ASSEMBLYDEBUG](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Gibt die Einstellungen für die /ASSEMBLYDEBUG-Option des Linkers an. Folgende Werte sind möglich:<br /><br /> -   **Kein Attribut "Debuggable" ausgegeben,**.<br />-   **Laufzeit nachverfolgen und deaktivierte Optimierungen (/ ASSEMBLYDEBUG)**. Dies ist die Standardeinstellung.<br />-   **Keine Common Language Runtime-Überwachung und aktivieren Sie optimizations(/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<erben von der übergeordneten oder ein Projekt standardmäßig >**.<br />-Weitere Informationen finden Sie unter [ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Sie können diese Einstellungen im Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen") programmgesteuert über die Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings-Schnittstelle ändern. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Erstellen und Verwalten von Visual C++-Projekten](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Gängige Makros für Buildbefehle und -eigenschaften.](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



