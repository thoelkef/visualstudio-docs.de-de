---
title: IDebugMemoryBytes2::Writeat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727520"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Schreibt die angegebene Anzahl von Bytes an Arbeitsspeicher, beginnend mit der angegebenen Adresse.

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
[in] Das [IDebugMemoryContext2-Objekt,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) das angibt, wo mit dem Schreiben von Bytes begonnen werden soll.

`dwCount`\
[in] Die Anzahl der zu schreibenden Bytes.

`rgbMemory`\
[in] Die zu schreibenden Bytes. Es wird davon ausgegangen, `dwCount` dass dieses Array mindestens Bytes groß ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird `S_FALSE` zurückgegeben, wenn nicht alle Bytes geschrieben `E_FAIL`werden könnten, oder einen Fehlercode zurückgibt (normalerweise ).

## <a name="remarks"></a>Bemerkungen
 Wenn sich die Startadresse nicht innerhalb des Speicherfensters befindet, das durch dieses `E_FAIL` [IDebugMemoryBytes2-Objekt](../../../extensibility/debugger/reference/idebugmemorybytes2.md) dargestellt wird, erfolgt kein Schreiben und es wird ein Fehlercode von zurückgegeben – auch wenn sich der Schreibbetrag im Speicherbereich überschneidet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
