---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f208c52bd45953aaad9efab9b6b65b15b3b759c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735361"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Erstellt einen Enumerator von Haltepunkten, die an dieses Ereignis gebunden waren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt ein [IEnumDebugBoundBreakpoints2-Objekt](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) zurück, das alle von diesem Ereignis gebundenen Haltepunkte aufzählt.

## <a name="return-value"></a>Rückgabewert
Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine gebundenen Haltepunkte vorhanden sind; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Die Liste der gebundenen Haltepunkte ist für diejenigen, die an dieses Ereignis gebunden sind, und ist möglicherweise nicht die gesamte Liste der Haltepunkte, die von einem ausstehenden Haltepunkt gebunden sind. Um eine Liste aller Haltepunkte abzurufen, die an einen ausstehenden Haltepunkt gebunden sind, rufen Sie die [GetPendingBreakpoint-Methode](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) auf, um das zugeordnete [IDebugPendingBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) abzurufen, und rufen Sie dann die [EnumBoundBreakpoints-Methode](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) auf, um ein [IEnumDebugBoundBreakpoints2-Objekt](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) abzurufen, das alle gebundenen Haltepunkte für den ausstehenden Haltepunkt enthält.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CBreakpointSetDebugEventBase-Objekt** implementiert wird, das die [IDebugBreakpointBoundEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) verfügbar macht.

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
