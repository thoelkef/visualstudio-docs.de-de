---
title: BP_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738060"
---
# <a name="bp_flags"></a>BP_FLAGS
Stellt optionale Flags bereit, die beim Festlegen eines halte Punkts zum Angeben zusätzlicher Informationen verwendet werden können.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Felder
`BP_FLAG_NONE`\
Gibt kein breakpointflag an.

`BP_FLAG_MAP_DOCPOSITION`\
Gibt an, dass die Debug-Engine (de) den Breakpoint mithilfe der Dokument Position zuordnen soll. Dies gilt nur für Breakpoints, die in Skript orientierten Quelldateien, z. b. Active Server Seiten (ASP), festgelegt sind.

`BP_FLAG_DONT_STOP`\
Gibt an, dass der Breakpoint von der Debug-Engine verarbeitet werden soll, dass die Debug-Engine jedoch letztendlich nicht angehalten werden soll (d. h., ein [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Ereignis Objekt sollte nicht gesendet werden). Dieses Flag ist so konzipiert, dass es hauptsächlich mit Ablauf Verfolgungs Punkten verwendet wird.

## <a name="remarks"></a>Bemerkungen
Wird für den `dwFlags` Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) -Strukturen verwendet.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
