---
title: IDebugProgram2::Continue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f52fccf640cca32d4291b3d6fb8626c38370ded3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Wird fortgesetzt, Status "beendet" dieses Programm ausführen. Alle vorherigen Ausführungsstatus (z. B. einem Schritt) wird beibehalten, und das Programm gestartet wird, erneut ausführen.  
  
> [!NOTE]
>  Diese Methode ist veraltet. Verwenden der [Fortfahren](../../../extensibility/debugger/reference/idebugprocess3-continue.md) Methode stattdessen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, auf dieses Programm unabhängig davon, wie viele Programme, die debuggt werden oder welche Programm das Stopping-Ereignis generiert wurde. Die Implementierung muss den vorherigen Ausführungsstatus (z. B. einem Schritt) beibehalten und Ausführung wird fortgesetzt, als wäre er nie beendet wurde, vor dem Abschluss der vorherigen Ausführung. Wenn ein Thread an diesem Programm einen Schritt-Over-Vorgang ausführen wurde und wurde beendet, weil ein anderes Programm beendet, und klicken Sie dann diese Methode aufgerufen wurde, muss das Programm, also der ursprünglichen Schritt mit Failover-Vorgang abgeschlossen.  
  
> [!WARNING]
>  Keine Stopping-Ereignis oder ein sofort (synchron) Ereignis senden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) während der Bearbeitung dieser Aufruf; andernfalls der Debugger reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)