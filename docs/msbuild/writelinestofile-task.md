---
title: WriteLinesToFile-Aufgabe | Microsoft-Dokumentation
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630664"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile-Aufgabe

Schreibt die Pfade der angegebenen Elemente in die angegebene Textdatei.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `WriteLinestoFile`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`File`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die Datei an, in die Elemente geschrieben werden sollen|
|`Lines`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Elemente an, die in die Datei geschrieben werden sollen|
|`Overwrite`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, überschreibt die Aufgabe den vorhandenen Inhalt in der Datei|
|`Encoding`|Optionaler `String`-Parameter.<br /><br /> Wählt die Zeichencodierung aus, z.B. „Unicode“  Siehe auch <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird die angegebene Zieldatei (sofern vorhanden) zuerst gelesen, um den Inhalt mit der Ausgabe des Tasks zu vergleichen. Wenn beides identisch ist, wird die Datei nicht auf den Datenträger geschrieben, und der Zeitstempel bleibt erhalten.|

## <a name="remarks"></a>Bemerkungen

 Wenn `Overwrite``true` ist, wird eine neue Datei erstellt. Anschließend werden die Inhalte in die Datei geschrieben und diese wird geschlossen. Ist die Zieldatei bereits vorhanden, wird sie überschrieben. Wenn `Overwrite``false` ist, wird der Inhalt an die Datei angefügt und die Zieldatei erstellt, wenn sie nicht bereits vorhanden ist.

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

 Das folgende Beispiel verwendet die Aufgabe `WriteLinesToFile`, um Pfade der Elemente in der `MyItems`-Elementauflistung in die von der `MyTextFile`-Elementauflistung angegebene Datei zu schreiben.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

In diesem Beispiel wird eine Eigenschaft mit eingebettetem Zeilenvorschub verwendet, um Textdateien zu schreiben, die aus mehreren Zeilen bestehen. Wenn ein Eintrag in `Lines` eingebettete Zeilenumbruchzeichen aufweist, werden die neuen Zeilen in die Ausgabedatei eingefügt. Dadurch können Sie auf Eigenschaften verweisen, die aus mehreren Zeilen bestehen.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
