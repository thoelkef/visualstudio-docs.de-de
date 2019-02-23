---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb0fc6511def34c1f15f91fca22fa9903daa08a9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699560"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Gibt zurück, der Codekontext, eine Position darstellt, wenn ein Stapel zu, Vorgang Entladen aufgetreten ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

#### <a name="parameters"></a>Parameter
 `ppCodeContext`

 [out] Gibt eine [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das Kontext codespeicherort darstellt, wenn eine stapelentladung aufgetreten ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Auch wenn diese Methode einen Codekontext für den Speicherort nach einer stapelentladung zurückgeben kann, bedeutet dies nicht unbedingt, dass der stapelentladung tatsächlich in den aktuellen Stapelrahmen auftreten kann.

## <a name="see-also"></a>Siehe auch
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)