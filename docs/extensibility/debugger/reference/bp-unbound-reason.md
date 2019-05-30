---
title: BP_UNBOUND_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9de6812f3a61feca8ca8e7153fb281369c3312bd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350557"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Gibt den Grund an, die, den ein Haltepunkt aufgehoben wurde.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Felder
`BPUR_UNKNOWN`\
Der Grund dafür ist unbekannt.

`BPUR_CODE_UNLOADED`\
Der Code mit dem Haltepunkt wurde entladen.

`BPUR_BREAKPOINT_REBIND`\
Der Haltepunkt wurde an einen anderen Speicherort erneut gebunden wurde. Dies kann auftreten, die nach dem Bearbeiten und Vorgänge fortgesetzt, wenn der Haltepunkt verschoben wird oder wenn der Breakpoint in einer Datei mit einem Pfad gebunden ist, die nicht mehr gültig ist.

`BPUR_ BREAKPOINT_ERROR`\
Der Haltepunkt wird bestimmt, um die Fehler werden, nachdem er gebunden ist. Dies geschieht mit verwalteten Haltepunkte, deren Bedingungen nicht mehr gültig sind.

## <a name="remarks"></a>Hinweise
Zurückgegeben von der [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
