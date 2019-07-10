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
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587008"
---
# <a name="custombuild-task"></a>CustomBuild-Aufgabe

Umschließt das Visual C++-Compilertool (cmd.exe). Diese Klasse wird von [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md) abgeleitet, ermittelt jedoch keine Abhängigkeiten mit der Dateinachverfolgung. Alle Abhängigkeiten sollten explizit als AdditionalDependencies festgelegt werden, um eine ordnungsgemäße Funktion von inkrementellen Builds sicherzustellen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **CustomBuild-Aufgabe** beschrieben.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**BuildSuffix**|Optionaler **string**-Parameter|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|
|**TrackerLogDirectory**|Optionaler **string**-Parameter|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
