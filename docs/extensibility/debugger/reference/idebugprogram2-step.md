---
title: IDebugProgram2::Step | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10685adb27c9bf2e962beccb7e68f19ce5c27eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Führt einen Schritt aus.  
  
> [!NOTE]
>  Diese Methode ist veraltet. Verwenden der [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode stattdessen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread wird in Einzelschritten darstellt.  
  
 `sk`  
 [in] Ein Wert aus der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der den Typ des Schritts angibt.  
  
 `step`  
 [in] Ein Wert aus der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) -Enumeration, die Einheit des Schritts (z. B. von einer Anweisung oder der Anweisung) angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für den Fall, dass Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollten andere Threads in die Anwendung ausführen, Prozedurschritt ein bestimmter Thread ausgeführt wird.  
  
> [!WARNING]
>  Keine Stopping-Ereignis oder ein sofort (synchron) Ereignis senden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) während der Bearbeitung dieser Aufruf; andernfalls der Debugger reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)