---
title: IDebugProcess2::GetServer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20eed8cb3689ac58b1303f4dec7359d75d0c0f40
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343637"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Ruft den Server ab, dem diesen Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServer( 
   IDebugCoreServer2** ppServer
);
```

```csharp
int GetServer( 
   out IDebugCoreServer2 ppServer
);
```

## <a name="parameters"></a>Parameter
`ppServer`\
[out] Gibt eine [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Objekt, das den Server darstellt, auf dem dieser Vorgang ausgeführt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Mehr als ein Server kann auf einem einzelnen Computer ausgeführt werden.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)