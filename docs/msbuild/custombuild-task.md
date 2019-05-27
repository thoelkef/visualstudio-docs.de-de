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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 6d466dec85a0bdf242120ef5e88a0d5f5d2ac48e
ms.sourcegitcommit: 0ef51e3517436a85cfb85bf492722d566ce602c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934515"
---
# <a name="custombuild-task"></a>CustomBuild-Aufgabe

Umschließt das Visual C++-Compilertool (cmd.exe). Diese Klasse wird von [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md) abgeleitet, ermittelt jedoch keine Abhängigkeiten mit der Dateinachverfolgung. Alle Abhängigkeiten sollten explizit als AdditionalDependencies festgelegt werden, um eine ordnungsgemäße Funktion von inkrementellen Builds sicherzustellen.


## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **CustomBuild-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**BuildSuffix**|Optionaler **string**-Parameter|
|**Sources**|Erforderlicher **ITaskItem[]**-Parameter.|
|**TrackerLogDirectory**|Optionaler **string**-Parameter|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
