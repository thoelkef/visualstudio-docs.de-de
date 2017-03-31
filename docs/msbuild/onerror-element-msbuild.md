---
title: OnError-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 0e5a449ef396e7b9fd23a2c018bdc7f8791b7b38
ms.openlocfilehash: 710eecad79b43c7544565d51536136e39c080d5f
ms.lasthandoff: 03/13/2017

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

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Erforderliches Attribut.<br /><br /> Die Ziele, die ausgeführt werden, wenn bei einer Aufgabe ein Fehler auftritt. Trennen Sie mehrere Ziele durch Semikolons. Mehrere Ziele werden in der angegebenen Reihenfolge ausgeführt.|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Ziel](../msbuild/target-element-msbuild.md)|Containerelement für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgaben.|  

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

