---
title: IDebugMemoryBytes2::Readat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727533"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Liest eine Folge von Bytes, beginnend an einem bestimmten Speicherort.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parameter
`pStartContext`\
[in] Das [IDebugMemoryContext2-Objekt,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) das angibt, wo bytes gelesen werden soll.

`dwCount`\
[in] Die Anzahl der zu lesenden Bytes. Gibt auch die Länge `rgbMemory` des Arrays an.

`rgbMemory`\
[in, out] Array, das mit den tatsächlich gelesenen Bytes gefüllt wurde.

`pdwRead`\
[out] Gibt die Anzahl der zusammenhängenden Bytes zurück, die tatsächlich gelesen wurden.

`pdwUnreadable`\
[in, out] Gibt die Anzahl der nicht lesbaren Bytes zurück. Kann ein Nullwert sein, wenn der Client kein Interesse an der Anzahl der nicht lesbaren Bytes hat.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn 100 Bytes angefordert werden und die ersten 50 lesbar sind, die nächsten 20 nicht lesbar sind und die restlichen 30 lesbar sind, gibt diese Methode zurück:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 In diesem Fall `*pdwRead + *pdwUnreadable < dwCount`muss der Aufrufer einen zusätzlichen Aufruf zum Lesen der verbleibenden 30 Bytes der angeforderten ursprünglichen `pStartContext` 100 bytes vornehmen, und das im Parameter [übergebene IDebugMemoryContext2-Objekt](../../../extensibility/debugger/reference/idebugmemorycontext2.md) muss um 70 erweitert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
