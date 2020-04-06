---
title: IDebugObject::IsEqual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726501"
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
[in] Ein [IDebugObject-Objekt,](../../../extensibility/debugger/reference/idebugobject.md) das das zu vergleichende Objekt darstellt.

`pfIsEqual`\
[out] Gibt einen Wert`TRUE`ungleich Null zurück ( ), wenn die Werte der Objekte gleich sind; Andernfalls wird Null`FALSE`zurückgegeben ( ).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In der Regel kann diese Methode die `pObject` Adressen der durch den Parameter und dieses [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) dargestellten Werte vergleichen. Wenn die Adressen gleich sind, können die Objekte als gleich betrachtet werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
