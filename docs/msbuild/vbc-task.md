---
title: "Vbc Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Vbc task [MSBuild]"
  - "MSBuild, Vbc task"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vbc Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt vbc.exe, womit folgendes erzeugt wird: ausführbare Dateien \(.exe\), Dynamic Link Library\-Dateien \(.dll\) und Codemodule \(.  NETMODULE\-Dateien\).  Weitere Informationen zu vbc.exe finden Sie unter [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Vbc`\-Aufgabe beschrieben.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt zusätzliche Ordner an, in denen nach den im References\-Attribut angegebenen Assemblys gesucht werden soll.|  
|`AddModules`|Optionaler `String[]`\-Parameter.<br /><br /> Bewirkt, dass der Compiler dem Projekt, das Sie gerade kompilieren, sämtliche Typinformationen aus den angegebenen Dateien bereitstellt.  Dieser Parameter entspricht dem [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule)\-Schalter des vbc.exe\-Compilers.|  
|`BaseAddress`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Basisadresse der DLL an.  Dieser Parameter entspricht dem [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress)\-Schalter des vbc.exe\-Compilers.|  
|`CodePage`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an.  Dieser Parameter entspricht dem [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage)\-Schalter des vbc.exe\-Compilers.|  
|`DebugType`|Optionaler `String[]`\-Parameter.<br /><br /> Bewirkt, dass der Compiler Debuginformationen generiert.  Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Der Standardwert ist `full`. Durch diesen wird das Anfügen eines Debuggers an das laufende Programm aktiviert.  Der Wert `pdbonly` ermöglicht das Debuggen von Quellcode, wenn das Programm im Debugger gestartet wird. Der Code in Assemblersprache wird jedoch nur angezeigt, wenn das laufende Programm an den Debugger angefügt ist.  Weitere Informationen finden Sie unter [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Optionaler `String[]`\-Parameter.<br /><br /> Definiert Konstanten für die bedingte Kompilierung.  Symbol\/Wert\-Paare werden durch Semikolons getrennt und mit der folgenden Syntax angegeben:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Dieser Parameter entspricht dem [\/define](/dotnet/visual-basic/reference/command-line-compiler/define)\-Schalter des vbc.exe\-Compilers.|  
|`DelaySign`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, fügt die Aufgabe den öffentlichen Schlüssel in die Assembly ein.  Lautet der Wert `false`, signiert die Aufgabe die Assembly vollständig.  Der Standardwert ist `false`. Dieser Parameter hat nur Auswirkungen, wenn er mit dem `KeyFile`\-Parameter oder dem `KeyContainer`\-Parameter verwendet wird.  Dieser Parameter entspricht dem [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)\-Schalter des vbc.exe\-Compilers.|  
|`DisabledWarnings`|Optionaler `String`\-Parameter.<br /><br /> Unterdrückt die angegebenen Warnungen.  Sie müssen lediglich den numerischen Teil des Warnungsbezeichners angeben.  Mehrere Warnungen werden durch Semikolons getrennt.  Dieser Parameter entspricht dem [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)\-Schalter des vbc.exe\-Compilers.|  
|`DocumentationFile`|Optionaler `String`\-Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu der angegebenen XML\-Datei.  Dieser Parameter überschreibt das `GenerateDocumentation`\-Attribut.  Weitere Informationen hierzu finden Sie unter [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, generiert die Aufgabe Debuginformationen und fügt sie in eine PDB\-Datei ein.  Weitere Informationen finden Sie unter [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Optionaler `String`\-Parameter.<br /><br /> Gibt an, wie die Aufgabe interne Compilerfehler melden soll.  Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Wenn `prompt` angegeben ist und ein interner Compilerfehler auftritt, wird der Benutzer aufgefordert anzugeben, ob die Fehlerdaten an Microsoft gesendet werden sollen.<br /><br /> Wenn `send` angegeben ist und ein interner Compilerfehler auftritt, sendet die Aufgabe die Fehlerdaten an Microsoft.<br /><br /> Der Standardwert ist `none`, d. h., Fehler werden nur in einer Textausgabe gemeldet.<br /><br /> Dieser Parameter entspricht dem [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)\-Schalter des vbc.exe\-Compilers.|  
|`FileAlignment`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Ausrichtung der Abschnitte der Ausgabedatei in Bytes an.  Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Dieser Parameter entspricht dem [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign)\-Schalter des vbc.exe\-Compilers.|  
|`GenerateDocumentation`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Dokumentationsinformationen generiert und in eine XML\-Datei eingefügt, deren Name dem der von der Aufgabe erstellten ausführbaren Datei oder Bibliothek entspricht.  Weitere Informationen hierzu finden Sie unter [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Importiert Namespaces aus den angegebenen Elementauflistungen.  Dieser Parameter entspricht dem [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports)\-Schalter des vbc.exe\-Compilers.|  
|`KeyContainer`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Namen des Kryptografieschlüsselcontainers an.  Dieser Parameter entspricht dem [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)\-Schalter des vbc.exe\-Compilers.|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Namen der Datei an, die den kryptografischen Schlüssel enthält.  Weitere Informationen hierzu finden Sie unter [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Optionaler [String](assetId:///String?qualifyHint=False&autoUpgrade=True)\-Parameter.<br /><br /> Gibt die Sprachversion an, entweder "9"oder "10".|  
|`LinkResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Erstellt einen Link zu einer .NET Framework\-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert.  Dieser Parameter entspricht dem [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource)\-Schalter des vbc.exe\-Compilers.|  
|`MainEntryPoint`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Klasse oder das Modul an, die bzw. das die `Sub Main`\-Prozedur enthält.  Dieser Parameter entspricht dem [\/main](/dotnet/visual-basic/reference/command-line-compiler/main)\-Schalter des vbc.exe\-Compilers.|  
|`ModuleAssemblyName`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Assembly an, zu der dieses Modul gehört.|  
|`NoConfig`|Optionaler `Boolean`\-Parameter.<br /><br /> Gibt an, dass der Compiler die Datei vbc.rsp nicht verwenden soll.  Dieser Parameter entspricht dem [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig)\-Schalter des vbc.exe\-Compilers.|  
|`NoLogo`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, wird die Anzeige der Compilerbannerinformationen unterdrückt.  Dieser Parameter entspricht dem [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo)\-Schalter des vbc.exe\-Compilers.|  
|`NoStandardLib`|Optionaler `Boolean`\-Parameter.<br /><br /> Bewirkt, dass der Compiler nicht auf die Standardbibliotheken verweist.  Dieser Parameter entspricht dem [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib)\-Schalter des vbc.exe\-Compilers.|  
|`NoVBRuntimeReference`|Optionaler `Boolean`\-Parameter.<br /><br /> Wird nur intern verwendet.  Bei true wird der automatischer Verweis auf Microsoft.VisualBasic.dll vermieden.|  
|`NoWarnings`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, unterdrückt die Aufgabe alle Warnungen.  Weitere Informationen hierzu finden Sie unter [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Compileroptimierungen aktiviert.  Dieser Parameter entspricht dem [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize)\-Schalter des vbc.exe\-Compilers.|  
|`OptionCompare`|Optionaler `String`\-Parameter.<br /><br /> Gibt an, wie Zeichenfolgenvergleiche durchgeführt werden.  Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Der Wert `binary` gibt an, dass die Aufgabe binäre Zeichenfolgenvergleiche verwendet.  Der Wert `text` gibt an, dass die Aufgabe textbasierte Zeichenfolgenvergleiche verwendet.  Der Standardwert dieses Parameters ist `binary`.  Dieser Parameter entspricht dem [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)\-Schalter des vbc.exe\-Compilers.|  
|`OptionExplicit`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, müssen Variablen explizit deklariert werden.  Dieser Parameter entspricht dem [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)\-Schalter des vbc.exe\-Compilers.|  
|`OptionInfer`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, wird der Typrückschluss von Variablen ermöglicht.|  
|`OptionStrict`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, erzwingt die Aufgabe strikte Typsemantik, um implizite Typkonvertierungen zu beschränken.  Dieser Parameter entspricht dem [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)\-Schalter des vbc.exe\-Compilers.|  
|`OptionStrictType`|Optionaler `String`\-Parameter.<br /><br /> Gibt an, welche strikte Typsemantik eine Warnung generiert.  Derzeit wird nur "custom" unterstützt.  Dieser Parameter entspricht dem [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)\-Schalter des vbc.exe\-Compilers.|  
|`OutputAssembly`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an.  Dieser Parameter entspricht dem [\/out](/dotnet/visual-basic/reference/command-line-compiler/out)\-Schalter des vbc.exe\-Compilers.|  
|`Platform`|Optionaler `String`\-Parameter.<br /><br /> Gibt die von der Ausgabedatei verwendete Prozessorplattform an.  Dieser Parameter kann den Wert `x86`, `x64`, `Itanium` oder `anycpu` aufweisen.  Der Standardwert ist `anycpu`.  Dieser Parameter entspricht dem [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform)\-Schalter des vbc.exe\-Compilers.|  
|`References`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen von den angegebenen Elementen ins aktuelle Projekt importiert.  Dieser Parameter entspricht dem [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference)\-Schalter des vbc.exe\-Compilers.|  
|`RemoveIntegerChecks`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Überprüfungen auf Ganzzahlüberlauf deaktiviert.  Der Standardwert ist `false`.  Dieser Parameter entspricht dem [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks)\-Schalter des vbc.exe\-Compilers.|  
|`Resources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Bettet eine .NET Framework\-Ressource in die Ausgabedatei ein.  Dieser Parameter entspricht dem [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource)\-Schalter des vbc.exe\-Compilers.|  
|`ResponseFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Antwortdatei an, die Befehle für diese Aufgabe enthält.  Dieser Parameter entspricht der [@ \(Antwortdatei festlegen\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)\-Option des vbc.exe\-Compilers.|  
|`RootNamespace`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Stammnamespace für alle Typdeklarationen an.  Dieser Parameter entspricht dem [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)\-Schalter des vbc.exe\-Compilers.|  
|`SdkPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Speicherort von mscorlib.dll und microsoft.visualbasic.dll an.  Dieser Parameter entspricht dem [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath)\-Schalter des vbc.exe\-Compilers.|  
|`Sources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt eine oder mehrere [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Quelldateien an.|  
|`TargetCompactFramework`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, verwendet die Aufgabe [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  Dieser Schalter entspricht dem [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf)\-Schalter des vbc.exe\-Compilers.|  
|`TargetType`|Optionaler `String`\-Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an.  Dieser Parameter kann den Wert `library` aufweisen, durch den eine Codebibliothek erstellt wird, den Wert `exe`, durch den eine Konsolenanwendung erstellt wird, den Wert `module`, durch den ein Modul erstellt wird, oder den Wert `winexe`, durch den ein Windows\-Programm erstellt wird.  Der Standardwert ist `library`.  Dieser Parameter entspricht dem [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)\-Schalter des vbc.exe\-Compilers.|  
|`Timeout`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Zeit in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird.  Der Standardwert lautet `Int.MaxValue`. Dieser gibt an, dass kein Timeoutintervall festgelegt ist.|  
|`ToolPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Speicherort an, von dem die Aufgabe die zugrunde liegende ausführbare Datei \(vbc.exe\) lädt.  Wird dieser Parameter nicht angegeben, verwendet die Aufgabe den SDK\-Installationspfad für die Framework\-Version, in der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ausgeführt wird.|  
|`TreatWarningsAsErrors`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` ist, werden alle Warnungen als Fehler behandelt.  Weitere Informationen finden Sie unter [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Optionaler `Boolean`\-Parameter.<br /><br /> Weist die Aufgabe auf, das prozessinterne Compilerobjekt zu verwenden, falls verfügbar.  Wird nur von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwendet.|  
|`Utf8Output`|Optionaler `Boolean`\-Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF\-8\-Codierung.  Dieser Parameter entspricht dem [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output)\-Schalter des vbc.exe\-Compilers.|  
|`Verbosity`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Ausführlichkeitsgrad der Compilerausgabe an.  Der Ausführlichkeitsgrad kann `Quiet`, `Normal` \(Standard\) oder `Verbose` sein.|  
|`WarningsAsErrors`|Optionaler `String`\-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen.  Weitere Informationen finden Sie unter [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Dieser Parameter überschreibt den `TreatWarningsAsErrors`\-Parameter.|  
|`WarningsNotAsErrors`|Optionaler `String`\-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen.  Weitere Informationen finden Sie unter [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Dieser Parameter ist nur nützlich, wenn der `TreatWarningsAsErrors`\-Parameter auf `true` festgelegt wird.|  
|`Win32Icon`|Optionaler `String`\-Parameter.<br /><br /> Fügt eine ICO\-Datei in der Assembly, die der Ausgabedatei die gewünschte Darstellung im Datei\-Explorer gibt.  Dieser Parameter entspricht dem [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)\-Schalter des vbc.exe\-Compilers.|  
|`Win32Resources`|Optionaler `String`\-Parameter.<br /><br /> Fügt eine Win32\-Ressourcendatei \(.res\) in die Ausgabedatei ein.  Dieser Parameter entspricht dem [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)\-Schalter des vbc.exe\-Compilers.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekt kompiliert.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## Siehe auch  
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)