---
title: Projekteinstellungen für eine C++-Debugkonfiguration | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687559"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Projekteinstellungen für eine C++-Debugkonfiguration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Projekteinstellungen für eine C-oder Visual C++-Debugkonfiguration im Dialogfeld **Eigenschaften Seiten** ändern, wie unter Gewusst [wie: Festlegen von Debug-und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)erläutert. Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Dialogfeld **Eigenschaftenseiten** zu finden sind.  
  
> [!WARNING]
> Die debugprojekteinstellungen in der Kategorie **Konfigurations Eigenschaften/Debuggen** für Windows Store-Apps und Komponenten, die in C++ geschrieben sind, unterscheiden sich. Weitere Informationen finden Sie unter [Starten einer Debugsitzung (VB, c#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) im Windows-Entwicklungs Center.  
  
 Geben Sie den Debugger an, der im Listenfeld **zum Starten des Debuggers** verwendet werden soll. Die Auswahl beeinflusst, welche Eigenschaften angezeigt werden.  
  
 Jede Debugeigenschafteneinstellung wird automatisch in die "Pro Benutzer"-Datei (.vcxproj.user) der Projektmappe geschrieben und dort gespeichert, sobald Sie die Projektmappe speichern.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen")  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Debugger to launch** (Zu startender Debugger)|Gibt den auszuführenden Debugger mit den folgenden Auswahlmöglichkeiten an:<br /><br /> -   **Lokaler Windows-Debugger**<br />-   **Remote-Windows-Debugger**<br />-   **Webbrowserdebugger**<br />-   **Webdienst-Debugger**|  
|**Befehl** (Lokaler Windows-Debugger)|Gibt den Startbefehl für das auf dem lokalen Computer zu debuggende Programm an.|  
|**Remotebefehl** (Remote-Windows-Debugger)|Der Pfad für die EXE-Datei auf dem Remotecomputer. Geben Sie den Pfad wie auf dem Remotecomputer ein.|  
|**Befehlsargumente** (lokaler Windows-Debugger und Remote-Windows-Debugger)|Gibt Argumente für den oben aufgeführten Befehl an.<br /><br /> In diesem Feld können die folgenden Umleitungsoperatoren verwendet werden:<br /><br /> < `file`<br /> Liest "stdin" aus der Datei.<br /><br /> > `file`<br /> Schreibt "stdout" in die Datei.<br /><br /> >> `file`<br /> Fügt "stdout" an die Datei an.<br /><br /> 2> `file`<br /> Schreibt "stderr" in die Datei.<br /><br /> 2>> `file`<br /> Fügt "stderr" an die Datei an.<br /><br /> 2> &1<br /> Sendet "stderr (2)"-Ausgaben an denselben Speicherort wie "stdout (1)".<br /><br /> 1> &2<br /> Sendet "stdout (1)"-Ausgaben an denselben Speicherort wie "stderr (2)".<br /><br /> In den meisten Fällen sind diese Operatoren nur auf Konsolenanwendungen anwendbar.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des zu debuggenden Programms bezogen auf das Projektverzeichnis an, in dem sich die EXE-Datei befindet. Wenn Sie kein Arbeitsverzeichnis festlegen, wird das Projektverzeichnis verwendet. Beim Remotedebuggen befindet sich das Projektverzeichnis auf dem Remoteserver.|  
|**Anfügen** (Lokaler Windows-Debugger und Remote-Windows-Debugger)|Gibt an, ob die Anwendung gestartet oder angefügt werden soll. Die Standardeinstellung ist "Nein".|  
|**Remoteservername** (Remote-Windows-Debugger)|Gibt den Namen eines anderen Remotecomputers an, auf dem Sie eine Anwendung debuggen möchten.<br /><br /> Das RemoteMachine-Build-Makro wird auf den Wert dieser Eigenschaft festgelegt. Weitere Informationen finden Sie unter [Makros für Buildbefehle und-Eigenschaften](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Verbindung** (Remote-Windows-Debugger)|Ermöglicht es Ihnen, für das Remotedebugging zwischen den Verbindungstypen "Standard" und "Ohne Authentifizierung" zu wechseln. Geben Sie im Feld **Remoteservername** den Namen des Remotecomputers an. Folgende Verbindungstypen stehen zur Verfügung:<br /><br /> -   **Remote mit Windows-Authentifizierung**<br />-   **Remote ohne Authentifizierung (nur System eigen)**<br /><br /> **Hinweis:** Der Remotecomputer ist durch das Remotedebuggen ohne Authentifizierung möglicherweise anfällig für Sicherheitsverletzungen. Der Windows-Authentifizierungsmodus ist sicherer.<br /><br /> Weitere Informationen finden Sie unter [Einrichten des Remote Debuggens](../debugger/remote-debugging.md).|  
|**HTTP-URL** (Webdienst- und Webbrowserdebugger)|Gibt die URL zu dem Projekt an, das Sie debuggen.|  
|**Debuggertyp**|Gibt den Typ des zu verwendenden Debuggers an: **Nur nativ**, **Nur verwaltet**, **Nur GPU**, **Gemischt**, **Automatisch** (Standardeinstellung) oder **Skript**.<br /><br /> -   Die Einstellung **Nur nativ** eignet sich für nicht verwalteten C++-Code.<br />-   Die Einstellung **Nur verwaltet** ist für Code konzipiert, der in der Common Language Runtime ausgeführt wird (verwalteter Code).<br />-   Mit **Gemischt** werden Debugger sowohl für verwalteten als auch für nicht verwalteten Code aufgerufen.<br />-   Die Einstellung **Automatisch** legt den Debuggertyp anhand von Compilerdaten und EXE-Daten fest.<br />-   **Skript** ruft einen Debugger für Skripts auf.<br />-   Die Einstellung **Nur GPU** ist für C++ AMP-Code vorgesehen, der auf einem GPU-Gerät oder im DirectX-Referenzraster ausgeführt wird. Siehe [Debugging von GPU-Code](../debugger/debugging-gpu-code.md).|  
|**Umgebung** (lokaler Windows-Debugger)|Gibt die Umgebungsvariablen für das Programm an, das Sie debuggen. Verwenden Sie die standardmäßige Umgebungsvariablensyntax (z. B. `PATH="%SystemRoot%\..."`). Je nach Einstellung der **Zusammenführungsumgebung** überschreiben diese Variablen die Systemumgebung oder werden mit der Systemumgebung zusammengeführt. Wenn Sie auf die Spalte "Einstellungen" klicken, wird "Bearbeiten..." angezeigt. Klicken Sie auf diesen Link, um die Umgebungsvariablen zu bearbeiten.|  
|**Zusammenführungsumgebung** (Lokaler Windows-Debugger)|Legt fest, ob die in dem Feld **Umgebung** angegebenen Variablen mit der vom verwendeten Betriebssystem definierten Umgebung zusammengeführt werden. Die Standardeinstellung ist "Ja".|  
|**SQL-Debugging** (alle außer MPI-Clusterdebugger)|Ermöglicht das Debuggen von SQL-Prozeduren über die [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Anwendung. Die Standardeinstellung ist "Nein".|  
|**Debuggingbeschleunigungstyp** (nur GPU-Debugging)|Gibt das für das Debugging zu verwendende GPU-Gerät an. Durch die Installation von Gerätetreibern für kompatible GPU-Geräte werden zusätzliche Optionen hinzugefügt. Die Standardeinstellung lautet "GPU – Softwareemulator".|  
|**GPU-Standardhaltepunktverhalten** (nur GPU-Debugging)|Gibt an, ob für jeden Thread in einer SIMD-Verzerrung ein Haltepunktereignis ausgelöst werden soll. Die Standardeinstellung gibt an, das Haltepunktereignis nur einmal pro Verzerrung auszulösen.|  
|**Amp-Standard Beschleuniger** (nur GPU-Debugging)|Gibt den Standard-AMPAccelerator beim Debuggen von GPU-Code an. Wählen Sie **WARP-Softwarebeschleunigung** aus, um zu untersuchen, ob ein Problem von der Hardware oder einem Treibers verursacht wird und nicht vom Code.|  
|**Bereitstellungsverzeichnis** (Remote-Windows-Debugger)|Gibt den Pfad auf dem Remotecomputer an, in den die Projektausgabe vor dem Start kopiert wird. Der Pfad kann eine Netzwerkfreigabe auf dem Remotecomputer sein oder ein Pfad zu einem Ordner auf dem Remotecomputer. Die Standardeinstellung ist leer, was bedeutet, dass die Projektausgabe nicht in eine Netzwerkfreigabe kopiert wird. Sie müssen im Dialogfeld „Konfigurations-Manager“ auch das Kontrollkästchen **Bereitstellen** aktivieren, um die Bereitstellung der Dateien zu ermöglichen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Zusätzliche bereitzustellende Dateien** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, handelt es sich hierbei um eine durch Semikolons getrennte Liste zusätzlicher Dateien, die in das Bereitstellungsverzeichnis kopieren werden sollen. Die Standardeinstellung ist leer, was bedeutet, dass keine zusätzlichen Dateien in den Bereitstellungsordner kopiert werden. Sie müssen im Dialogfeld „Konfigurations-Manager“ auch das Kontrollkästchen **Bereitstellen** aktivieren, um die Bereitstellung der Dateien zu ermöglichen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Visual C++-Debug-Laufzeitbibliotheken bereitstellen** (Remote-Windows-Debugger)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, wird hierdurch angegeben, ob die Visual C++ Debugging-Laufzeitbibliotheken für die aktuelle Plattform in die Netzwerkfreigabe kopiert werden sollen. Die Standardeinstellung ist "Ja".|  
  
### <a name="cc-folder-general-category"></a>Ordner "C/C++" (Kategorie "Allgemein")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Debuginformationsformat** ([/Z7, /Zd, Zi, /ZI](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Gibt den Typ der Debuginformationen an, die für das Projekt erstellt werden sollen.<br /><br /> Mit der Standardoption (/ZI) wird eine Programmdatenbank (.pdb) in einem Format erstellt, das mit "Bearbeiten und Fortfahren" kompatibel ist. Weitere Informationen finden Sie unter [/Z7,/ZD,/Zi,/Zi (Debuginformationsformat)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Ordner "C/C++" (Kategorie "Optimierung")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Optimization**|Gibt an, ob der Compiler den erstellten Code optimieren soll. Durch die Optimierung wird der auszuführende Code geändert. Optimierter Code entspricht nicht mehr dem Quellcode. Dadurch wird das Debuggen erschwert.<br /><br /> Die Standardoption (**deaktiviert (/0d**) unterdrückt die Optimierung. Sie können mit unterdrückter Optimierung entwickeln und sie anschließend bei der Erstellung der Code-Produktionsversion aktivieren.|  
  
### <a name="linker-folder-debugging-category"></a>Ordner "Linker" (Kategorie "Debuggen")  
  
|Einstellung|Beschreibung|  
|-------------|-----------------|  
|**Debuginfo generieren** ([/DEBUG](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Weist den Linker an, Debuginformationen in dem durch /Z7, /Zd, Zi oder /ZI festgelegten Format einzulesen.|  
|**Programmdatenbankdatei erstellen** ([/PDB:Name](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|In diesem Feld geben Sie den Namen einer PDB-Datei an. Sie müssen ZI oder /Zi als Debuginformationsformat auswählen.|  
|**Private Symbole entfernen** ([/PDBSTRIPPED:Dateiname](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Wenn die PDB-Datei keine privaten Symbole enthalten soll, geben Sie in diesem Feld den Namen einer PDB-Datei ein. Mit dieser Option wird eine zweite Programmdatenbank-Datei (PDB) generiert, wenn das Programmabbild mit einer der Compiler- oder Linkeroptionen erstellt wurde, mit denen eine PDB-Datei generiert wird, wie "/DEBUG", "/Z7" oder "/Zd". Oder "/Zi". Die zweite PDB-Datei enthält keine Symbole, die nicht an Kunden weitergegeben werden. Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Zuordnungsdatei generieren** ([/MAP](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Weist den Linker an, während der Verknüpfung eine Zuordnungsdatei zu generieren. Die Standardeinstellung ist "Nein". Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Zuordnungsdateiname** ([/MAP:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*Name*)|Bei Auswahl von "Zuordnungsdatei generieren" können Sie in diesem Feld die Zuordnungsdatei angeben. Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Zuordnungsexporte** ([/MAPINFO:EXPORTS](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Fügt exportierte Funktionen in die Zuordnungsdatei ein. Die Standardeinstellung ist "Nein". Weitere Informationen finden Sie unter [/MAPINFO (Daten in Zuordnungsdatei einfügen)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Debugfähige Assembly** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Gibt die Einstellungen für die /ASSEMBLYDEBUG-Option des Linkers an. Es sind folgende Werte möglich:<br /><br /> -   **Das Attribut „Debuggable“ wurde nicht ausgegeben**.<br />-   **Problemnachverfolgung zur Laufzeit und deaktivierte Optimierungen (/ASSEMBLYDEBUG)** . Dies ist die Standardeinstellung.<br />-   **Keine Problemnachverfolgung zur Laufzeit und aktivierte Optimierungen (/ASSEMBLYDEBUG)** .<br />-   **\<inherit from parent or project defaults>**.<br />Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (Add DebuggableAttribute) (/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen))](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Sie können diese Einstellungen im Ordner "Konfigurationseigenschaften" (Kategorie "Debuggen") programmgesteuert über die Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings-Schnittstelle ändern. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von nativem Code](../debugger/debugging-native-code.md)   
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Erstellen und Verwalten von Visual C++ Projekten](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG ("Debug"-Attribut hinzufügen)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Gängige Makros für Buildbefehle und -eigenschaften.](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)
