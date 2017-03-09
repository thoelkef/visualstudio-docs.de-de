---
title: "Link-Aufgabe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ForceFileOutput"
  - "VC.Project.VCLinkerTool.LinkStatus"
  - "VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck"
  - "VC.Project.VCLinkerTool.SpecifySectionAttributes"
  - "VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL"
  - "VC.Project.VCLinkerTool.MinimumRequiredVersion"
  - "VC.Project.VCLinkerTool.PerUserRedirection"
  - "VC.Project.VCLinkerTool.CreateHotPatchableImage"
  - "VC.Project.VCLinkerTool.DataExecutionPrevention"
  - "VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors"
  - "vc.task.link"
  - "VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers"
  - "VC.Project.VCLinkerTool.CLRSupportLastError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (Visual C++), Link-Aufgabe"
  - "Link-Aufgabe (MSBuild (Visual C++))"
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Link-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das Visual C++-Linkertool link.exe. Das Linkertool verbindet Common Object File Format (COFF)-Objektdateien und Bibliotheken zum Erstellen einer ausführbaren Datei (.exe) oder eine Dynamic Link Library (DLL). Weitere Informationen finden Sie unter [Linkeroptionen](/visual-cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parameter  
 Die folgende Tabelle beschreibt die Parameter der **Link** Aufgabe. Die meisten Aufgabenparameter und einige Sätze von Parametern entsprechen einer Befehlszeilenoption.  
  
-   **AdditionalDependencies**  
  
     Optionale **String []** Parameter.  
  
     Gibt eine Liste von Eingabedateien, die dem Befehl hinzufügen.  
  
     Weitere Informationen finden Sie unter [LINK-Eingabedateien](/visual-cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     Optionale **String []** Parameter.  
  
     Überschreibt den Bibliothekspfad der Umgebung. Geben Sie einen Verzeichnisnamen an.  
  
     Weitere Informationen finden Sie unter [/LIBPATH (Libpath-Pfad)](/visual-cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     Optionale **String []** Parameter.  
  
     Gibt Attribute, die in eingefügt werden, die `dependency` Abschnitt der Manifestdatei.  
  
     Weitere Informationen finden Sie unter [/MANIFESTDEPENDENCY (Specify Manifest Dependencies)](/visual-cpp/build/reference/manifestdependency-specify-manifest-dependencies). Siehe auch "Publisher Configuration Files" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **AdditionalOptions**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Eine Liste der Optionen des Linkers wie angegeben in der Befehlszeile. Z. B. **"***option1/option2 /option#*". Mit diesem Parameter können Sie die Optionen des Linkers angeben, die nicht von einem beliebigen anderen dargestellt werden **Link** Task-Parameter.  
  
     Weitere Informationen finden Sie unter [Linkeroptionen](/visual-cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     Optionale **String []** Parameter.  
  
     Fügt einen Modulverweis in eine Assembly.  
  
     Weitere Informationen finden Sie unter [ASSEMBLYMODULE (Add MSIL-Modul zur Assembly)](/visual-cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **AllowIsolation**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, bewirkt, dass das Betriebssystem nach Manifesten und lädt. Wenn `false`, gibt an, dass DLLs geladen werden, als ob es kein Manifest gäbe.  
  
     Weitere Informationen finden Sie unter [/ALLOWISOLATION (Manifest Lookup)](/visual-cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt die **DebuggableAttribute** Attribut zusammen mit Debug Informationen nachverfolgen und deaktiviert die JIT-Optimierungen. Wenn `false`, gibt die **DebuggableAttribute** Attribut aber deaktiviert die Überwachung von Debuginformationen und aktiviert JIT-Optimierungen.  
  
     Weitere Informationen finden Sie unter [ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **AssemblyLinkResource**  
  
     Optionale **String []** Parameter.  
  
     Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei an. die Ressourcendatei wird nicht in der Ausgabedatei platziert. Geben Sie den Namen der Ressource.  
  
     Weitere Informationen finden Sie unter [/ASSEMBLYLINKRESOURCE (mit .NET Framework-Ressource verknüpfen)](/visual-cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Implizite **booleschen** Parameter.  
  
     Ermöglicht tiefere Datei nachverfolgen, um die inkrementelle Verknüpfung Verhalten zu erfassen. Gibt immer `true` zurück.  
  
-   **BaseAddress-Element**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Legt eine Basisadresse für das Programm oder die DLL erstellt wird. Geben Sie `{address[,size] | @filename,key}` an.  
  
     Weitere Informationen finden Sie unter [/Base (Basisadresse)](/visual-cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     Optionale **booleschen** Parameter.  
  
     True gibt an, dass MSBuild von der IDE aufgerufen wird. Andernfalls gibt an, dass MSBuild von der Befehlszeile aus aufgerufen wird.  
  
     Dieser Parameter hat keine entsprechende Linkeroption.  
  
-   **CLRImageType**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Legt den Typ eines Image der common Language Runtime (CLR) fest.  
  
     Geben Sie einen der folgenden Werte an, von die jeder einer Linkeroption entspricht.  
  
    -   **Standard-** - *\< none>*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE: PURE**  
  
    -   **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
     Weitere Informationen finden Sie unter [/CLRIMAGETYPE (angeben Type of CLR Image)](/visual-cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **CLRSupportLastError**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Behält den letzten Fehlercode von Funktionen, die durch den P/Invoke-Mechanismus aufgerufen.  
  
     Geben Sie einen der folgenden Werte an, von die jeder einer Linkeroption entspricht.  
  
    -   **Aktiviert** - **/CLRSupportLastError**  
  
    -   **Deaktivierte** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
     Weitere Informationen finden Sie unter [/CLRSUPPORTLASTERROR (beibehalten letzten Fehlercode für PInvoke-Aufrufe)](/visual-cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **CLRThreadAttribute**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Das Threadingattribut für den Einstiegspunkt des CLR-Programms angibt explizit.  
  
     Geben Sie einen der folgenden Werte an, von die jeder einer Linkeroption entspricht.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: KEINE**  
  
    -   **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
     Weitere Informationen finden Sie unter [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](/visual-cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Optionale **booleschen** Parameter.  
  
     Gibt an, ob der Linker **SuppressUnmanagedCodeSecurityAttribute** auf vom Linker generierte P/Invoke-Aufrufe von verwaltetem Code in systemeigene DLLs.  
  
     Weitere Informationen finden Sie unter [/CLRUNMANAGEDCODECHECK (Hinzufügen von SuppressUnmanagedCodeSecurity-Attribut)](/visual-cpp/build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute).  
  
-   **CreateHotPatchableImage**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Bereitet ein Image für Hotpatching vor.  
  
     Geben Sie einen der folgenden Werte, die eine Linkeroption entspricht.  
  
    -   **Aktiviert** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
     Weitere Informationen finden Sie unter [/FUNCTIONPADMIN (Erstellen eines Hotpatch-fähigen Abbildes)](/visual-cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt an, dass eine ausführbare Datei mit der Windows-Feature Datenausführungsverhinderung kompatibel ist.  
  
     Weitere Informationen finden Sie unter [/NXCOMPAT (kompatibel mit Datenausführungsverhinderung)](/visual-cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     Optionale **String []** Parameter.  
  
     Mit diesem Parameter wird *Verzögertes Laden* DLLs. Geben Sie den Namen einer DLL für verzögertes Laden.  
  
     Weitere Informationen finden Sie unter [/DELAYLOAD (Laden von Import verzögern)](/visual-cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, eine Assembly teilweise signiert. Standardmäßig ist der Wert `false`.  
  
     Weitere Informationen finden Sie unter [/delaysign (teilweise Signieren eine Assembly)](/visual-cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Treiber**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Geben Sie diesen Parameter, um einen Windows NT-Kernelmodustreiber zu erstellen.  
  
     Geben Sie einen der folgenden Werte an, von die jeder einer Linkeroption entspricht.  
  
    -   **NotSet** - *\< none>*  
  
    -   **Treiber** - **Image**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** - **/DRIVER: WDM**  
  
     Weitere Informationen finden Sie unter [/Driver (Treiber für Windows NT-Kernel-Modus)](/visual-cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     Optionale **String []** Parameter.  
  
     Bettet eine Ressourcendatei in eine Assembly. Geben Sie den Dateinamen für die angeforderte Ressource. Geben Sie optional den logischen Namen, die zum Laden der Ressource verwendet wird, und die **PRIVATE** Option, die im Assemblymanifest gibt an, dass die Ressourcendatei privat ist.  
  
     Weitere Informationen finden Sie unter [/ASSEMBLYRESOURCE (Embed a Managed Resource)](/visual-cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, können Sie identische COMDAT-Faltung.  
  
     Weitere Informationen finden Sie unter der `ICF[= iterations]` Argument der [/OPT (Optimierungen)](/visual-cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt an, dass Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.  
  
     Weitere Informationen finden Sie unter [/MANIFESTUAC (bettet UAC-Informationen in Manifest)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt eine Einstiegspunktfunktion als Startadresse für eine .exe-Datei oder DLL an. Geben Sie einen Funktionsnamen als Parameterwert an.  
  
     Weitere Informationen finden Sie unter [/Entry (Symbol für Einstiegspunkt)](/visual-cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, ein Programm oder eine DLL, die geladen werden kann nur an seine bevorzugte Basisadresse erstellt.  
  
     Weitere Informationen finden Sie unter [/fixed (Feste Basisadresse)](/visual-cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Weist den Linker an, erstellen Sie eine gültige .exe-Datei oder DLL selbst ein Symbol, aber nicht verwiesen wird definiert, oder mehrfach definiert ist.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Aktiviert** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/Force: Multiple**  
  
    -   **UndefinedSymbolOnly** - **/FORCE: nicht AUFGELÖSTE**  
  
     Weitere Informationen finden Sie unter [/Force (DateiAusgabe erzwingen)](/visual-cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     Optionale **String []** Parameter.  
  
     Dieser Parameter weist den Linker an das angegebene Symbol der Symboltabelle hinzuzufügen.  
  
     Weitere Informationen finden Sie unter [/Include (Symbolverweise erzwingen)](/visual-cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Dieser Parameter optimiert das Programm durch die Platzierung der angegebenen Paketfunktionen (COMDATs) in das Bild in einer vorherbestimmten Reihenfolge.  
  
     Weitere Informationen finden Sie unter [/Order (Put Functions in Order)](/visual-cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, werden Debuginformationen für die .exe-Datei oder DLL erstellt.  
  
     Weitere Informationen finden Sie unter [/Debug (Debuginfo generieren)](/visual-cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird eine Seite-an-Seite-Manifestdatei erstellt.  
  
     Weitere Informationen finden Sie unter [/Manifest (Create Side-by-Side Assemblymanifest)](/visual-cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, erstellt eine *Zuordnungsdatei*. Die Erweiterung der Zuordnungsdatei ist .map.  
  
     Weitere Informationen finden Sie unter [/Map (Zuordnungsdatei generieren)](/visual-cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Menge des physischen Speichers auf dem Heap zu einem Zeitpunkt belegt werden soll.  
  
     Weitere Informationen finden Sie unter der `commit` -Argument in [/HEAP (Heapgröße festlegen)](/visual-cpp/build/reference/heap-set-heap-size). Siehe auch die **HeapReserveSize** Parameter.  
  
-   **HeapReserveSize**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die gesamte Heapreservierung im virtuellen Speicher an.  
  
     Weitere Informationen finden Sie unter der `reserve` -Argument in [/HEAP (Heapgröße festlegen)](/visual-cpp/build/reference/heap-set-heap-size). Siehe auch die **HeapCommitSize** -Parameter in dieser Tabelle.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist den Linker an, entfernen Sie eine oder mehrere Standardbibliotheken aus der Liste der Bibliotheken durchsucht beim Auflösen externer Verweise.  
  
     Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/visual-cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt an, dass die IDL-Attribute im Quellcode nicht in eine IDL-Datei verarbeitet werden sollen.  
  
     Weitere Informationen finden Sie unter [/IGNOREIDL (Don't Process Attributes into MIDL)](/visual-cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt an, dass die von dieser Konfiguration generierte Importbibliothek nicht in abhängige Projekte importiert werden soll.  
  
     Dieser Parameter entspricht keiner Linkeroption.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Optionale **String []** Parameter.  
  
     Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken mit Semikolons.  
  
     Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/visual-cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, der Linker erstellt ein Abbild nur, wenn auch eine Tabelle sicherer Ausnahmehandler für das Abbild erstellt werden kann.  
  
     Weitere Informationen finden Sie unter [/SAFESEH (Abbild verfügt über sichere Ausnahmehandler)](/visual-cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Ein Name der benutzerdefinierten importieren, die die Standard-Bibliotheksnamen ersetzt.  
  
     Weitere Informationen finden Sie unter [/IMPLIB (Name der Importbibliothek)](/visual-cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Container, der den Schlüssel für eine signierte Assembly enthält.  
  
     Weitere Informationen finden Sie unter [/keycontainer (Geben Sie einen Schlüsselcontainer zum Signieren einer Assembly)](/visual-cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Siehe auch die **KeyFile** -Parameter in dieser Tabelle.  
  
-   **KeyFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt eine Datei, die den Schlüssel für eine signierte Assembly enthält.  
  
     Weitere Informationen finden Sie unter [/keyfile (Geben Sie Schlüssel oder Schlüsselpaar zum Signieren einer Assembly)](/visual-cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Siehe auch die **KeyContainer** Parameter.  
  
-   **LargeAddressAware**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, Adressen, die größer als 2 GB von der Anwendung verarbeitet werden kann.  
  
     Weitere Informationen finden Sie unter [/LARGEADDRESSAWARE (umfangreiche Adressen verarbeiten)](/visual-cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, erstellt eine DLL als Hauptausgabe-Datei.  
  
     Weitere Informationen finden Sie unter [/DLL (DLL erstellen)](/visual-cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Sie können Informationen interner Compilerfehler (ICE) direkt an Microsoft zu senden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NoErrorReport** - **/errorreport: NONE**  
  
    -   **PromptImmediately** - **Absturzinformationen**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **/errorreport: Send**  
  
     Weitere Informationen finden Sie unter [/errorreport (internen Linkerfehlern)](/visual-cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird inkrementelles Verknüpfen aktiviert.  
  
     Weitere Informationen finden Sie unter [/INCREMENTAL (inkrementell verknüpfen)](/visual-cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     Optionale **booleschen** Parameter.  
  
     `true` gibt an, dass die Bibliotheksausgaben von Projektabhängigkeiten automatisch eingebunden werden.  
  
     Dieser Parameter entspricht keiner Linkeroption.  
  
-   **LinkStatus**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, gibt an, dass der Linker eine Statusanzeige angezeigt, die anzeigt, welcher Anteil des abgeschlossen ist.  
  
     Weitere Informationen finden Sie unter der `STATUS` Argument der [/LTCG (Link-Time Code Generation)](/visual-cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt Optionen für Profilgesteuerte Optimierung.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard-** - *\< none>*  
  
    -   **UseLinkTimeCodeGeneration** - **"/ LTCG"**  
  
    -   **PGInstrument** - **/LTCG: PGINSTRUMENT**  
  
    -   **PGOptimization** - **/LTCG: PGOPTIMIZE**  
  
    -   **PGUpdate**  
  
         \- **PGUPDATE**  
  
     Weitere Informationen finden Sie unter [/LTCG (Link-Time Code Generation)](/visual-cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **ManifestFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Ändert den Standardnamen der Manifestdatei an den angegebenen Dateinamen.  
  
     Weitere Informationen finden Sie unter [ManifestFile (Name Manifest File)](/visual-cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist den Linker an, exportierte Funktionen in eine Zuordnungsdatei einzufügen.  
  
     Weitere Informationen finden Sie unter der `EXPORTS` Argument der [/MapInfo (Include Information in Mapfile)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Ändert den Standardnamen für die Zuordnung zu dem angegebenen Dateinamen.  
  
-   **MergedIDLBaseFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Dateinamen und die Erweiterung der IDL-Datei.  
  
     Weitere Informationen finden Sie unter [/IDLOUT (Namen MIDL-Ausgabedateien)](/visual-cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Kombiniert Abschnitte in einem Bild. Geben Sie `from-section=to-section` an.  
  
     Weitere Informationen finden Sie unter [/Merge (Abschnitte kombinieren)](/visual-cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Geben Sie den Namen einer Datei, die MIDL-Befehlszeilenoptionen enthält.  
  
     Weitere Informationen finden Sie unter [/MIDL (Optionen für MIDL-Befehlszeile festlegen)](/visual-cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich von 0 bis 65535.  
  
-   **ModuleDefinitionFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen einer [Moduldefinitionsdatei](/visual-cpp/build/reference/module-definition-dot-def-files).  
  
     Weitere Informationen finden Sie unter [/DEF (Moduldefinitionsdatei festlegen)](/visual-cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Fügt das angegebene MS-DOS-Stub-Programm an ein Win32-Programm an.  
  
     Weitere Informationen finden Sie unter [/Stub (Name der MS-DOS-Stubdatei)](/visual-cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird eine reine Ressourcen-DLL.  
  
     Weitere Informationen finden Sie unter [/NOENTRY (kein Einstiegspunkt)](/visual-cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Implizite **String []** Parameter.  
  
     Gibt die Objektdateien, die verknüpft sind.  
  
-   **OptimizeReferences**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, löscht Funktionen und/oder Daten, die nie verwiesen werden.  
  
     Weitere Informationen finden Sie unter der `REF` -Argument in [/OPT (Optimierungen)](/visual-cpp/build/reference/opt-optimizations).  
  
-   **Ausgabedatei**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt.  
  
     Weitere Informationen finden Sie unter [/OUT (Ausgabedateiname)](/visual-cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true` und Ausgabe registrieren aktiviert ist, erzwingt Registrierung schreibt in **HKEY_CLASSES_ROOT** umgeleitet werden **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Optionaler `ITaskItem[]`-Parameter.  
  
     Definiert ein Array, der Präprozessorausgabe-Elemente, die genutzt und Aufgaben ausgegeben werden können.  
  
-   **PreventDllBinding**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, Bind.exe gibt an, dass das verknüpfte Image nicht gebunden werden soll.  
  
     Weitere Informationen finden Sie unter [/ALLOWBIND (Prevent DLL Binding)](/visual-cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profil**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, erzeugt eine Ausgabedatei, die mit verwendet werden, kann die **Leistungstools** Profiler.  
  
     Weitere Informationen finden Sie unter [/Profile (Leistungstools-Profiler)](/visual-cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der PGD-Datei, die zum Speichern von Informationen zum ausgeführten Programm verwendet werden  
  
     Weitere Informationen finden Sie unter [/PGD (Angeben der Datenbank für die profilgesteuerte Optimierung)](/visual-cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt einen Namen für die Programmdatenbank (PDB), die der Linker erstellt.  
  
     Weitere Informationen finden Sie unter [/PDB (Programmdatenbank verwenden)](/visual-cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, generiert ein ausführbares Abbild, die nach dem Zufallsprinzip zur Ladezeit mit zurückgesetzt werden kann die *Adresse Space Layout Randomization* (ASLR)-Funktion von Windows.  
  
     Weitere Informationen finden Sie unter [/DynamicBase (Address Space Layout Randomization verwenden)](/visual-cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, die primäre Ausgabe dieses Builds registriert.  
  
-   **SectionAlignment**  
  
     Optionale **Ganzzahl** Parameter.  
  
     Gibt die Ausrichtung der einzelnen Abschnitte innerhalb des linearen Adressraums des Programms. Der Parameterwert ist eine Einheit Anzahl von Bytes und eine Potenz von zwei ist.  
  
     Weitere Informationen finden Sie unter [/align (Abschnittsausrichtung)](/visual-cpp/build/reference/align-section-alignment).  
  
-   **SetChecksum**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird die Prüfsumme im Header einer .exe-Datei.  
  
     Weitere Informationen finden Sie unter [/Release (Prüfsumme festlegen)](/visual-cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Ausführlichkeitsgrad von Statusberichten für die Verknüpfungsoperation an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\< none>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/verbose: lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
     Weitere Informationen finden Sie unter [/Verbose (Print Progress Messages)](/visual-cpp/build/reference/verbose-print-progress-messages).  
  
-   **Datenquellen**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **SpecifySectionAttributes**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Attribute eines Abschnitts. Dies überschreibt die Attribute, die beim Kompilieren der OBJ-Datei für den Abschnitt festgelegt wurden.  
  
     Weitere Informationen finden Sie unter [/Section (Abschnittsattribute festlegen)](/visual-cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Menge an physikalischem Speicher in jeder Zuordnung an, wenn zusätzlicher Speicher belegt wird.  
  
     Weitere Informationen finden Sie unter der `commit` Argument der [/Stack (Stapelreservierungen)](/visual-cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Gesamtanzahl der stapelreservierung im virtuellen Speicher.  
  
     Weitere Informationen finden Sie unter der `reserve` Argument der [/Stack (Stapelreservierungen)](/visual-cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Erstellt eine zweite Programmdatenbank (PDB)-Datei, die keine Symbole enthält, die Sie nicht an Ihre Kunden verteilen möchten. Geben Sie den Namen der zweiten PDB-Datei.  
  
     Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **SubSystem**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Umgebung für die ausführbare Datei an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\< none>*  
  
    -   **Konsole** - **/Subsystem: Console**  
  
    -   **Windows** - **/Subsystem: Windows**  
  
    -   **Systemeigene** - **/Subsystem: native**  
  
    -   **EFI-Anwendung** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **EFI-Start-Service-Treiber** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI-ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI-Laufzeit** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
     Weitere Informationen finden Sie unter [/Subsystem (Subsystem angeben)](/visual-cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist den Linker nicht bindbar Importadresstabelle (IAT) in das endgültige Image einzuschließen.  
  
     Weitere Informationen finden Sie unter der `NOBIND` Argument der [/Delay (Laden von Importeinstellungen verzögern)](/visual-cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist die Hilfsfunktion verzögert zu laden, um explizite Entladen der DLL zu unterstützen.  
  
     Weitere Informationen finden Sie unter der `UNLOAD` Argument der [/Delay (Laden von Importeinstellungen verzögern)](/visual-cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     Optionale **booleschen** Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
     Weitere Informationen finden Sie unter [/nologo (Startbanner unterdrücken) (Linker)](/visual-cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist das Betriebssystem zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann die Bilddatei von dort aus auszuführen.  
  
     Weitere Informationen finden Sie unter der `CD` Argument der [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/visual-cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch die **SwapRunFromNET** Parameter.  
  
-   **SwapRunFromNET**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, weist das Betriebssystem zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann die Bilddatei von dort aus auszuführen.  
  
     Weitere Informationen finden Sie unter der `NET` Argument der [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/visual-cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch die **SwapRunFromCD** -Parameter in dieser Tabelle.  
  
-   **TargetMachine**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Zielplattform für das Programm oder die DLL an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\< none>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X 64**  
  
    -   **MachineX86** - **/MACHINE:X 86**  
  
     Weitere Informationen finden Sie unter [/Machine (Zielplattform angeben)](/visual-cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, setzt ein Flag in das Feld IMAGE_OPTIONAL_HEADER DllCharacteristics Programm Header des Abbilds optional. Wenn dieses Flag festgelegt ist, wird Terminalserver nicht bestimmte Änderungen an der Anwendung vornehmen.  
  
     Weitere Informationen finden Sie unter [/TSAWARE (Terminal Server beachten Anwendung erstellen)](/visual-cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt das Verzeichnis des Nachverfolgungsprotokolls an.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird keine Ausgabedatei generiert, wenn der Linker eine Warnung generiert.  
  
     Weitere Informationen finden Sie unter [/WX (Linkerwarnungen als Fehler behandeln)](/visual-cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, ein Bild für die aktuelle Ausgabedatei ohne .NET Framework-Assembly erstellt.  
  
     Weitere Informationen finden Sie unter [/NOASSEMBLY (Erstellen eines MSIL-Moduls)](/visual-cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Dateinamen und die Erweiterung der TLB-Datei. Geben Sie einen Dateinamen oder einen Pfad und Dateinamen ein.  
  
     Weitere Informationen finden Sie unter [/TLBOUT (Name. TLB-Datei)](/visual-cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     Optionale **Ganzzahl** Parameter.  
  
     Kennzeichnet einen benutzerdefinierten Wert für die vom Linker erstellte Typbibliothek. Geben Sie einen Wert zwischen 1 und 65535 ein.  
  
     Weitere Informationen finden Sie unter [/TLBID (Ressourcen-ID für TypeLib festlegen)](/visual-cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die angeforderte Ausführungsebene für die Anwendung an, mit der Benutzerkontensteuerung unter ausgeführt wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **"AsInvoker"** - `level='asInvoker'`  
  
    -   **"HighestAvailable"** - `level='highestAvailable'`  
  
    -   **"RequireAdministrator"** - `level='requireAdministrator'`  
  
     Weitere Informationen finden Sie unter der `level` Argument der [/MANIFESTUAC (bettet UAC-Informationen in Manifest)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, die Anwendung Sicherheitsebenen für Benutzeroberflächen umgangen, und die Eingaben für höhere Berechtigungen von Windows auf dem Desktop, und andernfalls `false`.  
  
     Weitere Informationen finden Sie unter der `uiAccess` Argument der [/MANIFESTUAC (bettet UAC-Informationen in Manifest)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, die Eingaben für das Bibliothekarstool verwendet werden, sondern die Bibliotheksdatei beim Bibliothek Projekt Abhängigkeiten gibt sich selbst verknüpft werden.  
  
-   **Version**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Fügen Sie eine Versionsnummer im Header des .exe oder .dll-Datei. Geben Sie "`major[.minor]`". Die `major` und `minor` Argumente sind Dezimalzahlen im Bereich von 0 bis 65535.  
  
     Weitere Informationen finden Sie unter [/Version (Versionsinformationen)](/visual-cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)