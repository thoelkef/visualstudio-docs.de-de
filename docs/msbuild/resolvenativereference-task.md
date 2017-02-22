---
title: "ResolveNativeReference Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveNativeReference task"
  - "ResolveNativeReference task [MSBuild]"
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveNativeReference Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Löst systemeigene Verweise auf.  Implementiert die <xref:Microsoft.Build.Tasks.ResolveNativeReference>\-Klasse.  Diese Klasse unterstützt die .NET Framework\-Infrastruktur, die nicht für die direkte Verwendung in Code bestimmt ist.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `ResolveNativeReference`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AdditionalSearchPaths`|Erforderlicher [String](assetId:///String?qualifyHint=False&autoUpgrade=True)`[]`\-Parameter.<br /><br /> Ruft die Suchpfade zum Auflösen von Assemblyidentitäten von systemeigenen Verweisen ab oder legt diese fest.|  
|`ContainedComComponents`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft die COM\-Komponenten der systemeigenen Assembly ab oder legt diese fest.|  
|`ContainedLooseEtcFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft die im systemeigenen Manifest aufgelisteten freien ETC\-Dateien ab oder legt diese fest.|  
|`ContainedLooseTlbFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft die freien TLB\-Dateien der systemeigenen Assembly ab oder legt diese fest.|  
|`ContainedPrerequisiteAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft Assemblys ab, die vorhanden sein müssen, damit das Manifest verwendet werden kann, oder legt diese fest.|  
|`ContainedTypeLibraries`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft die Typbibliotheken der systemeigenen Assembly ab oder legt diese fest.|  
|`ContainingReferenceFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Ruft die Verweisdateien ab oder legt diese fest.|  
|`NativeReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Ruft die Verweise auf systemeigene Win32\-Assemblys ab oder legt diese fest.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)