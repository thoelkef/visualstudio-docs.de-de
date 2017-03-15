---
title: "Projekteinstellungen f&#252;r eine C++-Debugkonfiguration | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".pdb-Dateien, Projekteinstellungen von Debugbuilds"
  - "/DEBUG (Linkeroption)"
  - "/MAP (Linkeroption)"
  - "/MAPINFO (Linkeroption)"
  - "/PDB (Linkeroption)"
  - "/PDBSTRIPPED (Linkeroption)"
  - "/Z7-Compileroption [C++]"
  - "/Zd (Compileroption) [C++]"
  - "/ZI-Compileroption [C++]"
  - "Debugbuilds, Projekteinstellungen"
  - "Debugkonfigurationen, C++"
  - "DEBUG (Linkeroption)"
  - "-DEBUG (Linkeroption)"
  - "Debuggen [C++], Debuggereinstellungen"
  - "MAP (Linkeroption)"
  - "-MAP (Linkeroption)"
  - "Zuordnungsdateien, Projekteinstellungen"
  - "MAPINFO (Linkeroption)"
  - "-MAPINFO (Linkeroption)"
  - "PDB-Dateien, Projekteinstellungen von Debugbuilds"
  - "PDB (Linkeroption)"
  - "-PDB (Linkeroption)"
  - "PDBSTRIPPED (Linkeroption)"
  - "-PDBSTRIPPED (Linkeroption)"
  - "Projektkonfigurationen, Debug"
  - "Projekteinstellungen [Visual Studio]"
  - "Projekteinstellungen [Visual Studio], Debugkonfigurationen"
  - "Projekte [Visual Studio], Debugkonfigurationen"
  - "Z7-Compileroption [C++]"
  - "-Z7-Compileroption [C++]"
  - "Zd (Compileroption) [C++]"
  - "-Zd (Compileroption) [C++]"
  - "ZI-Compileroption [C++]"
  - "-Zl (Compileroption) [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Projekteinstellungen f&#252;r eine C++-Debugkonfiguration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Projekteinstellungen für eine C\- oder Visual C\+\+\-Debugkonfiguration im Dialogfeld **Eigenschaftenseiten** entsprechend der Anweisung unter [Gewusst wie: Festlegen von Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md) ändern.  Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Dialogfeld **Eigenschaftenseiten** zu finden sind.  
  
> [!WARNING]
>  Die Debugprojekteinstellungen in der Kategorie **Konfigurationseigenschaften\/Debugging** für die in C\+\+ geschriebenen Windows Store\-Apps und Komponenten sind unterschiedlich.  Weitere Informationen hierzu erhalten Sie im Windows Developer Center unter [Starten einer Debugsitzung \(VB, C\#, C\+\+ und XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Geben Sie im Listenfeld **Zu startender Debugger** an, welcher Debugger verwendet werden soll.  Die Auswahl beeinflusst, welche Eigenschaften angezeigt werden.  
  
 Jede Debugeigenschafteneinstellung wird automatisch in die "Pro Benutzer"\-Datei \(.vcxproj.user\) der Projektmappe geschrieben und dort gespeichert, sobald Sie die Projektmappe speichern.  
  
### Ordner "Konfigurationseigenschaften" \(Kategorie "Debuggen"\)  
  
|**Einstellung**|**Beschreibung**|  
|---------------------|----------------------|  
|**Zu startender Debugger**|Gibt den auszuführenden Debugger mit den folgenden Auswahlmöglichkeiten an:<br /><br /> -   **Lokaler Windows\-Debugger**<br />-   **Remote\-Windows\-Debugger**<br />-   **Webbrowserdebugger**<br />-   **Webdienst\-Debugger**|  
|**Befehl** \(Lokaler Windows\-Debugger\)|Gibt den Startbefehl für das auf dem lokalen Computer zu debuggende Programm an.|  
|**Remotebefehl** \(Remote\-Windows\-Debugger\)|Der Pfad für die EXE\-Datei auf dem Remotecomputer.  Geben Sie den Pfad wie auf dem Remotecomputer ein.|  
|**Befehlsargumente** \(Lokaler Windows\-Debugger und Remote\-Windows\-Debugger\)|-   Gibt Argumente für den oben aufgeführten Befehl an.<br /><br /> In diesem Feld können die folgenden Umleitungsoperatoren verwendet werden:<br /><br /> \< `file`<br /> Liest "stdin" aus der Datei.<br /><br /> \> `file`<br /> Schreibt "stdout" in die Datei.<br /><br /> \>\> `file`<br /> Fügt "stdout" an die Datei an.<br /><br /> 2\> `file`<br /> Schreibt "stderr" in die Datei.<br /><br /> 2\>\> `file`<br /> Fügt "stderr" an die Datei an.<br /><br /> 2\> &1<br /> Sendet "stderr \(2\)"\-Ausgaben an denselben Speicherort wie "stdout \(1\)".<br /><br /> 1\> &2<br /> Sendet "stdout \(1\)"\-Ausgaben an denselben Speicherort wie "stderr \(2\)".<br /><br /> In den meisten Fällen sind diese Operatoren nur auf Konsolenanwendungen anwendbar.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des zu debuggenden Programms bezogen auf das Projektverzeichnis an, in dem sich die EXE\-Datei befindet.  Wenn Sie kein Arbeitsverzeichnis festlegen, wird das Projektverzeichnis verwendet.  Beim Remotedebuggen befindet sich das Projektverzeichnis auf dem Remoteserver.|  
|**Anfügen** \(Lokaler Windows\-Debugger und Remote\-Windows\-Debugger\)|Gibt an, ob die Anwendung gestartet oder angefügt werden soll.  Die Standardeinstellung ist "Nein".|  
|**Remoteservername** \(Remote\-Windows\-Debugger\)|Gibt den Namen eines anderen Remotecomputers an, auf dem Sie eine Anwendung debuggen möchten.<br /><br /> Das RemoteMachine\-Buildmakro wird auf den Wert dieser Eigenschaft festgelegt. Weitere Informationen hierzu finden Sie unter [Makros für Buildbefehle und \-eigenschaften](/visual-cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Verbindung** \(Remote\-Windows\-Debugger\)|Ermöglicht es Ihnen, für das Remotedebugging zwischen den Verbindungstypen "Standard" und "Ohne Authentifizierung" zu wechseln.  Geben Sie im Feld **Remoteservername** den Namen eines Remotecomputers an.  Folgende Verbindungstypen stehen zur Verfügung:<br /><br /> -   **Remote mit Windows\-Authentifizierung**<br />-   **Remote ohne Authentifizierung \(nur systemeigen\)**<br /><br /> **Hinweis** Der Remotecomputer ist durch das Remotedebuggen ohne Authentifizierung u. U. anfällig für Sicherheitsverletzungen.  Der Windows\-Authentifizierungsmodus ist sicherer.<br /><br /> Weitere Informationen finden Sie unter [Remote Debugging – Setup](../debugger/remote-debugging.md).|  
|**HTTP\-URL** \(Webdienst\- und Webbrowserdebugger\)|Gibt die URL zu dem Projekt an, das Sie debuggen.|  
|**Debuggertyp**|Gibt den Typ des zu verwendenden Debuggers an: **Nur systemeigen**, **Nur verwaltet**, **Nur GPU**, **Gemischt**, **Automatisch** \(Standard\) oder **Skript**.<br /><br /> -   Die Einstellung **Nur systemeigen** eignet sich für nicht verwalteten C\+\+\-Code.<br />-   Die Einstellung **Nur verwaltet** ist für Code konzipiert, der in der Common Language Runtime ausgeführt wird \(verwalteter Code\).<br />-   Mit **Gemischt** werden Debugger sowohl für verwalteten als auch für nicht verwalteten Code aufgerufen.<br />-   Die Einstellung **Automatisch** legt den Debuggertyp anhand von Compilerdaten und EXE\-Daten fest.<br />-   **Skript** ruft einen Debugger für Skripts auf.<br />-   Die Einstellung **Nur GPU** ist für C\+\+ AMP\-Code vorgesehen, der auf einem GPU\-Gerät oder im DirectX\-Referenzrasterprogramm ausgeführt wird.  Siehe [Debuggen von GPU\-Code](../debugger/debugging-gpu-code.md).|  
|**Umgebung** \(Lokaler Windows\-Debugger\)|Gibt die Umgebungsvariablen für das Programm an, das Sie debuggen.  Verwenden Sie die standardmäßige Umgebungsvariablensyntax \(z. B. `PATH="%SystemRoot%\..."`\).  Diese Variablen überschreiben die Systemumgebungsvariablen oder werden mit den Systemumgebungsvariablen zusammengeführt, je nach Einstellung der **Zusammenführungsumgebung**.  Wenn Sie auf die Spalte "Einstellungen" klicken, wird "Bearbeiten..." angezeigt.  Klicken Sie auf diesen Link, um die Umgebungsvariablen zu bearbeiten.|  
|**Zusammenführungsumgebung** \(Lokaler Windows\-Debugger\)|Legt fest, ob die in dem Feld **Umgebung** angegebenen Variablen mit der vom verwendeten Betriebssystem definierten Umgebung zusammengeführt werden.  Die Standardeinstellung ist "Ja".|  
|**SQL\-Debugging** \(alle außer MPI\-Clusterdebugger\)|Ermöglicht das Debuggen von SQL\-Prozeduren über die [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Anwendung.  Die Standardeinstellung ist "Nein".|  
|**Debuggingbeschleunigungstyp** \(nur GPU\-Debugging\)|Gibt das für das Debugging zu verwendende GPU\-Gerät an.  Durch die Installation von Gerätetreibern für kompatible GPU\-Geräte werden zusätzliche Optionen hinzugefügt.  Die Standardeinstellung lautet "GPU – Softwareemulator".|  
|**GPU\-Standardhaltepunktverhalten** \(nur GPU\-Debugging\)|Gibt an, ob für jeden Thread in einer SIMD\-Verzerrung ein Haltepunktereignis ausgelöst werden soll.  Die Standardeinstellung gibt an, das Haltepunktereignis nur einmal pro Verzerrung auszulösen.|  
|**Amp\-Standard\-Accelerator** \(nur GPU\-Debuggen\)|Gibt den Standard\-AMPAccelerator beim Debuggen von GPU\-Code an.  Wählen Sie **WARP\-Softwarebeschleunigung** aus, um zu untersuchen, ob ein Problem von der Hardware oder einem Treibers verursacht wird und nicht vom Code.|  
|**Bereitstellungsverzeichnis** \(Remote\-Windows\-Debugger\)|Gibt den Pfad auf dem Remotecomputer an, in den die Projektausgabe vor dem Start kopiert wird.  Der Pfad kann eine Netzwerkfreigabe auf dem Remotecomputer sein oder ein Pfad zu einem Ordner auf dem Remotecomputer.  Die Standardeinstellung ist leer, was bedeutet, dass die Projektausgabe nicht in eine Netzwerkfreigabe kopiert wird.  Um die Bereitstellung der Dateien zu ermöglichen, müssen Sie im Dialogfeld "Konfigurations\-Manager" auch das Kontrollkästchen **Bereitstellen** aktivieren.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Zusätzliche bereitzustellende Dateien** \(Remote\-Windows\-Debugger\)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, handelt es sich hierbei um eine durch Semikolons getrennte Liste zusätzlicher Dateien, die in das Bereitstellungsverzeichnis kopieren werden sollen.  Die Standardeinstellung ist leer, was bedeutet, dass keine zusätzlichen Dateien in den Bereitstellungsordner kopiert werden.  Um die Bereitstellung der Dateien zu ermöglichen, müssen Sie im Dialogfeld "Konfigurations\-Manager" auch das Kontrollkästchen **Bereitstellen** aktivieren.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).|  
|**Visual C\+\+ Debugging\-Laufzeitbibliotheken bereitstellen** \(Remote\-Windows\-Debugger\)|Wenn die Eigenschaft "Bereitstellungsverzeichnis" festgelegt wird, wird hierdurch angegeben, ob die Visual C\+\+ Debugging\-Laufzeitbibliotheken für die aktuelle Plattform in die Netzwerkfreigabe kopiert werden sollen.  Die Standardeinstellung ist "Ja".|  
  
### Ordner "C\/C\+\+" \(Kategorie "Allgemein"\)  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Debuginformationsformat** \([\/Z7, \/Zd, Zi, \/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|Gibt den Typ der Debuginformationen an, die für das Projekt erstellt werden sollen.<br /><br /> Mit der Standardoption \(\/ZI\) wird eine Programmdatenbank \(.pdb\) in einem Format erstellt, das mit "Bearbeiten und Fortfahren" kompatibel ist.  Weitere Informationen hierzu finden Sie unter [\/Z7, \/Zd, \/Zi, \/ZI \(Debuginformationsformat\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
### Ordner "C\/C\+\+" \(Kategorie "Optimierung"\)  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Optimierung**|Gibt an, ob der Compiler den erstellten Code optimieren soll.  Durch die Optimierung wird der auszuführende Code geändert.  Optimierter Code entspricht nicht mehr dem Quellcode.  Dadurch wird das Debuggen erschwert.<br /><br /> Die Standardoption \(**Deaktiviert \(\/0d\)**\) dient zum Unterdrücken der Optimierung.  Sie können mit unterdrückter Optimierung entwickeln und sie anschließend bei der Erstellung der Code\-Produktionsversion aktivieren.|  
  
### Ordner "Linker" \(Kategorie "Debuggen"\)  
  
|Einstellung|Beschreibung|  
|-----------------|------------------|  
|**Debuginfo generieren** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|Weist den Linker an, Debuginformationen in dem durch \/Z7, \/Zd, Zi oder \/ZI festgelegten Format einzulesen.|  
|**Programmdatenbankdatei erstellen** \([\/PDB:Name](/visual-cpp/build/reference/pdb-use-program-database)\)|In diesem Feld geben Sie den Namen einer PDB\-Datei an.  Sie müssen ZI oder \/Zi als Debuginformationsformat auswählen.|  
|**Private Symbole entfernen** \([\/PDBSTRIPPED:Dateiname](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|Wenn die PDB\-Datei keine privaten Symbole enthalten soll, geben Sie in diesem Feld den Namen einer PDB\-Datei ein.  Mit dieser Option wird eine zweite Programmdatenbank\-Datei \(PDB\) generiert, wenn das Programmabbild mit einer der Compiler\- oder Linkeroptionen erstellt wurde, mit denen eine PDB\-Datei generiert wird, wie "\/DEBUG", "\/Z7" oder "\/Zd".  Oder "\/Zi".  Die zweite PDB\-Datei enthält keine Symbole, die nicht an Kunden weitergegeben werden.  Weitere Informationen finden Sie unter [\/PDBSTRIPPED \(Private Symbole entfernen\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Zuordnungsdatei generieren** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|Weist den Linker an, während der Verknüpfung eine Zuordnungsdatei zu generieren.  Die Standardeinstellung ist "Nein".  Weitere Informationen finden Sie unter [\/MAP \(Zuordnungsdatei generieren\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Zuordnungsdateiname** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*Name*\)|Bei Auswahl von "Zuordnungsdatei generieren" können Sie in diesem Feld die Zuordnungsdatei angeben.  Weitere Informationen finden Sie unter [\/MAP \(Zuordnungsdatei generieren\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Zuordnungsexporte** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Fügt exportierte Funktionen in die Zuordnungsdatei ein.  Die Standardeinstellung ist "Nein".  Weitere Informationen finden Sie unter [\/MAPINFO \(Daten in Zuordnungsdatei einfügen\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Debugfähige Assembly** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Gibt die Einstellungen für die \/ASSEMBLYDEBUG\-Option des Linkers an.  Folgende Werte sind möglich:<br /><br /> -   **Das Attribut "Debuggable" wurde nicht ausgegeben**.<br />-   **Problemnachverfolgung zur Laufzeit und deaktivierte Optimierungen \(\/ASSEMBLYDEBUG\)**.  Dies ist die Standardeinstellung.<br />-   **Keine Problemnachverfolgung zur Laufzeit und aktivierte Optimierungen \(\/ASSEMBLYDEBUG\)**.<br />-   **\<Vom übergeordneten Projekt erben oder Projektstandard\>**.<br />-   Weitere Informationen finden Sie unter [\/ASSEMBLYDEBUG \(DebuggableAttribute hinzufügen\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Sie können diese Einstellungen im Ordner "Konfigurationseigenschaften" \(Kategorie "Debuggen"\) programmgesteuert über die Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings\-Schnittstelle ändern.  Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## Siehe auch  
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Erstellen und Verwalten von Visual C\+\+\-Projekten](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(DebuggableAttribute hinzufügen\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Makros für Buildbefehle und \-eigenschaften](/visual-cpp/ide/common-macros-for-build-commands-and-properties)