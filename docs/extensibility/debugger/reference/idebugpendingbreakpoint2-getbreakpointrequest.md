---
title: "IDebugPendingBreakpoint2::GetBreakpointRequest | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::GetBreakpointRequest"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::GetBreakpointRequest-Methode"
  - "GetBreakpointRequest-Methode"
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::GetBreakpointRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Haltepunkt Anforderungen ab, die verwendet wurde, um den anstehenden Haltepunkt zu erstellen.  
  
## Syntax  
  
```cpp#  
HRESULT GetBreakpointRequest(   
   IDebugBreakpointRequest2** ppBPRequest  
);  
```  
  
```c#  
int GetBreakpointRequest(   
   out IDebugBreakpointRequest2 ppBPRequest  
);  
```  
  
#### Parameter  
 `ppBPRequest`  
 \[out\]  Gibt ein Objekt zurück, das die [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Anforderung Haltepunkt darstellt, die verwendet wurde, um den anstehenden Haltepunkt zu erstellen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)