---
title: "CPPClean Task | Microsoft Docs"
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
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), CPPClean task"
  - "CPPClean task (MSBuild (Visual C++))"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CPPClean Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C\+\+\-Projekt erstellt wird.  Das Löschen von Builddateien wird als *Bereinigung* bezeichnet.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der **CPPClean** \-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**DeletedFiles**|Optionaler `ITaskItem[]`\-Ausgabeparameter.<br /><br /> Definiert ein Array von MSBuild\-Ausgabedateielementen, die von Aufgaben aufgenommen und ausgegeben werden können.|  
|**DoDelete**|Optionaler **Boolean**\-Parameter.<br /><br /> Wenn `true`, bereinigen Sie temporäre Builddateien.|  
|**FilePatternsToDeleteOnClean**|Erforderlicher `String`\-Parameter.<br /><br /> Gibt eine durch Semikolons getrennte Liste von Dateierweiterungen von zu bereinigenden Dateien an.|  
|**FilesExcludedFromClean**|Optionaler `String`\-Parameter.<br /><br /> Gibt eine durch Semikolons getrennte Liste von Dateien an, die nicht bereinigt werden sollen.|  
|**FoldersToClean**|Erforderlicher `String`\-Parameter.<br /><br /> Gibt eine durch Semikolons getrennte Liste von Verzeichnissen für die Reinigung an.  Sie können einen vollständigen oder einen relativen Pfad angeben, und der Pfad kann das Platzhaltersymbol \(**\***\) enthalten.|  
  
## Hinweise  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)