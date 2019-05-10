---
title: AssignProjectConfiguration-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bc9fb3ab600c106d762d5f4ec55b6bc7117e101
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822899"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration-Aufgabe
Diese Aufgabe akzeptiert eine Liste von Konfigurationszeichenfolgen und weist sie angegebenen Projekten zu.

## <a name="task-parameters"></a>Aufgabenparameter
 In der folgenden Tabelle werden die Parameter der `AssignProjectConfiguration` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`SolutionConfigurationContents`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält eine XML-Zeichenfolge mit einer Projektkonfiguration für jedes Projekt. Die Konfigurationen werden den benannten Projekten zugewiesen.|
|`DefaultToVcxPlatformMapping`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält eine durch Semikolons getrennte Liste mit Zuordnungen zwischen den von den meisten Typen verwendeten Plattformnamen und den von *VCXPROJ*-Dateien verwendeten Plattformnamen.<br /><br /> Beispiel:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string`-Ausgabeparameter.<br /><br /> Enthält eine durch Semikolons getrennte Liste mit Zuordnungen zwischen *VCXPROJ*-Plattformnamen und den von den meisten Typen verwendeten Plattformnamen.<br /><br /> Beispiel:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält die Konfiguration für das aktuelle Projekt.|
|`CurrentProjectPlatform`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält die Plattform für das aktuelle Projekt.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, dass Verweise erstellt werden sollen, auch wenn sie in der Projektkonfiguration deaktiviert wurden.|
|`ShouldUnsetParentConfigurationAndPlatform`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, ob die übergeordnete Konfiguration und Plattform gelöscht werden sollen.|
|`OutputType`|Optionaler `string`-Ausgabeparameter.<br /><br /> Enthält den Ausgabetyp für das Projekt.|
|`ResolveConfigurationPlatformUsingMappings`|Optionaler `bool`-Ausgabeparameter.<br /><br /> Enthält ein Flag, das angibt, ob der Build die Standardzuordnungen verwenden soll, um die Konfiguration und Plattform der übergebenen Projektverweise aufzulösen.|
|`AssignedProjects`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Liste der aufgelösten Verweispfade.|
|`UnassignedProjects`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Liste der Projektverweiselemente, die nicht mithilfe der Liste vorab aufgelöster Ausgaben aufgelöst werden konnten.|

## <a name="remarks"></a>Anmerkungen
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)