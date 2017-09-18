---
title: "IDebugStackFrame2::GetThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetThread"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetThread"
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Thread ab, der einem Stapelrahmen zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```c#  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### Parameter  
 `ppThread`  
 \[out\]  Gibt ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt zurück, das den Thread darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)