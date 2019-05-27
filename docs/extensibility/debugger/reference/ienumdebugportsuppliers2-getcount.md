---
title: IEnumDebugPortSuppliers2::GetCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::GetCount
helpviewer_keywords:
- IEnumDebugPortSuppliers2::GetCount
ms.assetid: 004f78dd-87d0-41a8-bcaa-f7fadbfeb8fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551857f1f8e0220c50c8c201a8ee550733d68e9f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203400"
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode ist nicht Teil die übliche com-Enumerationsschnittstelle, der angibt, dass nur die `Next`, `Clone`, `Skip`, und `Reset` Methoden implementiert werden müssen.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)