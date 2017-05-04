---
title: "IDebugAsyncOperation::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Start"
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Start
Veranlasst den asynchronen Operation zu starten.  
  
## Syntax  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### Parameter  
 `padocb`  
 Die Rückrufschnittstelle, die Statusereignisse von diesem Vorgang empfängt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_UNEXPECTED`|Ein Vorgang ist bereits vorhanden.|  
  
## Hinweise  
 Diese Methode wird `IDebugSyncOperation::Execute`, im Thread asynchron aufgerufen werden von abgerufenen `IDebugSyncOperation::GetTargetThread`.  Diese Methode sollte nur aus dem Debuggerthread aufgerufen werden; Andernfalls gibt sie nicht zurück, bis der Vorgang abgeschlossen ist.  
  
## Siehe auch  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)