---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738048"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Zählt gültige Werte für optionale Flags auf. Die optionalen Flags können verwendet werden, um zusätzliche Informationen anzugeben, wenn Sie einen Haltepunkt festlegen. Diese Enumeration erweitert [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) die BP_FLAGS-Enumeration.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Felder
`BP90_FLAG_NONE`\
Gibt kein Haltepunktflag an.

`BP90_FLAG_MAP_DOCPOSITION`\
Gibt an, dass das Debugmodul (DE) den Haltepunkt mithilfe der Dokumentposition zuordnen soll. Dies gilt nur für Haltepunkte, die in skriptorientierten Quelldateien wie Active Server Pages (ASP) festgelegt sind.

`BP90_FLAG_DONT_STOP`\
Gibt an, dass der Haltepunkt vom Debugmodul verarbeitet werden soll, dass das Debugmodul jedoch nicht dort anhalten sollte. Das heißt, ein [IDebugBreakpointEvent2-Ereignisobjekt](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) sollte nicht gesendet werden. Dieses Flag ist so konzipiert, dass es hauptsächlich mit Ablaufverfolgungspunkten verwendet werden kann.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Wird vom systemeigenen Debugmodul verwendet, um zu bestimmen, ob der Schrittstatus gelöscht werden soll. Sie unterscheidet sich von BP90_FLAG_DONT_STOP, da BP90_FLAG_DONT_STOP nicht festgelegt ist, wenn der Ablaufverfolgungspunkt ein Makro ausführt.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
