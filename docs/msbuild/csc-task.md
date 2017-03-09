---
title: "Csc-Aufgabe | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc-Aufgabe [MSBuild]"
  - "MSBuild Csc-Aufgabe"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Csc-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schließt CSC.exe und erzeugt ausführbare Dateien (.exe-Dateien), Dynamic Link Libraries (DLL-Dateien) und Codemodule (NETMODULE-Dateien). Weitere Informationen zu CSC.exe finden Sie unter [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Csc`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Optionaler `String[]` -Parameter.<br /><br /> Gibt zusätzliche Verzeichnisse an, in denen nach Verweisen gesucht wird. Weitere Informationen finden Sie unter [/lib (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Optionaler `String` -Parameter.<br /><br /> Gibt mindestens Modul an, das Bestandteil dieser Assembly sein soll. Weitere Informationen finden Sie unter [/addmodule (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, kompiliert Code, der die [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) Schlüsselwort. Weitere Informationen finden Sie unter [/ unsafe (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Optionaler `String` -Parameter.<br /><br /> Gibt die Konfigurationsdatei der Anwendung, die die bindungseinstellungen für die Assembly enthält.|  
|`BaseAddress`|Optionaler `String` -Parameter.<br /><br /> Gibt die bevorzugte Basisadresse an, unter der eine DLL geladen werden soll. Die Standard-Basisadresse für eine DLL-DATEI festgelegt ist, durch die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] common Language Runtime. Weitere Informationen finden Sie unter [/baseaddress (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Optionaler `Boolean` -Parameter.<br /><br /> Gibt an, ob Ganzzahlarithmetik, die die Grenzen des Datentyps führt zu einem Überlauf zur Laufzeit eine Ausnahme auslöst. Weitere Informationen finden Sie unter [/ checked (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Weitere Informationen finden Sie unter [/Codepage (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Optionaler `String` -Parameter.<br /><br /> Gibt den Debugtyp an. `DebugType` kann `full` oder `pdbonly`. Die Standardeinstellung ist `full`, die ermöglicht es dem Debugger ein ausgeführtes Programm zugeordnet werden soll. Angeben von `pdbonly` Quellcode ermöglicht, zu Codedebuggen, wenn das Programm im Debugger gestartet wird, aber nur Assembler angezeigt, wenn das ausgeführte Programm an den Debugger angefügt ist.<br /><br /> Dieser Parameter überschreibt die `EmitDebugInformation` Parameter.<br /><br /> Weitere Informationen finden Sie unter [/Debug (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Optionaler `String` -Parameter.<br /><br /> Definiert Präprozessorsymbole. Weitere Informationen finden Sie unter [/ define (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, gibt an, dass eine Assembly vollständig signiert werden soll. Wenn `false`, gibt an, dass Sie nur den öffentlichen Schlüssel in die Assembly einfügen möchten.<br /><br /> Dieser Parameter hat keine Auswirkung, wenn Sie entweder mit der `KeyFile` oder `KeyContainer` Parameter.<br /><br /> Weitere Informationen finden Sie unter [/delaysign (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Optionaler `String` -Parameter.<br /><br /> Gibt die Liste der Warnungen deaktiviert werden soll. Weitere Informationen finden Sie unter [/nowarn (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Optionaler `String` -Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu einer XML-Datei. Weitere Informationen finden Sie unter [/doc (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, die Aufgabe generiert Debuginformationen und platziert sie in eine Programmdatenbankdatei (.pdb). Wenn `false`, die Aufgabe gibt keine Debuginformationen. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [/Debug (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Optionaler `String` -Parameter.<br /><br /> Bietet eine einfache Möglichkeit, einen internen C#-Fehler an Microsoft gemeldet. Dieser Parameter kann den Wert des haben `prompt`, `send`, oder `none`. Wenn der Parameter, um festgelegt ist `prompt`, Sie werden aufgefordert, wenn ein interner Compilerfehler auftritt. Die Aufforderung können Sie einen Fehlerbericht elektronisch an Microsoft senden. Wenn der Parameter, um festgelegt ist `send`, wird automatisch ein Problembericht gesendet. Wenn der Parameter, um festgelegt ist `none`, wird der Fehler nur in der Textausgabe des Compilers gemeldet. Der Standardwert ist `none`. Weitere Informationen finden Sie unter [/errorreport (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Größe der Abschnitte in der Ausgabedatei an. Weitere Informationen finden Sie unter [/filealign (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, gibt den absoluten Pfad zur Datei in der Compilerausgabe an. Wenn `false`, gibt den Namen der Datei. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [/fullpaths (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen des kryptografischen Schlüsselcontainers an. Weitere Informationen finden Sie unter [/keycontainer (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Optionaler `String` -Parameter.<br /><br /> Gibt den Dateinamen mit dem kryptografischen Schlüssel an. Weitere Informationen finden Sie unter [/keyfile (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Optionaler `String` -Parameter.<br /><br /> Gibt die Version der zu verwendenden Sprache an. Weitere Informationen finden Sie unter [/langversion (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Optionale <xref:Microsoft.Build.Framework.ITaskItem>`[]` Parameter.<br /><br /> Erstellt einen Link zu einer [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ressource in der Ausgabedatei die Ressourcendatei befindet sich nicht in der Ausgabedatei.<br /><br /> Elemente, die an diesen Parameter übergebenen können optionale Metadaten-Einträge, die mit dem Namen `LogicalName` und `Access`. `LogicalName` entspricht der `identifier` Parameter von der `/linkresource` zu wechseln und `Access` entspricht `accessibility-modifier` Parameter. Weitere Informationen finden Sie unter [/linkresource (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Optionaler `String` -Parameter.<br /><br /> Gibt den Speicherort der `Main` Methode. Weitere Informationen finden Sie unter [/Main (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen der Assembly, der dieses Modul gehören wird.|  
|`NoConfig`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, weist den Compiler an, nicht mit der Datei csc.rsp zu kompilieren. Weitere Informationen finden Sie unter [/noconfig (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, unterdrückt die Anzeige der Compilerbannerinformationen. Weitere Informationen finden Sie unter [/nologo (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, verhindert den Import der Datei mscorlib.dll, die den gesamten System-Namespace definiert. Verwenden Sie diesen Parameter, wenn Sie Ihren eigenen System-Namespace und Objekte definieren oder erstellen möchten. Weitere Informationen finden Sie unter [/nostdlib (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, schließen Sie nicht das Standard-Win32-Manifest.|  
|`Optimize`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, Optimierungen aktiviert. Wenn `false`, deaktiviert Optimierungen. Weitere Informationen finden Sie unter [/ optimize (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an. Weitere Informationen finden Sie unter [/out (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Optionaler `String` -Parameter.<br /><br /> Gibt den Dateinamen der Debug-Informationen. Der Standardname ist der Ausgabedateiname mit .pdb-Erweiterung.|  
|`Platform`|Optionaler `String` -Parameter.<br /><br /> Gibt die Prozessorplattform an, die das Ziel der Ausgabedatei darstellen soll. Dieser Parameter kann den Wert des haben `x86`, `x64`, oder `anycpu`. Der Standardwert ist `anycpu`. Weitere Informationen finden Sie unter [/Platform (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Optionale <xref:Microsoft.Build.Framework.ITaskItem>`[]` Parameter.<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen aus den angegebenen Elementen im aktuellen Projekt zu importieren. Weitere Informationen finden Sie unter [/Reference (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Sie können angeben, eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Verweisalias in eine [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Datei, indem Sie die Metadaten hinzufügen `Aliases` auf dem ursprünglichen Element "Verweis". Geben Sie beispielsweise Folgendes ein, um den Alias "LS1" in der folgenden CSC-Befehlszeile festlegen:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Verwenden Sie:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Optionale <xref:Microsoft.Build.Framework.ITaskItem>`[]` Parameter.<br /><br /> Bettet eine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ressource in die Ausgabedatei.<br /><br /> Elemente, die an diesen Parameter übergebenen können optionale Metadaten-Einträge, die mit dem Namen `LogicalName` und `Access`. `LogicalName` entspricht der `identifier` Parameter von der `/resource` zu wechseln und `Access` entspricht `accessibility-modifier` Parameter. Weitere Informationen finden Sie unter [/Resource (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Optionaler `String` -Parameter.<br /><br /> Gibt die Antwortdatei an, die Befehle für diese Aufgabe enthält. Weitere Informationen finden Sie unter [@ (Antwortdatei festlegen)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Optionale <xref:Microsoft.Build.Framework.ITaskItem>`[]` Parameter.<br /><br /> Gibt ein oder mehrere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Quelldateien.|  
|`TargetType`|Optionaler `String` -Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann den Wert aufweisen `library`, erstellt eine Codebibliothek `exe`, erstellt eine Konsolenanwendung, `module`, ein Modul erstellt oder `winexe`, dem ein Windows-Programm erstellt. Der Standardwert ist `library`. Weitere Informationen finden Sie unter [/target (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, alle Warnungen als Fehler behandelt. Weitere Informationen finden Sie unter [/warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Optionaler `Boolean` -Parameter.<br /><br /> Weist die Aufgabe, das prozessinterne Compilerobjekt zu verwenden, falls verfügbar. Verwendet nur von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Optionaler `Boolean` -Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF-8-Codierung. Weitere Informationen finden Sie unter [/utf8output (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Warnstufe für den Compiler an. Weitere Informationen finden Sie unter [/ warn (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Optionaler `String` -Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Dieser Parameter überschreibt die `TreatWarningsAsErrors` Parameter.|  
|`WarningsNotAsErrors`|Optionaler `String` -Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Dieser Parameter ist nur nützlich, wenn die `TreatWarningsAsErrors` Parameter den Wert `true`.|  
|`Win32Icon`|Optionaler `String` -Parameter.<br /><br /> Fügt eine ICO-Datei in der Assembly, wodurch der Ausgabedatei in Datei-Explorer das gewünschte Aussehen. Weitere Informationen finden Sie unter [/win32icon (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Optionaler `String` -Parameter.<br /><br /> Gibt das Win32-Manifest eingeschlossen werden sollen.|  
|`Win32Resource`|Optionaler `String` -Parameter.<br /><br /> Fügt eine Win32-Ressourcendatei (. res) in die Ausgabedatei ein. Weitere Informationen finden Sie unter [/win32res (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der `Microsoft.Build.Tasks.ManagedCompiler` -Klasse, die von erbt die <xref:Microsoft.Build.Tasks.ToolTaskExtension> Klasse, die selbst erbt von der <xref:Microsoft.Build.Utilities.ToolTask> Klasse. Eine Übersicht über diese zusätzlichen Parameter und deren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `Csc` Aufgabe zum Kompilieren Sie einer ausführbare Datei aus der Quelldateien in der `Compile` Auflistung.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)