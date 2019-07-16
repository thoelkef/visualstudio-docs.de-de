---
title: GetFrameworkPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7bf2432e37278c924d1604e735feec7b848b01
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747554"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath-Aufgabe
Ruft den Pfad zu den .NET Framework-Assemblys ab.

## <a name="task-parameters"></a>Aufgabenparameter
In der folgenden Tabelle werden die Parameter der `GetFrameworkPath` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`FrameworkVersion11Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den Assemblys der Framework-Version 1.1, sofern vorhanden. Andernfalls wird `null` zurückgegeben.|
|`FrameworkVersion20Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den Assemblys der Framework-Version 2.0, sofern vorhanden. Andernfalls wird `null` zurückgegeben.|
|`FrameworkVersion30Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den Assemblys der Framework-Version 3.0, sofern vorhanden. Andernfalls wird `null` zurückgegeben.|
|`FrameworkVersion35Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den Assemblys der Framework-Version 3.5, sofern vorhanden. Andernfalls wird `null` zurückgegeben.|
|`FrameworkVersion40Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den Assemblys der Framework-Version 4.0, sofern vorhanden. Andernfalls wird `null` zurückgegeben.|
|`Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den neuesten Frameworkassemblys, sofern diese verfügbar sind. Andernfalls wird `null` zurückgegeben.|

## <a name="remarks"></a>Anmerkungen
Wenn mehrere Versionen von .NET Framework installiert sind, gibt dieser Task die Version zurück, in der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ausgeführt werden soll.

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird mit dem Task `GetFrameworkPath` der Pfad zu .NET Framework in der `FrameworkPath`-Eigenschaft gespeichert.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
