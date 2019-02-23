---
title: BP_PASSCOUNT_STYLE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 809c63fe536166efe0779cd4e4dc0149b219390a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686053"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Gibt die Bedingung, die die Anzahl der Haltepunkt-übergeben, die bewirkt, dass der Breakpoint ausgelöst werden zugeordnet.

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

## <a name="members"></a>Member
BP_PASSCOUNT_NONE gibt kein Haltepunkt Pass-Count-Stil an.

BP_PASSCOUNT_EQUAL wird der Haltepunkt Pass Anzahl fest. Der Haltepunkt wird ausgelöst, wenn die Anzahl der Häufigkeit, mit die der Haltepunkt erreicht wird die Anzahl der Durchläufe entspricht.

BP_PASSCOUNT_EQUAL_OR_GREATER legt den Haltepunkt Pass-Count-Stil auf gleich oder größer fest. Der Haltepunkt wird ausgelöst, wenn die Anzahl der Häufigkeit, mit die der Haltepunkt erreicht wird, gleich oder größer als die Anzahl der übergeben wird.

BP_PASSCOUNT_MOD gibt einen modulo-Anzahl zu übergeben. Wenn die Anzahl der Durchläufe des Typs ist z. B. `BP_PASSCOUNT_MOD` und der Pass-Count-Wert ist 4, der Haltepunkt ausgelöst wird, jedes Mal, wenn die Trefferanzahl ein Vielfaches von 4 ist.

## <a name="remarks"></a>Hinweise
Verwendet für die `stylePassCount` Mitglied der [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die wiederum Mitglied ist die [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
