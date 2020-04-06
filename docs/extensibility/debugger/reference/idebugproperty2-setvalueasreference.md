---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721255"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises fest.

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
[in] Ein Array von Argumenten, die an den verwalteten Codeeigenschaftensetter übergeben werden sollen. Wenn der Eigenschaftensetter keine Argumente annimmt oder wenn dieses [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) nicht auf einen solchen Eigenschaftensetter verweist, `rgpArgs` sollte es sich um einen NULL-Wert handelt. Dieser Parameter ist in der Regel ein NULL-Wert.

`dwArgCount`\
[in] Die Anzahl der `rgpArgs` Argumente im Array.

`pValue`\
[in] Ein Verweis in Form eines [IDebugReference2-Objekts](../../../extensibility/debugger/reference/idebugreference2.md) auf den Wert, der zum Festlegen dieser Eigenschaft verwendet werden soll.

`dwTimeout`\
[in] Wie lange dauert, um den Wert in Millisekunden festzulegen. Ein typischer `INFINITE`Wert ist . Dies wirkt sich auf die Dauer der möglichen Auswertung aus.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird andernfalls ein Fehlercode zurückgegeben, in der Regel einer der folgenden:

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Das Festlegen des Werts aus einem Verweis wird nicht unterstützt.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, da diese Eigenschaft auf eine Methode verweist.|
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
