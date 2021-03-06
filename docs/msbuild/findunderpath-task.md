---
title: FindUnderPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d97b727dcba8cd16fe97ee33764947797c36db7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634135"
---
# <a name="findunderpath-task"></a>FindUnderPath-Aufgabe

Bestimmt, welche Elemente in der angegebenen Elementauflistung über Pfade im oder unter dem angegebenen Ordner verfügen

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `FindUnderPath`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Dateien an, deren Pfade mit dem von der `Path`-Eigenschaft angegebenen Parameter verglichen werden sollen|
|`InPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die unter dem angegebenen Pfad gefunden wurden|
|`OutOfPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die unter dem angegebenen Pfad nicht gefunden wurden|
|`Path`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Ordnerpfad an, der als Verweis verwendet werden soll|
|`UpdateToAbsolutePaths`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn TRUE, werden die Pfade der Ausgabeelemente als absolute Pfade aktualisiert.|

## <a name="remarks"></a>Bemerkungen

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die `FindUnderPath`-Aufgabe verwendet um zu bestimmen, ob die im `MyFiles`-Element enthaltenen Dateien über Pfade verfügen, die unter dem Pfad existieren, der von der `SearchPath`-Eigenschaft angegeben wird. Nach Abschluss der Aufgabe enthält das Element `FilesNotFoundInPath` die Datei *File1.txt*. Das Element `FilesFoundInPath` enthält die Datei *File2.txt*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
