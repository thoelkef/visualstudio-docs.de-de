---
title: "GetFrameworkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath task [MSBuild]"
  - "MSBuild, GetFrameworkPath task"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetFrameworkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft den Pfad zu den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Assemblys ab.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GetFrameworkPath`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`FrameworkVersion11Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad auf die Framework\-Version 1.1\-Assemblys, sofern vorhanden.  Andernfalls wird `null` zurückgegeben.|  
|`FrameworkVersion20Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad auf die Framework\-Version 2.0\-Assemblys, sofern vorhanden.  Andernfalls wird `null` zurückgegeben.|  
|`FrameworkVersion30Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad auf die Framework\-Version 3.0\-Assemblys, sofern vorhanden.  Andernfalls wird `null` zurückgegeben.|  
|`FrameworkVersion35Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad auf die Framework\-Version 3.5\-Assemblys, sofern vorhanden.  Andernfalls wird `null` zurückgegeben.|  
|`FrameworkVersion40Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad auf die Framework\-Version 4.0\-Assemblys, sofern vorhanden.  Andernfalls wird `null` zurückgegeben.|  
|`Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad zu den neuesten Framework\-Assemblys, wenn welche verfügbar sind.  Andernfalls wird `null` zurückgegeben.|  
  
## Hinweise  
 Wenn mehrere Versionen von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert sind, gibt diese Aufgabe die Version zurück, für die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] konzipiert ist.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `GetFrameworkPath`\-Aufgabe verwendet, um den Pfad zu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in der `FrameworkPath`\-Eigenschaft zu speichern.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)