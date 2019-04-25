---
title: TaskBody-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f788df1dd3cad2baddd6d2966b04195af01fe7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938960"
---
# <a name="taskbody-element-msbuild"></a>TaskBody-Element (MSBuild)
Enthält die Daten, die an `UsingTask` `TaskFactory` übergeben werden. Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<TaskBody>

## <a name="syntax"></a>Syntax

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Evaluate`|Optionales boolesches Attribut.<br /><br /> Bei `true` wertet MSBuild alle inneren Elemente aus und erweitert Elemente und Eigenschaften, bevor die Informationen an `TaskFactory` übergeben werden, wenn die Aufgabe instanziiert wird.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Daten|Der Text zwischen den `TaskBody`-Tags wird wörtlich an `TaskFactory` gesendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Bietet eine Möglichkeit, Aufgaben in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zu registrieren. Es kann kein oder mehrere `UsingTask`-Elemente in einem Projekt geben. |

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung des Elements `TaskBody` mit dem Attribut `Evaluate` gezeigt.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
