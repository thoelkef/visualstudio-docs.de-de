---
title: "Output Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> Element [MSBuild]"
  - "Output Element [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Output Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Speichert Aufgabenausgabewerte in Elementen und Eigenschaften.  
  
## Syntax  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`TaskParameter`|Erforderliches Attribut.<br /><br /> Der Name des Ausgabeparameters der Aufgabe.|  
|`PropertyName`|Entweder das `PropertyName`\-Attribut oder das `ItemName`\-Attribut ist erforderlich.<br /><br /> Die Eigenschaft, die den Ausgabeparameterwert der Aufgabe empfängt.  Das Projekt kann dann mit der Syntax `$(`*PropertyName*`)` auf die Eigenschaft verweisen.  Dieser Eigenschaftenname kann entweder ein neuer Eigenschaftenname oder ein im Projekt bereits definierter Name sein.<br /><br /> Dieses Attribut kann nicht verwendet werden, wenn `ItemName` ebenfalls verwendet wird.|  
|`ItemName`|Entweder das `PropertyName`\-Attribut oder das `ItemName`\-Attribut ist erforderlich.<br /><br /> Das Element, das den Ausgabeparameterwert der Aufgabe empfängt.  Das Projekt kann dann mit der Syntax `@(`*ItemName*`)` auf das Element verweisen.  Der Elementname kann entweder ein neuer Elementname oder ein im Projekt bereits definierter Name sein.<br /><br /> Dieses Attribut kann nicht verwendet werden, wenn `PropertyName` ebenfalls verwendet wird.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Erstellt eine Instanz einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe und führt diese aus.|  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie die `Csc`\-Aufgabe innerhalb eines `Target`\-Elements ausgeführt wird.  Die Deklaration der an die Aufgabenparameter übergebenen Elemente und Eigenschaften ist in diesem Beispiel nicht enthalten.  Der Wert des Ausgabeparameters `OutputAssembly` wird im `FinalAssemblyName`\-Element gespeichert, der Wert des Ausgabeparameters `BuildSucceeded` in der `BuildWorked`\-Eigenschaft.  Weitere Informationen finden Sie unter [Tasks](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)