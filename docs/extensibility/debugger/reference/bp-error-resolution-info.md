---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738086"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Beschreibt die Auflösung eines Fehlerhaltepunkts, einschließlich Speicherort, Programm und Thread.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) Werten aus der BPERESI_FIELDS-Enumeration, die angibt, welche Felder dieser Struktur ausgefüllt werden.

`bpResLocation`\
Die [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Union, die die Position der Bruchpunktauflösung angibt.

`pProgram`\
Das [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das die Anwendung darstellt, in der der Haltepunktfehler aufgetreten ist.

`pThread`\
Das [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, auf dem die Anwendung ausgeführt wird, die den Haltepunktfehler generiert hat.

`bstrMessage`\
Eine Zeichenfolge, die eine Warnung oder Fehlermeldung enthält, die aus dieser Fehlerbehebung resultiert.

`dwType`\
Ein Wert [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) aus der BP_ERROR_TYPE-Enumeration, der den Breakpoint-Fehlertyp angibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [GetResolutionInfo-Methode](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
