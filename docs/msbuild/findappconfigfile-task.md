---
title: "FindAppConfigFile Task | Microsoft Docs"
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
  - "FindAppConfigFile task [MSBuild]"
  - "MSBuild, FindAppConfigFile task"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindAppConfigFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sucht in den angegebenen Listen die Datei app.config, sofern vorhanden.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `FindAppConfigFile`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AppConfigFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt das erste übereinstimmende Element in der Liste an, sofern vorhanden.|  
|`PrimaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die primäre zu durchsuchende Liste an.|  
|`SecondaryList`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die sekundäre zu durchsuchende Liste an.|  
|`TargetPath`|Erforderlicher `String`\-Parameter.<br /><br /> Gibt den Wert an, der als Metadaten hinzugefügt werden soll.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)