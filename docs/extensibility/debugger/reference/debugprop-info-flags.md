---
title: DEBUGPROP_INFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 131e014e3714df708c5ef1526ecb911531c5a5c3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689108"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Gibt an, welche Informationen Sie über ein Debug-Eigenschaft-Objekt abzurufen.

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

## <a name="members"></a>Member
DEBUGPROP_INFO_FULLNAME initialisieren und Verwenden der `bstrFullName` Feld.

DEBUGPROP_INFO_NAME initialisieren und Verwenden der `bstrName` Feld.

DEBUGPROP_INFO_TYPE initialisieren und Verwenden der `bstrType` Feld.

DEBUGPROP_INFO_VALUE initialisieren und Verwenden der `bstrValue` Feld.

DEBUGPROP_INFO_ATTRIB initialisieren und Verwenden der `dwAttrib` Feld.

DEBUGPROP_INFO_PROP initialisieren und Verwenden der `pProperty` Feld mit einem [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.

DEBUGPROP_INFO_VALUE_AUTOEXPAND gibt an, dass das Feld "Wert" den Wert automatisch erweitert, für diesen Objekttyp enthalten soll.

DEBUGPROP_INFO_VALUE_NOFUNCEVAL als veraltet markiert.

DEBUGPROP_INFO_VALUE_RAW werden keine Werte verschönert oder Member zurück (d. h. nicht formatieren die Werte).

DEBUGPROP_INFO_VALUE_NO_TOSTRING führen keine spezielle synthetischen Werte zurückgegeben (z. B. rufen nicht `ToString()` auf ein Objekt, das einen Wert zu erzeugen).

DEBUGPROP_INFO_NONE gibt an, die keine Flags festgelegt sind.

DEBUGPROP_INFO_STANDARD initialisieren und Verwenden der `dwAttrib`, `bstrName`, `bstrType`, und `bstrValue` Felder.

DEBUGPROP_INFO_All gibt eine Maske aller Flags an.

## <a name="remarks"></a>Hinweise
Diese Werte werden übergeben, um die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), und [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) Methoden, um anzugeben, welche Felder initialisiert werden, werden die [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.

Diese Werte werden auch verwendet, für die `dwFields` Mitglied der `DEBUG_PROPERTY_INFO` Struktur, um anzugeben, welche Felder der Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
