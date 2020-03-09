---
title: UsingTask-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d977892956c90fd88ff913b9c9300b0176323a4
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263122"
---
# <a name="usingtask-element-msbuild"></a>UsingTask-Element (MSBuild)

Ordnet den in einem [Task](../msbuild/task-element-msbuild.md)-Element referenzierten Task der Assembly zu, die die Taskimplementierung enthält.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Im Gegensatz zu Eigenschaften und Elementen wird das *erste* `UsingTask`-Element verwendet, das auf ein `TaskName` angewendet wird. Sie müssen ein neues `UsingTask`-Element *vor* dem vorhandenen definieren.

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`AssemblyName`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Namen zu ladenden Assembly. Das Attribut `AssemblyName` akzeptiert Assemblys mit sicheren Namen, auch wenn sichere Namen nicht erforderlich sind. Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.Load%2A>-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyFile`-Attribut verwendet wird.|
|`AssemblyFile`|Entweder ist das Attribut `AssemblyName` oder das Attribut `AssemblyFile` erforderlich.<br /><br /> Der Dateipfad der Assemblydatei. Dieses Attribut akzeptiert vollständige oder relative Pfade. Relative Pfade sind relativ zum Verzeichnis der Projektdatei oder Zieldatei, in dem das `UsingTask`-Element deklariert ist. Die Verwendung dieses Attributs entspricht dem Laden einer Assembly mit der <xref:System.Reflection.Assembly.LoadFrom%2A>-Methode in .NET.<br /><br /> Sie können dieses Attribut nicht verwenden, wenn das `AssemblyName`-Attribut verwendet wird.|
|`TaskFactory`|Optionales Attribut.<br /><br /> Gibt die Klasse in der Assembly an, die für das Generieren von Instanzen des angegebenen `Task`-Namens verantwortlich ist.  Der Benutzer kann auch `Task` als ein untergeordnetes Element angeben, welches durch die Aufgabenfactory empfangen und zum Generieren der Aufgabe verwendet wird. Der Inhalt von `Task` ist für die Aufgabenfactory spezifisch.|
|`TaskName`|Erforderliches Attribut.<br /><br /> Der Name der aus einer Assembly zu referenzierenden Aufgabe. Wenn Mehrdeutigkeiten möglich sind, sollte dieses Attribut immer vollständige Namespaces angeben. Wenn Mehrdeutigkeiten vorliegen, wählt MSBuild eine willkürliche Übereinstimmung auf, die zu unerwarteten Ergebnissen führen kann.|
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Der Satz an Parametern, die in der Aufgabe angezeigt werden, welche durch die angegebene `TaskFactory` generiert wurde.|
|[Aufgabe](../msbuild/task-element-msbuild.md)|Die `TaskFactory` weitergegebenen Daten zum Generieren einer Instanz der Aufgabe.|

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |

## <a name="remarks"></a>Hinweise

 Auf Umgebungsvariablen, Befehlszeileneigenschaften sowie auf Eigenschaften und Elemente auf Projektebene kann in den `UsingTask`-Elementen, die in der Projektdatei enthalten sind, entweder direkt oder über eine importierte Projektdatei verwiesen werden. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Eigenschaften und Elemente auf Projektebene haben keine Bedeutung, wenn das `UsingTask`-Element aus einer der *TASKS*-Dateien stammt, die global in der MSBuild-Engine registriert sind. Werte auf Projektebene sind in MSBuild nicht global.

 In MSBuild 4.0 kann das Laden mithilfe von Aufgaben aus *OVERRIDETASK*-Dateien erfolgen.

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyName` gezeigt.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die Verwendung des Elements `UsingTask` mit dem Attribut `AssemblyFile` gezeigt.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
