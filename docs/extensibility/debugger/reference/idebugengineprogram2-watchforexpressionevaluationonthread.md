---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ermöglicht \(oder nicht zulässig sind\), Ausdrucksauswertung, die auf dem angegebenen Thread ausgeführt, selbst wenn das Programm beendet wurde.  
  
## Syntax  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### Parameter  
 `pOriginatingProgram`  
 \[in\]  Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm darstellt, das einen Ausdruck auswertet.  
  
 `dwTid`  
 \[in\]  Gibt den Bezeichner des Threads an.  
  
 `dwEvalFlags`  
 \[in\]  Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration, die angeben, wie die Evaluierung ausgeführt werden soll.  
  
 `pExprCallback`  
 \[in\]  Ein Debug\-, um Ereignisse zu senden [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt verwendet werden soll, die während der Ausdrucksauswertung auftreten.  
  
 `fWatch`  
 \[in\]  Wenn ungleich 0 \(`TRUE`\), Ausdrucksauswertung für den Thread ermöglicht, der vom `dwTid`identifiziert wird. Andernfalls Null \(nicht zulässig\)`FALSE`Ausdrucksauswertung für diesen Thread.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn der Debug\- Manager der Sitzung \(SDM\), um ein Programm aufgefordert wird, identifiziert durch den `pOriginatingProgram`\-Parameter, um einen Ausdruck auszuwerten, benachrichtigt sie alle anderen angefügten Programme, indem er diese Methode aufgerufen wird.  
  
 Ausdrucksauswertung in einem Programm kann aufgrund anderer Code, an der Funktionsauswertung oder der Auswertung aller `IDispatch`\-Eigenschaften.  Deswegen kann diese Methode Ausdrucksauswertung, die ausgeführt werden soll und abzuschließen, obwohl der Thread in diesem Programm beendet wird.  
  
## Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)