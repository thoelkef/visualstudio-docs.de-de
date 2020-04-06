---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82f12b12c9afbc24f9416ec2639a4b9768d8fd0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735416"
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

## <a name="parameters"></a>Parameter
`dwHitCount`\
[in] Die zu setzende Trefferanzahl.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` zurück, wenn der Status des `BPS_DELETED` gebundenen Haltepunktobjekts auf (Teil der BP_STATE-Enumeration) festgelegt ist. [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Bemerkungen
 Die Trefferanzahl gibt an, wie oft dieser Haltepunkt während des aktuellen Ablaufs der Sitzung ausgelöst wurde.

 Diese Methode wird in der Regel vom Debugmodul aufgerufen, um die aktuelle Trefferanzahl auf diesem Haltepunkt zu aktualisieren.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
