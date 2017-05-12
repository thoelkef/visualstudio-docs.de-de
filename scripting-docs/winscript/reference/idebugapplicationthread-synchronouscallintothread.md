---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SynchronousCallIntoThread"
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SynchronousCallIntoThread
Stellt einen Mechanismus für den Aufrufer um Code im Anwendungsthread bereit.  
  
## Syntax  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Parameter  
 `pstcb`  
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
 Diese Methode stellt einen Mechanismus für den Aufrufer um Code im Debuggerthread bereit.  Sprachmodule und Hosts verwenden diese Methode normalerweise, um Freethreadobjekte auf ihre Singlethreadanwendung Implementierungen zu implementieren.  
  
## Siehe auch  
 [IDebugApplicationThread\-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall\-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)