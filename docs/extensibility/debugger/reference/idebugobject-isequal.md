---
title: IDebugObject::IsEqual | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf592fa83a18c47bf676b84073c0be0e4cb476e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323583"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Vergleicht ein Objekt mit diesem Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parameter
`pObject`\
[in] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das das zu vergleichende Objekt darstellt.

`pfIsEqual`\
[out] Ungleich NULL zurück (`TRUE`), wenn die Werte der Objekte gleich ist; andernfalls sind, gibt NULL zurück (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In der Regel kann diese Methode vergleichen die Adressen der-Werte dargestellt werden, indem die `pObject` -Parameter, und dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, wenn die Adressen gleich sind, und klicken Sie dann die Objekte als gleich betrachtet werden können.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)