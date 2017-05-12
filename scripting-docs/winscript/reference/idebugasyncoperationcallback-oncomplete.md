---
title: "IDebugAsyncOperationCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperationCallBack.onComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugAsyncOperationCallBack::onComplete"
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperationCallBack::onComplete
signalisiert, dass ein Ergebnis aus einem asynchronen Debugvorgang verfügbar ist.  
  
## Syntax  
  
```  
HRESULT onComplete();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 dieser Methode signalisiert, dass ein Ergebnis von einem `IDebugAsyncOperation`\-Objekt verfügbar ist.  Das Ereignis wird im Debuggerthread.  
  
## Siehe auch  
 [IDebugAsyncOperationCallBack\-Schnittstelle](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)