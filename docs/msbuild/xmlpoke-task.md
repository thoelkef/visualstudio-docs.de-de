---
title: "XmlPoke Task | Microsoft Docs"
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
  - "XmlPoke task [MSBuild]"
  - "MSBuild, XmlPoke task"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# XmlPoke Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt Werte wie von einer XPath\-Abfrage angegeben in einer XML\-Datei fest.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `XmlPoke`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Namespaces`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Namespaces für XPath\-Abfragepräfixe an.|  
|`Query`|Optionaler `String`\-Parameter.<br /><br /> Gibt die XPath\-Abfrage an.|  
|`Value`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die Ausgabedatei an.|  
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt die XML\-Eingabe als einen Dateipfad an.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)