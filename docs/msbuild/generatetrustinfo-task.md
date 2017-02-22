---
title: "GenerateTrustInfo Task | Microsoft Docs"
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
  - "MSBuild, GenerateTrustInfo task"
  - "GenerateTrustInfo task [MSBuild]"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTrustInfo Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Generiert die Vertrauenswürdigkeit der Anwendung aus dem Basismanifest sowie aus der `TargetZone`\-Eigenschaft und den `ExcludedPermissions`\-Parametern.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `GenerateTrustInfo`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`ApplicationDependencies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die abhängigen Assemblys an.|  
|`BaseManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt das Basismanifest an, aus dem die Vertrauenswürdigkeit der Anwendung generiert werden soll.|  
|`ExcludedPermissions`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen oder mehrere durch Kommas getrennte Berechtigungsidentitätswerte an, die aus dem Standardberechtigungssatz der Zone ausgeschlossen werden sollen.|  
|`TargetZone`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen Zonenstandardberechtigungssatz an, der von der Computerrichtlinie abgerufen wird.|  
|`TrustInfoFile`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt die Datei an, die die Vertrauenswürdigkeitsinformationen für die Anwendungssicherheit enthält.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)