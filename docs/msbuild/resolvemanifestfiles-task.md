---
title: "ResolveManifestFiles Task | Microsoft Docs"
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
  - "ResolveManifestFiles task [MSBuild]"
  - "MSBuild, ResolveManifestFiles task"
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# ResolveManifestFiles Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Löst die folgenden Elemente im Buildprozess in Dateien für die Manifestgenerierung auf: erstellte Elemente, Abhängigkeiten, Satelliten, Inhalte, Debugsymbole und Dokumentation.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `ResolveManifestFiles`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`DeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Namen des Bereitstellungsmanifests an.|  
|`EntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die verwaltete Assembly oder den ClickOnce\-Manifestverweis an, die den Einstiegspunkt in das Manifest darstellen.|  
|`ExtraFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die zusätzlichen Dateien an.|  
|`ManagedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die verwalteten Assemblys an.|  
|`NativeAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die systemeigenen Assemblys an.|  
|`OutputAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die generierten Assemblys an.|  
|`OutputDeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt den Einstiegspunkt des Ausgabebereitstellungsmanifests an.|  
|`OutputEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt den Einstiegspunkt der Ausgabe an.|  
|`OutputFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die Ausgabedateien an.|  
|`PublishFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt die Veröffentlichungsdateien an.|  
|`SatelliteAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt die Satellitenassemblys an.|  
|`SigningManifests`|Optionaler `Boolean`\-Parameter.<br /><br /> Beim Wert `true` werden die Manifeste signiert.|  
|`TargetCulture`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Zielkultur für Satellitenassemblys an.|  
|`TargetFrameworkVersion`|Optionaler `String`\-Parameter.<br /><br /> Gibt die .NET Framework\-Zielversion an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)