---
title: IDebugClassField::EnumNestedClasses | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75b963f7a342a9ce2b276cc03ea5dece9316ff6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313126"
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

## <a name="parameters"></a>Parameter
`ppEnum`\
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
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
