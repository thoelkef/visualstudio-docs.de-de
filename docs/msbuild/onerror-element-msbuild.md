---
title: OnError-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633082"
---
# <a name="onerror-element-msbuild"></a>OnError-Element (MSBuild)

Bewirkt, dass mindestens ein Ziel ausgeführt wird, wenn das `ContinueOnError`-Attribut für eine Aufgabe, bei der ein Fehler aufgetreten ist, `false` ist.

 \<Project> \<Target> \<OnError>

## <a name="syntax"></a>Syntax

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Erforderliches Attribut.<br /><br /> Die Ziele, die ausgeführt werden, wenn bei einer Aufgabe ein Fehler auftritt. Trennen Sie mehrere Ziele durch Semikolons. Mehrere Ziele werden in der angegebenen Reihenfolge ausgeführt.|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Target](../msbuild/target-element-msbuild.md) | Containerelement für MSBuild-Aufgaben. |

## <a name="remarks"></a>Hinweise

 MSBuild führt das `OnError`-Element aus, wenn eine der Aufgaben des `Target`-Elements bei Festlegung des `ContinueOnError`-Attributs auf `ErrorAndStop` (oder `false`) nicht erfolgreich ist. Wenn bei der Aufgabe ein Fehler auftritt, werden die im `ExecuteTargets`-Attribut festgelegten Ziele ausgeführt. Wenn das Ziel mehrere `OnError`-Elemente enthält, werden die `OnError`-Elemente sequenziell ausgeführt, wenn bei der Aufgabe ein Fehler auftritt.

 Weitere Informationen zu den `ContinueOnError`-Attributen finden Sie unter [Aufgabenelement (MSBuild)](../msbuild/task-element-msbuild.md). Informationen zu Zielen finden Sie unter [Targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Beispiel

 Der folgende Code führt die `TaskOne`- und `TaskTwo`-Aufgabe aus. Wenn es bei `TaskOne` zu einem Fehler kommt, wertet MSBuild das `OnError`-Element aus und führt das `OtherTarget`-Ziel aus.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Siehe auch

- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [Ziele](../msbuild/msbuild-targets.md)
