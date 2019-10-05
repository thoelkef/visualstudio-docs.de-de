---
title: IDebugProgramEngines2::SetEngine | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7541971da9420b0527b7c9885f1421b8c2ce0075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182176"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Weist das Programm oder Programm-Knoten die Debug-Engine (DE) zu verwenden, um dieses Programm zu debuggen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

#### <a name="parameters"></a>Parameter
 `guidEngine`

 [in] Die GUID des DE.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)