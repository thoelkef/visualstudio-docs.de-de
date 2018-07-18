---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3f89502beeb1e8165450c7c07f3f55f83dd39e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112328"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Auswertung von Ausdrücken für den angegebenen Thread ausgeführt wird, selbst wenn die Anwendung beendet wurde ermöglicht (oder lässt nicht zu).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pOriginatingProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm, das Auswerten eines Ausdrucks darstellt.  
  
 `dwTid`  
 [in] Gibt den Bezeichner des Threads.  
  
 `dwEvalFlags`  
 [in] Eine Kombination aus Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung ausgeführt werden.  
  
 `pExprCallback`  
 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt um Debugereignisse zu senden, die auftreten, während der Auswertung von Ausdrücken verwendet werden soll.  
  
 `fWatch`  
 [in] Wenn ungleich 0 (`TRUE`), ermöglicht die Auswertung von Ausdrücken auf den identifizierten Thread `dwTid`ist, andernfalls 0 (null) (`FALSE`) lässt keine Auswertung von Ausdrücken in diesem Thread.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Sitzungs-Manager (SDM) fragt ein Programm, identifiziert durch die `pOriginatingProgram` Parameter, die zum Auswerten eines Ausdrucks werden allen anderen angefügten Programme benachrichtigt, indem beim Aufrufen dieser Methode.  
  
 Auswertung von Ausdrücken in einem Programm kann dazu führen, dass der Code zum Ausführen in einer anderen, aufgrund einer funktionsauswertung oder Auswertung aller `IDispatch` Eigenschaften. Aus diesem Grund kann diese Methode die Auswertung von Ausdrücken ausgeführt und abgeschlossen, obwohl der Thread an diesem Programm beendet werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)