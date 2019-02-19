---
title: Link-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4575516304862b4d50060a101a08a74f88db4597
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54768513"
---
# <a name="link-task"></a>Link-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umschließt das Visual C++-Linkertool link.exe. Das Linkertool ist ein Tool, das Objektdateien und Bibliotheken im COFF-Format (Common Object File Format) miteinander verbindet, um eine ausführbare Datei (.exe) oder eine DLL (Dynamic Link Library) zu erstellen. Weitere Informationen finden Sie unter [Linkeroptionen](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **Link**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige andere Parameter entsprechen einer Befehlszeilenoption.  
  
- **AdditionalDependencies**  
  
   Optionaler **String[]**-Parameter.  
  
   Gibt eine Liste von Eingabedateien an, die dem Befehl hinzugefügt werden sollen.  
  
   Weitere Informationen finden Sie unter [LINK-Eingabedateien](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Optionaler **String[]**-Parameter.  
  
   Überschreibt den Bibliothekspfad der Umgebung. Geben Sie einen Verzeichnisnamen an.  
  
   Weitere Informationen finden Sie unter [/LIBPATH (Libpath-Pfad hinzufügen)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Optionaler **String[]**-Parameter.  
  
   Gibt Attribute an, die in den `dependency`-Abschnitt der Manifestdatei eingefügt werden.  
  
   Weitere Informationen finden Sie unter [/MANIFESTDEPENDENCY (Angeben von Manifestabhängigkeiten)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Siehe auch „Publisher Configuration Files“ auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website.  
  
- **AdditionalOptions**  
  
   Optionaler **String**-Parameter.  
  
   Eine Liste von Linkeroptionen, wie in der Befehlszeile angegeben. Beispiel: **"**_/option1 /option2 /option#_". Verwenden Sie diesen Parameter, um Linkeroptionen anzugeben, die nicht durch einen anderen **Link**-Aufgabenparameter repräsentiert werden.  
  
   Weitere Informationen finden Sie unter [Linkeroptionen](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Optionaler **String[]**-Parameter.  
  
   Fügt einer Assembly einen Modulverweis hinzu.  
  
   Weiter Informationen finden Sie unter [/ASSEMBLYMODULE (MSIL-Modul zur Assembly hinzufügen)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` bewirkt, dass das Betriebssystem Manifestsuch- und -ladevorgänge durchführt. `false` gibt an, dass DLLs geladen werden, als ob es kein Manifest gäbe.  
  
   Weitere Informationen finden Sie unter [/ALLOWISOLATION (Manifestsuche)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt das **DebuggableAttribute**-Attribut mit Debuginformationsnachverfolgung aus und deaktiviert die JIT-Optimierungen. Wenn `false` das **DebuggableAttribute**-Attribut ausgibt, aber Debuginformationsnachverfolgung deaktiviert und JIT-Optimierungen aktiviert.  
  
   Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Optionaler **String[]**-Parameter.  
  
   Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert. Geben Sie den Namen der Ressource an.  
  
   Weitere Informationen finden Sie unter [/ASSEMBLYLINKRESOURCE (Mit .NET Framework-Ressource verknüpfen)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Impliziter **boolescher** Parameter.  
  
   Ermöglicht die Nachverfolgung tieferer Dateien, um das inkrementelle Verhalten des Links zu erfassen. Gibt immer `true` zurück.  
  
- **BaseAddress**  
  
   Optionaler **String**-Parameter.  
  
   Legt eine Basisadresse für das Programm oder die erstellte DLL fest. Geben Sie `{address[,size] | @filename,key}`an.  
  
   Weitere Informationen finden Sie unter [/BASE (Basisadresse)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Optionaler **Boolean**-Parameter.  
  
   Zeigt bei TRUE an, dass MSBuild von der IDE aufgerufen wird. Andernfalls zeigt er an, dass MSBuild von der Befehlszeile aufgerufen wird.  
  
   Dieser Parameter hat keine entsprechende Linkeroption.  
  
- **CLRImageType**  
  
   Optionaler **String**-Parameter.  
  
   Legt den Typ eines Common Language Runtime (CLR) Images fest.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Standard** - *\<none>*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
    Weitere Informationen finden Sie unter [/CLRIMAGETYPE (Angeben des CLR-Bildtyps)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Optionaler **String**-Parameter.  
  
   Behält den letzten Fehlercode von Funktionen bei, die vom P/Invoke-Mechanismus aufgerufen werden.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Aktiviert** - **/CLRSupportLastError**  
  
  - **Deaktiviert** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Weitere Informationen finden Sie unter [/CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Optionaler **String**-Parameter.  
  
   Gibt das Threadingattribut für den Einstiegspunkt des CLR-Programms explizit an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
  - **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Weitere Informationen finden Sie unter [/CLRTHREADATTRIBUTE (Festlegen des CLR-Threadattributs)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Optionaler **Boolean**-Parameter.  
  
   Gibt an, ob der Linker **SuppressUnmanagedCodeSecurityAttribute** auf vom Linker generierte PInvoke-Anrufe von verwaltetem Code an nativen DLLs anwendet.  
  
   Weitere Informationen finden Sie unter [/CLRUNMANAGEDCODECHECK (Hinzufügen von SuppressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Optionaler **String**-Parameter.  
  
   Bereitet ein Image für Hotpatching vor.  
  
   Geben Sie einen der folgenden Werte an, der einer Linkeroption entspricht.  
  
  - **Aktiviert** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Weitere Informationen finden Sie unter [/FUNCTIONPADMIN (Erstellen eines Hotpatch-fähigen Abbildes)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass eine ausführbare Datei mit der Windows-Funktion zur Datenausführungsverhinderung kompatibel ist.  
  
   Weitere Informationen finden Sie unter [/NXCOMPAT (kompatibel mit Datenausführungsverhinderung)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Optionaler **String[]**-Parameter.  
  
   Dieser Parameter bewirkt ein *verzögertes Laden* des DLLs. Geben Sie den Namen einer DLL an, die mit einer Verzögerung geladen werden soll.  
  
   Weitere Informationen finden Sie unter [/DELAYLOAD (Laden von Import verzögern)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` signiert eine Assembly teilweise. In der Standardeinstellung ist der Wert `false`.  
  
   Weitere Informationen finden Sie unter [/DELAYSIGN (Assembly teilweise signieren)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Treiber**  
  
   Optionaler **String**-Parameter.  
  
   Geben Sie diesen Parameter an, um einen Windows NT-Kernelmodustreiber zu erstellen.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NotSet** - *\<none>*  
  
  - **Treiber** - **/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** - **/DRIVER:WDM**  
  
    Weitere Informationen finden Sie unter [/DRIVER (Treiber für den Kernelmodus von Windows NT)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Optionaler **String[]**-Parameter.  
  
   Bettet eine Ressourcendatei in eine Assembly ein. Geben Sie den Dateinamen für die angeforderte Ressource an. Geben Sie optional den logischen Namen ein, der zum Laden der Ressource verwendet wird, und die **PRIVATE**-Option, die im Assemblymanifest angibt, dass die Ressourcendatei privat ist.  
  
   Weitere Informationen finden Sie unter [/ASSEMBLYRESOURCE (Verwaltete Ressource einbetten)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` ermöglicht eine identische COMDAT-Faltung.  
  
   Weitere Informationen finden Sie unter dem `ICF[= iterations]`-Argument der [/OPT (Optimierungen)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.  
  
   Weitere Informationen finden Sie unter [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Optionaler **String**-Parameter.  
  
   Gibt eine Einstiegspunktfunktion als Startadresse für eine EXE-Datei oder DLL an. Geben Sie einen Funktionsnamen als Parameterwert an.  
  
   Weitere Informationen finden Sie unter [/ENTRY (Symbol für Einstiegspunkt)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt ein Programm oder eine DLL, das nur an seiner bevorzugten Basisadresse geladen werden kann.  
  
   Weitere Informationen finden Sie unter [/FIXED (Feste Basisadresse)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Optionaler **String**-Parameter.  
  
   Weist den Linker an, eine gültige EXE-Datei oder DLL auch dann zu erstellen, wenn auf ein Symbol verwiesen wird, dieses Symbol aber nicht oder mehrmals definiert wurde.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Aktiviert** - **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
  - **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
    Weitere Informationen finden Sie unter [//FORCE (Dateiausgabe erzwingen)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Optionaler **String[]**-Parameter.  
  
   Dieser Parameter weist den Linker an, der Symboltabelle ein bestimmtes Symbol hinzuzufügen.  
  
   Weitere Informationen finden Sie unter [/INCLUDE (Symbolverweise erzwingen)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Optionaler **String**-Parameter.  
  
   Dieser Parameter optimiert das Programm durch die Platzierung der angegebenen Paketfunktionen (COMDATs) in das Image in einer vorherbestimmten Reihenfolge.  
  
   Weitere Informationen finden Sie unter [/ORDER (Reihenfolge von Funktionen festlegen)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt Debuginformationen für die EXE-Datei oder DLL.  
  
   Weitere Informationen finden Sie unter [/DEBUG (Debuginfo generieren)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt eine parallele Manifestdatei.  
  
   Weitere Informationen finden Sie unter [/MANIFEST (Erstellen eines Manifests für eine parallele Assembly)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt eine *Zuordnungsdatei*. Das Suffix der Zuordnungsdatei ist .map.  
  
   Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die physische Speichermenge auf dem Heap an, die zu einem Zeitpunkt zugeordnet werden soll.  
  
   Weitere Informationen finden Sie unter dem `commit`-Argument in [/HEAP (Heapgröße festlegen)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Siehe auch den **HeapReserveSize**-Parameter.  
  
- **HeapReserveSize**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Gesamtgröße der Heapzuordnung im virtuellen Speicher an.  
  
   Weitere Informationen finden Sie unter dem `reserve`-Argument in [/HEAP (Heapgröße festlegen)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Siehe auch den Parameter **HeapCommitSize** in dieser Tabelle.  
  
- **IgnoreAllDefaultLibraries**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist den Linker an, mindestens eine Standardbibliothek aus der Liste der Bibliotheken, die durchsucht werden, zu entfernen, wenn externe Verweise aufgelöst werden.  
  
   Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass IDL-Attribute im Quellcode nicht in einer IDL-Datei verarbeitet werden sollten.  
  
   Weiter Informationen finden Sie unter [/IGNOREIDL (Attribute nicht in MIDL verarbeiten)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass die von dieser Konfiguration generierte Importbibliothek nicht in abhängige Projekte importiert werden sollte.  
  
   Dieser Parameter entspricht keiner Linkeroption.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Optionaler **String[]**-Parameter.  
  
   Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken mit Semikolons.  
  
   Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Optionaler **Boolean**-Parameter.  
  
   Bei `true` erstellt der Linker nur dann ein Image, wenn auch eine Tabelle mit den sicheren Ausnahmehandlern des Images erstellt werden kann.  
  
   Weitere Informationen finden Sie unter [/SAFESEH (Abbild verfügt über sichere Ausnahmehandler)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Ein benutzerdefinierter Importbibliotheksname, der den Standard-Bibliotheksnamen ersetzt.  
  
   Weitere Informationen finden Sie unter [/IMPLIB (Name der Importbibliothek)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Optionaler **String**-Parameter.  
  
   Container, der den Schlüssel für eine signierte Assembly enthält.  
  
   Weitere Informationen finden Sie unter [/KEYCONTAINER (Schlüsselcontainer zum Signieren einer Assembly festlegen)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Siehe auch den Parameter **KeyFile** in dieser Tabelle.  
  
- **KeyFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt eine Datei an, die den Schlüssel für eine signierte Assembly enthält.  
  
   Weitere Informationen finden Sie unter [/KEYFILE (Schlüsselcontainer oder Schlüsselpaar zum Signieren einer Assembly festlegen)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Siehe auch den Parameter **KeyContainer**.  
  
- **LargeAddressAware**  
  
   Optionaler **Boolean**-Parameter.  
  
   Bei `true` kann die Anwendung Adressen verarbeiten, die größer als 2 GB sind.  
  
   Weitere Informationen finden Sie unter [/LARGEADDRESSAWARE (Umfangreiche Adressen verarbeiten)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt eine DLL als Hauptausgabedatei.  
  
   Weitere Informationen finden Sie unter [/DLL (DLL erstellen)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Optionaler **String**-Parameter.  
  
   Ermöglicht Ihnen, Informationen über interne Compilerfehler direkt an Microsoft zu senden.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NoErrorReport** - **/ERRORREPORT:NONE**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    Weitere Informationen finden Sie unter [/ERRORREPORT (Weiterleiten von internen Linkerfehlern)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` aktiviert die inkrementelle Verknüpfung.  
  
   Weitere Informationen finden Sie unter [/INCREMENTAL (inkrementell verknüpfen)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass die Bibliotheksausgaben von Projektabhängigkeiten automatisch eingebunden werden.  
  
   Dieser Parameter entspricht keiner Linkeroption.  
  
- **LinkStatus**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt an, dass der Linker eine Statusanzeige ausgibt, die anzeigt, welcher Prozentsatz des Links abgeschlossen ist.  
  
   Weitere Informationen finden Sie unter dem`STATUS`-Argument in [/LTCG (Code zur Verknüpfungszeit generieren)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Optionaler **String**-Parameter.  
  
   Gibt Optionen für die profilgesteuerte Optimierung an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Default** - *\<none>*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Weitere Informationen finden Sie unter [/LTCG (Code zur Verknüpfungszeit generieren)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Optionaler **String**-Parameter.  
  
   Ändert den Standardnamen der Manifestdatei in den angegebenen Dateinamen.  
  
   Weitere Informationen finden Sie unter [/MANIFESTFILE (Benennen der Manifestdatei)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist den Linker an, exportierte Funktionen in eine Zuordnungsdatei einzufügen.  
  
   Weitere Informationen finden Sie unter dem `EXPORTS`-Argument in [/MAPINFO (Daten in Zuordnungsdatei einfügen)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Optionaler **String**-Parameter.  
  
   Ändert den Standardnamen der Zuordnungsdatei in den angegebenen Dateinamen.  
  
- **MergedIDLBaseFileName**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Dateinamen und die Dateinamenerweiterung der IDL-Datei an.  
  
   Weitere Informationen finden Sie unter [/IDLOUT (Namen der MIDL-Ausgabedateien)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Optionaler **String**-Parameter.  
  
   Kombiniert Abschnitte in einem Image. Geben Sie `from-section=to-section` an.  
  
   Weitere Informationen finden Sie unter [/MERGE (Abschnitte kombinieren)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Optionaler **String**-Parameter.  
  
   Geben Sie den Namen einer Datei an, die MIDL-Befehlszeilenoptionen enthält.  
  
   Weitere Informationen finden Sie unter [/MIDL (Optionen für MIDL-Befehlszeile festlegen)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich von 0 bis 65535.  
  
- **ModuleDefinitionFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Namen einer [Moduldefinitionsdatei](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8) an.  
  
   Weitere Informationen finden Sie unter [/DEF (Moduldefinitionsdatei festlegen)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Optionaler **String**-Parameter.  
  
   Fügt ein MS-DOS-Stubprogramm an ein Win32-Programm an.  
  
   Weitere Informationen finden Sie unter [/STUB (Name der MS-DOS-Stubdatei)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt eine DLL an, die nur als Ressource dient.  
  
   Weitere Informationen finden Sie unter [/NOENTRY (Kein Einstiegspunkt)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Impliziter **String[]**-Parameter.  
  
   Gibt die Objektdateien an, die verknüpft sind.  
  
- **OptimizeReferences**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` schließt Funktionen und/oder Daten aus, auf die nie verwiesen wird.  
  
   Weitere Informationen finden Sie unter dem `REF`-Argument der [/OPT (Optimierungen)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Optionaler **String**-Parameter.  
  
   Überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt.  
  
   Weitere Informationen finden Sie unter [/OUT (Ausgabedateiname)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Optionaler **Boolean**-Parameter.  
  
   Wenn `true` und Ausgabe registrieren aktiviert ist, erzwingen die Registrierungsschreibvorgänge die Umleitung von **HKEY_CLASSES_ROOT** nach **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Optionaler `ITaskItem[]` -Parameter.  
  
   Definiert ein Array von Präprozessor-Ausgabeelementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
- **PreventDllBinding**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` gibt Bind.exe an, dass das verknüpfte Image nicht gebunden werden soll.  
  
   Weitere Informationen finden Sie unter [/ALLOWBIND (DLL-Bindung verhindern)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profil**  
  
   Optionaler **boolescher** Parameter.  
  
   `true` erstellt eine Ausgabedatei, die mit dem **Leistungstools**-Profiler verwendet werden kann.  
  
   Weitere Informationen finden Sie unter [/PROFILE (Leistungstools-Profiler)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Namen der PGD-Datei an, die zum Speichern von Informationen zum ausgeführten Programm verwendet werden  
  
   Weitere Informationen finden Sie unter [/PGD (Angeben einer Datenbank für die profilgesteuerte Optimierungen)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt einen Namen für die Programmdatenbank (PDB) an, die der Linker erstellt.  
  
   Weitere Informationen finden Sie unter [/PDB (Programmdatenbank verwenden)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` generiert ein ausführbares Image, für das zur Ladezeit mit der *Address Space Layout Randomization*-Funktion (ASLR) von Windows nach dem Zufallsprinzip ein Rebase-Vorgang ausgeführt werden kann.  
  
   Weitere Informationen finden Sie unter [/DYNAMICBASE (Address Space Layout Randomization verwenden)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` registriert die primäre Ausgabe dieses Builds.  
  
- **SectionAlignment**  
  
   Optionaler **Integer**-Parameter.  
  
   Gibt die Ausrichtung der einzelnen Abschnitte innerhalb des linearen Adressraums des Programms an. Der Parameterwert ist eine Einheit von Bytes und eine Potenz von zwei.  
  
   Weitere Informationen finden Sie unter [/ALIGN (Abschnittsausrichtung)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` legt die Prüfsumme im Header einer EXE-Datei fest.  
  
   Weitere Informationen finden Sie unter [/RELEASE (Prüfsumme festlegen)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Ausführlichkeitsgrad von Statusberichten für die Verknüpfungsoperation an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NotSet** - *\<none>*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Weitere Informationen finden Sie unter [/VERBOSE (Statusmeldungen ausgeben)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Sources**  
  
   Erforderlicher `ITaskItem[]` -Parameter.  
  
   Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
- **SpecifySectionAttributes**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Attribute eines Abschnitts an. Dies überschreibt die Attribute, die beim Kompilieren der OBJ-Datei für den Abschnitt festgelegt wurden.  
  
   Weitere Informationen finden Sie unter [/SECTION (Abschnittsattribute festlegen)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Menge an physikalischem Speicher in jeder Zuordnung an, wenn zusätzlicher Speicher belegt wird.  
  
   Weitere Informationen finden Sie unter dem `commit`-Argument in [/STACK (Stapelreservierungen)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Gesamtgröße der Stapelreservierung im virtuellen Speicher an.  
  
   Weitere Informationen finden Sie unter dem `reserve`-Argument in [/STACK (Stapelreservierungen)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Optionaler **String**-Parameter.  
  
   Erstellt eine zweite Programmdatenbank (PDB)-Datei, die keine Symbole enthält, die Sie nicht an Ihre Kunden verteilen möchten. Geben Sie den Namen der zweiten PDB-Datei an.  
  
   Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **SubSystem**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Umgebung für die ausführbare Datei an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NotSet** - *\<none>*  
  
  - **Konsole** - **/SUBSYSTEM:CONSOLE**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Nativ** - **/SUBSYSTEM:NATIVE**  
  
  - **EFI-Anwendung** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **EFI-Startdiensttreiber** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI-ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **EFI-Laufzeit** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Weitere Informationen finden Sie unter [/SUBSYSTEM (Subsystem angeben)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist den Linker an, keine bindbare Importadresstabelle (IAT) in das endgültige Image einzuschließen.  
  
   Weitere Informationen finden Sie unter dem `NOBIND`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist die Hilfsfunktion für das verzögerte Laden an, das explizite Entladen der DLL zu unterstützen.  
  
   Weitere Informationen finden Sie unter dem `UNLOAD`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Optionaler **Boolean**-Parameter.  
  
   Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
   Weitere Informationen finden Sie unter [/NOLOGO (Startbanner unterdrücken) (Linker)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.  
  
   Weitere Informationen finden Sie unter dem `CD`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Siehe auch den **SwapRunFromNET**-Parameter.  
  
- **SwapRunFromNET**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.  
  
   Weitere Informationen finden Sie unter dem `NET`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Siehe auch den **SwapRunFromCD**-Parameter in dieser Tabelle.  
  
- **TargetMachine**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Zielplattform für das Programm oder die DLL an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NotSet** - *\<none>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X64**  
  
  - **MachineX86** - **/MACHINE:X86**  
  
    Weitere Informationen finden Sie unter [/MACHINE (Zielplattform angeben)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` setzt ein Flag in das Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programm-Images. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.  
  
   Weitere Informationen finden Sie unter [/TSAWARE (Terminalserverfähige Anwendung erstellen)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Optionaler **String**-Parameter.  
  
   Gibt das Verzeichnis des Nachverfolgungsprotokolls an.  
  
- **TreatLinkerWarningAsErrors**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` bewirkt, dass keine Ausgabedatei generiert wird, wenn der Linker eine Warnung generiert.  
  
   Weitere Informationen finden Sie unter [/WX (Linkerwarnungen als Fehler behandeln)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Optionaler **Boolean**-Parameter.  
  
   `true` erstellt ein Image für die aktuelle Ausgabedatei ohne eine .NET Framework-Assembly.  
  
   Weitere Informationen finden Sie unter [/NOASSEMBLY (MSIL-Modul erstellen)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Dateinamen und die Dateinamenerweiterung der TLB-Datei an. Geben Sie einen Dateinamen oder einen Pfad und Dateinamen ein.  
  
   Weitere Informationen finden Sie unter [/TLBOUT (TLB-Datei benennen)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Optionaler **Integer**-Parameter.  
  
   Kennzeichnet einen benutzerdefinierten Wert für die vom Linker erstellte Typbibliothek. Geben Sie einen Wert von 1 bis 65535 an.  
  
   Weitere Informationen finden Sie unter [/TLBID (Ressourcen-ID für TypeLib festlegen)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die angeforderte Ausführungsebene für die Anwendung an, wenn diese mit Benutzerkontensteuerung ausgeführt wird.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Weitere Informationen finden Sie unter dem `level`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Optionaler **Boolean**-Parameter.  
  
   Bei `true` umgeht die Anwendung Sicherheitsebenen für Benutzeroberflächen und steuert die Eingabe in Fenster mit höheren Berechtigungen auf dem Desktop; andernfalls `false`.  
  
   Weitere Informationen finden Sie unter dem `uiAccess`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Optionaler **Boolean**-Parameter.  
  
   Bei `true` werden die Eingaben in das Bibliothekstool eher verwendet als die Bibliotheksdatei selbst, wenn Bibliotheksausgaben von Projektabhängigkeiten verknüpft sind.  
  
- **Version**  
  
   Optionaler **String**-Parameter.  
  
   Fügen Sie eine Versionsnummer im Header der EXE- oder DLL-Datei ein. Geben Sie „`major[.minor]`“ an. Die `major` und `minor`-Argumente sind Dezimalzahlen von 0 bis 65535.  
  
   Weitere Informationen finden Sie unter [/VERSION (Versionsinformationen)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
