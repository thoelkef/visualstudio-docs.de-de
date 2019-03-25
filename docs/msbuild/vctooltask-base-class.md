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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070443"
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