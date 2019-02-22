---
title: IDebugPendingBreakpoint2::Enable | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a06ed6e7d3c5f95e0de2ee88c63783924c2b015d
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450008"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Schaltet den aktivierten Zustand des ausstehenden Haltepunkts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable(
    int fEnable
);
```

#### <a name="parameters"></a>Parameter
`fEnable`  
[in] Festlegen der zu ungleich Null (`TRUE`) um ein ausstehender Haltepunkt zu aktivieren, oder 0 (null) (`FALSE`) deaktivieren.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.

## <a name="remarks"></a>Hinweise
Wenn ein ausstehender Haltepunkt aktiviert oder deaktiviert ist, werden alle Breakpoints, die von ihm gebunden mit demselben Status festgelegt.

Diese Methode kann aufgerufen werden, so oft wie erforderlich, selbst wenn der Haltepunkt bereits aktiviert oder deaktiviert ist.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CPendingBreakpoint` -Objekt, das macht die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle.

```cpp
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the bound breakpoint member variable is valid, then enable or
        // disable the bound breakpoint.
        if (m_pBoundBP)
        {
            m_pBoundBP->Enable(fEnable);
        }
        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to enabled or disabled depending on the passed BOOL condition.
        m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;
        hr = S_OK;

    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
