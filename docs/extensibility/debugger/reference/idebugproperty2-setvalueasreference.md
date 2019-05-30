---
title: IDebugProperty2::SetValueAsReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9e98465f16f58f734ef6fd58b66494b4aaf0b65
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314611"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parameter
`rgpArgs`\
[in] Ein Array von Argumenten, die an den Eigenschaftensetter für verwalteten Code übergeben werden sollen. Wenn Setter für die Eigenschaft über keine Argumente akzeptiert, oder wenn diese [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt verweist nicht auf solche einen Eigenschaften-Setter `rgpArgs` sollte ein null-Wert sein. Dieser Parameter ist in der Regel einen null-Wert.

`dwArgCount`\
[in] Die Anzahl der Argumente in der `rgpArgs` Array.

`pValue`\
[in] Ein Verweis in Form einer [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das den Wert, der zum Festlegen dieser Eigenschaft.

`dwTimeout`\
[in] Wie lange ausführen, um den Wert in Millisekunden festgelegt. Ein typischer Wert `INFINITE`. Dies wirkt sich auf die Länge der Zeit, die alle möglichen Auswertung aus.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; andernfalls ein Fehler code wird zurückgegeben, in der Regel eine der folgenden:

|Fehler|Beschreibung|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Festlegen des Werts aus einem Verweis wird nicht unterstützt.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, wie diese Eigenschaft auf eine Methode verweist.|
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|

## <a name="see-also"></a>Siehe auch
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)