---
title: "CombinePath Task | Microsoft Docs"
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
  - "MSBuild, CombinePath task"
  - "CombinePath task [MSBuild]"
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CombinePath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kombiniert die angegebenen Pfade in einem einzelnen Pfad.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der [CombinePath Task](../msbuild/combinepath-task.md) beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`BasePath`|Erforderlicher `String`\-Parameter.<br /><br /> Der Basispfad zur Verbindung mit anderen Pfaden.  Der Pfad kann relativ, absolut oder nicht angegeben sein.|  
|`Paths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Eine Liste einzelner Pfade, die mit BasePath kombiniert werden sollen, um den kombinierten Pfad zu bilden.  Hierbei kann es sich um relative oder absolute Pfade handeln.|  
|`CombinedPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Der von dieser Aufgabe erstellte kombinierte Pfad.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)