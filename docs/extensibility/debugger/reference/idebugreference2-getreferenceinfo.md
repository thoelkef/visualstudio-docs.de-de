---
title: IDebugReference2::GetReferenceInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa198a3ded56a0dd054cf225bfb6b10968d1da3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720420"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Ruft die [DEBUG_REFERENCE_INFO-Struktur](../../../extensibility/debugger/reference/debug-reference-info.md) ab, die einen Verweis beschreibt. Für die zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Flags aus der DEBUGREF_INFO_FLAGS-Enumeration, die die Felder bestimmen, die in der [DEBUG_REFERENCE_INFO-Struktur](../../../extensibility/debugger/reference/debug-reference-info.md) ausgefüllt werden sollen.

`nRadix`\
[in] Der Radix, der zum Formatieren numerischer Informationen verwendet werden soll.

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`rgpArgs`\
[in] Ein Array von [IDebugReference2-Objekten.](../../../extensibility/debugger/reference/idebugreference2.md) Reserviert für die zukünftige Verwendung; auf einen NULL-Wert festgelegt.

`dwArgCount`\
[in] Die Anzahl der Referenzargumente im `rgpArgs` Array. Reserviert für die zukünftige Verwendung; auf 0 gesetzt.

`pReferenceInfo`\
[out] Eine [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur, die mit einer Beschreibung der Eigenschaft ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
