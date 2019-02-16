---
title: BP_ERROR_RESOLUTION_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03742dc00f0d42066eb80adfef6946904cae1d77
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317106"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Beschreibt die Auflösung von einem Fehler Haltepunkt, einschließlich der Standort, Anwendung und Thread an.

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
`dwFields`  
Eine Kombination von Werten aus der [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) Enumeration, die angibt, welche Felder dieser Struktur ausgefüllt werden.

`bpResLocation`  
Die [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Union, der die Position des Haltepunkts Auflösung angibt.

`pProgram`  
Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das die Anwendung darstellt, in dem der haltepunktfehler aufgetreten ist.

`pThread`  
Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, auf dem die Anwendung, die den Breakpoint-Fehler generiert hat, ausgeführt wird.

`bstrMessage`  
Eine Zeichenfolge, die Warnung oder Fehlermeldung an, die durch diese Fehlerbehebung enthält.

`dwType`  
Ein Wert aus der [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) Enumeration, die den Breakpoint-Fehlertyp angibt.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zurückgegeben, die [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)  
[BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)  
[BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
