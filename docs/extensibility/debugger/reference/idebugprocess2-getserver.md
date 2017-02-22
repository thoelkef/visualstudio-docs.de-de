---
title: "IDebugProcess2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetServer"
helpviewer_keywords: 
  - "IDebugProcess2::GetServer"
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Server ab, die in diesem Prozess ausgeführt wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```c#  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### Parameter  
 `ppServer`  
 \[out\]  Gibt ein [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)\-Objekt zurück, das den Server darstellt, auf dem der Prozess ausgeführt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Mehrere Server kann auf einem einzelnen Computer ausgeführt werden.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)