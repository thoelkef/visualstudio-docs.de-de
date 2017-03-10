---
title: Link-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7efa5c21454ec3cde3e07aa091919703544cc908
ms.lasthandoff: 02/22/2017

---
# <a name="link-task"></a>Link-Aufgabe
Umschließt das Visual C++-Linkertool link.exe. Das Linkertool ist ein Tool, das Objektdateien und Bibliotheken im COFF-Format (Common Object File Format) miteinander verbindet, um eine ausführbare Datei (.exe) oder eine DLL (Dynamic Link Library) zu erstellen. Weitere Informationen finden Sie unter [Linkeroptionen](/visual-cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **Link**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige andere Parameter entsprechen einer Befehlszeilenoption.  
  
-   **AdditionalDependencies**  
  
     Optionaler **String[]**-Parameter.  
  
     Gibt eine Liste von Eingabedateien an, die dem Befehl hinzugefügt werden sollen.  
  
     Weitere Informationen finden Sie unter [LINK-Eingabedateien](/visual-cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     Optionaler **String[]**-Parameter.  
  
     Überschreibt den Bibliothekspfad der Umgebung. Geben Sie einen Verzeichnisnamen an.  
  
     Weitere Informationen finden Sie unter [/LIBPATH (Libpath-Pfad hinzufügen)](/visual-cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     Optionaler **String[]**-Parameter.  
  
     Gibt Attribute an, die in den `dependency`-Abschnitt der Manifestdatei eingefügt werden.  
  
     Weitere Informationen finden Sie unter [/MANIFESTDEPENDENCY (Angeben von Manifestabhängigkeiten)](/visual-cpp/build/reference/manifestdependency-specify-manifest-dependencies). Siehe auch „Publisher Configuration Files“ auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website.  
  
-   **AdditionalOptions**  
  
     Optionaler **String**-Parameter.  
  
     Eine Liste von Linkeroptionen, wie in der Befehlszeile angegeben. Beispiel: **"***/option1 /option2 /option#*". Verwenden Sie diesen Parameter, um Linkeroptionen anzugeben, die nicht durch einen anderen **Link**-Aufgabenparameter repräsentiert werden.  
  
     Weitere Informationen finden Sie unter [Linkeroptionen](/visual-cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     Optionaler **String[]**-Parameter.  
  
     Fügt einer Assembly einen Modulverweis hinzu.  
  
     Weiter Informationen finden Sie unter [/ASSEMBLYMODULE (MSIL-Modul zur Assembly hinzufügen)](/visual-cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **AllowIsolation**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` bewirkt, dass das Betriebssystem Manifestsuch- und -ladevorgänge durchführt. `false` gibt an, dass DLLs geladen werden, als ob es kein Manifest gäbe.  
  
     Weitere Informationen finden Sie unter [/ALLOWISOLATION (Manifestsuche)](/visual-cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt das **DebuggableAttribute**-Attribut mit Debuginformationsnachverfolgung aus und deaktiviert die JIT-Optimierungen. Wenn `false` das **DebuggableAttribute**-Attribut ausgibt, aber Debuginformationsnachverfolgung deaktiviert und JIT-Optimierungen aktiviert.  
  
     Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **AssemblyLinkResource**  
  
     Optionaler **String[]**-Parameter.  
  
     Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert. Geben Sie den Namen der Ressource an.  
  
     Weitere Informationen finden Sie unter [/ASSEMBLYLINKRESOURCE (Mit .NET Framework-Ressource verknüpfen)](/visual-cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Impliziter **boolescher** Parameter.  
  
     Ermöglicht die Nachverfolgung tieferer Dateien, um das inkrementelle Verhalten des Links zu erfassen. Gibt immer `true` zurück.  
  
-   **BaseAddress**  
  
     Optionaler **String**-Parameter.  
  
     Legt eine Basisadresse für das Programm oder die erstellte DLL fest. Geben Sie `{address[,size] | @filename,key}` an.  
  
     Weitere Informationen finden Sie unter [/BASE (Basisadresse)](/visual-cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     Optionaler **boolescher** Parameter.  
  
     Zeigt bei TRUE an, dass MSBuild von der IDE aufgerufen wird. Andernfalls zeigt er an, dass MSBuild von der Befehlszeile aufgerufen wird.  
  
     Dieser Parameter hat keine entsprechende Linkeroption.  
  
-   **CLRImageType**  
  
     Optionaler **String**-Parameter.  
  
     Legt den Typ eines Common Language Runtime (CLR) Images fest.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard** - *\<none>*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
    -   **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
     Weitere Informationen finden Sie unter [/CLRIMAGETYPE (Angeben des CLR-Bildtyps)](/visual-cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **CLRSupportLastError**  
  
     Optionaler **String**-Parameter.  
  
     Behält den letzten Fehlercode von Funktionen bei, die vom P/Invoke-Mechanismus aufgerufen werden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Aktiviert** - **/CLRSupportLastError**  
  
    -   **Deaktiviert** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
     Weitere Informationen finden Sie unter [/CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)](/visual-cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **CLRThreadAttribute**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Threadingattribut für den Einstiegspunkt des CLR-Programms explizit an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
    -   **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
     Weitere Informationen finden Sie unter [/CLRTHREADATTRIBUTE (Festlegen des CLR-Threadattributs)](/visual-cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Optionaler **boolescher** Parameter.  
  
     Gibt an, ob der Linker **SuppressUnmanagedCodeSecurityAttribute** auf vom Linker generierte PInvoke-Anrufe von verwaltetem Code an nativen DLLs anwendet.  
  
     Weitere Informationen finden Sie unter [/CLRUNMANAGEDCODECHECK (Hinzufügen von SuppressUnmanagedCodeSecurity-Attribut)](/visual-cpp/build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute).  
  
-   **CreateHotPatchableImage**  
  
     Optionaler **String**-Parameter.  
  
     Bereitet ein Image für Hotpatching vor.  
  
     Geben Sie einen der folgenden Werte an, der einer Linkeroption entspricht.  
  
    -   **Aktiviert** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
     Weitere Informationen finden Sie unter [/FUNCTIONPADMIN (Erstellen eines Hotpatch-fähigen Abbildes)](/visual-cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass eine ausführbare Datei mit der Windows-Funktion zur Datenausführungsverhinderung kompatibel ist.  
  
     Weitere Informationen finden Sie unter [/NXCOMPAT (kompatibel mit Datenausführungsverhinderung)](/visual-cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     Optionaler **String[]**-Parameter.  
  
     Dieser Parameter bewirkt ein *verzögertes Laden* des DLLs. Geben Sie den Namen einer DLL an, die mit einer Verzögerung geladen werden soll.  
  
     Weitere Informationen finden Sie unter [/DELAYLOAD (Laden von Import verzögern)](/visual-cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` signiert eine Assembly teilweise. In der Standardeinstellung ist der Wert `false`.  
  
     Weitere Informationen finden Sie unter [/DELAYSIGN (Assembly teilweise signieren)](/visual-cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Treiber**  
  
     Optionaler **String**-Parameter.  
  
     Geben Sie diesen Parameter an, um einen Windows NT-Kernelmodustreiber zu erstellen.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Treiber** - **/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** - **/DRIVER:WDM**  
  
     Weitere Informationen finden Sie unter [/DRIVER (Treiber für den Kernelmodus von Windows NT)](/visual-cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     Optionaler **String[]**-Parameter.  
  
     Bettet eine Ressourcendatei in eine Assembly ein. Geben Sie den Dateinamen für die angeforderte Ressource an. Geben Sie optional den logischen Namen ein, der zum Laden der Ressource verwendet wird, und die **PRIVATE**-Option, die im Assemblymanifest angibt, dass die Ressourcendatei privat ist.  
  
     Weitere Informationen finden Sie unter [/ASSEMBLYRESOURCE (Verwaltete Ressource einbetten)](/visual-cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` ermöglicht eine identische COMDAT-Faltung.  
  
     Weitere Informationen finden Sie unter dem `ICF[= iterations]`-Argument der [/OPT (Optimierungen)](/visual-cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.  
  
     Weitere Informationen finden Sie unter [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     Optionaler **String**-Parameter.  
  
     Gibt eine Einstiegspunktfunktion als Startadresse für eine EXE-Datei oder DLL an. Geben Sie einen Funktionsnamen als Parameterwert an.  
  
     Weitere Informationen finden Sie unter [/ENTRY (Symbol für Einstiegspunkt)](/visual-cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt ein Programm oder eine DLL, das nur an seiner bevorzugten Basisadresse geladen werden kann.  
  
     Weitere Informationen finden Sie unter [/FIXED (Feste Basisadresse)](/visual-cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     Optionaler **String**-Parameter.  
  
     Weist den Linker an, eine gültige EXE-Datei oder DLL auch dann zu erstellen, wenn auf ein Symbol verwiesen wird, dieses Symbol aber nicht oder mehrmals definiert wurde.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Aktiviert** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
     Weitere Informationen finden Sie unter [//FORCE (Dateiausgabe erzwingen)](/visual-cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     Optionaler **String[]**-Parameter.  
  
     Dieser Parameter weist den Linker an, der Symboltabelle ein bestimmtes Symbol hinzuzufügen.  
  
     Weitere Informationen finden Sie unter [/INCLUDE (Symbolverweise erzwingen)](/visual-cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     Optionaler **String**-Parameter.  
  
     Dieser Parameter optimiert das Programm durch die Platzierung der angegebenen Paketfunktionen (COMDATs) in das Image in einer vorherbestimmten Reihenfolge.  
  
     Weitere Informationen finden Sie unter [/ORDER (Reihenfolge von Funktionen festlegen)](/visual-cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt Debuginformationen für die EXE-Datei oder DLL.  
  
     Weitere Informationen finden Sie unter [/DEBUG (Debuginfo generieren)](/visual-cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt eine parallele Manifestdatei.  
  
     Weitere Informationen finden Sie unter [/MANIFEST (Erstellen eines Manifests für eine parallele Assembly)](/visual-cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt eine *Zuordnungsdatei*. Das Suffix der Zuordnungsdatei ist .map.  
  
     Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/visual-cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die physische Speichermenge auf dem Heap an, die zu einem Zeitpunkt zugeordnet werden soll.  
  
     Weitere Informationen finden Sie unter dem `commit`-Argument in [/HEAP (Heapgröße festlegen)](/visual-cpp/build/reference/heap-set-heap-size). Siehe auch den **HeapReserveSize**-Parameter.  
  
-   **HeapReserveSize**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Gesamtgröße der Heapzuordnung im virtuellen Speicher an.  
  
     Weitere Informationen finden Sie unter dem `reserve`-Argument in [/HEAP (Heapgröße festlegen)](/visual-cpp/build/reference/heap-set-heap-size). Siehe auch den Parameter **HeapCommitSize** in dieser Tabelle.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist den Linker an, mindestens eine Standardbibliothek aus der Liste der Bibliotheken, die durchsucht werden, zu entfernen, wenn externe Verweise aufgelöst werden.  
  
     Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/visual-cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass IDL-Attribute im Quellcode nicht in einer IDL-Datei verarbeitet werden sollten.  
  
     Weiter Informationen finden Sie unter [/IGNOREIDL (Attribute nicht in MIDL verarbeiten)](/visual-cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass die von dieser Konfiguration generierte Importbibliothek nicht in abhängige Projekte importiert werden sollte.  
  
     Dieser Parameter entspricht keiner Linkeroption.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Optionaler **String[]**-Parameter.  
  
     Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken mit Semikolons.  
  
     Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/visual-cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Optionaler **boolescher** Parameter.  
  
     Bei `true` erstellt der Linker nur dann ein Image, wenn auch eine Tabelle mit den sicheren Ausnahmehandlern des Images erstellt werden kann.  
  
     Weitere Informationen finden Sie unter [/SAFESEH (Abbild verfügt über sichere Ausnahmehandler)](/visual-cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Ein benutzerdefinierter Importbibliotheksname, der den Standard-Bibliotheksnamen ersetzt.  
  
     Weitere Informationen finden Sie unter [/IMPLIB (Name der Importbibliothek)](/visual-cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     Optionaler **String**-Parameter.  
  
     Container, der den Schlüssel für eine signierte Assembly enthält.  
  
     Weitere Informationen finden Sie unter [/KEYCONTAINER (Schlüsselcontainer zum Signieren einer Assembly festlegen)](/visual-cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Siehe auch den Parameter **KeyFile** in dieser Tabelle.  
  
-   **KeyFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt eine Datei an, die den Schlüssel für eine signierte Assembly enthält.  
  
     Weitere Informationen finden Sie unter [/KEYFILE (Schlüsselcontainer oder Schlüsselpaar zum Signieren einer Assembly festlegen)](/visual-cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Siehe auch den Parameter **KeyContainer**.  
  
-   **LargeAddressAware**  
  
     Optionaler **boolescher** Parameter.  
  
     Bei `true` kann die Anwendung Adressen verarbeiten, die größer als 2 GB sind.  
  
     Weitere Informationen finden Sie unter [/LARGEADDRESSAWARE (Umfangreiche Adressen verarbeiten)](/visual-cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt eine DLL als Hauptausgabedatei.  
  
     Weitere Informationen finden Sie unter [/DLL (DLL erstellen)](/visual-cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     Optionaler **String**-Parameter.  
  
     Ermöglicht Ihnen, Informationen über interne Compilerfehler direkt an Microsoft zu senden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NoErrorReport** - **/ERRORREPORT:NONE**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **/ERRORREPORT:SEND**  
  
     Weitere Informationen finden Sie unter [/ERRORREPORT (Weiterleiten von internen Linkerfehlern)](/visual-cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` aktiviert die inkrementelle Verknüpfung.  
  
     Weitere Informationen finden Sie unter [/INCREMENTAL (inkrementell verknüpfen)](/visual-cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass die Bibliotheksausgaben von Projektabhängigkeiten automatisch eingebunden werden.  
  
     Dieser Parameter entspricht keiner Linkeroption.  
  
-   **LinkStatus**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt an, dass der Linker eine Statusanzeige ausgibt, die anzeigt, welcher Prozentsatz des Links abgeschlossen ist.  
  
     Weitere Informationen finden Sie unter dem`STATUS`-Argument in [/LTCG (Code zur Verknüpfungszeit generieren)](/visual-cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     Optionaler **String**-Parameter.  
  
     Gibt Optionen für die profilgesteuerte Optimierung an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard** - *\<none>*  
  
    -   **UseLinkTimeCodeGeneration** - **/LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
     Weitere Informationen finden Sie unter [/LTCG (Code zur Verknüpfungszeit generieren)](/visual-cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **ManifestFile**  
  
     Optionaler **String**-Parameter.  
  
     Ändert den Standardnamen der Manifestdatei in den angegebenen Dateinamen.  
  
     Weitere Informationen finden Sie unter [/MANIFESTFILE (Benennen der Manifestdatei)](/visual-cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist den Linker an, exportierte Funktionen in eine Zuordnungsdatei einzufügen.  
  
     Weitere Informationen finden Sie unter dem `EXPORTS`-Argument in [/MAPINFO (Daten in Zuordnungsdatei einfügen)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     Optionaler **String**-Parameter.  
  
     Ändert den Standardnamen der Zuordnungsdatei in den angegebenen Dateinamen.  
  
-   **MergedIDLBaseFileName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Dateinamen und die Dateinamenerweiterung der IDL-Datei an.  
  
     Weitere Informationen finden Sie unter [/IDLOUT (Namen der MIDL-Ausgabedateien)](/visual-cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     Optionaler **String**-Parameter.  
  
     Kombiniert Abschnitte in einem Image. Geben Sie `from-section=to-section` an.  
  
     Weitere Informationen finden Sie unter [/MERGE (Abschnitte kombinieren)](/visual-cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     Optionaler **String**-Parameter.  
  
     Geben Sie den Namen einer Datei an, die MIDL-Befehlszeilenoptionen enthält.  
  
     Weitere Informationen finden Sie unter [/MIDL (Optionen für MIDL-Befehlszeile festlegen)](/visual-cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich von 0 bis 65535.  
  
-   **ModuleDefinitionFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen einer [Moduldefinitionsdatei](/visual-cpp/build/reference/module-definition-dot-def-files) an.  
  
     Weitere Informationen finden Sie unter [/DEF (Moduldefinitionsdatei festlegen)](/visual-cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     Optionaler **String**-Parameter.  
  
     Fügt ein MS-DOS-Stubprogramm an ein Win32-Programm an.  
  
     Weitere Informationen finden Sie unter [/STUB (Name der MS-DOS-Stubdatei)](/visual-cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt eine DLL an, die nur als Ressource dient.  
  
     Weitere Informationen finden Sie unter [/NOENTRY (Kein Einstiegspunkt)](/visual-cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Impliziter **String[]**-Parameter.  
  
     Gibt die Objektdateien an, die verknüpft sind.  
  
-   **OptimizeReferences**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` schließt Funktionen und/oder Daten aus, auf die nie verwiesen wird.  
  
     Weitere Informationen finden Sie unter dem `REF`-Argument der [/OPT (Optimierungen)](/visual-cpp/build/reference/opt-optimizations).  
  
-   **OutputFile**  
  
     Optionaler **String**-Parameter.  
  
     Überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt.  
  
     Weitere Informationen finden Sie unter [/OUT (Ausgabedateiname)](/visual-cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     Optionaler **boolescher** Parameter.  
  
     Wenn `true` und Ausgabe registrieren aktiviert ist, erzwingen die Registrierungsschreibvorgänge die Umleitung von **HKEY_CLASSES_ROOT** nach **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Optionaler `ITaskItem[]`-Parameter.  
  
     Definiert ein Array von Präprozessor-Ausgabeelementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **PreventDllBinding**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` gibt Bind.exe an, dass das verknüpfte Image nicht gebunden werden soll.  
  
     Weitere Informationen finden Sie unter [/ALLOWBIND (DLL-Bindung verhindern)](/visual-cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profil**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt eine Ausgabedatei, die mit dem **Leistungstools**-Profiler verwendet werden kann.  
  
     Weitere Informationen finden Sie unter [/PROFILE (Leistungstools-Profiler)](/visual-cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen der PGD-Datei an, die zum Speichern von Informationen zum ausgeführten Programm verwendet werden  
  
     Weitere Informationen finden Sie unter [/PGD (Angeben einer Datenbank für die profilgesteuerte Optimierungen)](/visual-cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt einen Namen für die Programmdatenbank (PDB) an, die der Linker erstellt.  
  
     Weitere Informationen finden Sie unter [/PDB (Programmdatenbank verwenden)](/visual-cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` generiert ein ausführbares Image, für das zur Ladezeit mit der *Address Space Layout Randomization*-Funktion (ASLR) von Windows nach dem Zufallsprinzip ein Rebase-Vorgang ausgeführt werden kann.  
  
     Weitere Informationen finden Sie unter [/DYNAMICBASE (Address Space Layout Randomization verwenden)](/visual-cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` registriert die primäre Ausgabe dieses Builds.  
  
-   **SectionAlignment**  
  
     Optionaler **Integer**-Parameter.  
  
     Gibt die Ausrichtung der einzelnen Abschnitte innerhalb des linearen Adressraums des Programms an. Der Parameterwert ist eine Einheit von Bytes und eine Potenz von zwei.  
  
     Weitere Informationen finden Sie unter [/ALIGN (Abschnittsausrichtung)](/visual-cpp/build/reference/align-section-alignment).  
  
-   **SetChecksum**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` legt die Prüfsumme im Header einer EXE-Datei fest.  
  
     Weitere Informationen finden Sie unter [/RELEASE (Prüfsumme festlegen)](/visual-cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Ausführlichkeitsgrad von Statusberichten für die Verknüpfungsoperation an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\<none>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
     Weitere Informationen finden Sie unter [/VERBOSE (Statusmeldungen ausgeben)](/visual-cpp/build/reference/verbose-print-progress-messages).  
  
-   **Sources**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **SpecifySectionAttributes**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Attribute eines Abschnitts an. Dies überschreibt die Attribute, die beim Kompilieren der OBJ-Datei für den Abschnitt festgelegt wurden.  
  
     Weitere Informationen finden Sie unter [/SECTION (Abschnittsattribute festlegen)](/visual-cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Menge an physikalischem Speicher in jeder Zuordnung an, wenn zusätzlicher Speicher belegt wird.  
  
     Weitere Informationen finden Sie unter dem `commit`-Argument in [/STACK (Stapelreservierungen)](/visual-cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Gesamtgröße der Stapelreservierung im virtuellen Speicher an.  
  
     Weitere Informationen finden Sie unter dem `reserve`-Argument in [/STACK (Stapelreservierungen)](/visual-cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     Optionaler **String**-Parameter.  
  
     Erstellt eine zweite Programmdatenbank (PDB)-Datei, die keine Symbole enthält, die Sie nicht an Ihre Kunden verteilen möchten. Geben Sie den Namen der zweiten PDB-Datei an.  
  
     Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **SubSystem**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Umgebung für die ausführbare Datei an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Konsole** - **/SUBSYSTEM:CONSOLE**  
  
    -   **Windows** - **/SUBSYSTEM:WINDOWS**  
  
    -   **Nativ** - **/SUBSYSTEM:NATIVE**  
  
    -   **EFI-Anwendung** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **EFI-Startdiensttreiber** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI-ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI-Laufzeit** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
     Weitere Informationen finden Sie unter [/SUBSYSTEM (Subsystem angeben)](/visual-cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist den Linker an, keine bindbare Importadresstabelle (IAT) in das endgültige Image einzuschließen.  
  
     Weitere Informationen finden Sie unter dem `NOBIND`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](/visual-cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist die Hilfsfunktion für das verzögerte Laden an, das explizite Entladen der DLL zu unterstützen.  
  
     Weitere Informationen finden Sie unter dem `UNLOAD`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](/visual-cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     Optionaler **Boolean**-Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
     Weitere Informationen finden Sie unter [/NOLOGO (Startbanner unterdrücken) (Linker)](/visual-cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.  
  
     Weitere Informationen finden Sie unter dem `CD`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/visual-cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch den **SwapRunFromNET**-Parameter.  
  
-   **SwapRunFromNET**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.  
  
     Weitere Informationen finden Sie unter dem `NET`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/visual-cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch den **SwapRunFromCD**-Parameter in dieser Tabelle.  
  
-   **TargetMachine**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Zielplattform für das Programm oder die DLL an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NotSet** - *\<none>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X64**  
  
    -   **MachineX86** - **/MACHINE:X86**  
  
     Weitere Informationen finden Sie unter [/MACHINE (Zielplattform angeben)](/visual-cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` setzt ein Flag in das Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programm-Images. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.  
  
     Weitere Informationen finden Sie unter [/TSAWARE (Terminalserverfähige Anwendung erstellen)](/visual-cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Verzeichnis des Nachverfolgungsprotokolls an.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` bewirkt, dass keine Ausgabedatei generiert wird, wenn der Linker eine Warnung generiert.  
  
     Weitere Informationen finden Sie unter [/WX (Linkerwarnungen als Fehler behandeln)](/visual-cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     Optionaler **boolescher** Parameter.  
  
     `true` erstellt ein Image für die aktuelle Ausgabedatei ohne eine .NET Framework-Assembly.  
  
     Weitere Informationen finden Sie unter [/NOASSEMBLY (MSIL-Modul erstellen)](/visual-cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Dateinamen und die Dateinamenerweiterung der TLB-Datei an. Geben Sie einen Dateinamen oder einen Pfad und Dateinamen ein.  
  
     Weitere Informationen finden Sie unter [/TLBOUT (TLB-Datei benennen)](/visual-cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     Optionaler **Integer**-Parameter.  
  
     Kennzeichnet einen benutzerdefinierten Wert für die vom Linker erstellte Typbibliothek. Geben Sie einen Wert von 1 bis 65535 an.  
  
     Weitere Informationen finden Sie unter [/TLBID (Ressourcen-ID für TypeLib festlegen)](/visual-cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die angeforderte Ausführungsebene für die Anwendung an, wenn diese mit Benutzerkontensteuerung ausgeführt wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
     Weitere Informationen finden Sie unter dem `level`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     Optionaler **boolescher** Parameter.  
  
     Bei `true` umgeht die Anwendung Sicherheitsebenen für Benutzeroberflächen und steuert die Eingabe in Fenster mit höheren Berechtigungen auf dem Desktop; andernfalls `false`.  
  
     Weitere Informationen finden Sie unter dem `uiAccess`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/visual-cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     Optionaler **boolescher** Parameter.  
  
     Bei `true` werden die Eingaben in das Bibliothekstool eher verwendet als die Bibliotheksdatei selbst, wenn Bibliotheksausgaben von Projektabhängigkeiten verknüpft sind.  
  
-   **Version**  
  
     Optionaler **String**-Parameter.  
  
     Fügen Sie eine Versionsnummer im Header der EXE- oder DLL-Datei ein. Geben Sie „`major[.minor]`“ an. Die `major` und `minor`-Argumente sind Dezimalzahlen von 0 bis 65535.  
  
     Weitere Informationen finden Sie unter [/VERSION (Versionsinformationen)](/visual-cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
