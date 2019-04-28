---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431471"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hiermit (zugelassen oder verweigert) Auswertung von Ausdrücken für den angegebenen Thread ausgeführt wird, auch wenn die Anwendung beendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das das Programm, das Auswerten eines Ausdrucks darstellt.  
  
 `dwTid`  
 [in] Gibt den Bezeichner des Threads.  
  
 `dwEvalFlags`  
 [in] Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung ausgeführt werden.  
  
 `pExprCallback`  
 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt, das zum Senden von Debug-Ereignisse, die auftreten, während der Auswertung des Ausdrucks verwendet werden.  
  
 `fWatch`  
 [in] Wenn ungleich 0 (`TRUE`), ermöglicht die Auswertung von Ausdrücken für den Thread identifizierte `dwTid`ist, andernfalls 0 (null) (`FALSE`) lässt keine Auswertung des Ausdrucks in diesem Thread.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die sitzungsbasierter Debug-Manager (SDM) fordert ein Programm, das identifizierte die `pOriginatingProgram` Parameter, die zum Auswerten eines Ausdrucks, benachrichtigt er alle anderen angefügten Programme durch Aufrufen dieser Methode.  
  
 Auswertung des Ausdrucks in einem Programm kann dazu führen, dass Code zur Ausführung in einer anderen, aufgrund der funktionsauswertung oder Auswertung aller `IDispatch` Eigenschaften. Aus diesem Grund kann dieser Methode die Auswertung des Ausdrucks ausgeführt und abgeschlossen werden, auch wenn der Thread in diesem Programm beendet werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
