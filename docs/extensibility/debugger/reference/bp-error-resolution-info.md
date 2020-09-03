---
title: BP_ERROR_RESOLUTION_INFO | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738086"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Beschreibt die Auflösung eines Fehler-Breakpoints, einschließlich Speicherort, Programm und Thread.

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
Eine Kombination von Werten aus der [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) -Enumeration, die angibt, welche Felder dieser Struktur ausgefüllt werden.

`bpResLocation`\
Der [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Union, der den Speicherort für die Haltepunkt Auflösung angibt.

`pProgram`\
Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das die Anwendung darstellt, in der der Breakpoint-Fehler aufgetreten ist.

`pThread`\
Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, auf dem die Anwendung ausgeführt wird, die den Breakpoint-Fehler generiert hat.

`bstrMessage`\
Eine Zeichenfolge, die jede Warn-oder Fehlermeldung enthält, die aus dieser Fehler Auflösung resultiert.

`dwType`\
Ein Wert aus der [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) Enumeration, der den breakpointfehlertyp angibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [getresolutioninfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
