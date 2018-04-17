---
title: IDebugProcess3::Step | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbc19c339e5d53bc9dde13ebd4a1bbddd214810c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Bewirkt, dass den Prozess in einer Anweisung oder Anweisung wechseln.  
  
> [!NOTE]
>  Diese Methode sollte verwendet werden, anstelle von [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt, das den Thread wird in Einzelschritten darstellt.  
  
 `sk`  
 [in] Eines der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) Werte.  
  
 `step`  
 [in] Eines der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Werte.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für den Fall, dass Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollte die andere Threads im Prozess ausgeführt, Prozedurschritt ein bestimmter Thread ausgeführt wird.  
  
 **Warnung** keine Stopping-Ereignis oder ein sofort (synchron) Ereignis senden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) während der Bearbeitung dieser Aufruf; andernfalls der Debugger reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)