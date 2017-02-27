---
title: "FormatVersion Task | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatVersion Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fügt die Revisionsnummer an die Versionsnummer an.  
  
-   Fall 1: Eingabe: Version\=\<undefiniert\>; Revision\=\<egal\>; Ausgabe: OutputVersion\="1.0.0.0"  
  
-   Fall 2: Eingabe Version\="1.0.0.\*" Revision\="5" Ausgabe: OutputVersion\="1.0.0.5"  
  
-   Fall 3: Eingabe: Version\="1.0.0.0" Revision\=\<egal\>; Ausgabe: OutputVersion\="1.0.0.0"  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `FormatVersion`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`FormatType`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Formattyp an.<br /><br /> -   "Version" \= Version.<br />-   "Pfad" \= "." durch "\_" ersetzen;|  
|`OutputVersion`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt die Ausgabeversion an, die die Revisionsnummer enthält.|  
|`Revision`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Revisionsnummer an, die an die Version angefügt werden soll.|  
|`Version`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Versionsnummerzeichenfolge an, die formatiert werden soll.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)