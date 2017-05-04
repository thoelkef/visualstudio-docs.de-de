---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
Stellt den Rückgabewert bereit und gibt Objektparameter im synchronen Debugvorgang zurück.  
  
## Syntax  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parameter  
 `phrResult`  
 \[out\] Wenn der Vorgang abgeschlossen ist, ist `phrResult` der Rückgabewert von `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 \[out\] Wenn der Vorgang abgeschlossen ist, ist `ppunkResult` der Objektparameter, der vom Vorgang zurückgegeben wird.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang ist nicht abgeschlossen.|  
  
## Hinweise  
 Wenn der Vorgang abgeschlossen wurde, gibt diese Methode `HRESULT` und der Objektparameter von `IDebugSyncOperation::Execute`.  
  
## Siehe auch  
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)