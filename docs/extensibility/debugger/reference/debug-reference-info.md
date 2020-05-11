---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737415"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Beschreibt einen Verweis.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Flags aus der DEBUGREF_INFO_FLAGS-Enumeration, die angibt, welche Felder ausgefüllt werden.

`bstrName`\
Der benutzerspezifische Name des [IDebugReference2-Objekts.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
Der Verweistyp als formatierte Zeichenfolge.

`bstrValue`\
Der Referenzwert als formatierte Zeichenfolge

`dwAttrib`\
Eine Kombination von [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Flags aus der DBG_ATTRIB_FLAGS-Enumeration, die die Flags für die Debugeigenschaftenattribute angibt.

`dwRefType`\
Ein Wert [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) aus der REFERENCE_TYPE-Enumeration, der angibt, ob der Referenztyp stark oder schwach ist.

`m_pReference`\
Ein [IDebugReference2-Objekt,](../../../extensibility/debugger/reference/idebugreference2.md) das die Referenzinformationen angibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an einen Aufruf der [GetReferenceInfo-Methode](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) übergeben, die ausgefüllt werden soll. Diese Struktur wird auch als Teil einer Liste von der [IEnumDebugReferenceInfo2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) zurückgegeben, die wiederum von einem Aufruf der [EnumChildren-Methode](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
