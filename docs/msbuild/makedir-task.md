---
title: "MakeDir Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MakeDir task [MSBuild]"
  - "MSBuild, MakeDir task"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# MakeDir Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `MakeDir`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Directories`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Die Verzeichnisse, die erstellt werden sollen.|  
|`DirectoriesCreated`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Die Verzeichnisse, die von dieser Aufgabe erstellt wurden.  Wenn bestimmte Verzeichnisse nicht erstellt werden konnten, enthält dieser Ausgabeparameter möglicherweise nicht alle Elemente, die an den `Directories`\-Parameter übergeben wurden.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird die `MakeDir`\-Aufgabe verwendet, um das von der `OutputDirectory`\-Eigenschaft angegebene Verzeichnis zu erstellen.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)