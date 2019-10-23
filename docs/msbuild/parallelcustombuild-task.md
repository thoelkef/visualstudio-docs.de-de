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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747223"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild-Aufgabe

Führen Sie parallele Instanzen der [CustomBuild Aufgabe](../msbuild/custombuild-task.md) aus.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **ParallelCustomBuild**-Aufgabe beschrieben.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**BreakOnFirstFailure**|Optionaler **bool**-Parameter|
|**MaxItemsInBatch**|Optionaler **int**-Parameter.|
|**MaxProcesses**|Optionaler **int**-Parameter.|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)