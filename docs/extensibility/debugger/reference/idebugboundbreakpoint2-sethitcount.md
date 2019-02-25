---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac7cbfa337bfdcf54d213b299badc9ca56d8dcba
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716310"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Legt die Trefferanzahl für den gebundenen Haltepunkt fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

#### <a name="parameters"></a>Parameter
 `dwHitCount`

 [in] Die Trefferanzahl festgelegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Zustand des Objekts gebundene Haltepunkt, um festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).

## <a name="remarks"></a>Hinweise
 Die Trefferanzahl ist die Anzahl wie oft dieser Haltepunkt bei der aktuellen Ausführung der Sitzung ausgelöst wurde.

 Diese Methode wird von der Debug-Engine aktualisiert die aktuelle Trefferanzahl an diesem Haltepunkt in der Regel aufgerufen werden.

## <a name="see-also"></a>Siehe auch
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)