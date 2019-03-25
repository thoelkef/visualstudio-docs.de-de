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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: bd0c5510c754043a0a55b305c671ce9487cabb49
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070434"
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