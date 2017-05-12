---
title: "IDebugThreadCall::ThreadCallHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugThreadCall.ThreadCallHandler
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugThreadCall::ThreadCallHandler"
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall::ThreadCallHandler
Handleaufrufe um Code in einem anderen Thread.  
  
## Syntax  
  
```  
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### Parameter  
 `dwParam1`  
 \[in\] Der erste Parameter.  
  
 `dwParam2`  
 \[in\] Der zweite Parameter.  
  
 `dwParam3`  
 \[in\] Der dritte Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt Aufrufe, um Code im Debuggerthread auszuführen.  
  
## Siehe auch  
 [IDebugThreadCall\-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)