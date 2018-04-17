---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea52b8be040df50da1585165599c4fdea635557
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Sendet eine Benachrichtigung der Debug-Ereignissen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pEngine`  
 [in] Ein [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Objekt, das Debugging-Modul (DE) darstellt, der dieses Ereignis sendet. Eine bereitgestellten Kompatibilitätsrichtlinie ist erforderlich, um diesen Parameter ausfüllen.  
  
 `pProcess`  
 [in] Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess darstellt, in dem das Ereignis auftritt. Dieser Parameter wird von der Sitzung Debug-Manager (SDM) gefüllt. Ein DE übergibt immer einen null-Wert für diesen Parameter.  
  
 `pProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das die Anwendung darstellt, in dem dieses Ereignis tritt auf. Dieser Parameter ist für die meisten Ereignisse keinen null-Wert.  
  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem dieses Ereignis tritt auf. Für Stoppereignisse darf nicht diesen Parameter ein null-Wert sein, wie der Stapelrahmen aus diesen Parameter abgerufen werden.  
  
 `pEvent`  
 [in] Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Objekt, das Debug-Ereignis darstellt.  
  
 `riidEvent`  
 [in] GUID, die die Ereignisschnittstelle zum Abrufen von identifiziert die `pEvent` Parameter.  
  
 `dwAttrib`  
 [in] Eine Kombination aus Flags aus der [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Beim Aufrufen dieser Methode die `dwAttrib` Parameter muss ein Rückgabewert übereinstimmen der [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) Methode als für das Ereignisobjekt zu übergeben, der `pEvent` Parameter.  
  
 Alle Debug-Ereignisse werden asynchron ausgeführt wird, unabhängig davon, ob ein Ereignis selbst asynchron oder nicht ist bereitgestellt. Wenn diese Methode in eine bereitgestellten Kompatibilitätsrichtlinie aufgerufen wird, gibt der zurückgegebene Wert nicht an, ob das Ereignis verarbeitet wurde, nur, ob das Ereignis empfangen wurde. In der Tat wurde in den meisten Fällen das Ereignis nicht verarbeitet Rückkehr dieser Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)