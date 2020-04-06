---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4b6e5f2d28d27deb5e4e1ff8278a071ff9110fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726518"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testet, ob es sich bei diesem Objekt um einen Nullverweis handelt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parameter
`pfIsNull`\
[out] Gibt einen Wert`TRUE`ungleich Null zurück ( ), wenn es sich bei diesem Objekt um einen Nullverweis handelt; Andernfalls wird Null`FALSE`zurückgegeben ( ).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein NULL-Verweis bezeichnet ein leeres Objekt oder ein Objekt, dem nicht zugewiesen wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
