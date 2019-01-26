---
title: IDebugProcess3::Step | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1b9dc08812722f843c091e1c87835377eb0621e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025318"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Bewirkt, dass den Prozess eine Anweisung oder Anweisung wechseln.  
  
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
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt, das den Thread wird abgestuften darstellt.  
  
 `sk`  
 [in] Eines der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) Werte.  
  
 `step`  
 [in] Eines der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Werte.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für den Fall, dass alle Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollte die andere Threads im Prozess ausgeführt, wenn ein bestimmter Thread stepping ist.  
  
 **Warnung** senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)