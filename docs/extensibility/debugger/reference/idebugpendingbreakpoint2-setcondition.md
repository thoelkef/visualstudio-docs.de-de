---
title: IDebugPendingBreakpoint2::SetCondition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4683d944f2489b8b21ff545c86e3d867283d644a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725721"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Legt die Bedingung fest, die dem ausstehenden Haltepunkt zugeordnet ist, oder ändert sie.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parameter
`bpCondition`\
[in] Eine [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur, die die festzulegende Bedingung angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jede Bedingung, die zuvor dem ausstehenden Haltepunkt zugeordnet war, geht verloren. Alle Haltepunkte, die von diesem ausstehenden Haltepunkt gebunden sind, werden aufgerufen, um ihre Bedingung auf den im `bpCondition` Parameter angegebenen Wert festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
