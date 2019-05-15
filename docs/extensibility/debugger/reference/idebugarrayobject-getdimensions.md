---
title: IDebugArrayObject::GetDimensions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60ee75454bf105f12b79d60e032549bcb84ab465
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615238"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ruft die Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
[in] Die Anzahl der Dimensionen, die abgerufen werden.

`dwDimensions`\
[in, out] Ein Array, das mit der Größe der einzelnen Dimensionen gefüllt ist. `dwCount` Gibt an, die maximale Größe der `dwDimensions` Array.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein mehrdimensionales Array kann es sich um andere Größen für jede Dimension sein. Angenommen, das dreidimensionale Array `myarray[3][2][6]`, würde diese Methode zurückgeben, 3, 2 und 6 in der `dwDimensions` Parameter in dieser Reihenfolge.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)