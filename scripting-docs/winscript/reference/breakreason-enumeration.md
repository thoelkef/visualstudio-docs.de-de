---
title: "BREAKREASON-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON-Enumeration"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON-Enumeration
Gibt an, welche die Unterbrechung verursacht hat.  
  
## Syntax  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|BREAKREASON\_STEP|Das Sprachmodul ist im Tretenmodus.|  
|BREAKREASON\_BREAKPOINT|Das Sprachmodul hat einen expliziten Haltepunkt an.|  
|BREAKREASON\_DEBUGGER\_BLOCK|Das Sprachmodul auf einen Debuggerblock in einem anderen Thread an.|  
|BREAKREASON\_HOST\_INITIATED|Der Host erfordert eine Unterbrechung an.|  
|BREAKREASON\_LANGUAGE\_INITIATED|Das Sprachmodul erfordert eine Unterbrechung an.|  
|BREAKREASON\_DEBUGGER\_HALT|Der Debugger IDE erfordert eine Unterbrechung an.|  
|BREAKREASON\_ERROR|Ein Ausführungsfehler verursacht hat die Unterbrechung.|  
|BREAKREASON\_JIT|Jede durch JIT\-Debugging\-Start.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)