---
title: GetAssemblyIdentity-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a09bd4955cee6e50368f7155fb2e03c2c1758bf
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634018"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity-Aufgabe

Ruft die Assemblyidentitäten aus den angegebenen Dateien ab und gibt die Identitätsinformation aus

## <a name="task-parameters"></a>Aufgabenparameter

In der folgenden Tabelle werden die Parameter der `GetAssemblyIdentity` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die abgerufenen Assemblyidentitäten|
|`AssemblyFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Dateien an, aus denen Identitäten abgerufen werden sollen|

## <a name="remarks"></a>Hinweise

Die Elementausgabe des `Assemblies`-Parameters enthält Metadaten-Datensätze namens `Version`, `PublicKeyToken` und `Culture`.

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Identität der im `MyAssemblies`-Element angegebenen Dateien abgerufen und im `MyAssemblyIdentities`-Element ausgegeben.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
