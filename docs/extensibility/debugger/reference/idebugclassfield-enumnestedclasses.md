---
title: IDebugClassField::EnumNestedClasses | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b85d7a681d84f5549e0cb8f88d3c7a40773cc2f
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413201"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Erstellt einen Enumerator für die Klassen, die in dieser Klasse geschachtelt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parameter
`ppEnum`  
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der geschachtelten Klassen darstellt. Gibt einen null-Wert zurück, wenn es keine geschachtelte Klassen.

## <a name="return-value"></a>Rückgabewert
Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn es keine geschachtelte Klassen. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das eine geschachtelte Klasse beschreibt.

Eine geschachtelte Klasse ist eine Klasse, die innerhalb einer anderen Klasse definiert. Zum Beispiel:

```
class RootClass {
   class NestedClass { }
};
```

Die [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Enumeration enthält Objekt stellt die `NestedClass` Klasse.

## <a name="see-also"></a>Siehe auch
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
