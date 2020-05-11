---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734393"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ruft die Klasse ab, die diese Klasse umschließt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parameter
`ppClassField`\
[out] Gibt ein [IDebugClassField-Objekt](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das die einschließende Klasse darstellt. Gibt einen NULL-Wert zurück, wenn keine einschließende Klasse vorhanden ist.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Wenn die von diesem [IDebugClassField-Objekt](../../../extensibility/debugger/reference/idebugclassfield.md) dargestellte Klasse `ppClassField` eine `IDebugClassField` geschachtelte Klasse ist, gibt der Parameter ein Objekt zurück, das die einschließende Klasse darstellt. Beispielsweise wird diese Klassendefinition gegeben:

```
class RootClass {
    class NestedClass { }
};
```

Wenn `GetEnclosingClass` Sie die `IDebugClassField` Methode `NestedClass` für das `IDebugClassField` Objekt aufrufen, das die Klasse darstellt, wird ein Objekt zurückgegeben, das die Klasse `RootClass`darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
