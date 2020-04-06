---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728615"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Erstellt ein Arrayobjekt. Dieses Array kann entweder primitive oder Objektinstanzwerte enthalten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ot`\
[in] Gibt einen Wert [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) aus der OBJECT_TYPE-Enumeration an, der den Typ des neuen Arrayobjekts angibt.

`pClassField`\
[in] Ein [IDebugField-Objekt,](../../../extensibility/debugger/reference/idebugfield.md) das die Klasse eines Objekts darstellt, wenn ein Array von Objektinstanzwerten erstellt wird. Wenn Sie ein Array primitiver Objekte erstellen, ist dieser Parameter ein NULL-Wert.

`dwRank`\
[in] Der Rang oder die Anzahl der Dimensionen des Arrays.

`dwDims`\
[in] Die Größe jeder Dimension des Arrays.

`dwLowBounds`\
[in] Der Ursprung jeder Dimension (in der Regel 0 oder 1).

`ppObject`\
[out] Gibt ein [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Array darstellt. Dies ist eigentlich ein [IDebugArrayObject-Objekt.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das einen Arrayparameter für die Funktion darstellt, die durch die [IDebugFunctionObject-Schnittstelle](../../../extensibility/debugger/reference/idebugfunctionobject.md) dargestellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
