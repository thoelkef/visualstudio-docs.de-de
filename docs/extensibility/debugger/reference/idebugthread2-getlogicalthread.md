---
title: "IDebugThread2::GetLogicalThread | Microsoft Docs"
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
  - "IDebugThread2::GetLogicalThread"
helpviewer_keywords: 
  - "IDebugThread2::GetLogicalThread"
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Debuggen von Module implementieren diese Methode nicht.  
  
## Syntax  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```c#  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### Parameter  
 `pStackFrame`  
 \[in\]  Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Objekt, das den Stapelrahmen darstellt.  
  
 `ppLogicalThread`  
 \[out\]  Gibt eine `IDebugLogicalThread2`\-Schnittstelle zurück, die den zugeordneten logischen Thread darstellt.  Ein Debugmodul Implementierung sollte dies auf einen NULL\-Wert festlegen.  
  
## Rückgabewert  
 Debugmodul Implementierungen geben immer `E_NOTIMPL`.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)