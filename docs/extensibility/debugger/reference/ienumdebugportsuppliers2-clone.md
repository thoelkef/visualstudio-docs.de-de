---
title: IEnumDebugPortSuppliers2::Klonen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Clone
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc6dc6c055f9821c9c7f02312762d3dd0a44bc58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716094"
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
Gibt eine Kopie der aktuellen Enumeration als ein separates Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Clone(
   IEnumDebugPortSuppliers2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPortSuppliers2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Kopie der Enumeration hat den gleichen Status wie das Original zum Zeitpunkt des Aufrufs dieser Methode. Die Zustände der Kopie und des Originals sind jedoch getrennt und können einzeln geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
