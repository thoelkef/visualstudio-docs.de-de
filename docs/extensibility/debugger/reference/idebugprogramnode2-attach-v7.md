---
title: IDebugProgramNode2::Attach_V7 | Microsoft-Dokumentation
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
ms.openlocfilehash: ea09304d4481ed649f24985b3cabb2a6b1944311
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941632"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.

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

`pMDMProgram` [in] Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, die die Anwendung Anfügen an darstellt.

 `pCallback` [in] Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle, die verwendet werden, das SDM-Debug-Ereignissen an.

 `dwReason` [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, die den Grund für das Anfügen von angibt.

## <a name="return-value"></a>Rückgabewert

Eine Implementierung sollte immer zurückgeben `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise

> [!WARNING]
> Ab Visual Studio 2005, diese Methode wird nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL`. Finden Sie unter den [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle für ein alternativer Ansatz, wenn der Programm-Knoten muss, um anzugeben, es kann nicht angefügt werden, um oder Knotens Programm einfach die Anwendung festlegt `GUID`. Implementieren Sie andernfalls die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.

## <a name="prior-to-visual-studio-2005"></a>Vor Visual Studio 2005

Diese Methode muss implementiert werden, nur dann, wenn die DE im Adressraum des gedebuggten Programm ausgeführt wird. Andernfalls sollte diese Methode zurückgegeben `S_FALSE`.

Wenn diese Methode aufgerufen wird, muss die DE senden die [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) Ereignisobjekt, wenn er noch nicht für diese Instanz gesendet wurden die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle, als auch die [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) und [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) solcher Objekte. Die [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) Ereignisobjekt wird dann gesendet, wenn die `dwReason` Parameter `ATTACH_REASON_LAUNCH`.

Die DE muss aufgerufen werden die [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode für die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) angegebenen die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis Objekt aus, und dieses Programms GUID müssen gespeichert werden. in den Instanzdaten für die `IDebugProgram2` -Objekt, durch die DE implementiert.

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