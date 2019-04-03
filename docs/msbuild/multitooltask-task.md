---
title: MultiToolTask-Aufgabe | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: a16a61c06bf80bef3fbb78f155cd8b41905a8d72
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515180"
---
# <a name="multitooltask-task"></a>MultiToolTask-Aufgabe

Keine Beschreibung.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **MultiToolTask**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Optionaler **string[]**-Parameter|
|**SemaphoreProcCount**|Optionaler **string**-Parameter|
|**SchedulerFunction**|Optionaler **string**-Parameter|
|**SchedulerVerbose**|Optionaler **bool**-Parameter|
|**Sources**|Erforderlicher **ITaskItem[]**-Parameter.|
|**TaskAssemblyName**|Optionaler **string**-Parameter|
|**TaskName**|Erforderlicher **String**-Parameter.|
|**TrackerLogDirectory**|Erforderlicher **String**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)