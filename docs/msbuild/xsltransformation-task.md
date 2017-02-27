---
title: "XslTransformation Task | Microsoft Docs"
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
  - "MSBuild, XslTransformation task"
  - "XslTransformation task [MSBuild]"
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# XslTransformation Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Transformiert eine XML\-Eingabe mithilfe einer XSLT oder kompilierten XSLT und von Ausgaben in ein Ausgabegerät oder eine Datei.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `XslTransformation`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`OutputPaths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt die Ausgabedateien für die XML\-Transformation an.|  
|`Parameters`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Parameter für das XSLT\-Eingabedokument an.|  
|`XmlContent`|Optionaler `String`\-Parameter.<br /><br /> Gibt die XML\-Eingabe als Zeichenfolge an.|  
|`XmlInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt die XML\-Eingabedateien an.|  
|`XslCompiledDllPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die kompilierte XSLT an.|  
|`XslContent`|Optionaler `String`\-Parameter.<br /><br /> Gibt die XSLT\-Eingabe als Zeichenfolge an.|  
|`XslInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die XSLT\-Eingabedatei an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)