---
title: VCToolTask-Klasse | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515254"
---
# <a name="vctooltask-base-class"></a>VCToolTask-Basisklasse

Viele Aufgaben erben letztlich von der <xref:Microsoft.Build.Utilities.Task>-Klasse und [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)-Klasse. Diese Klasse fügt den Aufgaben, die ihr abgeleitet werden, mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **VCToolTask**-Basisklasse beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Optionaler Parameter **Dictionary\<string, ToolSwitch>**|
|**AdditionalOptions**|Optionaler **string**-Parameter|
|**EffectiveWorkingDirectory**|Optionaler **string**-Parameter|
|**EnableErrorListRegex**|Optionaler **bool**-Parameter<br/><br/>Der Standardwert ist `true`.|
|**ErrorListRegex**|Optionaler **ITaskItem[]**-Parameter.|
|**ErrorListListExclusion**|Optionaler **ITaskItem[]**-Parameter.|
|**GenerateCommandLine**|Optionaler **string**-Parameter<br/><br/>Verwendet die Werte **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Optionaler **string**-Parameter<br/><br/>Verwendet die Werte **string[]** *switchesToRemove*, **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)<br/>
[Aufgaben](../msbuild/msbuild-tasks.md)