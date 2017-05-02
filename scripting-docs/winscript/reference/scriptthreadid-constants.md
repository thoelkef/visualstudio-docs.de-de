---
title: "SCRIPTTHREADID-Konstanten | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# SCRIPTTHREADID-Konstanten
Wird verwendet, um den Typ des Threads anzugeben.  
  
## Syntax  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## Konstanten  
  
|Konstante|Wert|Bedeutung|  
|---------------|----------|---------------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|Der momentan ausführende Thread.|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|Der Basistyp Thread; das heißt, der Thread, in dem das Skriptmodul instanziiert wurde.|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|Alle Threads.|  
  
## Hinweise  
 Der `SCRIPTTHREADID`\-Typ wird durch `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread` verwendet, aber die Konstanten können durch `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread` nur verwendet werden.  
  
## Siehe auch  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)