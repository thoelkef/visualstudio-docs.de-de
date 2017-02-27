---
title: "CreateCSharpManifestResourceName Task | Microsoft Docs"
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
  - "MSBuild, CreateCSharpManifestResourceName task"
  - "CreateCSharpManifestResourceName task [MSBuild]"
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# CreateCSharpManifestResourceName Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt einen Manifestnamen im [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Format auf der Grundlage eines bestimmten RESX\-Dateinamens oder einer anderen Ressource.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der [CreateCSharpManifestResourceName Task](../msbuild/createcsharpmanifestresourcename-task.md) beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`ManifestResourceNames`|Schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Die resultierenden Manifestnamen.|  
|`ResourceFiles`|Erforderlicher `String`\-Parameter.<br /><br /> Der Name der Ressourcendatei, aus der der [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Manifestname erstellt werden soll.|  
|`RootNamespace`|Optionaler `String`\-Parameter.<br /><br /> Der Stammnamespace der Ressourcendatei, der normalerweise aus der Projektdatei übernommen wird.  Dieser kann `null` lauten.|  
|`PrependCultureAsDirectory`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird der Kulturname unmittelbar vor dem Manifestressourcennamen als Verzeichnisname hinzugefügt.  Der Standardwert lautet `true`.|  
|`ResourceFilesWithManifestResourceNames`|Optionaler schreibgeschützter `String`\-Ausgabeparameter.<br /><br /> Gibt den Namen der Ressourcendatei zurück, die jetzt den Manifestressourcennamen enthält.|  
  
## Hinweise  
 Durch die [CreateVisualBasicManifestResourceName Task](../msbuild/createvisualbasicmanifestresourcename-task.md) wird der entsprechende Manifestressourcenname ermittelt, der einer bestimmten RESX\- oder anderen Ressourcendatei zugewiesen werden soll.  Durch die Aufgabe wird einer Ressourcendatei ein logischer Name zur Verfügung gestellt, der dann in Metadatenform an einen Ausgabeparameter angefügt wird.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)