---
title: "ParameterGroup Element | Microsoft Docs"
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
  - "<ParameterGroup> element [MSBuild]"
  - "ParameterGroup element [MSBuild]"
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ParameterGroup Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein wird, die von einer `UsingTask`\-`TaskFactory` generiert wird. Weitere Informationen finden Sie unter [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Syntax  
  
```  
<ParameterGroup />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Parameter](../msbuild/parameter-element.md)|Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask` `TaskFactory` generiert wird.  Der Name des Elements ist der Name des Parameters.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Bietet eine Möglichkeit, Aufgaben in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zu registrieren.  Es kann keine oder mehrere `UsingTask`\-Elemente in einem Projekt geben.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `ParameterGroup`\-Elements veranschaulicht.  
  
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