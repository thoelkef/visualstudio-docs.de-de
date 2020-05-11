---
title: VCToolTask-Klasse | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591670"
---
# <a name="vctooltask-base-class"></a>VCToolTask-Basisklasse

Viele Aufgaben erben von der <xref:Microsoft.Build.Utilities.Task>-Klasse und der [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)-Klasse. Diese Klasse fügt den Aufgaben, die ihr abgeleitet werden, mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **VCToolTask**-Basisklasse beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Optionaler Parameter **Dictionary\<string, ToolSwitch>**|
|**AdditionalOptions**|Optionaler **string**-Parameter|
|**EffectiveWorkingDirectory**|Optionaler **string**-Parameter|
|**EnableErrorListRegex**|Optionaler **bool**-Parameter.<br/><br/>Der Standardwert ist `true`.|
|**ErrorListRegex**|Optionaler **ITaskItem[]** -Parameter.|
|**ErrorListListExclusion**|Optionaler **ITaskItem[]** -Parameter.|
|**GenerateCommandLine**|Optionaler **string**-Parameter<br/><br/>Verwendet die Werte **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Optionaler **string**-Parameter<br/><br/>Verwendet die Werte **string[]** *switchesToRemove*, **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)<br/>
[Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
