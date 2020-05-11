---
title: IDebugReference2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b2fec782ce88dfb2200df35f56b35b304beda5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720633"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Hier wird eine Liste der ausgewählten untergeordneten Elemente einer Referenz abgesucht. Für die zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Flags aus der DEBUGREF_INFO_FLAGS-Enumeration, die angibt, welche Felder in den aufgezählten [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen ausgefüllt werden sollen. [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)

`dwRadix`\
[in] Der Radix, der zum Formatieren numerischer Informationen verwendet werden soll.

`dwAttribFilter`\
[in] Eine Kombination von Flags aus der DBG_ATTRIB_FLAGS-Enumeration, die `pszNameFilter` als Filter in Kombination mit dem Parameter verwendet wird, um auszuwählen, welche Strukturen aufgezählt werden sollen. [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)

`pszNameFilter`\
[in] Eine Zeichenfolge, die einen Filter angibt, z. `dwAttribFilter` B. "MyX", der in Kombination mit dem Parameter verwendet wird, um die aufzuzählenden Strukturen auszuwählen.

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`ppEnum`\
[out] Gibt ein [IEnumDebugReferenceInfo2-Objekt](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) zurück, das eine Liste der angeforderten untergeordneten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
