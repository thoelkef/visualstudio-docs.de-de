---
title: "GetReferenceAssemblyPaths Task | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetReferenceAssemblyPaths Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Verweisassemblypfade der verschiedenen Frameworks zurück.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `GetReferenceAssemblyPaths`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`ReferenceAssemblyPaths`|Optionaler `String[]`\-Ausgabeparameter.<br /><br /> Gibt den Pfad zurück, basierend auf dem `TargetFrameworkMoniker`\-Parameter.  Wenn die `TargetFrameworkMoniker` null oder leer ist, wird dieser Pfad `String.Empty` sein.|  
|`FullFrameworkReferenceAssemblyPaths`|Optionaler `String[]`\-Ausgabeparameter.<br /><br /> Gibt den Pfad, basierend auf dem `TargetFrameworkMoniker`\- Parameter, ohne Berücksichtigung des Profilteils des Monikers zurück.  Wenn die `TargetFrameworkMoniker` null oder leer ist, wird dieser Pfad `String.Empty` sein.|  
|`TargetFrameworkMoniker`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Zielframework\-Moniker an, der den Verweispfaden der Assembly zugeordnet ist.|  
|`RootPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Stammpfad an, mit dem der Verweisassemblypfad generiert wird.|  
|`BypassFrameworkInstallChecks`|Optionaler [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True)\-Parameter.<br /><br /> Wenn `true`, werden die grundlegenden Überprüfungen umgangen, die `GetReferenceAssemblyPaths` in der Standardeinstellung ausführt, um sicherzustellen, dass bestimmte Laufzeitframeworks je nach Zielframework installiert werden.|  
|`TargetFrameworkMonikerDisplayName`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt den Anzeigenamen für den Zielframework\-Moniker an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)