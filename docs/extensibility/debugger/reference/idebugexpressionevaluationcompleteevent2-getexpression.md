---
title: "IDebugExpressionEvaluationCompleteEvent2::GetExpression | Microsoft Docs"
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
  - "IDebugExpressionEvaluationCompleteEvent2::GetExpression"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetExpression"
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluationCompleteEvent2::GetExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den ursprünglichen Ausdruck ab oder legt ihn fest.  
  
## Syntax  
  
```cpp#  
HRESULT GetExpression(   
   IDebugExpression2** ppExpr  
);  
```  
  
```c#  
int GetExpression(   
   out IDebugExpression2 ppExpr  
);  
```  
  
#### Parameter  
 `ppExpr`  
 \[out\]  Gibt ein [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)\-Objekt zurück, das den Ausdruck darstellt, der analysiert wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode gibt das Objekt zurück, das bei einem Aufruf der [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode erstellt wurde.  
  
## Siehe auch  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)