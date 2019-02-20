---
title: DEBUG_REFERENCE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3167deaa7e088ed75584f9fdc0777a608f11a47e
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413474"
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
dwFields  
Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, der angibt, welche Felder ausgefüllt sind.

bstrName  
Die vom Benutzer angegebener Name des der [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt.

bstrType  
Der Verweistyp als formatierte Zeichenfolge.

bstrValue  
Der Verweiswert als formatierte Zeichenfolge

dwAttrib  
Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die die Flags für die Attribute der Debug-Eigenschaft angibt.

dwRefType  
Ein Wert aus der [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) -Enumeration, der angibt, ob der Verweistyp stark oder schwach ist.

m_pReference  
Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das die Verweisinformationen angibt.

## <a name="remarks"></a>Hinweise
Diese Struktur wird auf den Aufruf zum Übergeben der [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) Methode gefüllt werden soll. Diese Struktur wird auch zurückgegeben, als Teil einer Liste von der [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)  
[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)  
[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)  
[REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)  
[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)  
[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)  
[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
