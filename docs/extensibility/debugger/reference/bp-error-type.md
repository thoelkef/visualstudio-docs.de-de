---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738081"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Gibt den Fehlertyp eines Haltepunkts an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Felder
`BPET_NONE`\
Gibt keinen Haltepunktfehler an.

`BPET_TYPE_WARNING`\
Gibt einen Breakpoint-Fehler im Warnstil an.

`BPET_TYPE_ERROR`\
Gibt einen Fehler-Breakpoint-Fehler an.

`BPET_SEV_HIGH`\
Gibt einen Breakpoint-Fehler mit hohem Schweregrad an.

`BPET_SEV_GENERAL`\
Gibt einen Breakpoint-Fehler mit mittlerem Schweregrad an.

`BPET_SEV_LOW`\
Gibt einen Breakpoint-Fehler mit niedrigem Schweregrad an.

`BPET_TYPE_MASK`\
Gibt einen Breakpoint-Fehler im Maskenstil an.

`BPET_SEV_MASK`\
Gibt einen Haltepunktfehler im Stil eines Schweregrads an.

`BPET_GENERAL_WARNING`\
Gibt einen Breakpoint-Fehler im allgemeinen Warnhinweis an.

`BPET_GENERAL_ERROR`\
Gibt einen Breakpoint-Fehler im allgemeinen Fehlerstil an.

`BPET_ALL`\
Gibt alle Breakpoint-Fehlertypen an.

## <a name="remarks"></a>Bemerkungen
Diese Werte können mit einem `OR` Bitwise `dwType` kombiniert und für das Element der [BP_ERROR_RESOLUTION_INFO-Struktur](../../../extensibility/debugger/reference/bp-error-resolution-info.md) verwendet werden. Wird als Parameter an die [EnumErrorBreakpoints-Methode](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) übergeben.

Ein Breakpoint-Fehlertyp besteht aus einem Typ und einem Schweregrad. Dies bedeutet, dass ein Breakpoint-Fehlertyp nie `BPET_TYPE_ERROR`nur ein Typ (z. `BPET_SEV_GENERAL`B. ,) oder ein Schweregrad (z. B. ) für sich selbst ist. `BPET_GENERAL_WARNING`und `BPET_GENERAL_ERROR` stellen vordefinierte Werte für allgemeine Warn- und Fehlerhaltepunkte bereit.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
