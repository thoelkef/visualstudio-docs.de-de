---
title: IEnumDebugCustomAttributes::Weiter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08228fe4a630eac37c38f4eb247dc91678d8e2e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717234"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Ruft eine angegebene Anzahl benutzerdefinierter Attribute in einer Enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale `rgelt` Größe des Arrays an.

`rgelt`\
[out] Ein Array von [IDebugCustomAttribute-Objekten,](../../../extensibility/debugger/reference/idebugcustomattribute.md) die ausgefüllt werden sollen.

`pceltFetched`\
[out] Gibt die Anzahl der `rgelt`tatsächlich in zurückgegebenen Elemente zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
