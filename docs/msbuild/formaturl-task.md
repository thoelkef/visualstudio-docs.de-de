---
title: "FormatUrl Task | Microsoft Docs"
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
  - "MSBuild, FormatUrl task"
  - "FormatUrl task [MSBuild]"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatUrl Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Konvertiert eine URL in ein richtiges URL\-Format.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `FormatUrl`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`InputUrl`|Optionaler `String`\-Parameter.<br /><br /> Gibt die URL an, die formatiert werden soll.|  
|`OutputUrl`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt die formatierte URL an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)