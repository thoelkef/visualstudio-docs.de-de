---
title: IDebugProgramEngines2::SetEngine | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a8c48de1a068300bb514d10528592cc518004db
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343446"
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

## <a name="parameters"></a>Parameter
`guidEngine`\
[in] Die GUID des DE.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)