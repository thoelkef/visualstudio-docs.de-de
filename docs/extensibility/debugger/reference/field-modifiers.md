---
title: FIELD_MODIFIERS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b22559af26a0a5f6c8af68726a5ba336e1bcfb4a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689628"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Gibt die Modifizierer für ein Feld an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="members"></a>Member
FIELD_MOD_ACCESS_TYPE gibt an, dass das Feld nicht zugegriffen werden kann.

FIELD_MOD_ACCESS_PUBLIC gibt an, dass das Feld über öffentlichen Zugriff hat.

FIELD_MOD_ACCESS_PROTECTED gibt an, dass das Feld Zugriff geschützt ist.

FIELD_MOD_ACCESS_PRIVATE gibt an, dass das Feld privaten Zugriff hat.

FIELD_MOD_NOMODIFIERS gibt an, dass das Feld keine Modifizierer verfügt.

FIELD_MOD_STATIC gibt an, dass das Feld statisch ist.

FIELD_MOD_CONSTANT gibt an, dass das Feld eine Konstante ist.

FIELD_MOD_TRANSIENT gibt an, dass das Feld vorübergehend ist.

FIELD_MOD_VOLATILE gibt an, dass das Feld "volatile" ist.

FIELD_MOD_ABSTRACT gibt an, dass das Feld abstrakt ist.

FIELD_MOD_NATIVE gibt an, dass das Feld native.

FIELD_MOD_SYNCHRONIZED gibt an, dass das Feld synchronisiert wird.

FIELD_MOD_VIRTUAL gibt an, dass das Feld virtuell ist.

FIELD_MOD_INTERFACE gibt an, dass das Feld eine Schnittstelle.

FIELD_MOD_FINAL gibt an, dass das Feld Ihrem endgültigen Zustand vorliegt.

FIELD_MOD_SENTINEL gibt an, dass das Feld Sentinel.

FIELD_MOD_INNERCLASS gibt an, dass das Feld einer inneren Klasse.

FIELD_TYPE_OPTIONAL gibt an, dass das Feld optional ist.

FIELD_MOD_BYREF gibt an, dass das Feld mit einem Verweisargument ist. Dies ist insbesondere für Methodenargumente.

FIELD_MOD_HIDDEN gibt an, dass das Feld in einem anderen Kontext angezeigt oder ausgeblendet werden muss. z. B. [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statischen lokalen Variablen.

FIELD_MOD_MARSHALASOBJECT gibt an, dass das Feld repräsentiert den ein Objekt mit einer `IUnknown` Schnittstelle.

FIELD_MOD_SPECIAL_NAME gibt an, dass das Feld einen speziellen Namen, z. B. `.ctor` für einen Konstruktor ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] nur).

FIELD_MOD_HIDEBYSIG gibt an, die das Feld enthält den `Overloads` Schlüsselwort angewendet wird ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] nur).

FIELD_MOD_WRITEONLY gibt an, dass das Feld schreibgeschützt ist. Dieser Wert befindet sich nicht im `FIELD_MOD_ALL`, da nur mit diesen Feldern nur Schreibzugriff für die funktionsauswertung ist. Ein Benutzer muss explizit anfordern `FIELD_MOD_WRITEONLY` Felder.

Eine Maske für den Feldzugriff gibt FIELD_MOD_ACCESS_MASK an.

FIELD_MOD_MASK gibt eine Maske für feldmodifizierern an.

## <a name="remarks"></a>Hinweise
Verwendet für die `dwModifiers` Mitglied der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.

Diese Werte werden auch zum Übergeben der [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) Methode zum Filtern nach bestimmten Feldern.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
