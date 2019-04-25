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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963753"
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