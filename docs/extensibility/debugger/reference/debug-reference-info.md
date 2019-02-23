---
title: DEBUG_REFERENCE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c82e1d3894b9fa3ffbdffb5ab69c134ff73e0df7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720288"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
Beschreibt einen Verweis an.

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
DwFields eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, der angibt, welche Felder ausgefüllt sind.

Der vom Benutzer angegebene BstrName-Name, der die [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt.

Geben Sie BstrType der Verweis als eine formatierte Zeichenfolge.

BstrValue der Verweiswert als formatierte Zeichenfolge

DwAttrib eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die die Flags für die Attribute der Debug-Eigenschaft angibt.

DwRefType ein Wert aus der [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) -Enumeration, der angibt, ob der Verweistyp stark oder schwach ist.

M_pReference ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das die Verweisinformationen angibt.

## <a name="remarks"></a>Hinweise
Diese Struktur wird auf den Aufruf zum Übergeben der [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) Methode gefüllt werden soll. Diese Struktur wird auch zurückgegeben, als Teil einer Liste von der [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
