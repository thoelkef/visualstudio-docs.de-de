---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d47f3edfffadc74791d6d6b2267a37319a053d7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320830"
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