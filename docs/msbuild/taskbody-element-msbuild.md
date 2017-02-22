---
title: "TaskBody Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "TaskBody element [MSBuild]"
  - "<TaskBody> element [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# TaskBody Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält die Daten, die an eine `UsingTask` `TaskFactory` übergeben werden. Weitere Informationen finden Sie unter [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Syntax  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Evaluate`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, wertet MSBuild alle inneren Elemente aus und erweitert Elemente und Eigenschaften, bevor es die Informationen an die `TaskFactory` leitet, wenn die Aufgabe instanziiert wird.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Daten|Der Text zwischen den `TaskBody`\-Tags wird wörtlich an die `TaskFactory` gesendet.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Bietet eine Möglichkeit, Aufgaben in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zu registrieren.  Es kann keine oder mehrere `UsingTask`\-Elemente in einem Projekt geben.|  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie das `TaskBody`\-Element mit einem `Evaluate`\-Attribut verwendet wird.  
  
```  
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
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)