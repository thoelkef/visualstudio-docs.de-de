---
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734434"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Erstellt einen Enumerator für die Klassen, die in dieser Klasse geschachtelt sind.

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
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der geschachtelten Klassen darstellt. Gibt einen NULL-Wert zurück, wenn keine geschachtelten Klassen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine geschachtelten Klassen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Jedes Element der Enumeration ist ein [IDebugClassField-Objekt,](../../../extensibility/debugger/reference/idebugclassfield.md) das eine geschachtelte Klasse beschreibt.

Eine geschachtelte Klasse ist eine Klasse, die innerhalb einer anderen Klasse definiert ist. Beispiel:

```
class RootClass {
   class NestedClass { }
};
```

Die [IEnumDebugFields-Enumeration](../../../extensibility/debugger/reference/ienumdebugfields.md) würde ein `NestedClass` Objekt enthalten, das die Klasse darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
