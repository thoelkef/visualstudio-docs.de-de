---
title: "RequiresFramework35SP1Assembly Task | Microsoft Docs"
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
  - "RequiresFramework35SP1Assembly task [MSBuild]"
  - "MSBuild, RequiresFramework35SP1Assembly task"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RequiresFramework35SP1Assembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmt, ob die Anwendung .NET Framework 3.5 SP1 erfordert.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `RequiresFramework35SP1Assembly`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Assembly an, die in der Anwendung verwiesen wird.|  
|`CreateDesktopShortcut`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, wird ein Verknüpfungssymbol auf dem Desktop während der Installation erstellt.|  
|`DeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Namen der Manifestdatei für die Anwendung an.|  
|`EntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die Assembly an, die ausgeführt werden soll, wenn die Anwendung ausgeführt wird.|  
|`ErrorReportUrl`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Website an, die in den Dialogfeldern während ClickOnce\-Installationen angezeigt wird.|  
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Liste von Dateien an, die bereitgestellt werden, wenn die Anwendung veröffentlicht wird.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Assembly an, auf die im Projekt verwiesen wird.|  
|`RequiresMinimumFramework35SP1`|Optionaler `Boolean`\-Ausgabeparameter.<br /><br /> Beim Wert `true` erfordert die Anwendung .NET Framework 3.5 SP1.|  
|`SigningManifests`|Optionaler `Boolean`\-Ausgabeparameter.<br /><br /> Beim Wert `true` werden die ClickOnce\-Manifeste signiert.|  
|`SuiteName`|Optionaler `String`\-Parameter.<br /><br /> Hierdurch wird der Name des Ordners im Menü **Start** angegeben, in dem die Anwendung installiert wird.|  
|`TargetFrameworkVersion`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Version von .NET Framework an, für die diese Anwendung entwickelt wurde.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)