---
title: "IDebugStackFrame2::GetExpressionContext | Microsoft Docs"
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
  - "IDebugStackFrame2::GetExpressionContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen Auswertungs Elementkontext für die Ausdrucksauswertung innerhalb des aktuellen Kontexts eines Stapelrahmens und des Threads ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```c#  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### Parameter  
 `ppExprCxt`  
 \[out\]  Gibt ein [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Objekt zurück, das einen Kontext für die Ausdrucksauswertung darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Im Allgemeinen kann ein Ausdrucksauswertungs Elementkontext für einen Bereich für das Ausführen von Ausdrucksauswertung angesehen werden.  Rufen Sie die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode auf, um einen Ausdruck zu analysieren und die resultierenden [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) dann Methoden aufrufen, um den analysierten Ausdruck auszuwerten.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)