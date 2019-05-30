---
title: IEEDataStorage::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81796fe12c72e2e64f1eb1d5b1cc09e66112d13d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319675"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Gibt die Anzahl der Bytes, die in diesem Objekt enthalten sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parameter
`size`\
[out] Die Anzahl der Bytes, die in diesem Objekt enthalten sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Verwenden der [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) Methode, um die tatsächlichen Datenbytes abzurufen.

## <a name="see-also"></a>Siehe auch
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)