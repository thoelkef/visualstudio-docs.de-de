---
title: IDebugObject::IsEqual | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d909dc0896bcc1b130ce908699c04ad9543c73
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691110"
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

#### <a name="parameters"></a>Parameter
 `pObject`

 [in] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das das zu vergleichende Objekt darstellt.

 `pfIsEqual`

 [out] Ungleich NULL zurück (`TRUE`), wenn die Werte der Objekte gleich ist; andernfalls sind, gibt NULL zurück (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In der Regel kann diese Methode vergleichen die Adressen der-Werte dargestellt werden, indem die `pObject` -Parameter, und dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, wenn die Adressen gleich sind, und klicken Sie dann die Objekte als gleich betrachtet werden können.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)