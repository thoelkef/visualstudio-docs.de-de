---
title: IDebugMemoryBytes2::WriteAt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5eefaee08d64952681e91711cdf8347186123e57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347134"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Schreibt die angegebene Anzahl von Bytes des Arbeitsspeichers, ab der angegebenen Adresse an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parameter
`pStartContext`\
[in] Die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das angibt, wo Sie anfangen, Schreiben von Bytes.

`dwCount`\
[in] Die Anzahl der zu schreibenden Bytes kennzeichnet.

`rgbMemory`\
[in] Der zu schreibenden Bytes. Dieses Array wird davon ausgegangen, dass mindestens `dwCount` Bytes groß.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` Wenn nicht alle Bytes geschrieben werden kann, oder ein Fehlercode zurückgegeben (in der Regel `E_FAIL`).

## <a name="remarks"></a>Hinweise
 Ist die Startadresse nicht in das Fenster "Arbeitsspeicher" von diesem dargestellt [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Objekt, ohne das Schreiben von tritt ein, und einem Fehlercode von `E_FAIL` zurückgegeben – selbst wenn der Betrag, um das Schreiben in den Speicherbereich überschneidet sich mit.

## <a name="see-also"></a>Siehe auch
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)