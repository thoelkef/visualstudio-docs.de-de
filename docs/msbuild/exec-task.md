---
title: Exec-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f588ae1b32b8b8d47d6323ee32d02c9053a3de32
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634213"
---
# <a name="exec-task"></a>Exec-Aufgabe

Führt das angegebene Programm oder den Befehl mit den angegebenen Argumenten aus.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter für die `Exec`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Command`|Erforderlicher `String` -Parameter.<br /><br /> Der/die auszuführende(n) Befehl(e). Dies kann ein Systembefehl sein, z.B. „attrib“, oder eine ausführbare Datei wie *program.exe*, *runprogram.bat* oder *setup.msi*.<br /><br /> Dieser Parameter kann mehrere Zeilen mit Befehlen enthalten. Alternativ können Sie mehrere Befehle in einer Batchdatei speichern und sie ausführen, indem Sie diesen Parameter verwenden.|
|`ConsoleOutput`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Jede Elementausgabe stellt eine Zeile der Standardausgabe oder einen Standardfehlerstream dar, der vom Tool ausgegeben wird. Dies wird nur erfasst, wenn `ConsoleToMsBuild` auf `true` festgelegt ist.|
|`ConsoleToMsBuild`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, erfasst der Task den Standardfehler und die Standardausgabe des Tools und macht sie im Ausgabeparameter `ConsoleOutput` verfügbar.<br /><br />Standardwert: `false`.|
|`CustomErrorRegularExpression`|Optionaler `String`-Parameter.<br /><br /> Legt einen regulären Ausdruck fest, der verwendet wird, um Fehlerzeilen in der Ausgabe des Tools zu erkennen. Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.<br /><br />Standardwert: `null` (keine benutzerdefinierte Verarbeitung).|
|`CustomWarningRegularExpression`|Optionaler `String`-Parameter.<br /><br /> Legt einen regulären Ausdruck fest, der verwendet wird, um Warnungszeilen in der Ausgabe des Tools zu erkennen. Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.<br /><br />Standardwert: `null` (keine benutzerdefinierte Verarbeitung).|
|`EchoOff`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, gibt der Task nicht die erweiterte Form von `Command` an das MSBuild-Protokoll aus.<br /><br />Standardwert: `false`.|
|`ExitCode`|Optionaler schreibgeschützter `Int32`-Ausgabeparameter.<br /><br /> Gibt den durch den ausgeführten Befehl bereitgestellten Exitcode an.|
|`IgnoreExitCode`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, ignoriert die Aufgabe den durch den ausgeführten Befehl bereitgestellten Exitcode. Andernfalls gibt die Aufgabe `false` zurück, wenn der ausgeführte Befehl einen Exitcode ungleich null (0) zurückgibt.<br /><br />Standardwert: `false`.|
|`IgnoreStandardErrorWarningFormat`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `false`, werden Zeilen in der Ausgabe ausgewählt, die dem standardmäßigen Fehler-/Warnungsformat entsprechen, und als Fehler/Warnungen protokolliert. Wenn `true`, wird dieses Verhalten deaktiviert.<br /><br />Standardwert: `false`.|
|`Outputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ausgabeelemente aus der Aufgabe. Die `Exec`-Aufgabe legt diese nicht selbst fest. Stattdessen können Sie sie so bereitstellen, als ob die Aufgabe sie festgelegt hätte, damit sie später im Projekt verwendet werden können.|
|`StdErrEncoding`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Codierung des standardmäßigen Fehlerdatenstroms der erfassten Aufgabe an. Der Standardwert ist die aktuelle Konsolenausgabencodierung.|
|`StdOutEncoding`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Codierung des standardmäßigen Ausgabedatenstroms der erfassten Aufgabe an. Der Standardwert ist die aktuelle Konsolenausgabencodierung.|
|`WorkingDirectory`|Optionaler `String`-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem der Befehl ausgeführt wird.<br /><br />Standard: Das aktuelle Arbeitsverzeichnis des Projekts.|

## <a name="remarks"></a>Hinweise

Diese Aufgabe ist nützlich, wenn eine bestimmte MSBuild-Aufgabe für den auszuführenden Auftrag nicht verfügbar ist. Im Gegensatz zu einer spezifischeren Aufgabe kann die `Exec`-Aufgabe jedoch keine zusätzliche Verarbeitung oder bedingten Vorgänge durchführen, die auf dem Ergebnis des Tools oder des Befehls basieren, das bzw. der von dieser ausgeführt wird.

Die `Exec`-Aufgabe ruft *cmd.exe* auf, anstatt direkt einen Prozess aufzurufen.

Zusätzlich zu den in diesem Artikel aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die `Exec`-Aufgabe zum Ausführen eines Befehls verwendet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
