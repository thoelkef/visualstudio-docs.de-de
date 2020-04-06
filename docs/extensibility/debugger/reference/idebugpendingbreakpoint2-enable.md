---
title: IDebugPendingBreakpoint2::Aktivieren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f796aef9533e3861a870b0a0543ae6b4aeb11de1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725888"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Schaltet den aktivierten Status des ausstehenden Haltepunkts um.

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

## <a name="parameters"></a>Parameter
`fEnable`\
[in] Legen Sie einen`TRUE`Wert ungleich Null ( )`FALSE`fest, um einen ausstehenden Haltepunkt zu aktivieren, oder auf Null ( ) zum Deaktivieren.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.

## <a name="remarks"></a>Bemerkungen
Wenn ein ausstehender Haltepunkt aktiviert oder deaktiviert ist, werden alle von ihm gebundenen Haltepunkte auf denselben Zustand festgelegt.

Diese Methode kann so oft wie nötig aufgerufen werden, auch wenn der Haltepunkt bereits aktiviert oder deaktiviert ist.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CPendingBreakpoint` Methode für ein einfaches Objekt implementiert wird, das die [IDebugPendingBreakpoint2-Schnittstelle](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) verfügbar macht.

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

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
