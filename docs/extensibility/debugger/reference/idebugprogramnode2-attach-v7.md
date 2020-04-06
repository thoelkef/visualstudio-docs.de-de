---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722138"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Veraltet. NICHT VERWENDEN.

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

## <a name="parameters"></a>Parameter

`pMDMProgram`\
[in] Die [IDebugProgram2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprogram2.md) die das Programm darstellt, an das angefügt werden soll.

`pCallback`\
[in] Die [IDebugEventCallback2-Schnittstelle,](../../../extensibility/debugger/reference/idebugeventcallback2.md) die zum Senden von Debugereignissen an das SDM verwendet werden soll.

`dwReason`\
[in] Ein Wert [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) aus der ATTACH_REASON-Enumeration, der den Grund für das Anfügen angibt.

## <a name="return-value"></a>Rückgabewert

Eine Implementierung sollte `E_NOTIMPL`immer zurückgegeben werden.

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Ab Visual Studio 2005 wird diese Methode nicht `E_NOTIMPL`mehr verwendet und sollte immer zurückgegeben werden. Einen alternativen Ansatz finden Sie in der [IDebugProgramNodeAttach2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) wenn der Programmknoten angeben muss, `GUID`dass er nicht angefügt werden kann, oder wenn der Programmknoten einfach das Programm festlegt. Implementieren Sie [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) andernfalls die Attach-Methode.

## <a name="prior-to-visual-studio-2005"></a>Vor Visual Studio 2005

Diese Methode muss nur implementiert werden, wenn die DE im Adressraum des zu debuggenden Programms ausgeführt wird. Andernfalls sollte diese `S_FALSE`Methode zurückgeben .

Wenn diese Methode aufgerufen wird, muss die DE das [IDebugEngineCreateEvent2-Ereignisobjekt](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) senden, wenn es nicht bereits für diese Instanz der [IDebugEngine2-Schnittstelle](../../../extensibility/debugger/reference/idebugengine2.md) sowie für die Ereignisobjekte [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) und [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gesendet wurde. Das [IDebugEntryPointEvent2-Ereignisobjekt](../../../extensibility/debugger/reference/idebugentrypointevent2.md) wird `dwReason` dann `ATTACH_REASON_LAUNCH`gesendet, wenn der Parameter .

Die DE muss die [GetProgramId-Methode](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) für das [IDebugProgram2-Objekt](../../../extensibility/debugger/reference/idebugprogram2.md) aufrufen, das vom [IDebugProgramCreateEvent2-Ereignisobjekt](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) bereitgestellt `IDebugProgram2` wird, und die GUID dieses Programms in den Instanzdaten für das von der DE implementierte Objekt speichern.

## <a name="see-also"></a>Weitere Informationen

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
