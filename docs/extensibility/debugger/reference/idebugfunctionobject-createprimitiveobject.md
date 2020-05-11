---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728532"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Erstellt ein primitives Datenobjekt, z. B. eine einfache ganze Zahl.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ot`\
[in] Ein Wert [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) aus der OBJECT_TYPE-Enumeration, der den Typ des zu erstellenden Primitivs darstellt.

`ppObject`\
[out] Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das ein primitives Objekt darstellt, das ein Parameter für die Funktion ist, die durch die [IDebugFunctionObject-Schnittstelle](../../../extensibility/debugger/reference/idebugfunctionobject.md) dargestellt wird. Wenn die Ausdruckszeichenfolge z. B. "myString(5)" lautet, wird diese Methode verwendet, um ein Objekt zu erstellen, das die ganze Zahl 5 darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
