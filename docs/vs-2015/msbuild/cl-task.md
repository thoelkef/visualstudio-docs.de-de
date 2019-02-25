---
title: CL-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 136bc554abe6c231dfa80753b19dba89946830c3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54756662"
---
# <a name="cl-task"></a>CL-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umschließt das Visual C++-Compilertool cl.exe. Der Compiler generiert ausführbare Dateien (EXE), Dynamic Link Library-Dateien (DLL) oder Codemoduldateien (NETMODULE). Weitere Informationen finden Sie unter [Compileroptionen](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **CL**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige Parametersätze entsprechen einer Befehlszeilenoption.  
  
- **AdditionalIncludeDirectories**  
  
   Optionaler String[]-Parameter.  
  
   Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die nach Includedateien durchsucht werden.  
  
   Weitere Informationen finden Sie unter [/I (Zusätzliche Includeverzeichnisse)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Optionaler String-Parameter.  
  
   Eine Liste von Befehlszeilenoptionen. Beispielsweise „/*option1* /*option2* /*option#*“. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen Aufgabenparameter dargestellt werden.  
  
   Weitere Informationen finden Sie unter [Compileroptionen](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** Optionaler String []-Parameter.  
  
   Gibt ein Verzeichnis an, das der Compiler durchsucht, um Dateiverweise aufzulösen, die an die **#using**-Anweisung übergeben wurden.  
  
   Weitere Informationen finden Sie unter [/AI (Metadatenverzeichnisse festlegen)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Optionaler String-Parameter.  
  
   Eine Zeichenfolge, die immer in der Befehlszeile ausgegeben wird. Ihr Standardwert ist „**/c**“.  
  
- **AssemblerListingLocation**  
  
   Erstellt eine Listendatei, die Assemblycode enthält.  
  
   Weitere Informationen finden Sie unter der **/Fa**-Option in [/FA, /Fa (Listendatei)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Optionaler String-Parameter.  
  
   Erstellt eine Listendatei, die Assemblycode enthält.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NoListing** - *\<none>*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **All** - **/FAcs**  
  
    Weitere Informationen finden Sie unter den Optionen **/FA**, **/FAc**, **/FAs** und **/FAcs** in [/FA, /Fa (Listendatei)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Optionaler String-Parameter.  
  
   Aktiviert und deaktiviert die Funktion für Laufzeitfehlerüberprüfungen in Verbindung mit dem [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)-Pragma.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Default** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Weitere Informationen finden Sie unter [/RTC (Laufzeitfehlerüberprüfungen)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird eine Browseinformationsdatei erstellt.  
  
   Weitere Informationen finden Sie unter der **/FR**-Option in [/FR, /Fr (SBR-Datei erstellen)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Optionaler String-Parameter.  
  
   Gibt einen Dateinamen für die Browseinformationsdatei an.  
  
   Weitere Informationen finden Sie unter dem Parameter **BrowseInformation** in dieser Tabelle und unter [/FR, /Fr (SBR-Datei erstellen)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` werden einige Pufferüberläufe erkannt, die die Rückgabeadresse überschreiben – ein gängiges Verfahren zur Nutzung von Code, der keine Puffergrößeneinschränkungen erzwingt.  
  
   Weitere Informationen finden Sie unter [/GS (Puffer-Sicherheitsüberprüfung)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
- **BuildingInIDE**  
  
   Optionaler boolescher Parameter.  
  
   Zeigt bei `true` an, dass **MSBuild** von der IDE aufgerufen wird. Andernfalls wird **MSBuild** in der Befehlszeile aufgerufen.  
  
- **CallingConvention**  
  
   Optionaler String-Parameter.  
  
   Gibt die Aufrufkonvention an, mit der festgelegt wird, in welcher Reihenfolge die Funktionsargumente auf den Stapel verschoben werden, ob die aufrufende oder die aufgerufene Funktion die Argumente am Ende des Aufrufs aus dem Stapel entfernt, und welche Namensergänzungskonvention der Compiler zur Erkennung einzelner Funktionen verwendet.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **/Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    Weitere Informationen finden Sie unter [/Gd, /Gr, /Gv, /Gz (Aufrufkonvention)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Optionaler String-Parameter.  
  
   Gibt an, ob die Eingabedatei als C- oder C++-Quelldatei kompiliert wird.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Default** - *\<none>*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Weitere Informationen finden Sie unter [/Tc, /Tp, /TC, /TP (Typ der Quelldatei angeben)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Optionaler String-Parameter.  
  
   Ermöglicht Anwendungen und Komponenten, Funktionen aus der Common Language Runtime (CLR) zu verwenden.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **false** - *\<none>*  
  
  - **true** - **/clr**  
  
  - **Pure** - **/clr:pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird der Compiler angewiesen, ein Abbild für *Hotpatching* vorzubereiten. Durch diesen Parameter wird sichergestellt, dass die erste Anweisung jeder Funktion mindestens über die für das Hotpatching erforderliche Größe von zwei Bytes verfügt.  
  
   Weitere Informationen finden Sie unter [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Optionaler String-Parameter.  
  
   Wählt den Typ der Debuginformationen aus, der für Ihr Programm erstellt wird, und ob diese Informationen in Objektdateien (OBJ) oder in einer Programmdatenbank (PDB) gespeichert werden sollen.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Weitere Informationen finden Sie unter [/Z7, /Zi, /ZI (Debuginformationsformat)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Optionaler boolescher Parameter.  
  
   Bei **TRUE** wird der Compiler angewiesen, einen Fehler für Sprachkonstrukte auszugeben, die weder mit ANSI C noch mit ANSI C++ kompatibel sind.  
  
   Weitere Informationen finden Sie unter der **/Za**-Option in [/Za, /Ze (Spracherweiterungen deaktivieren)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Optionaler String[]-Parameter.  
  
   Deaktiviert die Warnzahlen, die in einer durch Semikolons getrennten Liste angegeben werden.  
  
   Weitere Informationen finden Sie unter der `/wd`-Option in [/w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Warnstufe)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Optionaler String-Parameter.  
  
   Gibt die Architektur für die Codegenerierung an, die Streaming SIMD Extensions (SSE)- und Streaming SIMD Extensions 2 (SSE2)-Anweisungen enthält.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    Weitere Informationen finden Sie unter [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird Fiber-Sicherheit für Daten unterstützt, die mit statischem lokalen Threadspeicher zugewiesen werden, d.h. mit `__declspec(thread)` zugewiesene Daten.  
  
   Weitere Informationen finden Sie unter [/GT (Fiber-sicheren lokalen Thread-Speicher unterstützen)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird die Codeanalyse aktiviert.  
  
   Weitere Informationen finden Sie unter [/analyze (Codeanalyse)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Optionaler String-Parameter.  
  
   Ermöglicht es Ihnen, Informationen über interne Compilerfehler (ICE) direkt an Microsoft zu senden. Standardmäßig lautet die Einstellung in IDE-Builds **Prompt** und in Befehlszeilenbuilds **Queue**.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Weitere Informationen finden Sie unter [/errorReport (Meldung über interne Compilerfehler)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Optionaler String-Parameter.  
  
   Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **false** - *\<none>*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Weitere Informationen finden Sie unter [/EH (Ausnahmebehandlungsmodell)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird eine Listendatei mit erweiterten Attributen erstellt, die in die Quelldatei eingefügt wird.  
  
   Weitere Informationen finden Sie unter [/Fx (Eingefügten Code zusammenführen)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Optionaler String-Parameter.  
  
   Gibt an, ob Codegröße oder Codegeschwindigkeit bevorzugt wird.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Neither** - *\<none>*  
  
  - **Size** - **/Os**  
  
  - **Speed** - **/Ot**  
  
    Weitere Informationen finden Sie unter [/Os, /Ot (Kompakten Code bevorzugen, Schnellen Code bevorzugen)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird das verlässliche Modell für Gleitkommaausnahmen aktiviert. Ausnahmen werden sofort ausgelöst, wenn sie auftreten.  
  
   Weitere Informationen finden Sie unter der Option /**fp:except** in [/fp (Festlegen des Gleitkommaverhaltens)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Optionaler String-Parameter.  
  
   Legt das Gleitkommamodell fest.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Precise** - **/fp:precise**  
  
  - **Strict** - **/fp:strict**  
  
  - **Fast** - **/fp:fast**  
  
    Weitere Informationen finden Sie unter [/fp (Festlegen des Gleitkommaverhaltens)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Optionaler boolescher Parameter.  
  
   Bei `true` wird Standard-C++-Verhalten in [for](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a)-Schleifen implementiert, die Microsoft-Erweiterungen ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)) verwenden.  
  
   Weitere Informationen finden Sie unter [/Zc:forScope (Übereinstimmung in for-Schleifenbereich erzwingen)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Optionaler `String[]` -Parameter.  
  
   Weist den Präprozessor an, eine oder mehrere angegebene Headerdateien zu verarbeiten.  
  
   Weitere Informationen finden Sie unter [/FI (Name der expliziten Includedatei)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Optionaler **String[]**-Parameter.  
  
   Weist den Präprozessor an, eine oder mehrere angegebene **#using**-Datei zu verarbeiten.  
  
   Weitere Informationen finden Sie unter [/FU (Name der expliziten #using-Datei)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird dem Compiler ermöglicht, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren.  
  
   Weitere Informationen finden Sie unter [/Gy (Funktionslevel-Linking aktivieren)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden vom Compiler Dokumentationskommentare in Quellcodedateien verarbeitet, und für jede derartige Quellcodedatei mit Dokumentationskommentaren wird eine XDC-Datei erstellt.  
  
   Weitere Informationen finden Sie unter [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Siehe auch den Parameter **XMLDocumentationFileName** in dieser Tabelle.  
  
- **IgnoreStandardIncludePath**  
  
   Optionaler `Boolean` -Parameter.  
  
   Hindert bei `true` den Compiler daran, in den Verzeichnissen, die in den Umgebungsvariablen PATH und INCLUDE angegeben sind, nach Includedateien zu suchen.  
  
   Weitere Informationen finden Sie unter [/X (Standardincludepfade ignorieren)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die Ebene der Inlinefunktionserweiterung für den Build an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Default** - *\<none>*  
  
  - **Disabled** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    Weitere Informationen finden Sie unter [/Ob (Inlinefunktionserweiterung)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden einige Funktionsaufrufe durch systeminterne oder sonstige spezielle Formen der Funktion ersetzt, die dazu beitragen, dass die Arbeitsgeschwindigkeit der Anwendung erhöht wird.  
  
   Weitere Informationen finden Sie unter [/Oi (Systeminterne Funktionen erstellen)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Mindestneuerstellung aktiviert, die bestimmt, ob C++-Quelldateien, die geänderte C++-Klassendefinitionen enthalten (die in Headerdateien (H) gespeichert sind), neu kompiliert werden müssen.  
  
   Weitere Informationen finden Sie unter [/Gm (Minimale Neuerstellung aktivieren)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden mehrere Prozessoren für das Kompilieren verwendet. Dieser Parameter erstellt einen Prozess für jeden effektiven Prozessor auf dem Computer.  
  
   Weitere Informationen finden Sie unter [/MP (Erstellen mit mehreren Prozessen)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Siehe auch den Parameter **ProcessorNumber** in dieser Tabelle.  
  
- **ObjectFileName**  
  
   Optionaler **String**-Parameter.  
  
   Gibt einen Namen für die Objektdatei (OBJ) oder das Verzeichnis an, der anstelle des Standardwerts verwendet werden soll.  
  
   Weitere Informationen finden Sie unter [/Fo (Name der Objektdatei)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Optionaler **String[]**-Parameter.  
  
   Eine Liste von Objektdateien.  
  
- **OmitDefaultLibName**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird der Name der Standard-C-Laufzeitbibliothek in der Objektdatei (OBJ) weggelassen. Standardmäßig legt der Compiler den Namen der Bibliothek in der OBJ-Datei ab, um den Linker zur richtigen Bibliothek zu leiten.  
  
   Weitere Informationen finden Sie unter [/Zl (Kein Standardbibliotheksname)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Erstellung von Framezeigern in der Anrufliste unterdrückt.  
  
   Weitere Informationen finden Sie unter [/Oy (Framezeiger unterdrücken)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` verarbeitet der Compiler OpenMP-Klauseln und -Direktiven.  
  
   Weitere Informationen finden Sie unter [/openmp (Aktivieren der OpenMP 2.0-Unterstützung)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optimization**  
  
   Optionaler **String**-Parameter.  
  
   Gibt die verschiedenen Codeoptimierungen für Geschwindigkeit und Größe an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Disabled** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** - **/O2**  
  
  - **Full** - **/Ox**  
  
    Weitere Informationen finden Sie unter [/O-Optionen (Code optimieren)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Optionaler **String**-Parameter.  
  
   Erstellt oder verwendet eine vorkompilierte Headerdatei (PCH) während des Builds.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **NotUsing** - *\<none>*  
  
  - **Create** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    Weitere Informationen finden Sie unter [/Yc (Datei der vorkompilierten Header erstellen)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) und [/Yu (Vorkompilierte Headerdatei verwenden)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Siehe auch die Parameter **PrecompiledHeaderFile** und **PrecompiledHeaderOutputFile** in dieser Tabelle.  
  
- **PrecompiledHeaderFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt den Namen einer vorkompilierten Headerdatei an, die erstellt oder verwendet werden soll.  
  
   Weitere Informationen finden Sie unter [/Yc (Datei der vorkompilierten Header erstellen)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) und [/Yu (Vorkompilierte Headerdatei verwenden)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Optionaler **String**-Parameter.  
  
   Gibt einen Pfadnamen für einen vorkompilierten Header an, der anstelle des Standardpfadnamens verwendet wird.  
  
   Weitere Informationen finden Sie unter [/Fp (Name der PCH-Datei)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden Kommentare bei der Vorverarbeitung beibehalten.  
  
   Weitere Informationen finden Sie unter [/C (Kommentare bei der Vorverarbeitung beibehalten)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Optionaler `String[]` -Parameter.  
  
   Definiert ein Präprozessorsymbol für Ihre Quelldatei.  
  
   Weitere Informationen finden Sie unter [/D (Preprocessor Definitions)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Optionaler `ITaskItem[]` -Parameter.  
  
   Definiert ein Array von Präprozessorausgabeelementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
- **PreprocessOutputPath**  
  
   Optionaler `String` -Parameter.  
  
   Gibt den Namen der Ausgabedatei an, in die der **PreprocessToFile**-Parameter die vorverarbeitete Ausgabe schreibt.  
  
   Weitere Informationen finden Sie unter [/Fi (Ausgabedateiname vorverarbeiten)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden C- und C++-Quelldateien vorverarbeitet, und die vorverarbeiteten Dateien werden auf das Standardausgabegerät kopiert.  
  
   Weitere Informationen finden Sie unter [/EP (Vorverarbeitung an „stdout“ ohne #line-Direktiven)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden C- und C++-Quelldateien vorverarbeitet, und die vorverarbeitete Ausgabe wird in eine Datei geschrieben.  
  
   Weitere Informationen finden Sie unter [/P (Vorverarbeitung in eine Datei)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Optionaler `Integer`-Parameter.  
  
   Gibt die maximale Anzahl von Prozessoren an, die in einer Kompilierung mit mehreren Prozessoren verwendet werden. Verwenden Sie diesen Parameter in Kombination mit dem Parameter **MultiProcessorCompilation**.  
  
- **ProgramDataBaseFileName**  
  
   Optionaler `String` -Parameter.  
  
   Gibt einen Dateinamen für die Programmdatenbankdatei (PDB) an.  
  
   Weitere Informationen finden Sie unter [/Fd (Programmdatenbank-Dateiname)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Optionaler `String` -Parameter.  
  
   Zeigt an, ob es sich bei einem Multithread-Modul um eine DLL handelt, und wählt Veröffentlichungs- oder Debugversionen der Laufzeitbibliothek aus.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Weitere Informationen finden Sie unter [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird Code hinzugefügt, um C++-Objekttypen während der Laufzeit zu überprüfen (Laufzeit-Typeninformationen).  
  
   Weitere Informationen finden Sie unter [/GR (Laufzeit-Typeninformation aktivieren)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` gibt der Compiler eine Liste der Includedateien aus.  
  
   Weitere Informationen finden Sie unter [/showIncludes (Includedateien auflisten)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird ein Laufzeitfehler gemeldet, wenn ein Wert einem kleineren Datentyp zugewiesen wird und dies einen Datenverlust verursacht.  
  
   Weitere Informationen finden Sie unter der Option **/RTCc** in [/RTC (Laufzeitfehlerüberprüfungen)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Sources**  
  
   Erforderlicher `ITaskItem[]` -Parameter.  
  
   Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.  
  
- **StringPooling**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` kann der Compiler eine Kopie identischer Zeichenfolgen im Programmabbild erstellen.  
  
   Weitere Informationen finden Sie unter [/GF (Doppelte Zeichenfolgen beseitigen)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **StructMemberAlignment**  
  
   Optionaler `String` -Parameter.  
  
   Gibt die Byte-Ausrichtung für alle Member in einer Struktur an.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Weitere Informationen finden Sie unter [/Zp (Ausrichten des Strukturmembers)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
   Weitere Informationen finden Sie unter [/nologo (Startbanner unterdrücken) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Optionaler `String` -Parameter.  
  
   Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle für diese Aufgabe gespeichert sind.  
  
   Weitere Informationen finden Sie unter den Parametern **TLogReadFiles** und **TLogWriteFiles** in dieser Tabelle.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Optionaler **String[]**-Parameter.  
  
   Behandelt die angegebene Liste von Compilerwarnungen als Fehler.  
  
   Weitere Informationen finden Sie unter der Option **/we**`n` in [/w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Warnstufe)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden alle Compilerwarnungen als Fehler behandelt.  
  
   Weitere Informationen finden Sie unter der Option **/WX** in [/w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Warnstufe)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird der `wchar_t`-Typ als nativer Typ behandelt.  
  
   Weitere Informationen finden Sie unter[/Zc:wchar_t (wchar_t ist der systemeigene Typ)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Definition der Microsoft-spezifischen Symbole aufgehoben, die der Compiler definiert.  
  
   Weitere Informationen finden Sie unter der Option **/u** in [/U, /u (Symboldefinitionen aufheben)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Optionaler `String[]` -Parameter.  
  
   Gibt eine Liste mit einem oder mehreren Präprozessorsymbolen an, deren Definition aufgehoben werden soll.  
  
   Weitere Informationen finden Sie unter der Option **/U** in [/U, /u (Symboldefinitionen aufheben)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird der vollständige Pfad der Quellcodedateien angezeigt, die in der Diagnostik an den Compiler übergeben werden.  
  
   Weitere Informationen finden Sie unter [/FC (Vollständiger Pfad der Quellcodedatei in Diagnostik)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Ausgabedatei im UTF-8-Format erstellt.  
  
   Weitere Informationen finden Sie unter der Option **/FAu** in [/FA, /Fa (Listendatei)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **WarningLevel**  
  
   Optionaler `String` -Parameter.  
  
   Gibt die höchste Warnstufe an, die vom Compiler generiert werden soll.  
  
   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** - **/Wall**  
  
    Weitere Informationen finden Sie unter der Option **/W**_n_ in [/w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Warnstufe)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird die Optimierung des ganzen Programms aktiviert.  
  
   Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Optionaler `String` -Parameter.  
  
   Gibt den Namen der generierten XML-Dokumentationsdateien an. Bei diesem Parameter kann es sich um einen Datei- oder Verzeichnisnamen handeln.  
  
   Weitere Informationen finden Sie unter dem `name`-Argument in [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Beachten Sie auch den Parameter **GenerateXMLDocumentationFiles** in dieser Tabelle.  
  
- **MinimalRebuildFromTracking**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` wird ein nachverfolgter inkrementeller Build ausgeführt; bei `false` erfolgt eine Neuerstellung.  
  
- **TLogReadFiles**  
  
   Optionaler `ITaskItem[]` -Parameter.  
  
   Gibt ein Array von Elementen an, die die *Read-Datei-Nachverfolgungsprotokolle* darstellen.  
  
   Ein Read-Datei Nachverfolgungsprotokoll (TLOG) enthält die Namen der Eingabedateien, die von einer Aufgabe gelesen und vom Projektbuildsystem verwendet werden, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter den Parametern **TrackerLogDirectory** und **TrackFileAccess** in dieser Tabelle.  
  
- **TLogWriteFiles**  
  
   Optionaler `ITaskItem[]` -Parameter.  
  
   Gibt ein Array von Elementen an, die die *Write-Datei-Nachverfolgungsprotokolle* darstellen.  
  
   Ein Write-Datei-Nachverfolgungsprotokoll (TLOG) enthält die Namen der Ausgabedateien, die von einer Aufgabe geschrieben und vom Projektbuildsystem verwendet werden, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter den Parametern **TrackerLogDirectory** und **TrackFileAccess** in dieser Tabelle.  
  
- **TrackFileAccess**  
  
   Optionaler `Boolean` -Parameter.  
  
   Bei `true` werden Dateizugriffsmuster nachverfolgt.  
  
   Weitere Informationen finden Sie unter den Parametern **TLogReadFiles** und **TLogWriteFiles** in dieser Tabelle.  
  
## <a name="remarks"></a>Anmerkungen  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
