---
title: CustomBuild-Aufgabe | Microsoft-Dokumentation
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748103"
---
# <a name="custombuild-task"></a>CustomBuild-Aufgabe

Umschließt das Microsoft C++-Compilertool (cmd.exe). Diese Klasse wird von [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md) abgeleitet, ermittelt jedoch keine Abhängigkeiten mit der Dateinachverfolgung. Alle Abhängigkeiten sollten explizit als AdditionalDependencies festgelegt werden, um eine ordnungsgemäße Funktion von inkrementellen Builds sicherzustellen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **CustomBuild-Aufgabe** beschrieben.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**BuildSuffix**|Optionaler **string**-Parameter|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|
|**TrackerLogDirectory**|Optionaler **string**-Parameter|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
