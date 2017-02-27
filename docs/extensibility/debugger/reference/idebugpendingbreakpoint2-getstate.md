---
title: "IDebugPendingBreakpoint2::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::GetState"
helpviewer_keywords: 
  - "GetState-Methode"
  - "IDebugPendingBreakpoint2::GetState-Methode"
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Zustand des anstehenden Haltepunkts ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetState(   
   PENDING_BP_STATE_INFO* pState  
);  
```  
  
```c#  
int GetState(   
   PENDING_BP_STATE_INFO[] pState  
);  
```  
  
#### Parameter  
 `pState`  
 \[in, out\]  Eine [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Struktur, die mit einer Beschreibung dieses anstehenden Haltepunkts gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)