---
title: IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735434"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Legt die Passanzahl fest, die diesem gebundenen Haltepunkt zugeordnet ist, oder ändert sie.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parameter
`bpPassCount`\
[in] Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die die Durchlaufanzahl angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` zurück, wenn der Status des `BPS_DELETED` gebundenen Haltepunktobjekts auf (Teil der BP_STATE-Enumeration) festgelegt ist. [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Bemerkungen
 Die Passanzahl bestimmt, wann der Haltepunkt ausgelöst wird. Die aktuelle Pass- oder Trefferanzahl kann durch Aufrufen der [GetHitCount-Methode](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) abgerufen werden.

 Jede Durchlaufanzahl, die zuvor diesem Haltepunkt zugeordnet war, geht verloren.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
