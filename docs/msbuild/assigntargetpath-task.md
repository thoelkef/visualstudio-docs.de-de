---
title: AssignTargetPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21678dd573030076d7248dfb7bbf47ea412cecae
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853455"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath-Aufgabe
Diese Aufgabe akzeptiert eine Liste von Dateien und fügt `<TargetPath>`-Attribute hinzu, wenn diese nicht bereits angegeben wurden.

## <a name="task-parameters"></a>Aufgabenparameter
In der folgenden Tabelle werden die Parameter der `AssignTargetPath` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`RootFolder`|Optionaler `string`-Eingabeparameter.<br /><br /> Enthält den Pfad zu dem Ordner, der die Ziellinks enthält.|
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Eingabeparameter.<br /><br /> Enthält die eingehende Liste von Dateien.|
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter.<br /><br /> Enthält die resultierende Liste von Dateien.|

## <a name="remarks"></a>Hinweise
Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel
Das folgende Beispiel führt die `AssignTargetPath`-Aufgabe aus, um ein Projekt zu konfigurieren.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch
[Aufgaben](../msbuild/msbuild-tasks.md)  
[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
