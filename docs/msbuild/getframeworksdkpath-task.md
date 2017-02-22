---
title: "GetFrameworkSdkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath task [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath task"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkSdkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft den Pfad zu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] ab.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GetFrameworkSdkPath`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`FrameworkSdkVersion20Path`|Optionaler schreibgeschützter `String`\-Ausgabeparameter.<br /><br /> Gibt den Pfad zu .NET SDK, Version 2.0, zurück, sofern vorhanden.  Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion35Path`|Optionaler schreibgeschützter `String`\-Ausgabeparameter.<br /><br /> Gibt den Pfad zu .NET SDK, Version 3.5, zurück, sofern vorhanden.  Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion40Path`|Optionaler schreibgeschützter `String`\-Ausgabeparameter.<br /><br /> Gibt den Pfad zu .NET SDK, Version 4.0, zurück, sofern vorhanden.  Andernfalls wird `String.Empty` zurückgegeben.|  
|`Path`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Enthält den Pfad zum neuesten .NET\-SDK, wenn Version vorhanden ist.  Andernfalls wird `String.Empty` zurückgegeben.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `GetFrameworkSdkPath`\-Aufgabe verwendet, um den Pfad zu [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] in der `SdkPath`\-Eigenschaft zu speichern.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)