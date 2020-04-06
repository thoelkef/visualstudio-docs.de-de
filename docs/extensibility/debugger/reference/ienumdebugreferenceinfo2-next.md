---
title: IEnumDebugReferenceInfo2::Weiter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Next
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Next
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb10504b2dbe02856364baa0670a7c825ef80cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715326"
---
# <a name="ienumdebugreferenceinfo2next"></a>IEnumDebugReferenceInfo2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG                   celt,
   DEBUG_REFERENCE_INFO ** rgelt,
   ULONG*                  pceltFetched
);
```

```csharp
int Next(
   uint                   celt,
   DEBUG_REFERENCE_INFO[] rgelt,
   ref uint               pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale `rgelt` Größe des Arrays an.

`rgelt`\
[in, out] Array von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Elementen, die ausgefüllt werden sollen.

`pceltFetched`\
[out] Gibt die Anzahl der `rgelt`tatsächlich in zurückgegebenen Elemente zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
