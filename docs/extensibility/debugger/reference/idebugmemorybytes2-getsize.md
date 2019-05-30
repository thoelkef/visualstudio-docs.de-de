---
title: IDebugMemoryBytes2::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c89e6c5c9ee2b60caef10c5f8378e699b4bc49d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324564"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Ruft die Größe in Bytes, des Arbeitsspeichers dargestellt durch diese [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

## <a name="parameters"></a>Parameter
`pqwSize`\
[out] Gibt die Größe, der den Speicherplatz in Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)