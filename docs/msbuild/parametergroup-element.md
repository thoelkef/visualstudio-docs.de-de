---
title: ParameterGroup-Element | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263074"
---
# <a name="parametergroup-element"></a>ParameterGroup-Element

Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von `UsingTask` `TaskFactory` generiert wird. Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Parameter](../msbuild/parameter-element.md)|Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask` `TaskFactory` generiert wird. Der Name des Elements ist der Name des Parameters.|

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Bietet eine Möglichkeit, Aufgaben in MSBuild zu registrieren. Es kann kein oder mehrere `UsingTask`-Elemente in einem Projekt geben. |

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die Verwendung des `ParameterGroup`-Elements veranschaulicht.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
