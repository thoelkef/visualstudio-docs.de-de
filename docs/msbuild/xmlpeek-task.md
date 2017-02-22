---
title: "XmlPeek Task | Microsoft Docs"
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
  - "XmlPeek task [MSBuild]"
  - "MSBuild, XmlPeek task"
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XmlPeek Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Werte wie von einer XPath\-Abfrage angegeben aus einer XML\-Datei zurück.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `XmlPeek`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Namespaces`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Namespaces für die XPath\-Abfragepräfixe an.|  
|`Query`|Optionaler `String`\-Parameter.<br /><br /> Gibt die XPath\-Abfrage an.|  
|`Result`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Ergebnisse, die von diesem Task zurückgegeben werden.|  
|`XmlContent`|Optionaler `String`\-Parameter.<br /><br /> Gibt die XML\-Eingabe als Zeichenfolge an.|  
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die XML\-Eingabe als einen Dateipfad an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)