---
title: IDebugDisassemblyStream2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75fa12b1e9e70601626667dd3707f1e230f5de0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732111"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Ruft die Größe in den Anweisungen dieses Demontagestreams ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parameter
`pnSize`\
[out] Gibt die Größe in Anweisungen zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der von dieser Methode zurückgegebene Wert kann verwendet werden, um ein Array von [DisassemblyData-Strukturen](../../../extensibility/debugger/reference/disassemblydata.md) zuzuweisen, das dann an die [Read-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) übergeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
