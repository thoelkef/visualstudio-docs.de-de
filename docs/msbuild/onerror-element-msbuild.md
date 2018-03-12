---
title: OnError-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ed8d48fe390f5a5990506a6b7eeab3d1efe8b5ed
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="onerror-element-msbuild"></a>OnError-Element (MSBuild)
Bewirkt, dass mindestens ein Ziel ausgeführt wird, wenn das `ContinueOnError`-Attribut für eine Aufgabe, bei der ein Fehler aufgetreten ist, `false` ist.  

 \<Project>  
 \<Target>  
 \<OnError>  

## <a name="syntax"></a>Syntax  

```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|description|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Erforderliches Attribut.<br /><br /> Die Ziele, die ausgeführt werden, wenn bei einer Aufgabe ein Fehler auftritt. Trennen Sie mehrere Ziele durch Semikolons. Mehrere Ziele werden in der angegebenen Reihenfolge ausgeführt.|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgaben.|  

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
 [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele)
