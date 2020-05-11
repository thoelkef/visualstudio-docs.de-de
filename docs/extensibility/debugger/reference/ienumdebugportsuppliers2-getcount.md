---
title: IEnumDebugPortSuppliers2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::GetCount
helpviewer_keywords:
- IEnumDebugPortSuppliers2::GetCount
ms.assetid: 004f78dd-87d0-41a8-bcaa-f7fadbfeb8fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 355b7434bb6c0392b93e4395c2ae7a04e796e708
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716052"
---
# <a name="ienumdebugportsuppliers2getcount"></a>IEnumDebugPortSuppliers2::GetCount
Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parameter
`pcelt`\
[out] Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Teil der üblichen COM-Enumerationsschnittstelle, `Skip`die `Reset` angibt, dass nur die `Next`, `Clone`, und Methoden implementiert werden müssen.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
