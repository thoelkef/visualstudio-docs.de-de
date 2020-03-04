---
title: Aufgabe löschen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634278"
---
# <a name="delete-task"></a>Delete-Aufgabe

Löscht die angegebene Datei.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `Delete` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DeletedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Dateien an, die erfolgreich gelöscht wurden.|
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Legt die zu löschenden Dateien fest.|
|`TreatErrorsAsWarnings`|Optionaler `Boolean`-Parameter<br /><br /> Wenn `true`, werden Fehler als Warnungen protokolliert. Der Standardwert ist `false`.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Seien Sie vorsichtig, wenn Sie Platzhalter mit dem `Delete`-Task verwenden. Es kann schnell passieren, dass Sie mit Ausdrücken wie `$(SomeProperty)\**\*.*` oder `$(SomeProperty)/**/*.*` die falschen Dateien löschen, insbesondere dann, wenn die Eigenschaft als leere Zeichenfolge ausgewertet wird. In diesem Fall kann der `Files`-Parameter in das Stammverzeichnis Ihres Laufwerks ausgewertet werden, was dazu führen kann, dass deutlich mehr gelöscht wird als gewünscht.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Datei *MyApp.pdb* gelöscht.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
