---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737881"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Enthält die Informationen, die zum Implementieren eines Haltepunkts erforderlich sind, einschließlich Kreditoren-GUID, Einschränkung und Tracepoint.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Flags aus der BPREQI_FIELDS-Enumeration, die angibt, welche Felder ausgefüllt werden.

`guidLanguage`\
Die Sprach-GUID.

`bpLocation`\
Die [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur an, die den Typ der Haltepunktposition angibt.

`pProgram`\
Das [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das die Anwendung darstellt, in der der Haltepunkt auftritt.

`bstrProgramName`\
Der Name der Anwendung, in der der Haltepunkt auftritt.

`pThread`\
Das [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, in dem der Haltepunkt auftritt.

`bstrThreadName`\
Der Name des Threads, in dem der Haltepunkt auftritt.

`bpCondition`\
Die [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur, die die Bedingungen beschreibt, unter denen der Haltepunkt ausgelöst wird.

`bpPassCount`\
Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die die Pass-Count-Informationen des Haltepunkts enthält.

`dwFlags`\
Eine Kombination von [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Flags aus der BP_FLAGS-Enumeration, die die Flags für den angeforderten Haltepunkt angibt.

`guidVendor`\
GUID des Anbieters. Kann ein Nullwert sein.

`bstrConstraint`\
Name der Haltepunkteinschränkung. Kann ein Nullwert sein.

`bstrTracepoint`\
Name des Ablaufverfolgungspunkts. Kann ein Nullwert sein.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [GetRequestInfo2-Methode](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
