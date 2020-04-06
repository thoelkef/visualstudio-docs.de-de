---
title: BP_UNBOUND_REASON | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737770"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Gibt den Grund an, warum ein Haltepunkt ungebunden war.

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
Der Code, der den Haltepunkt enthält, wurde entladen.

`BPUR_BREAKPOINT_REBIND`\
Der Haltepunkt wurde an einen anderen Ort zurückgebracht. Dies kann nach Bearbeitungs- und Fortsetzungsvorgängen geschehen, wenn der Haltepunkt verschoben wird oder wenn der Haltepunkt an eine Datei mit einem Pfad gebunden ist, der nicht mehr gültig ist.

`BPUR_ BREAKPOINT_ERROR`\
Der Haltepunkt wird als fehlerhaft ermittelt, nachdem er gebunden wurde. Dies geschieht bei verwalteten Haltepunkten, deren Bedingungen nicht mehr gültig sind.

## <a name="remarks"></a>Bemerkungen
Wird von der [GetReason-Methode](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
