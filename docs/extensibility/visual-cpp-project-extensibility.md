---
title: Visual C++-projekterweiterbarkeit
ms.custom: ''
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b9f8bfcaf9e6f584d4f0038ebef17daad3aa74a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850807"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++-Projekt Erweiterbarkeit und Toolset Systemintegration

Die *Visual C++-Projektsystem* vcxproj-Dateien verwendet wird. Es basiert auf der [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) und bietet zusätzlich spezifische C++-Erweiterungspunkte, mit denen eine einfache Integration von neue Toolsets, Build-Architekturen und Zielplattformen. 

## <a name="c-msbuild-targets-structure"></a>C++-MSBuild-Ziele-Struktur

Alle vcxproj-Dateien importieren, diese Dateien:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Diese Dateien definieren wenig selbst. Stattdessen importieren sie die anderen Dateien, die basierend auf diese Eigenschaftswerte:

- `$(ApplicationType)`

   Beispiele: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Dies muss eine gültige Versionszeichenfolge, der das Formular major.minor sein]].

   Beispiele: 1.0, 10.0.0.0

- `$(Platform)`

   Die Build-Architektur ist mit dem Namen "Platform" Historisch bedingt.

   Beispiele: Win32 "," X86, X64, ARM   

- `$(PlatformToolset)`

   Beispiele: v140, v141, v141_xp, llvm

Diese Eigenschaftswerte Geben Sie die Namen von Ordnern unter dem `$(VCTargetsPath)` Stammordner:

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Anwendungstyp*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Plattformen*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*\PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Plattformen\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(wird verwendet, wenn `$(ApplicationType)` leer ist, für Windows Desktop-Projekte)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*\PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Fügen Sie ein neues Plattformtoolset hinzu.

Erstellen ein neues Toolsets, z. B. "MyToolset" für die vorhandenen Win32-Plattform Hinzufügen einer *MyToolset* Unterordner `$(VCTargetsPath)`  *\\Plattformen\\Win32\\ \PlatformToolsets\\*, und erstellen Sie *Toolset.props* und *Toolset.targets* darin enthaltenen Dateien.

Ordnernamen weisen unter *\PlatformToolsets* wird in der **Projekteigenschaften** Dialogfeld als einen verfügbaren **Plattformtoolset** für die angegebene Plattform, wie hier gezeigt:

![Die Plattformtoolset-Eigenschaft in der Projekt-Eigenschaftenseiten (Dialogfeld)](media/vc-project-extensibility-platform-toolset-property.png "das Plattformtoolset-Eigenschaft in der Projekt-Eigenschaftenseiten (Dialogfeld)")

Erstellen Sie ähnliche *MyToolset* Ordner und *Toolset.props* und *Toolset.targets* Dateien in jedem vorhandenen Plattformordner dieses Toolset unterstützt.

### <a name="add-a-new-platform"></a>Hinzufügen einer neuen Plattform

Erstellen Sie eine neue Plattform, z. B. "MyPlatform", Hinzufügen einer *MyPlatform* Unterordner `$(VCTargetsPath)`  *\\Plattformen\\*, und erstellen Sie  *Platform.Default.props*, *Platform.props*, und *Platform.targets* darin enthaltenen Dateien. Erstellen Sie auch eine `$(VCTargetsPath)`  *\\Plattformen\\*<strong><em>MyPlatform</em></strong>*\\\PlatformToolsets\\*  Ordner, und mindestens ein Toolset erstellen.

Namen für alle Ordner unter der *Plattformen* Ordner für die einzelnen `$(ApplicationType)` und `$(ApplicationTypeRevision)` angezeigt werden, in der IDE als verfügbare **Plattform** Optionen für ein Projekt.

![Die neue Plattform Auswahl im Dialogfeld "Neue Projektplattform"](media/vc-project-extensibility-new-project-platform.png "der neuen Plattform Ihrer Wahl im Dialogfeld \"Neue Projektplattform\"")

### <a name="add-a-new-application-type"></a>Fügen Sie einen neuen Anwendungstyp hinzu.

Um einen neuen Anwendungstyp hinzuzufügen, erstellen Sie eine *MyApplicationType* Unterordner `$(VCTargetsPath)` *\\Anwendungstyp\\* , und erstellen Sie eine *Defaults.props* Datei. Mindestens eine Version für einen Anwendungstyp erforderlich ist, erstellen Sie damit auch eine `$(VCTargetsPath)`  *\\Anwendungstyp\\MyApplicationType\\1.0* Ordner, und erstellen Sie eine  *Defaults.props* Datei. Erstellen Sie auch eine `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\Plattformen* Ordner und mindestens eine Plattform erstellen.

`$(ApplicationType)` und `$(ApplicationTypeRevision)` Eigenschaften werden nicht in der Benutzeroberfläche angezeigt. Sie werden in den Projektvorlagen definiert und können nicht geändert werden, nachdem das Projekt erstellt wird.


## <a name="the-vcxproj-import-tree"></a>Die VCXPROJ-Import-Struktur

Eine vereinfachte Struktur von Direktiven für Dateien in Microsoft C++-Eigenschaften und-Zielen sieht wie folgt aus:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\ *"Microsoft.Common.props"*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*Standard*\\\*. *Eigenschaftendatei*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Plattformen* \\ `$(Platform)` \\  *Platform.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*Standard*\\\*. *Eigenschaftendatei*  

Windows-Desktop-Projekten nicht definieren `$(ApplicationType)`, sodass sie nur importieren

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\ *"Microsoft.Common.props"*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*Standard*\\\*. *Eigenschaftendatei*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Plattformen*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*Standard*\\\*. *Eigenschaftendatei*  

Wir verwenden die `$(_PlatformFolder)` Eigenschaft zum Speichern der `$(Platform)` Ordnerpfade Plattform. Diese Eigenschaft ist 

> `$(VCTargetsPath)`\\*Plattformen*\\`$(Platform)`

für Windows Desktop-apps und 

> `$(VCTargetsPath)`\\*Anwendungstyp*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Plattformen*\\`$(Platform)`

für alles andere.

Die Props-Dateien werden in dieser Reihenfolge importiert:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *Eigenschaftendatei*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*\PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *Eigenschaftendatei*  

Targets-Dateien werden in dieser Reihenfolge importiert:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *Ziele*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*\PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *Ziele*  

Wenn Sie einige Standardeigenschaften für das Toolset definieren müssen, können Sie Dateien in die entsprechenden ImportBefore und ImportAfter Ordner hinzufügen.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Autor Toolset.props und Toolset.targets-Dateien

*Toolset.props* und *Toolset.targets* Dateien können vollständig steuern zu können, was während eines Builds geschieht, wenn dieses Toolset verwendet wird. Sie können auch steuern, die verfügbaren Debuggern bereit, einige der IDE-Benutzeroberfläche, z. B. den Inhalt in die **Eigenschaftenseiten** Dialogfeld, und einige andere Aspekte der Verhalten von Projekten.

Obwohl ein Toolset für den gesamten Buildprozess überschrieben werden kann, möchten Sie in der Regel nur das Toolset zu ändern oder hinzuzufügen, dass einige Schritte nutzen oder anderen Buildtools als Teil eines vorhandenen Build-Prozesses zu verwenden. Um dieses Ziel zu erreichen, gibt es zahlreiche häufig verwendete Eigenschaften und-Zielen-Dateien, die Ihr Toolset importieren kann. Je nachdem, was Ihr Toolset tun soll möglicherweise hilfreich, die als Importe oder als Beispiele verwenden diese Dateien:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Diese Datei definiert die wichtigsten Teile des Buildprozesses native und auch importiert:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\ *"Microsoft.Common.targets"*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Legt Standardeinstellungen für die Toolsets, die die Microsoft-Compiler und Windows als Ziel.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Diese Datei bestimmt den Speicherort des Windows SDK und einige wichtigen Eigenschaften für apps und Windows definiert.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrieren Sie mit der standardmäßigen C++-Buildprozess Toolset-spezifische Ziele 

Die Standardeinstellung, die C++-Buildprozess wird definiert, *Microsoft.CppCommon.targets*. Die Ziele gibt es aufrufen kein bestimmten Build-Tools. Sie geben der Hauptknoten Schritte, deren Reihenfolge und die Abhängigkeiten erstellen.

Der C++-Build verfügt über drei Hauptschritte, die durch die folgenden Ziele dargestellt werden:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Da jede Buildschritt unabhängig voneinander ausgeführt werden kann, können nicht Ziele, die in einem Schritt ausgeführt basieren, für die Elementgruppen und Eigenschaften, die in den Zielen, die ausgeführt werden als Teil von einem anderen Schritt definiert. Dieser Trennung kann bestimmte Build leistungsoptimierungen. Obwohl es nicht standardmäßig verwendet wird, sollten Sie immer noch durch diese Trennung der bandbreitendrosselung zu berücksichtigen.

Die Ziele, die in jedem Schritt ausgeführt werden, werden anhand dieser Eigenschaften gesteuert:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Jeder Schritt hat auch vor und nach Eigenschaften. 

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Finden Sie unter den *Microsoft.CppBuild.targets* -Datei für die Beispiele für die Ziele, die in jedem Schritt enthalten sind:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Wenn Sie die Ziele, z. B. betrachten `_ClCompile`, sehen Sie sie nicht alles direkt von selbst, sondern stattdessen andere Ziele, einschließlich von `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` und andere Build-Tool-spezifische Ziele werden als leeren Ziele in definiert *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Da die `ClCompile` Ziel ist leer, es sei denn, es durch ein Toolset überschrieben wird, wird keine Aktion echter Build ausgeführt. Die Ziele Toolset können außer Kraft setzen der `ClCompile` abzielen, d. h., sie können einen anderen `ClCompile` Definition nach dem Import *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Trotz seines Namens aus, die erstellt wurde, bevor Visual Studio plattformübergreifende Unterstützung implementiert, die `ClCompile` Ziel nicht zum Aufrufen von CL.exe haben. Sie können auch Gcc, Clang oder andere Compiler aufrufen, mit der entsprechenden MSBuild-Aufgaben.

Die `ClCompile` Ziel sollten keine Abhängigkeiten mit Ausnahme der `SelectClCompile` Ziel, die für die Einzeldatei Compile-Befehl funktioniert in der IDE erforderlich ist.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>MSBuild-Aufgaben für die Verwendung im Toolset-Ziele

Wenn ein tatsächlicher Build-Tool aufrufen möchten, muss das Ziel eine MSBuild-Aufgabe aufrufen. Es ist eine grundlegende [Exec-Aufgabe](../msbuild/exec-task.md) , mit der Sie an einer Befehlszeile ausführen. Build-Tools müssen jedoch in der Regel viele Optionen, Eingaben. und Ausgaben für inkrementelle builds, nachverfolgen, deshalb ist es sinnvoller, die spezielle Aufgaben für Sie gespeichert haben. Z. B. die `CL` Task übersetzt von MSBuild-Eigenschaften in CL.exe-Switches, schreibt sie in einer Antwortdatei und ruft von CL.exe. Sie verfolgt auch alle Eingabe- und Dateien später inkrementelle Builds. Weitere Informationen finden Sie unter [inkrementeller Build, und überprüfen Sie auf dem neuesten Stand](#incremental-build-and-up-to-date-check).

Die Microsoft.Cpp.Common.Tasks.dll implementiert diese Aufgaben:

- `BSCMake`

- `CL`

- `ClangCompile` (Clang-Gcc-Schalter)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (z. B. Exec jedoch mit Eingabe und Ausgabe, die nachverfolgung)

- `SetEnv`

Wenn Sie ein Tool verfügen, die die gleiche Aktion wie ein vorhandenes Tool, und ähnliche Befehlszeilenoptionen (wie "Clang-cl" und CL) aufweist, können Sie die gleiche Aufgabe für beide Ausgaben.

Wenn Sie einen neuen Task für einen Buildtool erstellen möchten, können Sie anhand der folgenden Optionen auswählen:

1. Wenn Sie diese Aufgabe nur selten verwenden oder ein paar Sekunden für Ihren Build wichtig sind, nicht, können Sie MSBuild 'Inline'-Aufgaben verwenden:

   - XAML-Aufgabe (eine benutzerdefinierte Buildregel)

     Ein Beispiel für eine Deklaration einer XAML-Aufgabe, finden Sie unter `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*, und dessen Verwendung finden Sie unter `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Code-Aufgabe](../msbuild/msbuild-inline-tasks.md)

1. Wenn Sie eine bessere Leistung der Aufgabe oder nur die komplexere Funktionalität benötigen, verwenden Sie den reguläre MSBuild [Schreiben von Aufgaben](../msbuild/task-writing.md) Prozess.

   Wenn nicht alle Eingaben und Ausgaben des Tools in der Tool-Befehlszeile, als in aufgeführt sind die `CL`, `MIDL`, und `RC` Fällen, und wenn Sie automatische Eingabe und Ausgabe dateinachverfolgung und TLog-Datei erstellen möchten, leiten Sie Ihre Aufgabe aus der `Microsoft.Build.CPPTasks.TrackedVCToolTask`Klasse. Derzeit ist die Dokumentation für die Basis [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) Klasse, es gibt keine Beispiele oder Dokumentation für die Details der `TrackedVCToolTask` Klasse. Wenn dies von besonderem Interesse ist, fügen Sie Ihre Stimme auf eine Anforderung auf [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Inkrementelle Builds und auf dem neuesten Stand überprüft

Der inkrementelle Standardwert MSBuild-Build ausgerichtet ist, verwenden `Inputs` und `Outputs` Attribute. Wenn Sie diese angeben, ruft MSBuild das Ziel nur, wenn eine der Eingaben einen neueren Zeitstempel als alle Ausgaben auf. Da Quelldateien häufig enthalten oder andere Dateien importieren und Tools erzeugen verschiedene Ausgaben abhängig von den Optionen des Tools zu erstellen, ist schwierig, geben Sie alle Mögliche Eingaben und Ausgaben in MSBuild-Ziele.

Um dieses Problem zu lösen, verwendet der C++-Build eine andere Methode, um inkrementelle Builds zu unterstützen. Die meisten Ziele nicht angeben von Eingaben und Ausgaben, und es wird daher immer während des Buildvorgangs ausgeführt wird. Die Aufgaben, die aufgerufen wird, von Zielen zu schreiben, Informationen zu allen Eingaben und Ausgaben in *Tlog* Dateien, die eine TLog-Dateierweiterung aufweisen. Die Nachverfolgungsprotokolldateien sind von späteren Builds verwendet, um zu überprüfen, was hat sich geändert und muss neu erstellt werden, und was auf dem neuesten Stand ist.

Um die Eingaben und Ausgaben zu bestimmen, einheitlichen Aufgaben tracker.exe verwenden und die [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) Klasse, die von MSBuild bereitgestellt.

Microsoft.Build.CPPTasks.Common.dll definiert die `TrackedVCToolTask` öffentliche abstrakte Basisklasse. Die meisten systemeigenen Tools Aufgaben werden von dieser Klasse abgeleitet.

## <a name="tlog-files"></a>TLog-Dateien

Es gibt drei Arten von Nachverfolgungsprotokolldateien: *lesen*, *schreiben*, und *Befehlszeilen*. Lese- und Schreibvorgänge TLog-Dateien werden durch inkrementelle Builds und die aktualitätsprüfung in der IDE verwendet werden. Befehlszeile TLog-Dateien sind nur in inkrementelle Builds verwendet.

MSBuild stellt Hilfsklassen zum Lesen und Schreiben von TLog-Dateien:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Die [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) Klasse kann verwendet werden, um Zugriff auf Lese- und Nachverfolgungsprotokolldateien geschrieben und identifizieren die Eingaben, die höher als gibt oder wenn eine Ausgabe nicht vorhanden ist. Es wird in die aktualitätsprüfung verwendet.

Befehlszeile TLog-Dateien enthalten Informationen über die Befehlszeilen, die in den Build verwendet werden. Sie werden nur verwendet für inkrementelle Builds nicht auf dem neuesten Stand Überprüfungen aus, damit das interne Format von der MSBuild-Aufgabe bestimmt wird, die diese hervorbringen.

Wenn Nachverfolgungsprotokolldateien, die von einer Aufgabe erstellt werden, empfiehlt es sich, diese Hilfsklassen verwenden, um sie zu erstellen. Jedoch, weil die Standard-aktualitätsprüfung jetzt ausschließlich auf die Nachverfolgungsprotokolldateien verwendet, ist manchmal empfiehlt es sich um sie in einem Ziel ohne einen Task zu erstellen. Sie können diese schreiben, mit der `WriteLinesToFile` Aufgabe. Finden Sie unter den `_WriteMasmTlogs` im Ziel `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* als Beispiel.

### <a name="read-tlog-format"></a>Read-TLog-format

*Lesen* TLog-Dateien (\*. Read.\*. TLog) enthält Informationen zu den Quelldateien und ihre Abhängigkeiten.

Ein Caretzeichen (**^**) am Anfang einer Zeile gibt Sie an einer oder mehreren Quellen. Datenquellen, die gemeinsam die gleichen Abhängigkeiten werden durch einen senkrechten Strich getrennt (**\|**).

Nach der Quellen, die auf einer eigenen Zeile werden Abhängigkeitsdateien aufgeführt. Alle Dateinamen sind vollständige Pfade.

Nehmen wir beispielsweise an, die Ihre Projektquellen befinden sich unter *F:\\testen\\ConsoleApplication1\\ConsoleApplication1*. Wenn Ihre Quelldatei *"Class1.cpp"*, hat diese Anweisungen enthält,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

die *CL.read.1.tlog* -Datei enthält die Quelldatei, gefolgt von zwei Abhängigkeiten:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Dateinamen in Großbuchstaben zu schreiben ist nicht erforderlich, aber es ist eine bequeme Möglichkeit zum einige Tools.

### <a name="write-tlog-format"></a>Schreiben Sie TLog-format

*Schreiben von* .tlog (\*.write.\*. Nachverfolgungsprotokolldateien) verbinden Quellen und Ausgaben.

Ein Caretzeichen (**^**) am Anfang einer Zeile gibt Sie an einer oder mehreren Quellen. Mehrere Datenquellen werden getrennt durch einen senkrechten Strich (**\|**).

Die Ausgabedateien, die aus den Quellen erstellt, sollte nach der die Quellen, die auf einer eigenen Zeile aufgeführt werden. Alle Dateinamen muss die vollständige Pfade.

Z. B. für ein einfaches ConsoleApplication-Projekt, die eine zusätzliche Quelldatei *"Class1.cpp"*, *link.write.1.tlog* Datei enthalten kann:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Während der Entwurfszeit-build

In der IDE verwenden VCXPROJ-Projekte einen Satz von MSBuild-Ziele, zum Abrufen zusätzlicher Informationen aus dem Projekt und Ausgabedateien zu generieren. Einige dieser Ziele dienen nur zur Entwurfszeit-Builds, aber viele von ihnen in regelmäßige Erstellen von Builds und während der Entwurfszeit-Builds verwendet werden.

Allgemeine Informationen zu den Entwurfszeit-Builds, finden Sie in der CPS-Dokumentation für [erstellt während der Entwurfszeit](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Diese Dokumentation ist nur teilweise auf Visual C++-Projekte anwendbar.

Die `CompileDesignTime` und `Compile` Ziele, die in der Entwurfszeit erwähnt erstellt, Dokumentation, die nie für VCXPROJ-Projekte ausführen. Visual C++-VCXPROJ-Projekte verwenden verschiedene während der Entwurfszeit-Ziele, um IntelliSense-Informationen zu erhalten.

### <a name="design-time-targets-for-intellisense-information"></a>Während der Entwurfszeit-Ziele für IntelliSense-Informationen

Die während der Entwurfszeit-Ziele, die in der VCXPROJ-Projekten verwendet werden in definiert `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

Die `GetClCommandLines` Ziel erfasst Compileroptionen für IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – während der Entwurfszeit nur Ziele, die erforderlich sind, für die Entwurfszeit Initialisierung zu erstellen. Unter anderem deaktivieren Sie diese Ziele Teil der regulären Build-Funktionen zur Verbesserung der Leistung.

- `ComputeCompileInputsTargets` – eine Gruppe von Zielen, die Compileroptionen und Elemente ändert. Führen Sie diese Ziele in sowohl zur Entwurfszeit und regelmäßige Builds.

Die Ziel-Aufrufe der `CLCommandLine` Aufgabe erstellen Sie die Befehlszeile für IntelliSense verwendet. In diesem Fall kann es trotz seines Namens nicht nur CL-Optionen, sondern auch die Optionen ' Clang und Gcc verarbeiten. Der Typ, der den Compilerschaltern wird gesteuert, indem die `ClangMode` Eigenschaft.

Derzeit die Befehlszeile erstellt, durch die `CLCommandLine` Task verwendet CL-Switches immer (sogar im Clang-Modus), da sie einfacher für die IntelliSense-Engine analysiert werden.

Wenn Sie ein Ziel hinzufügen, die ausgeführt wird, vor der Kompilierung, regulären oder zur Entwurfszeit, stellen Sie sicher, dass es nicht unterbrechen kann zur Entwurfszeit erstellt oder auf die Leistung auswirken. Die einfachste Möglichkeit, testen Sie Ihr Ziel ist, öffnen Sie eine Developer-Eingabeaufforderung, und führen Sie diesen Befehl:

> MSBuild-/p:SolutionDir =*Lösung-Verzeichnis-mit-nachfolgende-umgekehrten Schrägstrich*; Konfiguration = Debuggen; Plattform = Win32; BuildingInsideVisualStudio = True; DesignTimebuild = "true" / t:\_PerfIntellisenseInfo/v: d/fl /fileloggerparameters:PerformanceSummary \*.vcxproj

Dieser Befehl erzeugt eine ausführliche Buildprotokoll *msbuild.log*, am Ende eine Zusammenfassung für die Ziele und Aufgaben Leistung aufweist.

Achten Sie darauf, verwenden Sie `Condition ="'$(DesignTimeBuild)' != 'true'"` in alle Vorgänge, die nur für regelmäßige Erstellen von Builds und nicht für die Entwurfszeit-Builds sinnvoll.

### <a name="design-time-targets-that-generate-sources"></a>Während der Entwurfszeit-Ziele, die Quellen generieren

*Dieses Feature ist für systemeigene Desktop-Projekte standardmäßig deaktiviert und wird derzeit nicht für zwischengespeicherte Projekte unterstützt*.

Wenn `GeneratorTarget` Metadaten für ein Projekt definiert ist, wird das Ziel wird automatisch sowohl ausgeführt, wenn das Projekt geladen wird und wenn die Quelldatei geändert wird.

Z. B. zum automatischen Generieren von .cpp oder. h-Dateien von XAML-Dateien, die `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* Dateien definieren Entitäten:

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Verwendung von `Task.HostObject` rufen Sie den nicht gespeicherten Inhalt von Quelldateien, die Ziele und die Aufgabe als registriert werden soll [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) für die angegebenen Projekte in einer Pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++-Projekt-Erweiterbarkeit in Visual Studio-IDE

Die Visual C++-Projektsystem beruht auf der [Visual Studio-Projektsystem](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md), und ihre Erweiterungspunkte verwendet. Allerdings die Projekt-Hierarchie-Implementierung ist Visual C++-spezifisch und nicht auf CPS basiert, daher Hierarchie Erweiterbarkeit ist auf Projektelemente.

### <a name="project-property-pages"></a>Projekteigenschaftenseiten

Weitere Informationen zum allgemeinen Entwurf, finden Sie unter [Plattformerweiterbarkeit - Teil 1](http://blogs.msdn.com/b/vsproject/archive/2009/06/10/platform-extensibility-part-1.aspx) und [plattformerweiterbarkeit - Teil 2](http://blogs.msdn.com/b/vsproject/archive/2009/06/18/platform-extensibility-part-2.aspx).

Im einfach ausgedrückt, die Eigenschaftenseiten finden Sie der **Projekteigenschaften** Dialogfeld für ein C++-Projekt definieren, indem *Regel* Dateien. Eine Regeldatei gibt es sich um einen Satz von Eigenschaften, die auf einer Eigenschaftenseite anzeigen und Datei, wie und wo sie in das Projekt gespeichert werden soll. Regeldateien sind XML-Dateien, die XAML-Format verwenden. Die Typen verwendet, um sie zu serialisieren, werden in beschrieben [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Weitere Informationen zur Verwendung der Regeldateien in Projekten, finden Sie unter [Eigenschaftenseite: XML-Regeldateien](/cpp/ide/property-page-xml-files).

Die Regel muss hinzugefügt werden die `PropertyPageSchema` Elementgruppe:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` Grenzwerte Regel Sichtbarkeit von Metadaten, die auch durch Regeltyp gesteuert und kann einen der folgenden Werte aufweisen:

> `Project` | `File` | `PropertySheet`

CPS unterstützt andere Werte für den Typ, aber sie können in Visual C++-Projekten nicht verwendet.

Wenn die Regel in mehr als einem Kontext angezeigt werden soll, verwenden Sie Semikolons (**;**) um die Kontextwerte zu trennen, wie hier gezeigt:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Regelformat und Haupttypen

Das Regelformat ist einfach, damit Sie diesem Abschnitt wird nur die Attribute beschrieben, die beeinflussen, wie die Regel in der Benutzeroberfläche aussieht.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

Die `PageTemplate` Attribut wird definiert, wie die Regel angezeigt wird, in der **Eigenschaftenseiten** Dialogfeld. Das Attribut kann einen der folgenden Werte aufweisen:


| Attribut | Beschreibung |
|------------| - |
| `generic` | Alle Eigenschaften werden auf einer Seite unter Kategorieüberschriften angezeigt.<br/>Die Regel kann für sichtbar sein `Project` und `PropertySheet` Kontexte, aber nicht `File`.<br/><br/> Beispiel: `$(VCTargetsPath)` \\ *1033*\\ *"debugger_general.xml"* |
| `tool` | Kategorien werden als Unterseiten angezeigt.<br/>Die Regel kann in allen Kontexten angezeigt werden: `Project`, `PropertySheet` und `File`.<br/>Die Regel in den Projekteigenschaften angezeigt wird, nur, wenn das Projekt Elemente mit der `ItemType` in definierten `Rule.DataSource`, es sei denn, der den Namen der Regel enthalten ist, in der `ProjectTools` Elementgruppe.<br/><br/>Beispiel: `$(VCTargetsPath)` \\ *1033*\\*clang.xml* |
| `debugger` | Die Seite wird als Teil der Seite "Debuggen" angezeigt.<br/>Kategorien werden derzeit ignoriert.<br/>Name der Regel sollte des Debuggen Startprogramm MEF-Objekts übereinstimmen `ExportDebugger` Attribut.<br/><br/>Beispiel: `$(VCTargetsPath)` \\ *1033*\\*Debugger\_lokalen\_windows.xml* |
| *custom* | Benutzerdefinierte Vorlage. Der Name der Vorlage sollte übereinstimmen der `ExportPropertyPageUIFactoryProvider` Attribut der `PropertyPageUIFactoryProvider` MEF-Objekt. Finden Sie unter **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Beispiel: `$(VCTargetsPath)` \\ *1033*\\*userMacros.xml* |

Wenn die Regel eine der Eigenschaftenraster-basierte Vorlagen verwendet, können sie diese Erweiterbarkeitspunkte für die zugehörigen Eigenschaften:

- [Eigenschaftswert-Editoren](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dynamische Enum-Werte-Anbieter](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Erweitern Sie eine Regel

Sollten Sie verwenden eine vorhandene Regel. allerdings müssen zum Hinzufügen oder entfernen (der verborgen wird) nur wenige Eigenschaften, die Sie erstellen eine [gruppenerweiterungsregel](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Überschreiben einer Regelsatzes

Vielleicht möchten Sie Ihr Toolset in den meisten Standardregeln Projekt verwenden, sondern nur einige davon ersetzt. Angenommen Sie, dass Sie nur ändern, die C/C++-Regel, um verschiedene Compilerschalter anzeigen möchten. Sie können eine neue Regel mit dem gleichen Namen geben und Namen als die vorhandene Regel anzeigen und nehmen Sie diese in die `PropertyPageSchema` Gruppe nach dem Import der Cpp-Standardziele. Nur eine Regel mit einem angegebenen Namen im Projekt verwendet wird, der als letztes enthaltenen und in der `PropertyPageSchema` Gruppe Wins Element.

#### <a name="project-items"></a>Projektelemente

Die *"projectitemsschema.xml" angezeigt* -Datei definiert die `ContentType` und `ItemType` Werte für Elemente, die als Projektelemente behandelt werden, und definiert `FileExtension` Elemente, um zu bestimmen, welche Gruppe eine neue Datei hinzugefügt wird.

Die standardmäßige ProjectItemsSchema-Datei befindet sich im `$(VCTargetsPath)` \\ *1033*\\ *"projectitemsschema.xml" angezeigt*. So erweitern, müssen Sie eine Schemadatei mit erstellen einen neuen Namen, z. B. *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Klicken Sie dann in den Targets-Datei, fügen Sie Folgendes hinzu:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Beispiel: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Debugger

Die Debug-Diensts in Visual Studio unterstützt die Erweiterbarkeit für die Debug-Engine. Weitere Informationen finden Sie in diesen Beispielen:

- [MIEngine, open-Source-Projekt, das debugging von Lldb unterstützt](https://github.com/Microsoft/MIEngine)

- [Visual Studio-Debug-Engine-Beispiel](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Um die Debug-Engines und andere Eigenschaften für die Debugsitzung angeben möchten, müssen Sie implementieren eine [Debuggen Startprogramm](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF-Komponente, und fügen eine `debugger` Regel. Ein Beispiel finden Sie unter den `$(VCTargetsPath)` \\1033\\Debugger\_lokalen\_windows.xml-Datei.

### <a name="deploy"></a>Bereitstellen

VCXPROJ-Projekte verwenden, die Visual Studio-Projektsystem-Erweiterbarkeit für [Deploy-Anbieter](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Überprüfen Sie auf dem neuesten Stand erstellen

Standardmäßig erfordert die aktualitätsprüfung Build Lese .tlog und Write-Nachverfolgungsprotokolldateien, die erstellt werden die `$(TlogLocation)` Ordner während des Buildvorgangs für alle Build-Eingaben und Ausgaben.

So verwenden Sie eine benutzerdefinierte Prüfung für die auf dem neuesten Stand:

1. Deaktivieren Sie die Standard-aktualitätsprüfung durch Hinzufügen der `NoVCDefaultBuildUpToDateCheckProvider` -Funktion in der *Toolset.targets* Datei:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementieren Sie eine eigene [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Upgraden von Projekten

### <a name="default-vcxproj-project-upgrader"></a>Standardmäßige VCXPROJ Projekt upgrader

Die VCXPROJ-Projekt Upgrader Änderungen am Standardverhalten bei der `PlatformToolset`, `ApplicationTypeRevision`, MSBuild-Toolset-Version und .net Framework. Die letzten zwei erhalten immer die Standardeinstellungen für den Visual Studio-Version, aber `PlatformToolset` und `ApplicationTypeRevision` kann gesteuert werden, indem spezielle MSBuild-Eigenschaften.

Die Upgrader verwendet diese Kriterien um zu entscheiden, ob ein Projekt oder nicht aktualisiert werden kann:

1. Für Projekte, die definieren, `ApplicationType` und `ApplicationTypeRevision`, ein Ordner mit einer höheren Revisionsnummer als die aktuelle vorhanden ist.

1. Die Eigenschaft `_UpgradePlatformToolsetFor_<safe_toolset_name>` für das aktuelle Toolset definiert ist und sein Wert entspricht nicht dem aktuellen Toolsets.

   In diesen Eigenschaftsnamen  *\<Safe_toolset_name >* mit allen nicht-alphanumerische Zeichen, die durch einen Unterstrich ersetzt der den Namen der Toolset darstellt (**\_**).

Wenn ein Projekt nicht aktualisiert werden kann, wird es beteiligt ist *Lösung Neuzuweisungen*. Weitere Informationen finden Sie unter [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Sollten Sie Projektnamen in Verzieren **Projektmappen-Explorer** Wenn Projekte ein bestimmtes Toolsets verwenden, definieren eine `_PlatformToolsetShortNameFor_<safe_toolset_name>` Eigenschaft.

Beispiele für `_UpgradePlatformToolsetFor_<safe_toolset_name>` und `_PlatformToolsetShortNameFor_<safe_toolset_name>` Eigenschaftendefinitionen, finden Sie unter den *Microsoft.Cpp.Default.props* Datei. Anwendungsbeispiele finden Sie unter den `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* Datei.

### <a name="custom-project-upgrader"></a>Benutzerdefinierte Projektvorlagen upgrader

Um ein benutzerdefiniertes Upgrader Projektobjekt zu verwenden, implementieren Sie eine MEF-Komponente, wie hier gezeigt:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Ihr Code kann importieren und das Standardobjekt für VCXPROJ Upgrader aufrufen:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` wird in definiert *Microsoft.VisualStudio.ProjectSystem.VS.dll* und ähnelt `IVsRetargetProjectAsync`.

Definieren der `VCProjectUpgraderObjectName` Eigenschaft anzuweisen, dass das Projektsystem, Ihre benutzerdefinierten upgrademodul-Objekt zu verwenden:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Upgraden von Projekten deaktivieren

Verwenden Sie zum Deaktivieren von Projektupgrades eine `NoUpgrade` Wert:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Ein projektcache und Erweiterbarkeit

Zur Verbesserung der Leistung bei der Arbeit mit großen C++-Projektmappen in Visual Studio 2017 die [Projekt Cache](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) wurde eingeführt. Die Implementierung erfolgt als eine SQLite-Datenbank, die mit Project-Daten aufgefüllt, und klicken Sie dann verwendet, um Projekte zu laden, ohne MSBuild oder CPS-Projekten in den Arbeitsspeicher geladen.

Keine CPS-Objekte, die für die VCXPROJ-Projekte, die aus dem Cache geladen vorhanden sind, die Erweiterung des MEF-Komponenten, die importiert werden, da `UnconfiguredProject` oder `ConfiguredProject` kann nicht erstellt werden. Um Erweiterbarkeit zu unterstützen, ist nicht der projektcache verwendet, wenn Visual Studio erkennt, ob ein Projekt MEF-Erweiterungen verwendet (oder vermutlich verwenden).

Diese Projekttypen sind immer vollständig geladen und CPS-Objekte im Arbeitsspeicher haben, damit alle MEF-Erweiterungen für sie erstellt werden:

- Startprojekte

- Projekte, die eine benutzerdefinierte Projektvorlagen Upgrader, d. h., sie definieren eine `VCProjectUpgraderObjectName` Eigenschaft

- Projekte, die Windows-Desktop, d. h. Ziel nicht, sie definieren eine `ApplicationType` Eigenschaft

- Freigegebene Elemente (.vcxitems) und alle Projekte, die auf durch .vcxitems Projekte importieren.

Wenn keine dieser Bedingungen erkannt werden, wird ein projektcache erstellt. Der Cache enthält alle Daten aus der MSBuild-Projekt erforderlich, um Antworten `get` Abfragen für `VCProjectEngine` Schnittstellen. Dies bedeutet, dass alle Änderungen an der MSBuild-Eigenschaften und Ziele auf der Dateiebene, die von einer Erweiterung ausgeführt sollte nur in Projekten, die aus dem Cache geladen.

## <a name="shipping-your-extension"></a>Versenden die Erweiterung

Informationen zum Erstellen von VSIX-Dateien finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md). Informationen dazu, wie, besondere Installationsspeicherorte, z. B. Dateien hinzuzufügen, zum Hinzufügen von Dateien unter `$(VCTargetsPath)`, finden Sie unter [installieren außerhalb der Ordner "Extensions"](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Der Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) bietet die Build-Engine und erweiterbares XML-basierte Format für Projektdateien. Sie sollten vertraut sein mit Basic [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md) und mit dem [MSBuild für Visual C++](/cpp/build/msbuild-visual-cpp-overview) funktioniert zum Erweitern von Visual C++-Projektsystem.

Das Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) stellt die Erweiterung der APIs, die von der CPS- und Visual C++-Projektsystem verwendet werden. Einen Überblick darüber, wie MEF von CPS verwendet wird, finden Sie unter [CPS und MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) in die [VSProjectSystem Überblick über MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Sie können das vorhandene Buildsystem zum Hinzufügen von Buildschritten oder neuer Dateitypen anpassen. Weitere Informationen finden Sie unter [Übersicht über MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview) und [arbeiten mit Projekteigenschaften](/cpp/ide/working-with-project-properties).
