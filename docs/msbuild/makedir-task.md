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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cc2e97a3024d768861a1967705137415a0d3aa2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633537"
---
# <a name="makedir-task"></a>MakeDir-Aufgabe

Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `MakeDir`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Directories`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Der Satz von zu erstellenden Verzeichnissen.|
|`DirectoriesCreated`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Die von dieser Aufgabe erstellten Verzeichnisse. Wenn bestimmte Verzeichnisse nicht erstellt werden konnten, enthält dieser Parameter möglicherweise nicht alle Elemente, die an den `Directories`-Parameter übergeben wurden.|

## <a name="remarks"></a>Bemerkungen

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

## <a name="see-also"></a>Weitere Informationen

- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
