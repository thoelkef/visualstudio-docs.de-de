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
ms.openlocfilehash: 5ceb23d34fab92fe0056f9bd82b9d9c63967dc4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094577"
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

 Im folgenden Beispiel (sofern es als importierte *TARGETS*-Datei verwendet wird) wird nach dem Erstellen des Projekts ein *ZIP*-Archiv aus dem Ausgabeverzeichnis erstellt. Normalerweise würde die `$(OutputPath)`-Eigenschaft in einer MSBuild-Projektdatei definiert werden. Daher erzeugt eine Projektdatei, die die folgende Datei importiert, das ZIP-Archiv `output.zip`:

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
