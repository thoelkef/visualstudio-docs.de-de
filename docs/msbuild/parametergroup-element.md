---
title: ParameterGroup-Element | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 6
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
ms.openlocfilehash: 52ee1e2022bb016cf032fbc3ef5c8e219cda5c92
ms.lasthandoff: 03/13/2017

---
# <a name="parametergroup-element"></a>ParameterGroup-Element
Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von `UsingTask``TaskFactory` generiert wird. Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  

## <a name="syntax"></a>Syntax  

```  
<ParameterGroup />  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  
 Keine.  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Parameter](../msbuild/parameter-element.md)|Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask``TaskFactory` generiert wird. Der Name des Elements ist der Name des Parameters.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Bietet eine Möglichkeit, Aufgaben in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zu registrieren. Es kann kein oder mehrere `UsingTask`-Elemente in einem Projekt geben.|  

## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `ParameterGroup`-Elements veranschaulicht.  

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
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Referenz zum MSBuild-Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)

