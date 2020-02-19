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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279265"
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
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)