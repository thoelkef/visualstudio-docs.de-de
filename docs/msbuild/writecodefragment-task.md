---
title: "WriteCodeFragment Task | Microsoft Docs"
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
  - "MSBuild, WriteCodeFragment task"
  - "WriteCodeFragment task [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteCodeFragment Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Generiert eine temporäre Codedatei mit dem angegebenen generierten Codefragment.  Löscht die Datei nicht.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `WriteCodeFragment`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AssemblyAttributes`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Beschreibung der zu schreibenden Attribute.  Der `Include`\-Wert des Elements ist der vollständige Typname des Attributs ist, z. B. "System.AssemblyVersionAttribute".<br /><br /> Alle Metadaten sind Name\-Wert\-Paare eines Parameters, der vom Typ `String`sein muss.  Einige Attribute erlauben nur positionelle Konstruktorargumente.  Jedoch können Sie solche Argumente in jedem Attribut verwenden.  Legen Sie positionale Konstruktorattribute mit Metadaten\-Namen fest, die "\_Parameter1", "\_Parameter2" und so weiter entsprechen.<br /><br /> Ein Parameter\-Index kann nicht übersprungen werden.|  
|`Language`|Erforderlicher `String`\-Parameter.<br /><br /> Gibt die Sprache für den zu generierenden Code an.<br /><br /> `Language` kann jede Sprache sein, für die ein CodeDom\-Anbieter verfügbar ist, beispielsweise "C\#" oder "VisualBasic".  Die ausgegebene Datei erhält die Standarddateinamenerweiterung für diese Sprache.|  
|`OutputDirectory`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Zielordner für den generierten Code an. In der Regel ist dies der Zwischenordner.|  
|`OutputFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt den Pfad der Datei an, die generiert wurde.  Wenn dieser Parameter festgelegt wird, indem Sie einen Dateinamen verwenden, wird der Zielordner dem Dateinamen vorangestellt.  Wenn er von einen Stamm festgelegt ist, wird der Zielordner ignoriert.<br /><br /> Wenn dieser Parameter nicht festgelegt wird, ist der Ausgabedateiname der Zielordner, ein beliebiger Dateiname und die Standarddateinamenerweiterung für die angegebene Sprache.|  
  
## Hinweise  
 Zusätzlich zu den Parametern, die in der Tabelle aufgeführt sind, erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)