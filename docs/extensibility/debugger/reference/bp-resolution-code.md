---
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbfd16025d338b54bec8e2e4276de62c8d00477e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737855"
---
# <a name="bp_resolution_code"></a>BP_RESOLUTION_CODE
Beschreibt den Speicherort eines Code-Breakpoints.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_CODE {
    IDebugCodeContext2* pCodeContext;
} BP_RESOLUTION_CODE;
```

```csharp
public struct BP_RESOLUTION_CODE {
    public IDebugCodeContext2 pCodeContext;
};
```

## <a name="members"></a>Member
`pCodeContext`\
Das [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das die Position des Haltepunkts im Code identifiziert.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Element der BP_RESOLUTION_LOCATION-Struktur, die wiederum ein Member der [BP_RESOLUTION_INFO-Struktur](../../../extensibility/debugger/reference/bp-resolution-info.md) ist, die von der [GetResolutionInfo-Methode](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
