---
title: "ResolveNonMSBuildProjectOutput Task | Microsoft Docs"
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
  - "MSBuild, ResolveNonMSBuildProjectOutput task"
  - "ResolveNonMSBuildProjectOutput task [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResolveNonMSBuildProjectOutput Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmt die Ausgabedateien für Projektverweise, die keine MSBuild\-Projektverweise sind.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `ResolveNonMSBuildProjectOutput`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`PreresolvedProjectOutputs`|Optionaler `String`\-Parameter.<br /><br /> Gibt eine XML\-Zeichenfolge an, die aufgelöste Projektausgaben enthält.|  
|`ProjectReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt die Projektverweise an.|  
|`ResolvedOutputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Liste der aufgelösten Verweispfade \(und behält die ursprünglichen Projektverweisattribute\).|  
|`UnresolvedProjectReferences`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Liste der Projektverweiselemente, die nicht mit der Liste von vorab aufgelösten Ausgaben aufgelöst werden konnten.<br /><br /> Da Visual Studio nur nicht MSBuild\-spezifische Projekte vorab auflöst, bedeutet dies, dass Projektverweise in dieser Liste im MSBuild\-Format sind.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)