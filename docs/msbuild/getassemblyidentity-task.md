---
title: "GetAssemblyIdentity Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GetAssemblyIdentity task"
  - "GetAssemblyIdentity task [MSBuild]"
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# GetAssemblyIdentity Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft die Assemblyidentitäten aus den angegebenen Dateien ab und gibt die Identitätsinformationen aus.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GetAssemblyIdentity`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die abgerufenen Assemblyidentitäten.|  
|`AssemblyFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Dateien an, aus denen Identitäten abgerufen werden sollen.|  
  
## Hinweise  
 Die vom `Assemblies`\-Parameter ausgegebenen Elemente enthalten Elementmetadateneinträge mit den Namen `Version`, `PublicKeyToken` und `Culture`.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die Identität aus den im `MyAssemblies`\-Element angegebenen Dateien abgerufen. Die abgerufenen Identitätsinformationen werden im `MyAssemblyIdentities`\-Element ausgegeben.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)