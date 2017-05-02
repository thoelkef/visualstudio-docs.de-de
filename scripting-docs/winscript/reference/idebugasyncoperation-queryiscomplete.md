---
title: "IDebugAsyncOperation::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::QueryIsComplete"
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::QueryIsComplete
Bestimmt, ob der Debugvorgang abgeschlossen ist.  
  
## Syntax  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Der Vorgang ist abgeschlossen.|  
|`S_FALSE`|Der Vorgang ist nicht vollständig.|  
  
## Hinweise  
 Diese Methode bestimmt, wenn der Debugvorgang abgeschlossen ist.  
  
## Siehe auch  
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)