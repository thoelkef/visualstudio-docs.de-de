---
title: "Move Task | Microsoft Docs"
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
  - "MSBuild, Move task"
  - "Move task [MSBuild]"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Move Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verschiebt Dateien an eine neue Position.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Move`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die Liste der Dateien an, zu denen die Quelldateien verschoben werden sollen.  Diese Liste soll der im `SourceFiles`\-Parameter angegebenen Liste eins zu eins entsprechen.  Das heißt, die erste in `SourceFiles` angegebene Datei wird an den ersten in `DestinationFiles` angegebenen Speicherort verschoben usw.|  
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien verschoben werden sollen.|  
|`MovedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich verschoben wurden.|  
|`OverwriteReadOnlyFiles`|Optionaler `Boolean`\-Parameter.<br /><br /> Beim Wert `true` werden Dateien auch dann überschrieben, wenn sie als schreibgeschützt markiert sind.|  
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die zu verschiebenden Dateien an.|  
  
## Hinweise  
 Es muss entweder der `DestinationFolder`\-Parameter oder der `DestinationFiles`\-Parameter angegeben werden, jedoch nicht beide.  Wenn beide angegeben werden, schlägt die Aufgabe fehl, und ein Fehler wird protokolliert.  
  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)