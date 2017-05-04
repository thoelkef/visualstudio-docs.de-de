---
title: "SCRIPTTHREADSTATE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE-Enumeration"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE-Enumeration
Gibt den Status eines Threads in einem Skriptmodul an.  Diese Enumeration wird von der [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)\-Methode verwendet.  
  
## Syntax  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|Angegebener Thread nicht nur behält ein vorbereitetes Ereignis wieder, verarbeitet sofort ausgeführten Skripttext oder führt ein Skriptmakro aus.|  
|SCRIPTTHREADSTATE\_RUNNING|Angegebener Thread aktiv behält ein vorbereitetes Ereignis wieder, verarbeitet sofort ausgeführten Skripttext oder führt ein Skriptmakro aus.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)