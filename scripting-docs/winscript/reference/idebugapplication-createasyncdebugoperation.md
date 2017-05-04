---
title: "IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateAsyncDebugOperation"
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateAsyncDebugOperation
Bietet asynchronen Zugriff auf einen angegebenen synchronen Debugvorgang.  
  
## Syntax  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### Parameter  
 `psdo`  
 \[in\] Das synchrone Debugvorgangsobjekt.  
  
 `ppado`  
 \[out\] Das asynchrone Debugvorgangsobjekt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Mit dieser Methode können Sprachmodulen, um Ausdrücke asynchron auszuwerten, ohne den Debuggerthread explizit zu synchronisieren.  Weitere Informationen finden Sie unter [IDebugSyncOperation\-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md) und [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation\-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation\-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)