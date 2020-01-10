---
title: ZipDirectory-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4bf72509610e9d397e4b208294112fcc0975b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588329"
---
# <a name="zipdirectory-task"></a>ZipDirectory-Aufgabe
Erstellt ein *ZIP*-Archiv aus den Inhalten eines Verzeichnisses.

>[!NOTE]
>Die `ZipDirectory`-Aufgabe ist nur in MSBuild 15.8 und höher verfügbar.

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `ZipDirectory` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DestinationFile`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter<br /><br /> Der vollständige Pfad der *ZIP*-Datei, die erstellt werden soll.|
|`Overwrite`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird die Zieldatei überschrieben, sofern diese vorhanden ist. Wird standardmäßig auf `false` festgelegt.|
|`SourceDirectory`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Legt das Verzeichnis fest, aus dem ein *ZIP*-Archiv erstellt werden soll.|

## <a name="remarks"></a>Hinweise
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird nach dem Erstellen des Projekts ein *ZIP*-Archiv aus dem Ausgabeverzeichnis erstellt.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
