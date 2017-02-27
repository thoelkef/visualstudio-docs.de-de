---
title: "VCMessage Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "VCMessage task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), VCMessage task"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# VCMessage Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Protokolliert Warn\- und Fehlermeldungen während eines Builds.  
  
## Hinweise  
 Diese Aufgabe ermöglicht die Implementierung von MSBuild für Visual C\+\+ und soll nicht vom Benutzer aufgerufen werden.  Weitere Informationen finden Sie unter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der **VCMessage** \-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**Arguments**|Optionaler **String**\-Parameter.<br /><br /> Eine durch Semikolons getrennte Liste der Meldungen, die angezeigt werden sollen.|  
|**Code**|Erforderlicher **String**\-Parameter.<br /><br /> Eine Fehlerzahl, die die Meldung qualifiziert.|  
|**Type**|Optionaler **String**\-Parameter.<br /><br /> Gibt die Art der Meldung an, die ausgegeben werden soll.  Geben Sie `"Warnung"` an, um eine Warnmeldung auszugeben, oder `"Fehler"`, um eine Fehlermeldung auszugeben.|  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)