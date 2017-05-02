---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
Stellt einen Mechanismus für den Aufrufer um Code im Debuggerthread bereit.  
  
## Syntax  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Parameter  
 `pptc`  
 \[in\] Das Objekt an den Aufruf.  
  
 `dwParam1`  
 \[in\] Erster Parameter, zu `IDebugThreadCall::ThreadCallHandler` der Methode zu übergeben.  
  
 `dwParam2`  
 \[in\] zweiten Parameter, zu `IDebugThreadCall::ThreadCallHandler` der Methode zu übergeben.  
  
 `dwParam3`  
 \[in\] Dritter Parameter, zu `IDebugThreadCall::ThreadCallHandler` der Methode zu übergeben.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sprachmodule und Hosts verwenden diese Methode normalerweise, um Freethreadobjekte auf ihre Singlethreadanwendung Implementierungen zu implementieren.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall\-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)