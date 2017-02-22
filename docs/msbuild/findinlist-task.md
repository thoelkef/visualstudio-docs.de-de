---
title: "FindInList Task | Microsoft Docs"
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
  - "FindInList task [MSBuild]"
  - "MSBuild, FindInList task"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindInList Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sucht ein Element in einer angegebenen Liste, das über eine entsprechende Elementspezifikation verfügt.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der [FindInList Task](../msbuild/findinlist-task.md) beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`CaseSensitive`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird bei der Suche die Groß\-\/Kleinschreibung beachtet, bei anderen Werten nicht.  Der Standardwert lautet `true`.|  
|`FindLastMatch`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird die letzte Übereinstimmung zurückgegeben, andernfalls die erste Übereinstimmung.  Der Standardwert lautet `false`.|  
|`ItemFound`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Das erste übereinstimmende Element in der Liste, sofern vorhanden.|  
|`ItemSpecToFind`|Erforderlicher `String`\-Parameter.<br /><br /> Die Elementspezifikation, nach der gesucht werden soll.|  
|`List`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Die Liste, in der nach der Elementspezifikation gesucht werden soll.|  
|`MatchFileNameOnly`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird nur der Dateiname der Elementspezifikation verglichen, andernfalls die gesamte Elementspezifikation.  Der Standardwert lautet `true`.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)