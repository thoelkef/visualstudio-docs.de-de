---
title: IDebugObject::GetMemoryContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38f913952c3e2f58b0d7bd2a27ac20e8f754da2f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323626"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Ruft ab, der Arbeitsspeicher-Kontext, der die Adresse des Werts des Objekts darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Parameter
`pContext`\
[out] Gibt eine [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das die Adresse des Werts des Objekts darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Kontext zurückgegebene Arbeitsspeicher gibt die Adresse des Werts an, wie durch diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt.

## <a name="see-also"></a>Siehe auch
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)