---
title: FIELD_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cafe4a34745f3b34070f7d8fed1a246c806375a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736861"
---
# <a name="field_kind"></a>FIELD_KIND
Gibt die Art des Felds an, das in einem [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) enthalten ist.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Felder
`FIELD_KIND_TYPE`\
Gibt an, dass es sich bei dem Feld nur um einen Typ handelt.

`FIELD_KIND_SYMBOL`\
Gibt an, dass es sich bei dem Feld um ein Symbol mit Typ, Name und anderen Informationen handelt.

`FIELD_TYPE_PRIMITIVE`\
Gibt an, dass es sich bei dem Feld um einen primitiven Datentyp handelt.

`FIELD_TYPE_STRUCT`\
Gibt an, dass es sich bei dem Feld um eine Struktur handelt.

`FIELD_TYPE_CLASS`\
Gibt an, dass es sich bei dem Feld um eine Klasse handelt.

`FIELD_TYPE_INTERFACE`\
Gibt an, dass es sich bei dem Feld um eine Schnittstelle handelt.

`FIELD_TYPE_UNION`\
Gibt an, dass es sich bei dem Feld um eine Union handelt.

`FIELD_TYPE_ARRAY`\
Gibt an, dass es sich bei dem Feld um ein Array handelt.

`FIELD_TYPE_METHOD`\
Gibt an, dass es sich bei dem Feld um eine Methode handelt.

`FIELD_TYPE_BLOCK`\
Gibt an, dass es sich bei dem Feld um einen Block handelt.

`FIELD_TYPE_POINTER`\
Gibt an, dass es sich bei dem Feld um einen Zeiger handelt.

`FIELD_TYPE_ENUM`\
Gibt an, dass es sich bei dem Feld um einen aufgezählten Datentyp handelt.

`FIELD_TYPE_LABEL`\
Gibt an, dass es sich bei dem Feld um eine Bezeichnung handelt.

`FIELD_TYPE_TYPEDEF`\
Gibt an, dass es sich bei dem Feld um einen typdef handelt.

`FIELD_TYPE_BITFIELD`\
Gibt an, dass es sich bei dem Feld um ein Bitfeld handelt.

`FIELD_TYPE_NAMESPACE`\
Gibt an, dass es sich bei dem Feld um einen Namespace handelt.

`FIELD_TYPE_MODULE`\
Gibt an, dass es sich bei dem Feld um ein Modul handelt.

`FIELD_TYPE_DYNAMIC`\
Gibt an, dass das Feld dynamisch ist.

`FIELD_TYPE_PROP`\
Gibt an, dass es sich bei dem Feld um eine Eigenschaft handelt.

`FIELD_TYPE_INNERCLASS`\
Gibt an, dass es sich bei dem Feld um eine innere Klasse handelt.

`FIELD_TYPE_REFERENCE`\
Gibt an, dass es sich bei dem Feld um einen Verweis handelt.

`FIELD_TYPE_EXTENDED`\
Für die zukünftige Verwendung reserviert.

`FIELD_SYM_MEMBER`\
Gibt an, dass das Feld ein Mitglied ist.

`FIELD_SYM_LOCAL`\
Gibt an, dass das Feld lokal ist.

`FIELD_SYM_PARAMETER`\
Gibt an, dass es sich bei dem Feld um einen Parameter handelt.

`FIELD_SYM_THIS`\
Gibt an, dass es sich bei dem Feld um den "this"-Zeiger handelt.

`FIELD_SYM_GLOBAL`\
Gibt an, dass das Feld global ist.

`FIELD_SYM_PROP_GETTER`\
Gibt an, dass das Feld Eigenschaften abruft.

`FIELD_SYM_PROP_SETTER`\
Gibt an, dass das Feld Eigenschaften festlegt.

`FIELD_SYM_EXTENDED`\
Für die zukünftige Verwendung reserviert.

`FIELD_KIND_MASK`\
Gibt eine Maske für Feldtypen an.

`FIELD_TYPE_MASK`\
Gibt eine Maske für Feldtypen an.

`FIELD_SYM_MASK`\
Gibt eine Maske für Symbolinformationen an.

## <a name="remarks"></a>Bemerkungen
Wird von einem Aufruf der [GetKind-Methode](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgegeben.

Je nach Art des Feldes kann [QueryInterface](/cpp/atl/queryinterface) auf der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) für eine spezifischere Form der Schnittstelle aufgerufen werden. Wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) beispielsweise `FIELD_TYPE_METHOD`zurückkehrt, können `QueryInterface` Sie`DebugField` i aufrufen, um die [IDebugMethodField-Schnittstelle](../../../extensibility/debugger/reference/idebugmethodfield.md) zu erhalten.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
