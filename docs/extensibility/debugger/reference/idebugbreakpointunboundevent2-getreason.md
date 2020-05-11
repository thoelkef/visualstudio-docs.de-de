---
title: IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9830309f0a40aee37982554e8920a95d289eb74c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734722"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
Ruft den Grund ab, warum der Haltepunkt ungebunden war.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason
);
```

```csharp
int GetReason(
    out enum_ BP_UNBOUND_REASON pdwUnboundReason
);
```

## <a name="parameters"></a>Parameter
`pdwUnboundReason`\
[out] Gibt einen Wert [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) aus der BP_UNBOUND_REASON-Enumeration zurück, der den Grund für die Ungebundenheit des Haltepunkts angibt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Gründe sind die Erneutkeit eines Haltepunkts an eine andere Position nach einem Bearbeitungs- und Weitervorgang oder die Feststellung, dass ein Haltepunkt irrtümlich gebunden wurde.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CBreakpointUnboundDebugEventBase-Objekt** implementiert wird, das die [IDebugBreakpointUnboundEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) verfügbar macht.

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason)
{
    HRESULT hRes = E_FAIL;

    if ( EVAL(pdwUnboundReason) )
    {
        *pdwUnboundReason = m_dwReason;

        hRes = S_OK;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
