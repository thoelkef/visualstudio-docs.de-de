---
title: IDebugEventCallback2::Ereignis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729895"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Sendet Benachrichtigungen über Debugereignisse.

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

## <a name="parameters"></a>Parameter
`pEngine`\
[in] Ein [IDebugEngine2-Objekt,](../../../extensibility/debugger/reference/idebugengine2.md) das das Debugmodul (DE) darstellt, das dieses Ereignis sendet. Zum Ausfüllen dieses Parameters ist ein DE erforderlich.

`pProcess`\
[in] Ein [IDebugProcess2-Objekt,](../../../extensibility/debugger/reference/idebugprocess2.md) das den Prozess darstellt, in dem das Ereignis auftritt. Dieser Parameter wird vom Sitzungsdebug-Manager (SDM) ausgefüllt. Ein DE übergibt immer einen Nullwert für diesen Parameter.

`pProgram`\
[in] Ein [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das das Programm darstellt, in dem dieses Ereignis auftritt. Bei den meisten Ereignissen ist dieser Parameter kein NULL-Wert.

`pThread`\
[in] Ein [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, in dem dieses Ereignis auftritt. Zum Beenden von Ereignissen kann dieser Parameter kein NULL-Wert sein, da der Stapelrahmen von diesem Parameter abgerufen wird.

`pEvent`\
[in] Ein [IDebugEvent2-Objekt,](../../../extensibility/debugger/reference/idebugevent2.md) das das Debugereignis darstellt.

`riidEvent`\
[in] GUID, die identifiziert, welche `pEvent` Ereignisschnittstelle vom Parameter abunabhängig ist.

`dwAttrib`\
[in] Eine Kombination von Flags aus der EVENTATTRIBUTES-Enumeration. [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Beim Aufrufen dieser `dwAttrib` Methode muss der Parameter mit dem Wert übereinstimmen, der von `pEvent` der [GetAttributes-Methode](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) zurückgegeben wird, wie sie für das im Parameter übergebene Ereignisobjekt aufgerufen wird.

 Alle Debugereignisse werden asynchron gesendet, unabhängig davon, ob ein Ereignis selbst asynchron ist oder nicht. Wenn eine DE diese Methode aufruft, gibt der Rückgabewert nicht an, ob das Ereignis verarbeitet wurde, sondern nur, ob das Ereignis empfangen wurde. In den meisten Fällen wurde das Ereignis nicht verarbeitet, wenn diese Methode zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
