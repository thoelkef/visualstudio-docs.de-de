---
title: IDebugCoreServer2::EnumPorts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 317f24fd6af107e50b12d86ace53fd8d7f1b4894
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337601"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
Ruft eine Liste aller verfügbaren Ports.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPorts( 
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPorts( 
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) -Objekt, das eine Liste aller Ports aus allen Portanbieter enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)