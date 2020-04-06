---
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736859"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Gibt Modifikatoren für einen Feldtyp an.

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

## <a name="fields"></a>Felder
`FIELD_MOD_ACCESS_TYPE`\
Gibt an, dass auf das Feld nicht zugegriffen werden kann.

`FIELD_MOD_ACCESS_PUBLIC`\
Gibt an, dass das Feld öffentlichen Zugriff hat.

`FIELD_MOD_ACCESS_PROTECTED`\
Gibt an, dass das Feld über geschützten Zugriff verfügt.

`FIELD_MOD_ACCESS_PRIVATE`\
Gibt an, dass das Feld über privaten Zugriff verfügt.

`FIELD_MOD_NOMODIFIERS`\
Gibt an, dass das Feld keine Modifikatoren enthält.

`FIELD_MOD_STATIC`\
Gibt an, dass das Feld statisch ist.

`FIELD_MOD_CONSTANT`\
Gibt an, dass es sich bei dem Feld um eine Konstante handelt.

`FIELD_MOD_TRANSIENT`\
Gibt an, dass das Feld vorübergehend ist.

`FIELD_MOD_VOLATILE`\
Gibt an, dass das Feld flüchtig ist.

`FIELD_MOD_ABSTRACT`\
Gibt an, dass das Feld abstrakt ist.

`FIELD_MOD_NATIVE`\
Gibt an, dass das Feld nativ ist.

`FIELD_MOD_SYNCHRONIZED`\
Gibt an, dass das Feld synchronisiert ist.

`FIELD_MOD_VIRTUAL`\
Gibt an, dass das Feld virtuell ist.

`FIELD_MOD_INTERFACE`\
Gibt an, dass es sich bei dem Feld um eine Schnittstelle handelt.

`FIELD_MOD_FINAL`\
Gibt an, dass das Feld endgültig ist.

`FIELD_MOD_SENTINEL`\
Gibt an, dass es sich bei dem Feld um einen Sentinel handelt.

`FIELD_MOD_INNERCLASS`\
Gibt an, dass es sich bei dem Feld um eine innere Klasse handelt.

`FIELD_TYPE_OPTIONAL`\
Gibt an, dass das Feld optional ist.

`FIELD_MOD_BYREF`\
Gibt an, dass es sich bei dem Feld um ein Referenzargument handelt. Dies ist speziell für Methodenargumente vorgesehen.

`FIELD_MOD_HIDDEN`\
Gibt an, dass das Feld ausgeblendet oder in einem anderen Kontext angezeigt werden muss. z. [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] B. statische Locals.

`FIELD_MOD_MARSHALASOBJECT`\
Gibt an, dass das `IUnknown` Feld ein Objekt mit einer Schnittstelle darstellt.

`FIELD_MOD_SPECIAL_NAME`\
Gibt an, dass das Feld einen `.ctor` speziellen Namen[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] hat, z. B. für einen Konstruktor (nur).

`FIELD_MOD_HIDEBYSIG`\
Gibt an, dass `Overloads` auf das[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] Feld das Schlüsselwort angewendet wurde (nur).

`FIELD_MOD_WRITEONLY`\
Gibt an, dass das Feld schreibgeschützt ist. Dieser Wert ist `FIELD_MOD_ALL`nicht in enthalten, da die einzige Verwendung solcher Schreibfelder für die Funktionsauswertung gilt. Ein Benutzer muss `FIELD_MOD_WRITEONLY` explizit nach Feldern fragen.

`FIELD_MOD_ACCESS_MASK`\
Gibt eine Maske für den Feldzugriff an.

`FIELD_MOD_MASK`\
Gibt eine Maske für Feldmodifikatoren an.

## <a name="remarks"></a>Bemerkungen
Wird für `dwModifiers` das Element der [FIELD_INFO-Struktur](../../../extensibility/debugger/reference/field-info.md) verwendet.

Diese Werte werden auch an die [EnumFields-Methode](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) übergeben, um nach bestimmten Feldern zu filtern.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
