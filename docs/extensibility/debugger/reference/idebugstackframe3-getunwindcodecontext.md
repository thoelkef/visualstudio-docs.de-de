---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 488f675c39bb01c87aca13a9bef8cc4a715ecf18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719500"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Gibt den Codekontext zurück, der einen Speicherort darstellt, wenn ein Stapelabspulenvorgang aufgetreten ist.

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

## <a name="parameters"></a>Parameter
`ppCodeContext`\
[out] Gibt ein [IDebugCodeContext2-Objekt](../../../extensibility/debugger/reference/idebugcodecontext2.md) zurück, das den Codekontextspeicherort darstellt, wenn die Abspulung eines Stapels erfolgt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Auch wenn diese Methode möglicherweise einen Codekontext für den Speicherort nach dem Abwickeln eines Stapels zurückgibt, bedeutet dies nicht notwendigerweise, dass die Stapelabladung tatsächlich im aktuellen Stapelrahmen auftreten kann.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
