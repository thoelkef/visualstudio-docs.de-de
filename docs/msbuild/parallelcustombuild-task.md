---
title: ParallelCustomBuild-Aufgabe | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 506ead6680bd9a0aaaf38d6959da02a14dfee337
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070403"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild-Aufgabe

Führen Sie parallele Instanzen der [CustomBuild Aufgabe](../msbuild/custombuild-task.md) aus.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **ParallelCustomBuild**-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**BreakOnFirstFailure**|Optionaler **bool**-Parameter|
|**MaxItemsInBatch**|Optionaler **int**-Parameter.|
|**MaxProcesses**|Optionaler **int**-Parameter.|
|**Sources**|Erforderlicher **ITaskItem[]**-Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)