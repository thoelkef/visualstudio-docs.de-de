---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737918"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Gibt die Bedingung an, die der Anzahl der Haltepunktdurchlauferzahl zugeordnet ist, wodurch der Haltepunkt ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Felder
`BP_PASSCOUNT_NONE`\
Gibt keinen Haltepunktpass-Zählstil an.

`BP_PASSCOUNT_EQUAL`\
Legt den Stil für die Anzahl der Haltepunktedurchbrüche auf gleich fest. Der Haltepunkt wird ausgelöst, wenn die Anzahl der Treffer des Haltepunkts der Anzahl der Durchlaufe entspricht.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Legt den Stil für die Anzahl der Haltepunktedurchlauferjahre auf gleich oder größer fest. Der Haltepunkt wird ausgelöst, wenn die Anzahl der Treffer des Haltepunkts gleich oder größer als die Anzahl der Durchlaufzeiten ist.

`BP_PASSCOUNT_MOD`\
Gibt eine Modulo-Passanzahl an. Wenn z. B. die Anzahl `BP_PASSCOUNT_MOD` der Durchlaufzeiten vom Typ ist und der Wert für die Anzahl der Durchlaufzeiten 4 ist, wird der Haltepunkt jedes Mal ausgelöst, wenn die Trefferanzahl ein Vielfaches von 4 ist.

## <a name="remarks"></a>Bemerkungen
Wird für `stylePassCount` das Element der BP_PASSCOUNT Struktur [verwendet,](../../../extensibility/debugger/reference/bp-passcount.md) die wiederum ein Mitglied der [BP_REQUEST_INFO-](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2-Strukturen](../../../extensibility/debugger/reference/bp-request-info2.md) ist.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
