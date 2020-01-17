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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac4e04c1a75fe7afdebc984381e17d7e55913fd4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594980"
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
