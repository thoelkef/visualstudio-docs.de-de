---
title: "CL-Aufgabe | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing"
  - "vc.task.cl"
  - "VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors"
  - "VC.Project.VCCLCompilerTool.CreateHotpatchableImage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (Visual C++) CL-Aufgabe"
  - "CL-Aufgabe (MSBuild (Visual C++))"
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CL-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das Visual C++-Compilertool cl.exe. Der Compiler generiert ausführbare Dateien (.exe), Dynamic Link Library (DLL)-Dateien oder Code-Moduldateien (NETMODULE-Dateien). Weitere Informationen finden Sie unter [Compileroptionen](/visual-cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parameter  
 Die folgende Tabelle beschreibt die Parameter der **CL** Aufgabe. Die meisten Aufgabenparameter und einige Sätze von Parametern entsprechen einer Befehlszeilenoption.  
  
-   **AdditionalIncludeDirectories**  
  
     Optionaler String []-Parameter.  
  
     Fügt ein Verzeichnis zur Liste der Verzeichnisse, die nach Includedateien durchsucht werden.  
  
     Weitere Informationen finden Sie unter [/i (Zusätzliche Includeverzeichnisse)](/visual-cpp/build/reference/i-additional-include-directories).  
  
-   **AdditionalOptions**  
  
     Optionaler String-Parameter.  
  
     Eine Liste der Befehlszeilenoptionen. Z. B. "/*option1* /*option2* /*Option-*". Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht von einem beliebigen anderen Aufgabenparameter dargestellt werden.  
  
     Weitere Informationen finden Sie unter [Compileroptionen](/visual-cpp/build/reference/compiler-options).  
  
-   **AdditionalUsingDirectories**Optionaler String []-Parameter.  
  
     Gibt das Verzeichnis an, die der Compiler durchsucht, um Dateiverweise auf aufzulösen der **#using** Richtlinie.  
  
     Weitere Informationen finden Sie unter [/AI (Metadatenverzeichnisse festlegen)](/visual-cpp/build/reference/ai-specify-metadata-directories).  
  
-   **AlwaysAppend**  
  
     Optionaler String-Parameter.  
  
     Eine Zeichenfolge, ruft, die immer in der Befehlszeile ausgegeben. Der Standardwert ist "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Erstellt eine Listendatei, die Assemblycode enthält.  
  
     Weitere Informationen finden Sie unter der **/FA** option [/FA, / FA (Listing File)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **AssemblerOutput**  
  
     Optionaler String-Parameter.  
  
     Erstellt eine Listendatei, die Assemblycode enthält.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NoListing** - *\< none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndSourceCode** - **Angabe von/FAS**  
  
    -   **Alle** - **/FAcs**  
  
     Weitere Informationen finden Sie unter der **/FA**, **/FAc**, **Angabe von/FAS**, und **/FAcs** Optionen in [/FA, / FA (Listing File)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **BasicRuntimeChecks**  
  
     Optionaler String-Parameter.  
  
     Aktiviert und deaktiviert die Laufzeitfehler-Überprüfungen-Funktion in Verbindung mit der [Runtime_checks](/visual-cpp/preprocessor/runtime-checks) Pragma.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard-** -                          *\< none>*  
  
    -   **StackFrameRuntimeCheck** - **RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     Weitere Informationen finden Sie unter [/RTC (Run-Time Error Checks)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **BrowseInformation**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, wird eine Browserinformationsdatei erstellt.  
  
     Weitere Informationen finden Sie unter der **/FR** option [/fr, / FR (erstellen. SBR-Datei)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BrowseInformationFile**  
  
     Optionaler String-Parameter.  
  
     Gibt einen Namen für die Browserinformationsdatei an.  
  
     Weitere Informationen finden Sie unter der **BrowseInformation** Parameter in dieser Tabelle und unter [/fr, / FR (erstellen. SBR-Datei)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BufferSecurityCheck**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, erkennt einige Pufferüberläufe, die die Rückgabeadresse, ein gängiges Verfahren zur Nutzung von Code, der keine puffergrößeneinschränkungen.  
  
     Weitere Informationen finden Sie unter [/GS (Puffersicherheitsprüfung)](/visual-cpp/build/reference/gs-buffer-security-check).  
  
-   **BuildingInIDE**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, gibt an, dass **MSBuild** wird von der IDE aufgerufen. Andernfalls **MSBuild** in der Befehlszeile aufgerufen wird.  
  
-   **CallingConvention**  
  
     Optionaler String-Parameter.  
  
     Gibt die Aufrufkonvention, die die Reihenfolge bestimmt, in welche, die Funktion Argumente auf dem Stapel abgelegt werden, ob die aufrufende oder die aufgerufene Funktion die Argumente am Ende des Aufrufs aus dem Stapel entfernt, und die Namensergänzungskonvention der Compiler, die zur Erkennung einzelner Funktionen verwendet.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Cdecl** - **/gd**  
  
    -   **FastCall** -                          **/GR**  
  
    -   **StdCall** -                          **/GZ**  
  
     Weitere Informationen finden Sie unter [/gd, / Gr, / GV, / GZ (Aufrufkonvention)](/visual-cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
-   **CompileAs**  
  
     Optionaler String-Parameter.  
  
     Gibt an, ob die Eingabedatei als C- oder C++-Quelldatei kompiliert wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard-** - *\< none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Weitere Informationen finden Sie unter [/TC, / TP, / TC, / TP (Typ der Quelldatei angeben)](/visual-cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
-   **CompileAsManaged**  
  
     Optionaler String-Parameter.  
  
     Ermöglicht Anwendungen und Komponenten, Funktionen aus der Common Language Runtime (CLR) zu verwenden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **false** - *\< none>*  
  
    -   **True,** - **/CLR**  
  
    -   **Reine** - **/clr: pure**  
  
    -   **Sichere** - **/clr: safe**  
  
    -   **OldSyntax** - **/clr: oldSyntax**  
  
     Weitere Informationen finden Sie unter [/clr (Common Language Runtime Compilation)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
-   **CreateHotpatchableImage**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, weist den Compiler zum Vorbereiten eines Abbilds für *HotPatching*. Dieser Parameter wird sichergestellt, dass die erste Anweisung jeder Funktion zwei Bytes, die für HotPatching erforderlich ist.  
  
     Weitere Informationen finden Sie unter [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
-   **DebugInformationFormat**  
  
     Optionaler String-Parameter.  
  
     Wählt den Typ der Debuginformationen für das Programm, und ob diese Informationen in Objektdateien (.obj) oder in einer Programmdatenbank (PDB) gespeichert werden erstellt.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Veraltete** - **"/ Z7"**  
  
    -   **ProgramDatabase** - **/Zi**  
  
    -   **EditAndContinue** - **/Zi**  
  
     Weitere Informationen finden Sie unter [/Z7, / Zi, / Zi (Debuginformationsformat)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).  
  
-   **DisableLanguageExtensions**  
  
     Optionaler boolescher Parameter.  
  
     Wenn **true**, teilt dem Compiler, einen Fehler für Sprachkonstrukte auszugeben, die nicht mit ANSI C- und ANSI C++ kompatibel sind.  
  
     Weitere Informationen finden Sie unter der **/Za** option [/Za, / Ze (Spracherweiterungen deaktivieren)](/visual-cpp/build/reference/za-ze-disable-language-extensions).  
  
-   **DisableSpecificWarnings**  
  
     Optionaler String []-Parameter.  
  
     Deaktiviert die warnungszahlen, die in einer durch Semikolons getrennten Liste angegeben werden.  
  
     Weitere Informationen finden Sie unter der `/wd` option [/w, / W0, /W1, /W2, /W3, "/ W4", /w1, /w2, /w3, "/ W4", / Wall, / WD, / wir, /, wo WV, / WX (Warnstufe)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **EnableEnhancedInstructionSet**  
  
     Optionaler String-Parameter.  
  
     Gibt die Architektur für die Generierung von Code, das Streaming SIMD Extensions (SSE) und Streaming SIMD Extensions 2 (SSE2)-Anweisungen enthält.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **StreamingSIMDExtensions** - **neben**  
  
    -   **StreamingSIMDExtensions2** - **/arch: SSE2**  
  
     Weitere Informationen finden Sie unter [/arch (x86)](/visual-cpp/build/reference/arch-x86).  
  
-   **EnableFiberSafeOptimizations**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, unterstützt Fiber-Sicherheit für Daten, die mithilfe statischer lokaler Threadspeicher, d. h. Daten, die mithilfe von `__declspec(thread)`.  
  
     Weitere Informationen finden Sie unter [/gt (Fiber-sicheren lokalen Thread-Speicher unterstützen)](/visual-cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
-   **EnablePREfast**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, aktiviert die Codeanalyse.  
  
     Weitere Informationen finden Sie unter [/ analyze (Codeanalyse)](/visual-cpp/build/reference/analyze-code-analysis).  
  
-   **ErrorReporting**  
  
     Optionaler String-Parameter.  
  
     Sie können Informationen interner Compilerfehler (ICE) direkt an Microsoft zu senden. Standardmäßig ist die Einstellung in IDE-Builds **Prompt** und die Einstellung in Befehlszeilenbuilds **Warteschlange**.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Keine** - **/errorreport: none**  
  
    -   **Aufforderung** - **Absturzinformationen**  
  
    -   **Warteschlange** - **/errorReport:queue**  
  
    -   **Senden von** - **/errorreport: Send**  
  
     Weitere Informationen finden Sie unter [/errorreport (Report Internal Compiler Errors)](/visual-cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
-   **ExceptionHandling**  
  
     Optionaler String-Parameter.  
  
     Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **false** - *\< none>*  
  
    -   **Asynchrone** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     Weitere Informationen finden Sie unter [/EH (Exception Handling Model)](/visual-cpp/build/reference/eh-exception-handling-model).  
  
-   **ExpandAttributedSource**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, erstellt eine Listendatei, die in die Quelldatei eingefügten Attributen erweitert wurde.  
  
     Weitere Informationen finden Sie unter [/FX (eingefügten Code zusammenführen)](/visual-cpp/build/reference/fx-merge-injected-code).  
  
-   **FavorSizeOrSpeed**  
  
     Optionaler String-Parameter.  
  
     Gibt an, ob Code Codegröße oder-Geschwindigkeit vorgezogen.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Weder** - *\< none>*  
  
    -   **Größe** - **/OS**  
  
    -   **Geschwindigkeit** - **/Ot**  
  
     Weitere Informationen finden Sie unter [/OS, / Ot (kompakten Code bevorzugen, schnellen Code bevorzugen)](/visual-cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
-   **FloatingPointExceptions**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, ermöglicht die zuverlässige Gleitkomma-Ausnahmemodell. Ausnahmen werden sofort ausgelöst, wenn sie auftreten.  
  
     Weitere Informationen finden Sie unter der /**fp: außer** option [/fp (Specify Floating-Point Behavior)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **FloatingPointModel**  
  
     Optionaler String-Parameter.  
  
     Legt das Gleitkommamodell fest Point-Modell.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Genaue** - **/fp: präzise**  
  
    -   **Strenge** - **/fp: strict**  
  
    -   **Schnelle** - **/fp: fast**  
  
     Weitere Informationen finden Sie unter [/fp (Specify Floating-Point Behavior)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **ForceConformanceInForLoopScope**  
  
     Optionaler boolescher Parameter.  
  
     Wenn `true`, implementiert der Standard-c++-Verhalten in [für](/visual-cpp/cpp/for-statement-cpp) Schleifen, die Microsoft-Erweiterungen verwenden ([/Ze](/visual-cpp/build/reference/za-ze-disable-language-extensions)).  
  
     Weitere Informationen finden Sie unter [/Zc: forScope (Übereinstimmung in for-Schleifenbereich erzwingen)](../Topic/-Zc:forScope%20\(Force%20Conformance%20in%20for%20Loop%20Scope\).md).  
  
-   **ForcedIncludeFiles**  
  
     Optionaler `String[]` -Parameter.  
  
     Weist den Präprozessor an, um eine oder mehrere angegebene Header-Dateien zu verarbeiten.  
  
     Weitere Informationen finden Sie unter [/Fi (Name Forced Include File)](/visual-cpp/build/reference/fi-name-forced-include-file).  
  
-   **ForcedUsingFiles**  
  
     Optionale **String []** Parameter.  
  
     Weist den Präprozessor Verarbeitung einer präziseren **#using** Dateien.  
  
     Weitere Informationen finden Sie unter [/FU (Name Forced #using-Datei)](/visual-cpp/build/reference/fu-name-forced-hash-using-file).  
  
-   **FunctionLevelLinking**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, kann der Compiler einzelne Funktionen in Form von Paketfunktionen (COMDATs).  
  
     Weitere Informationen finden Sie unter [/Gy (Funktionslevel Linking aktivieren)](/visual-cpp/build/reference/gy-enable-function-level-linking).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, verarbeitet der Compiler Kommentare in Quellcodedateien, und erstellen Sie eine XDC-Datei für jede Quelle Codedatei, die, Ursachen von Dokumentationskommentaren.  
  
     Weitere Informationen finden Sie unter [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Siehe auch die **XMLDocumentationFileName** -Parameter in dieser Tabelle.  
  
-   **IgnoreStandardIncludePath**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, verhindert, dass den Compiler für Includedateien in PATH und INCLUDE-Umgebungsvariablen angegebenen Verzeichnisse durchsucht.  
  
     Weitere Informationen finden Sie unter [/x (Ignore Standard Include Paths)](/visual-cpp/build/reference/x-ignore-standard-include-paths).  
  
-   **InlineFunctionExpansion**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Ebene der Inlinefunktionserweiterung für den Build.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard-** - *\< none>*  
  
    -   **Deaktivierte** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **"/ Ob1"**  
  
    -   **AnySuitable** - **Ob2**  
  
     Weitere Informationen finden Sie unter [/ob (Inline Function Expansion)](/visual-cpp/build/reference/ob-inline-function-expansion).  
  
-   **IntrinsicFunctions**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, ersetzt Sie einige Funktionsaufrufe mit systeminternen oder andernfalls besondere Formen der Funktion, mit denen Ihre Anwendung schneller ausgeführt.  
  
     Weitere Informationen finden Sie unter [/Oi (systeminterne Funktionen erstellen)](/visual-cpp/build/reference/oi-generate-intrinsic-functions).  
  
-   **MinimalRebuild**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, ermöglicht, die minimale Neuerstellung, die bestimmt, ob die C++-Quelldateien, die geänderte C++ enthalten Definitionen (gespeichert in Headerdateien (. h))-Klasse neu kompiliert werden muss.  
  
     Weitere Informationen finden Sie unter [/GM (minimale Neuerstellung aktivieren)](/visual-cpp/build/reference/gm-enable-minimal-rebuild).  
  
-   **MultiProcessorCompilation**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, mehrere Prozessoren verwenden, um zu kompilieren. Dieser Parameter erstellt einen Prozess für jeden effektiven Prozessor auf dem Computer.  
  
     Weitere Informationen finden Sie unter [/MP (erstellen mit mehreren Prozessen)](/visual-cpp/build/reference/mp-build-with-multiple-processes). Siehe auch die **ProcessorNumber** -Parameter in dieser Tabelle.  
  
-   **ObjectFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt einen Name der Objektdatei (obj) oder das Verzeichnis, das anstelle des Standardwerts verwendet werden.  
  
     Weitere Informationen finden Sie unter [/fo (Name der Objektdatei)](/visual-cpp/build/reference/fo-object-file-name).  
  
-   **ObjectFiles**  
  
     Optionale **String []** Parameter.  
  
     Eine Liste von Objektdateien.  
  
-   **OmitDefaultLibName**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, wird der Name für die Laufzeitbibliothek von C in der Objektdatei (obj). Standardmäßig legt der Compiler den Namen der Bibliothek in der OBJ-Datei an den Linker zur richtigen Bibliothek zu leiten.  
  
     Weitere Informationen finden Sie unter [/Zl (Omit Default Library Name)](/visual-cpp/build/reference/zl-omit-default-library-name).  
  
-   **OmitFramePointers**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, unterdrückt die Erstellung von Framezeigern in der Aufrufliste.  
  
     Weitere Informationen finden Sie unter [/Oy (Framezeiger unterdrücken)](/visual-cpp/build/reference/oy-frame-pointer-omission).  
  
-   **OpenMPSupport**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, generiert der Compiler OpenMP-Klauseln und Direktiven.  
  
     Weitere Informationen finden Sie unter [/OpenMP (Aktivieren der OpenMP 2.0-Unterstützung)](/visual-cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
-   **Optimierung**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die verschiedenen codeoptimierungen für Geschwindigkeit und Größe.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Deaktivierte** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Vollständige** - **/Ox**  
  
     Weitere Informationen finden Sie unter [/o-Optionen (Code optimieren)](/visual-cpp/build/reference/o-options-optimize-code).  
  
-   **PrecompiledHeader**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Erstellen oder Verwenden einer vorkompilierten Headerdatei (.pch) während des Builds.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **NOTlogische** - *\< none>*  
  
    -   **Erstellen Sie** - **/Yc**  
  
    -   **Verwendung** - **"/ Yu"**  
  
     Weitere Informationen finden Sie unter [/Yc (Datei der vorkompilierte Header erstellen)](/visual-cpp/build/reference/yc-create-precompiled-header-file) und [/Yu (vorkompilierte Headerdatei verwenden)](/visual-cpp/build/reference/yu-use-precompiled-header-file). Siehe auch die **PrecompiledHeaderFile** und **PrecompiledHeaderOutputFile** Parameter in dieser Tabelle.  
  
-   **PrecompiledHeaderFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Namen einer vorkompilierten Headerdatei erstellen oder verwenden.  
  
     Weitere Informationen finden Sie unter [/Yc (Datei der vorkompilierte Header erstellen)](/visual-cpp/build/reference/yc-create-precompiled-header-file) und [/Yu (vorkompilierte Headerdatei verwenden)](/visual-cpp/build/reference/yu-use-precompiled-header-file).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt einen Pfadnamen für einen vorkompilierten Header statt der Standard-Pfadname.  
  
     Weitere Informationen finden Sie unter [/fp (Name. PCH-Datei)](/visual-cpp/build/reference/fp-name-dot-pch-file).  
  
-   **PreprocessKeepComments**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, behält Kommentare beim Präprozessorlauf bei.  
  
     Weitere Informationen finden Sie unter [/c (beibehalten Kommentare beim Präprozessorlauf)](/visual-cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
-   **PreprocessorDefinitions**  
  
     Optionaler `String[]` -Parameter.  
  
     Definiert ein Vorverarbeitungssymbol für die Quelldatei an.  
  
     Weitere Informationen finden Sie unter [/D (Preprocessor Definitions)](/visual-cpp/build/reference/d-preprocessor-definitions).  
  
-   **PreprocessOutput**  
  
     Optionaler `ITaskItem[]`-Parameter.  
  
     Definiert ein Array, der Präprozessorausgabe-Elemente, die genutzt und Aufgaben ausgegeben werden können.  
  
-   **PreprocessOutputPath**  
  
     Optionaler `String` -Parameter.  
  
     Gibt den Namen der Ausgabedatei an, die die **PreprocessToFile** Parameter vorverarbeitete Ausgabe schreibt.  
  
     Weitere Informationen finden Sie unter [/Fi (Ausgabedateiname vorverarbeiten)](/visual-cpp/build/reference/fi-preprocess-output-file-name).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, C- und C++-Quelldateien vorverarbeitet und die vorverarbeiteten Dateien an das Standardausgabegerät.  
  
     Weitere Informationen finden Sie unter [/EP (Vorverarbeitung an "stdout" ohne #line-Direktiven)](/visual-cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
-   **PreprocessToFile**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, C- und C++-Quelldateien vorverarbeitet und die vorverarbeitete Ausgabe in eine Datei geschrieben.  
  
     Weitere Informationen finden Sie unter [/p (Vorverarbeitung in eine Datei)](/visual-cpp/build/reference/p-preprocess-to-a-file).  
  
-   **ProcessorNumber**  
  
     Optionaler `Integer`-Parameter.  
  
     Gibt die maximale Anzahl von Prozessoren in einer Kompilierung mit mehreren Prozessoren verwendet. Verwenden Sie diesen Parameter in Kombination mit der **MultiProcessorCompilation** Parameter.  
  
-   **ProgramDataBaseFileName**  
  
     Optionaler `String` -Parameter.  
  
     Gibt einen Dateinamen für die Programmdatenbankdatei (PDB).  
  
     Weitere Informationen finden Sie unter [/Fd (Programmdatenbank-Dateiname)](/visual-cpp/build/reference/fd-program-database-file-name).  
  
-   **RuntimeLibrary**  
  
     Optionaler `String` -Parameter.  
  
     Gibt an, ob eine Multithread-Modul eine DLL ist, und wählt von Retail oder Debug Versionen der Laufzeit-Bibliothek.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     Weitere Informationen finden Sie unter [/MD, / MT, / ld (Laufzeitbibliothek verwenden)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library).  
  
-   **RuntimeTypeInfo**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, wird Code zum Überprüfen von C++-Objekttypen zur Laufzeit (Laufzeit Typinformationen) hinzugefügt.  
  
     Weitere Informationen finden Sie unter [/GR (Enable Run-Time Type Information)](/visual-cpp/build/reference/gr-enable-run-time-type-information).  
  
-   **ShowIncludes**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, generiert der Compiler eine Liste der Includedateien auszugeben.  
  
     Weitere Informationen finden Sie unter [/showIncludes (Includedateien auflisten)](/visual-cpp/build/reference/showincludes-list-include-files).  
  
-   **SmallerTypeCheck**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, meldet einen Laufzeitfehler, wenn ein Wert einem kleineren Datentyp zugewiesen wird und einen Datenverlust verursacht.  
  
     Weitere Informationen finden Sie unter der **nach sich zieht** option [/RTC (Run-Time Error Checks)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **Datenquellen**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.  
  
-   **StringPooling**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, kann der Compiler eine Kopie identischer Zeichenfolgen im Programmimage erstellen.  
  
     Weitere Informationen finden Sie unter [/GF (Doppelte Zeichenfolgen beseitigen)](/visual-cpp/build/reference/gf-eliminate-duplicate-strings).  
  
-   **StructMemberAlignment**  
  
     Optionaler `String` -Parameter.  
  
     Gibt die Byte-Ausrichtung für alle Elemente in einer Struktur an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **Standard-** - **/Zp1**  
  
    -   **1 Byte** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **Option/Zp4**  
  
    -   **8Bytes** - **"/ zp8"**  
  
    -   **16Bytes** - **/Zp16**  
  
     Weitere Informationen finden Sie unter [/Zp (Ausrichten des Strukturmembers)](/visual-cpp/build/reference/zp-struct-member-alignment).  
  
-   **SuppressStartupBanner**  
  
     Optionaler `Boolean` -Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
     Weitere Informationen finden Sie unter [/nologo (Startbanner unterdrücken) (C/C++)](/visual-cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
-   **TrackerLogDirectory**  
  
     Optionaler `String` -Parameter.  
  
     Gibt das temporäre Verzeichnis, in dem Nachverfolgungsprotokolle für diese Aufgabe gespeichert werden.  
  
     Weitere Informationen finden Sie unter der **TLogReadFiles** und **TLogWriteFiles** Parameter in dieser Tabelle.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Optionale **String []** Parameter.  
  
     Die angegebene Liste von Compiler-Warnungen behandelt als Fehler.  
  
     Weitere Informationen finden Sie unter der **/we**`n` option [/w, / W0, /W1, /W2, /W3, "/ W4", /w1, /w2, /w3, "/ W4", / Wall, / WD, / wir, /, wo WV, / WX (Warnstufe)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWarningAsError**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, alle Compiler-Warnungen als Fehler behandeln.  
  
     Weitere Informationen finden Sie unter **/WX** option [/w, / W0, /W1, /W2, /W3, "/ W4", /w1, /w2, /w3, "/ W4", / Wall, / WD, / wir, /, wo WV, / WX (Warnstufe)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, behandelt der `wchar_t` einen systemeigenen Typ.  
  
     Weitere Informationen finden Sie unter [/Zc: wchar_t (Wchar_t ist der systemeigene Typ)](../Topic/-Zc:wchar_t%20\(wchar_t%20Is%20Native%20Type\).md).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, hebt die Definition der Microsoft-spezifische Symbole, die der Compiler definiert.  
  
     Weitere Informationen finden Sie unter der **/u** option [/u, / u (Symboldefinitionen aufheben Symbole)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Optionaler `String[]` -Parameter.  
  
     Gibt eine Liste von ein oder mehrere Präprozessorsymbole, heben Sie die Definition.  
  
     Weitere Informationen finden Sie unter **/u** option [/u, / u (Symboldefinitionen aufheben Symbole)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UseFullPaths**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, zeigt der vollständige Pfad der Quellcodedateien an den Compiler bei der Diagnose übergeben.  
  
     Weitere Informationen finden Sie unter [/FC (vollständiger Pfad der Quellcodedatei in Diagnose)](/visual-cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, wird die Ausgabedatei im UTF-8-Format erstellt werden.  
  
     Weitere Informationen finden Sie unter der **/FAu für** option [/FA, / FA (Listing File)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **WarningLevel**  
  
     Optionaler `String` -Parameter.  
  
     Gibt die höchste Ebene der Warnung, die vom Compiler generiert werden soll.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **"Level4"** - **"/ W4"**  
  
    -   **EnableAllWarnings** - **/Wall**  
  
     Weitere Informationen finden Sie unter der **/w***n* option [/w, / W0, /W1, /W2, /W3, "/ W4", /w1, /w2, /w3, "/ W4", / Wall, / WD, / wir, /, wo WV, / WX (Warnstufe)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **WholeProgramOptimization**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, aktiviert die Optimierung des ganzen Programms.  
  
     Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](/visual-cpp/build/reference/gl-whole-program-optimization).  
  
-   **XMLDocumentationFileName**  
  
     Optionaler `String` -Parameter.  
  
     Gibt den Namen des generierten XML-Dokumentationsdateien an. Dieser Parameter kann einen Datei- oder Verzeichnisnamens sein.  
  
     Weitere Informationen finden Sie unter der `name` -Argument in [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Siehe auch die **GenerateXMLDocumentationFiles** -Parameter in dieser Tabelle.  
  
-   **MinimalRebuildFromTracking**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, ein nachverfolgter inkrementeller Build ausgeführt wird, wenn `false`, eine Wiederherstellung erfolgt.  
  
-   **TLogReadFiles**  
  
     Optionaler `ITaskItem[]`-Parameter.  
  
     Gibt ein Array von Elementen, darstellen, die *-Datei Verfolgungsprotokolle*.  
  
     Read-Datei Nachverfolgungsprotokolls (.tlog) enthält die Namen der Eingabedateien, die durch eine Aufgabe gelesen werden und werden vom Projektsystem Build verwendet, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter der **TrackerLogDirectory** und **TrackFileAccess** Parameter in dieser Tabelle.  
  
-   **TLogWriteFiles**  
  
     Optionaler `ITaskItem[]`-Parameter.  
  
     Gibt ein Array von Elementen, darstellen, die *Datei Verfolgungsprotokolle schreiben*.  
  
     Write-Datei Nachverfolgungsprotokolls (.tlog) enthält die Namen der Ausgabedateien, die durch eine Aufgabe geschrieben werden, und werden durch das Projekt-Buildsystem verwendet, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter der **TrackerLogDirectory** und **TrackFileAccess** Parameter in dieser Tabelle.  
  
-   **TrackFileAccess**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, Zugriffsmuster der Datei nachverfolgt.  
  
     Weitere Informationen finden Sie unter der **TLogReadFiles** und **TLogWriteFiles** Parameter in dieser Tabelle.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)