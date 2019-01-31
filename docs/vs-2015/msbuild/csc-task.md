---
title: Csc-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3cab96aece51252c5a847e07fc3863e6b6f0bf5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766188"
---
# <a name="csc-task"></a>Csc-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umschließt CSC.exe und erzeugt ausführbare Dateien (EXE-Dateien), Dynamic Link Libraries (DLL-Dateien) und Codemodule (NETMODULE-Dateien). Weitere Informationen zu CSC.exe finden Sie unter [C# Compiler Options (C#-Compileroptionen)](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Csc` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Optionaler `String[]` -Parameter.<br /><br /> Gibt zusätzliche Verzeichnisse an, in denen nach Verweisen gesucht wird. Weitere Informationen finden Sie unter [/lib (C# Compiler Options)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Optionaler `String` -Parameter.<br /><br /> Gibt mindestens Modul an, das Bestandteil dieser Assembly sein soll. Weitere Informationen finden Sie unter [/addmodule (C# Compiler Options)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Optionaler `Boolean` -Parameter.<br /><br /> Ist der Wert `true`, wird Code kompiliert, der das[unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0)-Schlüsselwort verwendet. Weitere Informationen finden Sie unter [/unsafe (C# Compiler Options](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Optionaler `String` -Parameter.<br /><br /> Gibt die Anwendungskonfigurationsdatei mit den Assemblybindungseinstellungen an.|  
|`BaseAddress`|Optionaler `String` -Parameter.<br /><br /> Gibt die bevorzugte Basisadresse an, unter der eine DLL geladen werden soll. Die Standard-Basisadresse für eine DLL-Datei wird durch die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Common Language Runtime festgelegt. Weitere Informationen finden Sie unter [/baseaddress (C# Compiler Options)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Optionaler `Boolean` -Parameter.<br /><br /> Gibt an, ob Ganzzahlarithmetik, die die Grenzen des Datentyps überschreitet, zur Laufzeit eine Ausnahme auslöst. Weitere Informationen finden Sie unter [/checked (C# Compiler Options)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Weitere Informationen finden Sie unter [/codepage (C# Compiler Options)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Optionaler `String` -Parameter.<br /><br /> Gibt den Debugtyp an. `DebugType` kann `full` oder `pdbonly` sein. Die Standardeinstellung ist `full`. Dadurch kann ein Debugger einem aktiven Programm zugeordnet werden kann. Durch das Angeben von `pdbonly` ist ein Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist.<br /><br /> Dieser Parameter überschreibt den `EmitDebugInformation`-Parameter.<br /><br /> Weitere Informationen finden Sie unter [/debug (C# Compiler Options)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Optionaler `String` -Parameter.<br /><br /> Definiert Präprozessorsymbole. Weitere Informationen finden Sie unter [/define (C# Compiler Options)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Optionaler `Boolean` -Parameter.<br /><br /> Ist der Wert `true`, gibt dies an, dass die Assembly vollständig signiert werden soll. Ist der Wert `false`, gibt dies an, dass Sie nur den öffentlichen Schlüssel in die Assembly platzieren möchten.<br /><br /> Dieser Parameter hat nur dann Auswirkungen, wenn Sie ihn entweder mit dem `KeyFile`- oder `KeyContainer`-Parameter verwenden.<br /><br /> Weitere Informationen finden Sie unter [/delaysign (C# Compiler Options)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Optionaler `String` -Parameter.<br /><br /> Gibt die Liste der zu deaktivierenden Warnungen an. Weitere Informationen finden Sie unter [/nowarn (C# Compiler Options)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Optionaler `String` -Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu einer XML-Datei. Weitere Informationen finden Sie unter [/doc (C# Compiler Options)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Optionaler `Boolean` -Parameter.<br /><br /> Ist der Wert `true`, generiert die Aufgabe Debuginformationen und platziert sie in einer Programmdatenbankdatei (PDB-Datei). Ist der Wert `false`, erzeugt die Aufgabe keine Debuginformationen. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [/debug (C# Compiler Options)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Optionaler `String` -Parameter.<br /><br /> Bietet eine einfache Möglichkeit, einen internen C#-Fehler an Microsoft zu melden. Dieser Parameter kann den Wert `prompt`, `send` oder `none` haben. Wenn der Parameter auf `prompt` festgelegt ist, erhalten Sie eine Aufforderung, wenn ein interner Compilerfehler auftritt. Mithilfe der Aufforderung können Sie einen Fehlerbericht elektronisch an Microsoft senden. Wenn der Parameter auf `send` festgelegt ist, wird automatisch ein Problembericht gesendet. Wenn der Parameter auf `none` festgelegt ist, wird der Fehler nur in der Textausgabe des Compilers gemeldet. Der Standardwert ist `none`. Weitere Informationen finden Sie unter [/errorreport (C# Compiler Options)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die Größe der Abschnitte in der Ausgabedatei an. Weitere Informationen finden Sie unter [/filealign (C# Compiler Options)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Optionaler `Boolean` -Parameter.<br /><br /> Ist der Wert `true`, wird der absolute Pfad zur Datei in der Compilerausgabe angegeben. Ist der Wert `false`, wird der Dateiname angegeben. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [/fullpaths (C# Compiler Options)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen des kryptografischen Schlüsselcontainers an. Weitere Informationen finden Sie unter [/keycontainer (C# Compiler Options)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Optionaler `String` -Parameter.<br /><br /> Gibt den Dateinamen mit dem kryptografischen Schlüssel an. Weitere Informationen finden Sie unter [/keyfile (C# Compiler Options)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Optionaler `String` -Parameter.<br /><br /> Gibt die Version der zu verwendenden Sprache an. Weitere Informationen finden Sie unter [/langversion (C# Compiler Options)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Erstellt einen Link zu einer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert.<br /><br /> Elemente, die an diesen Parameter übergeben werden, können optionale Metadateneinträge mit dem Namen `LogicalName` und `Access` enthalten. `LogicalName` entspricht dem `identifier`-Parameter des `/linkresource`-Switches, und `Access` entspricht dem `accessibility-modifier`-Parameter. Weitere Informationen finden Sie unter [/linkresource (C# Compiler Options)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Optionaler `String` -Parameter.<br /><br /> Gibt den Speicherort der `Main`-Methode an. Weitere Informationen hierzu finden Sie unter [/main (C# Compiler Options)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen der Assembly an, zu der dieses Modul gehört.|  
|`NoConfig`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Compiler angewiesen, nicht mit der Datei „Vbc.rsp“ zu kompilieren. Weitere Informationen finden Sie unter [/noconfig (C# Compiler Options)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Compilerbannerinformationen unterdrückt. Weitere Informationen finden Sie unter [/nologo (C# Compiler Options)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Import der Datei „mscorlib.dll“ verhindert, die den gesamten Systemnamespace definiert. Verwenden Sie diesen Parameter, wenn Sie Ihren eigenen Systemnamespace und die entsprechenden Objekte definieren oder erstellen möchten. Weitere Informationen finden Sie unter [/nostdlib (C# Compiler Options)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, schließen Sie das Win32-Standardmanifest nicht ein.|  
|`Optimize`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, werden Optimierungen aktiviert. Wenn der Wert `false` ist, werden Optimierungen deaktiviert. Weitere Informationen finden Sie unter [/optimize (C# Compiler Options)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an. Weitere Informationen finden Sie unter [/out (C# Compiler Options)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Optionaler `String` -Parameter.<br /><br /> Gibt den Dateinamen der Debuginformationen an. Der Standardname ist der Ausgabedateiname mit einer .pdb-Erweiterung.|  
|`Platform`|Optionaler `String` -Parameter.<br /><br /> Gibt die Prozessorplattform an, die das Ziel der Ausgabedatei darstellen soll. Dieser Parameter kann den Wert `x86`, `x64` oder `anycpu` haben. Der Standardwert ist `anycpu`. Weitere Informationen finden Sie unter [/platform (C# Compiler Options)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen aus den angegebenen Elementen in das aktuelle Projekt importiert. Weitere Informationen finden Sie unter [/reference (C# Compiler Options)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Sie können einen [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Verweisalias in einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Datei angeben, indem Sie die Metadaten `Aliases` zum ursprünglichen „Verweis“-Element hinzufügen. Angenommen, Sie möchten den Alias „LS1“ in der folgenden CSC-Befehlszeile festlegen:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> In diesem Fall verwenden Sie:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Fügt eine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Ressource in die Ausgabedatei ein.<br /><br /> Elemente, die an diesen Parameter übergeben werden, können optionale Metadateneinträge mit dem Namen `LogicalName` und `Access` enthalten. `LogicalName`entspricht dem `identifier`-Parameter des `/resource`-Switches, und `Access` entspricht dem `accessibility-modifier`-Parameter. Weitere Informationen finden Sie unter [/resource (C# Compiler Options)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Optionaler `String` -Parameter.<br /><br /> Gibt die Antwortdatei an, die Befehle für den die Aufgabe enthalten. Weitere Informationen finden Sie unter [@ (C# Compiler Options)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f) (@ [C#-Compileroptionen]).|  
|`Sources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt mindestens eine [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Quelldatei an.|  
|`TargetType`|Optionaler `String` -Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann unterschiedliche Werte aufweisen: `library` erstellt eine Codebibliothek, `exe` erstellt eine Konsolenanwendung, `module` erstellt ein Modul, und `winexe` erstellt ein Windows-Programm. Der Standardwert ist `library`sein. Weitere Informationen finden Sie unter [/target (C# Compiler Options)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` ist, werden alle Warnungen als Fehler behandelt. Weitere Informationen finden Sie unter [/warnaserror (C# Compiler Options)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Optionaler `Boolean` -Parameter.<br /><br /> Weist die Aufgabe an, das prozessinterne Compilerobjekt (falls verfügbar) zu verwenden. Wird nur von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwendet.|  
|`Utf8Output`|Optionaler `Boolean` -Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF-8-Codierung. Weitere Informationen finden Sie unter [/utf8output (C# Compiler Options)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die vom Compiler anzuzeigende Warnstufe an. Weitere Informationen finden Sie unter [/warn (C# Compiler Options)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Optionaler `String` -Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (C# Compiler Options)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Dieser Parameter überschreibt den `TreatWarningsAsErrors`-Parameter.|  
|`WarningsNotAsErrors`|Optionaler `String` -Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (C# Compiler Options)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Dieser Parameter ist nur dann nützlich, wenn der `TreatWarningsAsErrors`-Parameter auf `true` gesetzt ist.|  
|`Win32Icon`|Optionaler `String` -Parameter.<br /><br /> Fügt der Assembly eine ICO-Datei hinzu, die der Ausgabedatei im Datei-Explorer das gewünschte Aussehen verleiht. Weitere Informationen finden Sie unter [/win32icon (C# Compiler Options)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Optionaler `String` -Parameter.<br /><br /> Gibt das Win32-Manifest an, das eingeschlossen werden sollen.|  
|`Win32Resource`|Optionaler `String` -Parameter.<br /><br /> Fügt eine Win32-Ressource (RES-Datei) in die Ausgabedatei ein. Weitere Informationen finden Sie unter [/win32res (C# Compiler Options)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der `Microsoft.Build.Tasks.ManagedCompiler`-Klasse, die selbst von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse erbt, welche wiederum von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `Csc`-Aufgabe verwendet, um eine ausführbare Datei aus den Quelldateien in der `Compile`-Elementauflistung zu kompilieren.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
