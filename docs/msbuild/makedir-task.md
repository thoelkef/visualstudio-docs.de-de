---
title: MakeDir-Aufgabe| Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89bfc33aaf4b3f80ee6b80a93ad6b71dd3786599
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627063"
---
# <a name="makedir-task"></a>MakeDir-Aufgabe
Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse

## <a name="parameters"></a>Parameter
In der folgenden Tabelle werden die Parameter der `MakeDir` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Directories`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Der Satz von zu erstellenden Verzeichnissen.|
|`DirectoriesCreated`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Die von dieser Aufgabe erstellten Verzeichnisse. Wenn bestimmte Verzeichnisse nicht erstellt werden konnten, enthält dieser Parameter möglicherweise nicht alle Elemente, die an den `Directories`-Parameter übergeben wurden.|

## <a name="remarks"></a>Anmerkungen
Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel
Im folgenden Codebeispiel wird das von der Eigenschaft `OutputDirectory` angegebene Verzeichnis mit der `MakeDir`-Aufgabe erstellt.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
