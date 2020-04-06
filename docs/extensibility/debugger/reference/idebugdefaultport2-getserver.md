---
title: IDebugDefaultPort2::GetServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbe6d813b85865b0fdbc20296473684203a3f1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732382"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Diese Methode ruft eine Schnittstelle zum Server ab, auf dem sich dieser Port befindet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Parameter
`ppServer`\
[out] Gibt ein Objekt zurück, das die [IDebugCoreServer3-Schnittstelle](../../../extensibility/debugger/reference/idebugcoreserver3.md) implementiert.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) wird von Visual Studio implementiert und stellt den Server dar, auf dem sich der Port befindet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
