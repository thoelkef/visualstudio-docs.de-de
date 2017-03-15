---
title: "UpdateManifest Task | Microsoft Docs"
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
  - "MSBuild, UpdateManifest task"
  - "UpdateManifest task [MSBuild]"
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# UpdateManifest Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aktualisiert ausgewählte Eigenschaften in einem Manifest und führt eine erneute Signierung aus.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `UpdateManifest`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`ApplicationManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt das Anwendungsmanifest an.|  
|`ApplicationPath`|Erforderlicher `String`\-Parameter.<br /><br /> Gibt den Pfad des Anwendungsmanifests an.|  
|`InputManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt das zu aktualisierende Manifest an.|  
|`OutputManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt das Manifest an, das aktualisierte Eigenschaften enthält.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>\-Klasse.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Task Base Class](../msbuild/task-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)