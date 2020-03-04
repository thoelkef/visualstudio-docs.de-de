---
title: CombinePath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 533f87eba9032efa7dc60ac682bbe400cb640727
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634434"
---
# <a name="combinepath-task"></a>CombinePath-Aufgabe

Kombiniert die angegebenen Pfade zu einem einzigen Pfad.
## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der [CombinePath-Aufgabe](../msbuild/combinepath-task.md) beschrieben.


|Parameter|Beschreibung|
|---------------|-----------------|
|`BasePath`|Erforderlicher `String` -Parameter.<br /><br /> Der Basispfad, der mit den anderen Pfaden kombiniert werden soll. Der Pfad kann relativ, absolut oder nicht angegeben sein.|
|`Paths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Eine Liste einzelner Pfade, die mit BasePath zu einem kombinierten Pfad kombiniert werden können. Pfade können relativ oder absolut sein.|
|`CombinedPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Der kombinierte Pfad, der durch diese Aufgabe erstellt wurde|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
