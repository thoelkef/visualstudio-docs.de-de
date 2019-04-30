---
title: IEEDataStorage::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eff31ef70fc8cb812ff820a92653b6bb0cab6cd5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868223"
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

#### <a name="parameters"></a>Parameter
 `size`

 [out] Die Anzahl der Bytes, die in diesem Objekt enthalten sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Verwenden der [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) Methode, um die tatsächlichen Datenbytes abzurufen.

## <a name="see-also"></a>Siehe auch
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)