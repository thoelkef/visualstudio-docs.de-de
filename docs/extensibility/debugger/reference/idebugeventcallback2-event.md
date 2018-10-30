---
title: IDebugEventCallback2::Event | Microsoft-Dokumentation
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
ms.openlocfilehash: dc61f6a8b2a8a069d0fb921e4dbfe631088b2925
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913318"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Sendet eine Benachrichtigung der Debug-Ereignisse.  
  
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
 [in] Ein [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Objekt, das die Debug-Engine (DE) darstellt, der dieses Ereignis sendet. Eine bereitgestellten Kompatibilitätsrichtlinie ist erforderlich, diesen Parameter einzugeben.  
  
 `pProcess`  
 [in] Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess darstellt, in dem das Ereignis eintritt. Dieser Parameter wird durch die sitzungsbasierter Debug-Manager (SDM) ausgefüllt. Eine bereitgestellten Kompatibilitätsrichtlinie wird immer einen null-Wert für diesen Parameter übergeben.  
  
 `pProgram`  
 [in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, in dem dieses Ereignis auftritt. Bei den meisten Ereignissen ist dieser Parameter keinen null-Wert.  
  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem dieses Ereignis auftritt. Für das Beenden der Ereignisse, darf nicht diesen Parameter ein null-Wert sein, wie der Stapelrahmen aus diesen Parameter abgerufen werden.  
  
 `pEvent`  
 [in] Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Objekt, das Debug-Ereignis darstellt.  
  
 `riidEvent`  
 [in] GUID, die die Senkenereignis-Schnittstelle zum Abrufen von identifiziert die `pEvent` Parameter.  
  
 `dwAttrib`  
 [in] Eine Kombination von Flags aus der [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Beim Aufrufen dieser Methode, die `dwAttrib` Parameter muss ein Rückgabewert übereinstimmen der [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) Methode wie für das Ereignisobjekt zu übergeben, der `pEvent` Parameter.  
  
 Alle Debug-Ereignisse werden asynchron gesendet, unabhängig davon, ob ein Ereignis selbst asynchron oder synchron ist. Wenn diese Methode in eine bereitgestellten Kompatibilitätsrichtlinie aufgerufen wird, wird der zurückgegebene Wert nicht angegeben, ob das Ereignis verarbeitet wurde, sondern nur, ob das Ereignis empfangen wurde. Tatsächlich wurde in den meisten Fällen das Ereignis nicht verarbeitet Rückkehr dieser Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)