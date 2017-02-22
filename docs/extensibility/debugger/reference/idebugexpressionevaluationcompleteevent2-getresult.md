---
title: "IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs"
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
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetResult"
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluationCompleteEvent2::GetResult
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Ergebnis der Ausdrucksauswertung ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```c#  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### Parameter  
 `ppResult`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das das Ergebnis der Ausdrucksauswertung darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das zurückgegebene Objekt enthält [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) den Wert des ausgewerteten Ausdrucks.  Beachten Sie, dass dieser Wert ein komplexer Wert wie ein Array sein kann, doch das Endergebnis ein numerisches oder ein Zeichenfolgenwert sein muss, die dem Benutzer angezeigt wird.  
  
## Siehe auch  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)