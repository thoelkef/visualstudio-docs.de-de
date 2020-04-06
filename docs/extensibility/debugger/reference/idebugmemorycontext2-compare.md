---
title: IDebugMemoryContext2::Vergleichen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727490"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Vergleicht den Speicherkontext mit jedem Kontext im angegebenen Array in der von Vergleichsflags angegebenen Weise und gibt einen Index des ersten Kontexts zurück, der übereinstimmt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parameter
`compare`\
[in] Ein Wert [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) aus der CONTEXT_COMPARE-Enumeration, die den Typ des Vergleichs bestimmt.

`rgpMemoryContextSet`\
[in] Ein Array von Verweisen auf die [IDebugMemoryContext2-Objekte,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) mit denen verglichen werden soll.

`dwMemoryContextSetLen`\
[in] Die Anzahl der Kontexte im `rgpMemoryContextSet` Array.

`pdwMemoryContext`\
[out] Gibt den Index des ersten Speicherkontexts zurück, der den Vergleich erfüllt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_COMPARE_CANNOT_COMPARE` zurück, wenn die beiden Kontexte nicht verglichen werden können.

## <a name="remarks"></a>Bemerkungen
 Ein Debugmodul (DE) muss nicht alle Arten von Vergleichen unterstützen, `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`aber `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`es muss mindestens , und .

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
