---
title: BP_UNBOUND_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737770"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Gibt den Grund für die Bindung eines Breakpoints an.

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
Der Grund ist unbekannt.

`BPUR_CODE_UNLOADED`\
Der Code, der den Breakpoint enthält, wurde entladen.

`BPUR_BREAKPOINT_REBIND`\
Der Breakpoint wurde an einen anderen Speicherort wieder gebunden. Dies kann nach dem Bearbeiten und Fortfahren erfolgen, wenn der Breakpoint verschoben wird, oder wenn der Breakpoint an eine Datei mit einem Pfad gebunden ist, der nicht mehr gültig ist.

`BPUR_ BREAKPOINT_ERROR`\
Der Haltepunkt wird als fehlerhaft festgelegt, nachdem er gebunden wurde. Dies geschieht bei verwalteten Haltepunkten, deren Bedingungen nicht mehr gültig sind.

## <a name="remarks"></a>Bemerkungen
Wird von der [geverrat](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
