---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e77acd4091abd7da5c9d302fb4c4dd6eb66af379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122989"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>Parameter

`pMDMProgram` [in] Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, die das Programm vermutlich zum Anfügen an darstellt.

 `pCallback` [in] Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle, die verwendet werden, das SDM-Debug-Ereignissen an.

 `dwReason` [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, der den Grund für das Anfügen von angibt.

## <a name="return-value"></a>Rückgabewert

Eine Implementierung sollte stets `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise

> [!WARNING]
> Ab Visual Studio 2005, diese Methode wird nicht mehr verwendet und sollten stets `E_NOTIMPL`. Finden Sie unter der [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle für ein alternativer Ansatz, wenn der Programm-Knoten angeben, es kann nicht angefügt werden, um muss oder das Programm Knoten für das Programm einfach Einstellung `GUID`. Implementieren Sie andernfalls die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.

## <a name="prior-to-visual-studio-2005"></a>Vor Visual Studio 2005

Diese Methode muss implementiert werden, nur dann, wenn die DE im Adressraum des zu debuggenden Programms ausgeführt wird. Andernfalls sollte diese Methode zurückgeben `S_FALSE`.

Die DE muss senden, wenn diese Methode aufgerufen wird, die [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) Ereignisobjekt, wenn er noch nicht für diese Instanz gesendet wurden die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle, als auch die [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) und [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Ereignisobjekten. Die [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) Ereignisobjekt wird dann gesendet, wenn die `dwReason` Parameter ist `ATTACH_REASON_LAUNCH`.

DE aufrufen muss die [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode auf die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) angegebenen der [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis Objekt und müssen die GUID für das Programm speichern in den Instanzdaten für die `IDebugProgram2` Objekt von der DE implementiert wird.

## <a name="see-also"></a>Siehe auch

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)