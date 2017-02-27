---
title: "Parameter Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Parameter element [MSBuild]"
  - "<Parameter> element [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Parameter Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask`\-`TaskFactory` generiert wird. Der Name des Elements ist der Name des Parameters. Weitere Informationen finden Sie unter [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Syntax  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`ParameterType`|Optionales Attribut.<br /><br /> Der .NET\-Typ des Parameters, beispielsweise "System.String".|  
|`Output`|Optionales boolesches Attribut.<br /><br /> Bei `true` ist dieser Parameter ein Ausgabeparameter für die Aufgabe.  Der Standardwert ist `false`.|  
|`Required`|Optionales boolesches Attribut.<br /><br /> Bei `true` ist dieser Parameter ein erforderlicher Parameter für die Aufgabe.  Der Standardwert ist `false`.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von einer `UsingTask`\-`TaskFactory` generiert wird.|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `Parameter`\-Elements veranschaulicht.  
  
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