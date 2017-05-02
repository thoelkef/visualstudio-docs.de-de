---
title: "ERRORRESUMEACTION-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION-Enumeration"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION-Enumeration
Beschreibt, wie von einem Laufzeitfehler fortgesetzt wird.  
  
## Syntax  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|Wieder\-führt die Anweisung, die den Fehler erzeugt wurde.|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|Ermöglicht das Sprachmodul den Fehler behandeln.|  
|ERRORRESUMEACTION\_SkipErrorStatement|Setzt die Ausführung im Code fortgesetzt, welche Anweisung folgt, die den Fehler erzeugt wurde.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)