---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737396"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Gibt an, welche Informationen zu einem Debugeigenschaftenobjekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Felder
`DEBUGPROP_INFO_FULLNAME`\
Initialisieren/verwenden `bstrFullName` Sie das Feld.

`DEBUGPROP_INFO_NAME`\
Initialisieren/verwenden `bstrName` Sie das Feld.

`DEBUGPROP_INFO_TYPE`\
Initialisieren/verwenden `bstrType` Sie das Feld.

`DEBUGPROP_INFO_VALUE`\
Initialisieren/verwenden `bstrValue` Sie das Feld.

`DEBUGPROP_INFO_ATTRIB`\
Initialisieren/verwenden `dwAttrib` Sie das Feld.

`DEBUGPROP_INFO_PROP`\
Initialisieren/verwenden `pProperty` Sie das Feld, das eine [IDebugProperty2-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty2.md) enthält.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Gibt an, dass das Wertfeld den automatisch erweiterten Wert (sofern verfügbar) für diesen Objekttyp enthalten soll.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Veraltet.

`DEBUGPROP_INFO_VALUE_RAW`\
Geben Sie keine verschönerten Werte oder Member zurück (d. h., formatieren Sie die Werte nicht).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Geben Sie keine speziellen synthetisierten Werte zurück `ToString()` (z. B. rufen Sie kein Objekt auf, um einen Wert zu erzeugen).

`DEBUGPROP_INFO_NONE`\
Gibt an, dass keine Flags festgelegt wurden.

`DEBUGPROP_INFO_STANDARD`\
Initialisieren/verwenden `dwAttrib`Sie `bstrName` `bstrType`die `bstrValue` Felder , , und.

`DEBUGPROP_INFO_All`\
Gibt eine Maske aller Flags an.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden an die Methoden [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)und [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) übergeben, um anzugeben, welche Felder in der [DEBUG_PROPERTY_INFO-Struktur](../../../extensibility/debugger/reference/debug-property-info.md) initialisiert werden sollen.

Diese Werte werden auch `dwFields` für `DEBUG_PROPERTY_INFO` das Element der Struktur verwendet, um anzugeben, welche Felder der Struktur verwendet werden und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
