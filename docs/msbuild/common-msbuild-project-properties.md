---
title: Gemeinsame MSBuild-Projekteigenschaften | Microsoft-Dokumentation
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0ecdd051ecc44cb3205ca8793653bf31a63abd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62570293"
---
# <a name="common-msbuild-project-properties"></a>Gemeinsame MSBuild-Projekteigenschaften
In der folgenden Tabelle werden häufig verwendete Eigenschaften aufgelistet, die in den Visual Studio-Projektdateien definiert oder in den *TARGETS*-Dateien enthalten sind, die von MSBuild bereitgestellt werden.

 Projektdateien in Visual Studio (*CSPROJ-*, *VBPROJ-*, *VCXPROJ*-Dateien und andere) enthalten MSBuild-XML-Code, der ausgeführt wird, wenn Sie ein Projekt mithilfe der IDE erstellen. Projekte importieren in der Regel mindestens eine *TARGETS*-Datei, um den entsprechenden Buildprozess zu definieren. Weitere Informationen finden Sie unter [TARGETS-Dateien von MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Liste häufig verwendeter Eigenschaften und Parameter

| Eigenschaften- oder Parametername | Beschreibung |
|------------------------------------| - |
| AdditionalLibPaths | Gibt weitere Ordner an, in denen Compiler nach Verweisassemblys suchen sollen. |
| AddModules | Bewirkt, dass der Compiler dem Projekt, das Sie kompilieren, sämtliche Typinformationen aus den angegebenen Dateien bereitstellt. Diese Eigenschaft entspricht dem `/addModules`-Compilerschalter. |
| ALToolPath | Der Pfad, unter dem *AL.exe* gespeichert ist. Diese Eigenschaft überschreibt die aktuelle Version von *AL.exe*, um die Verwendung einer anderen Version zu ermöglichen. |
| ApplicationIcon | Die *ICO*-Symboldatei, die zum Einbetten als Win32-Symbol an den Compiler übergeben wird. Die Eigenschaft entspricht dem `/win32icon`-Compilerschalter. |
| ApplicationManifest | Gibt den Pfad der Datei an, die verwendet wird, um externe Manifestinformationen zur Benutzerkontensteuerung (User Account Control, UAC) zu erzeugen. Bezieht sich nur auf Visual Studio-Projekte für [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> In den meisten Fällen wird das Manifest eingebettet. Wenn Sie jedoch COM ohne Registrierung oder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung verwenden, kann das Manifest eine externe Datei sein, die zusammen mit den Anwendungsassemblys installiert wird. Weitere Informationen finden Sie unter der "NoWin32Manifest"-Eigenschaft in diesem Thema. |
| AssemblyOriginatorKeyFile | Gibt die Datei an, die verwendet wird, um die Assembly (*SNK* oder *PFX*) zu signieren, und die an die [ResolveKeySource](../msbuild/resolvekeysource-task.md)-Aufgabe übergeben wird, um den tatsächlichen Schlüssel zu generieren, mit dem die Assembly signiert wird. |
| AssemblySearchPaths | Eine Liste von Speicherorten, die bei der Verweisassemblyauflösung zur Buildzeit durchsucht werden sollen. Die Reihenfolge der aufgelisteten Pfade ist von Bedeutung, da Pfade weiter oben in der Liste Vorrang vor weiter unten stehenden Pfaden haben. |
| AssemblyName | Der Name der endgültigen Ausgabeassembly, nachdem das Projekt erstellt wurde. |
| BaseAddress | Gibt die Basisadresse der Hauptausgabeassembly an. Diese Eigenschaft entspricht dem `/baseaddress`-Compilerschalter. |
| BaseOutputPath | Gibt den Basispfad für die Ausgabedatei an. Wenn dies festgelegt ist, verwendet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Beispielsyntax: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Der Ordner der obersten Ebene, in dem alle konfigurationsspezifischen Zwischenausgabeordner erstellt werden. Der Standardwert ist `obj\`sein. Codebeispiel: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | Ein boolescher Wert, der angibt, ob Projektverweise bei der Verwendung von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Multi-Proc parallel erstellt oder bereinigt werden. Der Standardwert ist `true`. Das bedeutet, dass Projekte parallel erstellt werden, wenn das System über mehrere Kerne oder Prozessoren verfügt. |
| BuildProjectReferences | Ein boolescher Wert, der angibt, ob Projektverweise von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] erstellt werden. Automatisch auf `false` festgelegt, wenn Sie Ihr Projekt in der integrierten Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellen, andernfalls `true`. `-p:BuildProjectReferences=false` kann in der Befehlszeile eingegeben werden, um die Überprüfung von Projekten, auf die verwiesen wird, auf Aktualität zu vermeiden. |
| CleanFile | Der Name der Datei, die als "Löschcache" verwendet wird. Der Löschcache ist eine Liste generierter Dateien, die während des Bereinigungsvorgangs gelöscht werden. Die Datei wird vom Buildprozess im Zwischenausgabepfad abgelegt.<br /><br /> Diese Eigenschaft gibt nur Dateinamen an, die keine Pfadinformationen aufweisen. |
| CodePage | Gibt für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Diese Eigenschaft entspricht dem `/codepage`-Compilerschalter. |
| CompilerResponseFile | Eine optionale Antwortdatei, die an die Compileraufgaben übergeben werden kann. |
| Konfiguration | Die Konfiguration, die Sie erstellen, entweder "Debug" oder "Release". |
| CscToolPath | Der Pfad von *csc.exe*, dem [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Compiler. |
| CustomBeforeMicrosoftCommonTargets | Der Name einer Projektdatei oder TARGETS-Datei, die vor dem allgemeinen TARGETS-Import automatisch importiert werden soll. |
| DebugSymbols | Ein boolescher Wert, der angibt, ob Symbole vom Build generiert werden.<br /><br /> Durch das Festlegen von **-p:DebugSymbols=false** in der Befehlszeile wird die Generierung von Programmdatenbank-Symboldateien (*PDB*-Dateien) deaktiviert. |
| DebugType | Definiert den Umfang der zu generierenden Debuginformationen. Gültige Werte sind „full“, „pdbonly“, „portable“, „embedded“ und „none“. |
| DefineConstants | Definiert Konstanten für die bedingte Kompilierung. Symbol-Wert-Paare werden durch Semikolons getrennt und mit der folgenden Syntax angegeben:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> Die Eigenschaft entspricht dem `/define`-Compilerschalter. |
| DefineDebug | Ein boolescher Wert, der angibt, ob die DEBUG-Konstante definiert werden soll. |
| DefineTrace | Ein boolescher Wert, der angibt, ob die TRACE-Konstante definiert werden soll. |
| DelaySign | Ein boolescher Wert, der angibt, ob Sie die Assembly verzögert oder voll signieren möchten. |
| Deterministic | Ein boolescher Wert, der angibt, ob der Compiler identische Assemblys für identische Eingaben erzeugen sollte. Dieser Parameter entspricht der `/deterministic`-Option der Compiler *vbc.exe* und *csc.exe*. |
| DisabledWarnings | Unterdrückt die angegebenen Warnungen. Lediglich der numerische Teil des Warnungsbezeichners muss angegeben werden. Mehrere Warnungen werden durch Semikolons getrennt. Dieser Parameter entspricht der `/nowarn`-Option des Compilers *vbc.exe*. |
| DisableFastUpToDateCheck | Ein boolescher Wert, der nur für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gilt. Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Build-Manager stellt mithilfe des "FastUpToDateCheck"-Prozesses fest, ob ein Projekt neu erstellt werden muss, damit es aktuell ist. Dieser Prozess ist schneller als die Verwendung von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Durch Festlegen der „DisableFastUpToDateCheck“-Eigenschaft auf `true` können Sie den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Build-Manager umgehen und die Verwendung von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zum Bestimmen der Aktualität des Projekts erzwingen. |
| DocumentationFile | Der Name der Datei, die als XML-Dokumentationsdatei generiert wird. Dieser Name umfasst nur den Dateinamen und weist keine Pfadinformationen auf. |
| ErrorReport | Gibt an, wie interne Compilerfehler von der Compileraufgabe gemeldet werden sollen. Gültige Werte sind "prompt", "send" und "none". Diese Eigenschaft entspricht dem `/errorreport`-Compilerschalter. |
| ExcludeDeploymentUrl | Dem Bereitstellungsmanifest wird durch die [GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md) ein deploymentProvider-Tag hinzugefügt, wenn die Projektdatei eines der folgenden Elemente enthält:<br /><br /> – UpdateUrl<br />– InstallUrl<br />– PublishUrl<br /><br /> Sie können mithilfe von „ExcludeDeploymentUrl“ jedoch verhindern, dass das „deploymentProvider“-Tag zum Bereitstellungsmanifest hinzugefügt wird, auch wenn eine der vorgenannten URLs angegeben wird. Fügen Sie der Projektdatei zu diesem Zweck die folgende Eigenschaft hinzu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Hinweis**:  „ExcludeDeploymentUrl“ wird in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE nicht zur Verfügung gestellt und kann nur festgelegt werden, indem die Projektdatei manuell bearbeitet wird. Das Festlegen dieser Eigenschaft hat keine Auswirkung auf die Veröffentlichung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das bedeutet, dass das Tag "deploymentProvider" weiterhin zu der durch "PublishUrl" angegebenen URL hinzugefügt wird. |
| FileAlignment | Gibt die Ausrichtung der Abschnitte der Ausgabedatei in Bytes an. Gültige Werte sind 512, 1024, 2048, 4096 und 8192. Diese Eigenschaft entspricht dem `/filealignment`-Compilerschalter. |
| FrameworkPathOverride | Gibt den Speicherort von *mscorlib.dll* und *microsoft.visualbasic.dll* an. Dieser Parameter entspricht der `/sdkpath`-Option des Compilers *vbc.exe*. |
| GenerateDocumentation | (Nur Visual Basic ) Ein boolescher Parameter, der angibt, ob eine Dokumentation vom Build generiert wird. Wenn der Wert `true` lautet, werden Dokumentationsinformationen vom Build generiert und zusammen mit dem Namen der ausführbaren Datei oder der Bibliothek, die von der Buildaufgabe erstellt wurde, in einer *XML*-Datei gespeichert. |
| IntermediateOutputPath | Der vollständige Zwischenausgabepfad wie von `BaseIntermediateOutputPath` abgeleitet, wenn kein Pfad angegeben wird. Beispiel: *\obj\debug\\*. |
| KeyContainerName | Der Name des Containers mit dem Schlüssel für einen starken Namen. |
| KeyOriginatorFile | Der Name der Datei mit dem Schlüssel für einen starken Namen. |
| MSBuildProjectExtensionsPath | Gibt den Pfad an, unter dem Projekterweiterungen gespeichert sind. Standardmäßig entspricht dies dem Wert von `BaseIntermediateOutputPath`. |
| ModuleAssemblyName | Der Name der Assembly, in die das kompilierte Modul integriert werden soll. Die Eigenschaft entspricht dem `/moduleassemblyname`-Compilerschalter. |
| NoLogo | Ein boolescher Wert, der angibt, ob das Compilerlogo deaktiviert werden soll. Diese Eigenschaft entspricht dem `/nologo`-Compilerschalter. |
| NoStdLib | Ein boolescher Wert, der angibt, ob Verweise auf die Standardbibliothek (*mscorlib.dll*) vermieden werden sollen. Der Standardwert ist `false`sein. |
| NoVBRuntimeReference | Ein boolescher Wert, der angibt, ob die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Runtime (*Microsoft.VisualBasic.dll*) als Verweis in das Projekt eingefügt werden soll. |
| NoWin32Manifest | Ein boolescher Wert, der angibt, ob Manifestinformationen zur Benutzerkontensteuerung (User Account Control, UAC) in die ausführbare Datei der Anwendung eingebettet werden. Bezieht sich nur auf Visual Studio-Projekte für [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. In Projekten, die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] und COM ohne Registrierung bereitgestellt werden, wird dieses Element ignoriert. `False` (der Standardwert) gibt an, dass Manifestinformationen zur Benutzerkontensteuerung in die ausführbare Datei der Anwendung eingebettet werden. `True` gibt an, dass UAC-Manifestinformationen nicht eingebettet werden.<br /><br /> Diese Eigenschaft wird nur auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekte für [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] angewendet. In Projekten, die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] und COM ohne Registrierung bereitgestellt werden, wird diese Eigenschaft ignoriert.<br /><br /> Sie dürfen „NoWin32Manifest“ nur hinzufügen, wenn Sie möchten, dass von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] keine Manifestinformationen in die ausführbare Datei der Anwendung einbettet werden. Dieser Vorgang wird als *Virtualisierung* bezeichnet. Legen Sie zur Verwendung der Virtualisierung `<ApplicationManifest>` zusammen mit `<NoWin32Manifest>` wie folgt fest:<br /><br /> – Entfernen Sie bei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekten den `<ApplicationManifest>`-Knoten. (In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekten wird `<NoWin32Manifest>` ignoriert, wenn ein `<ApplicationManifest>`-Knoten vorhanden ist.)<br />– Legen Sie bei [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten für `<ApplicationManifest>` den Wert `False` und für `<NoWin32Manifest>` den Wert `True` fest. (In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten wird `<ApplicationManifest>` von `<NoWin32Manifest>` überschrieben.)<br /> Diese Eigenschaft entspricht der `/nowin32manifest`-Compileroption von *vbc.exe*. |
| Optimize | Ein boolescher Wert, der Compileroptimierungen aktiviert, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optimize`-Compilerschalter. |
| OptionCompare | Gibt an, wie Zeichenfolgenvergleiche durchgeführt werden. Gültige Werte sind "binary" oder "text". Diese Eigenschaft entspricht der `/optioncompare`-Compileroption von *vbc.exe*. |
| OptionExplicit | Ein boolescher Wert, der angibt, dass Variablen im Quellcode explizit deklariert werden müssen, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optionexplicit`-Compilerschalter. |
| OptionInfer | Ein boolescher Wert, der den Typrückschluss von Variablen aktiviert, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optioninfer`-Compilerschalter. |
| OptionStrict | Ein boolescher Wert, bei dessen Festlegung auf `true` von der Buildaufgabe eine strikte Typsemantik erzwungen wird, um implizite Typkonvertierungen einzuschränken. Diese Eigenschaft entspricht der `/optionstrict`-Option des Compilers *vbc.exe*. |
| OutputPath | Gibt den Pfad zum Ausgabeverzeichnis relativ zum Projektverzeichnis an, zum Beispiel *bin\Debug*. |
| OutputType | Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann einen der folgenden Werte aufweisen:<br /><br /> – Library. Erstellt eine Codebibliothek. (Standardwert)<br />– Exe. Erstellt eine Konsolenanwendung.<br />– Module. Erstellt ein Modul.<br />– Winexe. Erstellt ein Windows-Programm.<br /><br /> Diese Eigenschaft entspricht der `/target`-Option des Compilers *vbc.exe*. |
| OverwriteReadOnlyFiles | Ein boolescher Wert, der angibt, ob schreibgeschützte Dateien vom Build überschrieben werden sollen oder ob ein Fehler ausgelöst werden soll. |
| PathMap | Gibt an, wie physische Pfade den Quellpfadnamen zugeordnet werden, die vom Compiler ausgegeben werden. Diese Eigenschaft entspricht der `/pathmap`-Option des Compilers *csc.exe*. |
| PdbFile | Der Dateiname der *PDB*-Datei, die Sie ausgeben. Diese Eigenschaft entspricht der `/pdb`-Option des Compilers *csc.exe*. |
| Plattform | Das Betriebssystem, für das Sie erstellen. Gültige Werte sind "Beliebige CPU", "x86" und "x64". |
| ProduceReferenceAssembly | Ein boolescher Wert, der auf `true` festgelegt wurde, ermöglicht die Produktion von [Verweisassemblys](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) für die aktuelle Assembly. `Deterministic` sollte beim Verwenden dieser Funktion `true` entsprechen. Diese Eigenschaft entspricht der `/refout`-Option der Compiler *vbc.exe* und *csc.exe*. |
| ProduceOnlyReferenceAssembly | Ein boolescher Wert, der den Compiler anweist, nur eine Verweisassembly und keinen kompilierten Code ausgegeben. Kann nicht in Verbindung mit `ProduceReferenceAssembly` verwendet werden.  Diese Eigenschaft entspricht der `/refonly`-Option der Compiler *vbc.exe* und *csc.exe*. |
| RemoveIntegerChecks | Ein boolescher Wert, der angibt, ob Überprüfungen auf Ganzzahlüberlauf-Fehler deaktiviert werden sollen. Der Standardwert ist `false`sein. Diese Eigenschaft entspricht der `/removeintchecks`-Option des Compilers *vbc.exe*. |
| SGenUseProxyTypes | Ein boolescher Wert, der angibt, ob Proxytypen von *SGen.exe* generiert werden sollen.<br /><br /> Das SGen-Ziel verwendet diese Eigenschaft, um das "UseProxyTypes"-Flag festzulegen. Diese Eigenschaft wird standardmäßig auf "true" festgelegt. Es ist keine Benutzeroberfläche verfügbar, um diesen Wert zu ändern. Fügen Sie diese Eigenschaft der Projektdatei hinzu, und legen Sie sie auf FALSE fest, bevor Sie *Microsoft.Common.Targets* oder *C#/VB.targets* importieren, um die Serialisierungsassembly für nicht webdienstbezogene Typen zu generieren. |
| SGenToolPath | Ein optionaler Toolpfad, der angibt, von wo *SGen.exe* abgerufen werden kann, wenn die aktuelle Version von *SGen.exe* überschrieben wurde. |
| StartupObject | Gibt die Klasse oder das Modul an, die bzw. das die "Main"-Methode oder die "Sub Main"-Prozedur enthält. Diese Eigenschaft entspricht dem `/main`-Compilerschalter. |
| ProcessorArchitecture | Die Prozessorarchitektur, die zum Auflösen von Assemblyverweisen verwendet wird. Gültige Werte sind "msil", "x86", "amd64" und "ia64". |
| RootNamespace | Der zu verwendende Stammnamespace, wenn Sie eine eingebettete Ressource benennen. Dieser Namespace ist Teil des Manifestnamens der eingebetteten Ressource. |
| Satellite_AlgorithmId | Die ID des zu verwendenden *AL.exe*-Hashalgorithmus beim Erstellen von Satellitenassemblys. |
| Satellite_BaseAddress | Die zu verwendende Basisadresse, wenn kulturspezifische Satellitenassemblys mit dem `CreateSatelliteAssemblies`-Ziel erstellt werden. |
| Satellite_CompanyName | Der Unternehmensname, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_Configuration | Der Konfigurationsname, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_Description | Der Beschreibungstext, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_EvidenceFile | Bettet die angegebene Datei in die Satellitenassembly mit dem Ressourcennamen "Security.Evidence" ein. |
| Satellite_FileVersion | Gibt eine Zeichenfolge für das Feld "File Version" in der Satellitenassembly an. |
| Satellite_Flags | Gibt einen Wert für das Feld "Flags" in der Satellitenassembly an. |
| Satellite_GenerateFullPaths | Veranlasst die Buildaufgabe, absolute Pfade für alle Dateien zu verwenden, die in einer Fehlermeldung gemeldet werden. |
| Satellite_LinkResource | Verknüpft die angegebenen Ressourcendateien mit einer Satellitenassembly. |
| Satellite_MainEntryPoint | Gibt den voll qualifizierten Namen (also "Klasse.Methode") der Methode an, die als Einstiegspunkt zu verwenden ist, wenn ein Modul während der Erstellung einer Satellitenassembly in eine ausführbare Datei konvertiert wird. |
| Satellite_ProductName | Gibt eine Zeichenfolge für das Feld "Product" in der Satellitenassembly an. |
| Satellite_ProductVersion | Gibt eine Zeichenfolge für das Feld "ProductVersion" in der Satellitenassembly an. |
| Satellite_TargetType | Gibt das Dateiformat der Ausgabedatei der Satellitenassembly als "library", "exe" oder "win" an. Der Standardwert ist "library". |
| Satellite_Title | Gibt eine Zeichenfolge für das Feld "Title" in der Satellitenassembly an. |
| Satellite_Trademark | Gibt eine Zeichenfolge für das Feld "Trademark" in der Satellitenassembly an. |
| Satellite_Version | Gibt die Versionsinformationen für die Satellitenassembly an. |
| Satellite_Win32Icon | Fügt eine *ICO*-Symboldatei in die Satellitenassembly ein. |
| Satellite_Win32Resource | Fügt eine Win32-Ressource (*RES*-Datei) in die Satellitenassembly ein. |
| SubsystemVersion | Gibt die mindestens erforderliche Version des Subsystems an, die die generierte ausführbare Datei verwenden kann. Diese Eigenschaft entspricht dem `/subsystemversion`-Compilerschalter. Informationen zum Standardwert dieser Eigenschaft finden Sie unter [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) oder [/subsystemversion (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Die Version von .NET Compact Framework, die zur Ausführung der zu erstellenden Anwendung erforderlich ist. Durch diese Angabe können Sie auf bestimmte Frameworkassemblys verweisen, auf die andernfalls möglicherweise nicht verwiesen werden kann. |
| TargetFrameworkVersion | Die Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], die zum Ausführen der zu erstellenden Anwendung erforderlich ist. Durch diese Angabe können Sie auf bestimmte Frameworkassemblys verweisen, auf die andernfalls möglicherweise nicht verwiesen werden kann. |
| TreatWarningsAsErrors | Ein boolescher Parameter. Wenn sein Wert `true` lautet, werden alle Warnungen als Fehler behandelt. Dieser Parameter entspricht dem `/nowarn`-Compilerschalter. |
| UseHostCompilerIfAvailable | Ein boolescher Parameter. Wenn sein Wert `true` lautet, verwendet die Buildaufgabe das prozessinterne Compilerobjekt, falls es verfügbar ist. Dieser Parameter wird nur von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwendet. |
| Utf8Output | Ein boolescher Parameter. Wenn sein Wert `true` lautet, wird die Compilerausgabe mithilfe der UTF-8-Codierung protokolliert. Dieser Parameter entspricht dem `/utf8Output`-Compilerschalter. |
| VbcToolPath | Ein optionaler Pfad, der einen anderen Speicherort für *vbc.exe* angibt, wenn die aktuelle Version von *vbc.exe* überschrieben wurde. |
| VbcVerbosity | Gibt den Ausführlichkeitsgrad der Ausgabe des [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Compilers an. Gültige Werte sind "Quiet", "Normal" (der Standardwert) und "Verbose". |
| VisualStudioVersion | Gibt die Version von Visual Studio an, mit der dieses Projekt ausgeführt werden sollte. Wenn diese Eigenschaft nicht angegeben wird, wird ein angemessener Standardwert von MSBuild festgelegt.<br /><br /> Diese Eigenschaft wird in mehreren Projekttypen verwendet, um den Satz der Ziele anzugeben, die für den Build verwendet werden. Wenn für `ToolsVersion` "4.0" oder ein höherer Wert für ein Projekt festgelegt wird, wird das zu verwendende Unter-Toolset mithilfe von `VisualStudioVersion` festgelegt. Weitere Informationen finden Sie unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Dieser Parameter entspricht dem `/warnaserror`-Compilerschalter. |
| WarningsNotAsErrors | Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Dieser Parameter entspricht dem `/warnaserror`-Compilerschalter. |
| Win32Manifest | Der Name der Manifestdatei, die in die endgültige Assembly eingebettet werden soll. Dieser Parameter entspricht dem `/win32Manifest`-Compilerschalter. |
| Win32Resource | Der Dateiname der Win32-Ressource, die in die endgültige Assembly eingebettet werden soll. Dieser Parameter entspricht dem `/win32resource`-Compilerschalter. |

## <a name="see-also"></a>Siehe auch
- [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
