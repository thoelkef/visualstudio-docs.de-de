---
title: TrackedVCToolTask-Klasse | Microsoft-Dokumentation
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
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515440"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask-Basisklasse

Viele Aufgaben erben von der <xref:Microsoft.Build.Utilities.Task>-Klasse und der [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)-Klasse. Diese Klasse fügt den von [VCToolTask](../msbuild/vctooltask-base-class.md) abgeleiteten Aufgaben mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **TrackedVCToolTask**-Basisklasse beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Optionaler **bool**-Parameter|
|**EnableExecuteTool**|Optionaler **bool**-Parameter|
|**ExcludedInputPaths**|Optionaler **ITaskItem[]**-Parameter.|
|**MinimalRebuildFromTracking**|Optionaler **bool**-Parameter|
|**PathOverride**|Optionaler **string**-Parameter|
|**PostBuildTrackingCleanup**|Optionaler **bool**-Parameter|
|**RootSource**|Optionaler **string**-Parameter|
|**SkippedExecution**|Optionaler **bool**-Ausgabeparameter|
|**SourcesCompiled**|Optionaler **ITaskItem[]**-Ausgabeparameter.|
|**TLogCommandFile**|Optionaler **ITaskItem**-Parameter|
|**TLogReadFiles**|Optionaler **ITaskItem[]**-Parameter.|
|**TLogWriteFiles**|Optionaler **ITaskItem[]**-Parameter.|
|**ToolArchitecture**|Optionaler **string**-Parameter|
|**TrackCommandLines**|Optionaler **bool**-Parameter|
|**TrackFileAccess**|Optionaler **bool**-Parameter|
|**TrackedInputFilesToIgnore**|Optionaler **ITaskItem[]**-Parameter.|
|**TrackedOutputFilesToIgnore**|Optionaler **ITaskItem[]**-Parameter.|
|**TrackerFrameworkPath**|Optionaler **string**-Parameter|
|**TrackerSdkPath**|Optionaler **string**-Parameter|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)<br/>
[Aufgaben](../msbuild/msbuild-tasks.md)