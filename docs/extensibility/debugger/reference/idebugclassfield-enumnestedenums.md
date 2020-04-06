---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734406"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Erstellt einen Enumerator für die geschachtelten Enumeratoren dieser Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der geschachtelten Enumerationen darstellt. Gibt einen NULL-Wert zurück, wenn keine geschachtelten Enumerationen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine verschachtelten Enumeratoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Jedes Element der Enumeration ist ein [IDebugEnumField-Objekt,](../../../extensibility/debugger/reference/idebugenumfield.md) das eine geschachtelte Enumeration beschreibt.

Eine innerhalb einer Klasse deklarierte Enumeration wird als verschachtelte Enumeration betrachtet. Zum Beispiel kann Folgendes gegeben sein:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Die `EnumNestedEnums` Methode gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das ein `NestedEnum` [IDebugEnumField-Objekt](../../../extensibility/debugger/reference/idebugenumfield.md) enthält, das die Enumeration darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
