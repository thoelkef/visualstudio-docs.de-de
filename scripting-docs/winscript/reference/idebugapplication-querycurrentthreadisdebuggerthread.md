---
title: "IDebugApplication::QueryCurrentThreadIsDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::QueryCurrentThreadIsDebuggerThread"
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::QueryCurrentThreadIsDebuggerThread
Bestimmt, ob der aktuelle Betriebsthread der Debuggerthread ist.  
  
## Syntax  
  
```  
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode erfolgreich war und der aktuelle Betriebsthread ist der Debuggerthread.|  
|`S_FALSE`|Der aktuelle Betriebsthread ist nicht der Debuggerthread.|  
  
## Hinweise  
 Diese Methode bestimmt, ob der aktuelle Betriebsthread der Debuggerthread ist.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)