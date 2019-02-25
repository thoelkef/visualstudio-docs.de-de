---
title: IDebugDefaultPort2::GetServer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cbfc81495c1f2319117a236246f1e7c47f3e582
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678645"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Diese Methode ruft eine Schnittstelle mit dem Server, dem auf diesen Port ist.

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

#### <a name="parameters"></a>Parameter
 `ppServer`

 [out] Gibt ein Objekt, das die [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) wird von Visual Studio implementiert und steht für den Server, der der Port auf befindet.

## <a name="see-also"></a>Siehe auch
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)