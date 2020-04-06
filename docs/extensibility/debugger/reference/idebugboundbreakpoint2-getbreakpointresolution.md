---
title: IDebugBoundBreakpoint2::GetBreakpointResolution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab88009eb1c1bbbd59bbad2dfcbf62567db3941f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735580"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Ruft die Haltepunktauflösung ab, die diesen Haltepunkt beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Parameter
`ppBPResolution`\
[out] Gibt die [IDebugBreakpointResolution2-Schnittstelle](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) zurück, die eine der folgenden Stellt:

- Das Breakpoint-Auflösungsobjekt, das die Position im Code beschreibt, an die ein Codehaltepunkt gebunden wurde.

- Der Datenspeicherort, an dem ein Datenhaltepunkt gebunden ist.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` zurück, wenn der Status des `BPS_DELETED` gebundenen Haltepunktobjekts auf (Teil der BP_STATE-Enumeration) festgelegt ist. [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Bemerkungen
Rufen Sie die [GetBreakpointType-Methode](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) auf, um zu bestimmen, ob die Breakpoint-Auflösung für Code oder Daten bestimmt ist.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CBoundBreakpoint` Methode für ein einfaches Objekt implementiert wird, das die [IDebugBoundBreakpoint2-Schnittstelle](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) verfügbar macht.

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
