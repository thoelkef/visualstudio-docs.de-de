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
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515427"
---
# <a name="custombuild-task"></a>CustomBuild-Aufgabe

Umschließt das Visual C++-Compilertool (cmd.exe).

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **CustomBuild-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**BuildSuffix**|Optionaler **string**-Parameter|
|**Sources**|Erforderlicher **ITaskItem[]**-Parameter.|
|**TrackerLogDirectory**|Optionaler **string**-Parameter|

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)