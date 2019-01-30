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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5a7ecc4c91dcb39d090c00b7b2ed37bd6bb906c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011896"
---
# <a name="onerror-element-msbuild"></a>OnError-Element (MSBuild)
Bewirkt, dass mindestens ein Ziel ausgeführt wird, wenn das `ContinueOnError`-Attribut für eine Aufgabe, bei der ein Fehler aufgetreten ist, `false` ist.  

 \<Project>  
 \<Target>  
 \<OnError>  

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
| [Target](../msbuild/target-element-msbuild.md) | Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgaben. |

## <a name="remarks"></a>Hinweise  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] führt das `OnError`-Element aus, wenn bei einer der Aufgaben des `Target`-Elements ein Fehler auftritt, wenn der `ContinueOnError`-Attributsatz auf `ErrorAndStop` (oder `false`) festgelegt ist. Wenn bei der Aufgabe ein Fehler auftritt, werden die im `ExecuteTargets`-Attribut festgelegten Ziele ausgeführt. Wenn das Ziel mehrere `OnError`-Elemente enthält, werden die `OnError`-Elemente sequenziell ausgeführt, wenn bei der Aufgabe ein Fehler auftritt.  

 Weitere Informationen zu den `ContinueOnError`-Attributen finden Sie unter [Aufgabenelement (MSBuild)](../msbuild/task-element-msbuild.md). Informationen zu Zielen finden Sie unter [Targets](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Beispiel  
 Der folgende Code führt die `TaskOne`- und `TaskTwo`-Aufgabe aus. Wenn bei `TaskOne` ein Fehler auftritt, wertet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das `OnError`-Element aus und führt das `OtherTarget`-Ziel aus.  

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
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Ziele](../msbuild/msbuild-targets.md)
