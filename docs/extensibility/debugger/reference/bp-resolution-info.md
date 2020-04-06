---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70e66a936ec1eaf1f818ad249aa4eb14b0b63749
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737823"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Beschreibt die gebundenen Haltepunktinformationen für einen Code-Breakpoint oder einen Datenhaltepunkt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Auflistung von [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) Flags aus der BPRESI_FIELDS-Enumerationen an, die angibt, welche Felder ausgefüllt werden.

`bpResLocation`\
Die [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Struktur, die die Position des Haltepunkts in Code oder Daten angibt.

`pProgram`\
Das [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das die Anwendung darstellt, in der der Haltepunktfehler aufgetreten ist.

`pThread`\
Das [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, in dem die Anwendung ausgeführt wird, die den Haltepunktfehler enthält.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
