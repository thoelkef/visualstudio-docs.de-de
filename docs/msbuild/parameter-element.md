---
title: Parameter-Element | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1ae8927c8a8f3a3fcd3f57075de281e3ee0679a1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="parameter-element"></a>Parameter-Element
Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask``TaskFactory` generiert wird.  Der Name des Elements ist der Name des Parameters.  Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>Syntax  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|description|  
|---------------|-----------------|  
|`ParameterType`|Optionales Attribut.<br /><br /> Der .NET-Typ des Parameters, z.B. „System.String“.|  
|`Output`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein Ausgabeparameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|  
|`Required`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein erforderlicher Parameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von `UsingTask``TaskFactory` generiert wird.|  

## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `Parameter`-Elements veranschaulicht.  

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
