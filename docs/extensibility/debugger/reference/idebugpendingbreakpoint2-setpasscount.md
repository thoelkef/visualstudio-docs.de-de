---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 732eadc955b9a6c9bdded3d52f038ff58ed9c217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725680"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Legt die Passanzahl fest, die dem ausstehenden Haltepunkt zugeordnet ist, oder ändert sie.

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
[in] Eine [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die die Durchlaufanzahl enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.

## <a name="remarks"></a>Bemerkungen
 Alle Durchlaufzählungen, die zuvor dem ausstehenden Haltepunkt zugeordnet waren, gehen verloren. Alle Haltepunkte, die von diesem ausstehenden Haltepunkt `bpPassCount` gebunden sind, werden aufgerufen, um ihre Durchlaufanzahl auf den Parameter festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
