---
title: "TaskExtension Base Class | Microsoft Docs"
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
  - "MSBuild, tool task base class"
  - "tool task base class [MSBuild]"
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# TaskExtension Base Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Viele Aufgaben erben von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Diese Vererbungskette fügt mehrere Parameter zu den Aufgaben hinzu, die davon abgeleitet werden.  Diese Parameter werden in diesem Dokument aufgeführt.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der Basisklassen beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine>\-Parameter.<br /><br /> Gibt die Build\-Engine\-Schnittstelle für Aufgaben an.  Das Buildmodul legt diesen Parameter automatisch fest, um Rückrufe durch Aufgaben zuzulassen.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine2>\-Parameter.<br /><br /> Gibt die Build\-Engine\-Schnittstelle für Aufgaben an.  Das Buildmodul legt diesen Parameter automatisch fest, um Rückrufe durch Aufgaben zuzulassen.<br /><br /> Dies ist eine benutzerfreundliche Eigenschaft, so dass Aufgabenautoren, die von dieser Klasse erben, nicht den Wert von `IBuildEngine` in `IBuildEngine2`umwandeln müssen.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Optionaler <xref:Microsoft.Build.Framework.IBuildEngine3>\-Parameter.<br /><br /> Gibt die vom Host bereitgestellte Buildmodulschnittstelle an.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Optionaler <xref:Microsoft.Build.Framework.ITaskHost>\-Parameter.<br /><br /> Gibt die Instanz des Hostobjekts an \(kann NULL sein\).  Wenn die Host\-IDE einem Hostobjekt diese spezielle Aufgabe zugeordnet hat, legt das Buildmodul diese Eigenschaft fest.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Optionaler schreibgeschützter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>\-Parameter.<br /><br /> Ruft ein `TaskLoggingHelperExtension`\-Objekt ab, das die Aufgabenprotokollierungsmethoden enthält.|  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)