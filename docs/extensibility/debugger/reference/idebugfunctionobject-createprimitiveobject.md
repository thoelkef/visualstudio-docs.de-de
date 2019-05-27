---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae31296d1264715c23a05ef893c159392baf245d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199090"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Erstellt ein Datenobjekt mit primitiven, z. B. einer einfachen ganzen Zahl.

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
[in] Ein Wert aus der [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Enumeration, die den Typ des primitiven Erstellung darstellt.

`ppObject`\
[out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , das das neu erstellte Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie diese Methode zum Erstellen eines Objekts, das ein Primitiv-Objekt, die einen Parameter an die Funktion der darstellt durch dargestellt wird, wird die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle. Wenn die Zeichenfolge des Ausdrucks "myString(5)" ist, würde z. B. diese Methode verwendet werden, erstellen Sie ein Objekt, das die ganze Zahl 5 darstellt.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)