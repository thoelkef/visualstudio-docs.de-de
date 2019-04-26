---
title: ResolveNonMSBuildProjectOutput-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7060141f81054bf5daa27cdd09a07639be6e0ae8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996707"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput-Aufgabe
Bestimmt die Ausgabedateien für Nicht-MSBuild-Projektverweise

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `ResolveNonMSBuildProjectOutput` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Optionaler `String` -Parameter.<br /><br /> Gibt eine XML-Zeichenfolge an, die aufgelöste Projektausgaben enthält|
|`ProjectReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Projektverweise an|
|`ResolvedOutputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält eine Liste der aufgelösten Verweispfade und behält die ursprünglichen Projektverweisattribute bei|
|`UnresolvedProjectReferences`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Liste der Projektverweiselemente, die nicht mithilfe der Liste vorab aufgelöster Ausgaben aufgelöst werden konnten<br /><br /> Da Visual Studio nur Nicht-MSBuild-Projekte vorab auflöst, weisen Projektverweise in dieser Liste das MSBuild-Format auf.|

## <a name="remarks"></a>Anmerkungen
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)