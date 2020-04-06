---
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737450"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Enthält Informationen zu einer Debugeigenschaft.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Member
`dwValidFields`\
Eine Kombination von [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Flags aus der DEBUGPROP_INFO_FLAGS-Enumeration, die angibt, welche Felder ausgefüllt werden.

`bstrFullName`\
Der vollständige Name der Eigenschaft.

`bstrName`\
Der Eigenschaftsname in einem Kontext.

`bstrType`\
Der Eigenschaftstyp als formatierte Zeichenfolge.

`bstrValue`\
Der Eigenschaftswert als formatierte Zeichenfolge.

`pProperty`\
Das [IDebugProperty2-Objekt,](../../../extensibility/debugger/reference/idebugproperty2.md) das von dieser Struktur beschrieben wird.

`dwAttrib`\
Eine Kombination von [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Flags aus der DBG_ATTRIB_FLAGS-Enumeration, die die Attribute dieser Eigenschaft beschreibt.

## <a name="remarks"></a>Bemerkungen
Eine Eigenschaft ist ein Objekt hierarchischer Natur mit einem Namen, Typ und Wert. Beispielsweise kann eine Eigenschaft lokale Variablen, Parameter, Überwachungsvariablen und Ausdrücke sowie Register beschreiben.

Diese Struktur wird an die [GetPropertyInfo-Methode](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) übergeben, bei der sie ausgefüllt wird. Diese Struktur wird auch als Teil einer Liste dieser Struktur von der [IEnumDebugPropertyInfo2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zurückgegeben, die wiederum von einem Aufruf der [EnumChildren-](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) und [EnumProperties-Methoden](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
