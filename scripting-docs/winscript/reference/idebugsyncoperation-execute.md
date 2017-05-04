---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
Führt den Vorgang synchron aus und gibt zurück.  
  
## Syntax  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parameter  
 `ppunkResult`  
 \[out\] Der Objektparameter zurückgegeben vom Vorgang.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_ABORT`|Der Vorgang wurde abgebrochen, indem die `IDebugSyncOperation::InProgressAbort`\-Methode aufgerufen wurde.|  
  
## Hinweise  
 Der Prozessdebug\-Manager im Zielthread ruft die `Execute`\-Methode synchron an.  
  
## Siehe auch  
 [IDebugSyncOperation\-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)