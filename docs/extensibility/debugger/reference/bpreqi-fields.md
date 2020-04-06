---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737748"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Gibt die Informationen an, die zu einer Haltepunktanforderung abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Felder
`BPREQI_BPLOCATION`\
Initialisieren/verwenden `bpLocation` Sie das Feld (Haltepunktposition) der [BP_REQUEST_INFO-](../../../extensibility/debugger/reference/bp-request-info.md) oder [BP_REQUEST_INFO2-Struktur.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Initialisieren/Verwenden `guidLanguage` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_PROGRAM`\
Initialisieren/Verwenden `pProgram` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_PROGRAMNAME`\
Initialisieren/Verwenden `bstrProgramName` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_THREAD`\
Initialisieren/Verwenden `pThread` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_THREADNAME`\
Initialisieren/Verwenden `bstrThreadName` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_PASSCOUNT`\
Initialisieren/Verwenden `bpPassCount` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_CONDITION`\
Initialisieren/Verwenden `bpCondition` des Feldes (Breakpoint-Bedingung) der `BP_REQUEST_INFO` oder-Struktur. `BP_REQUEST_INFO2`

`BPREQI_FLAGS`\
Initialisieren/Verwenden `dwFlags` Sie das `BP_REQUEST_INFO` `BP_REQUEST_INFO2` Feld der oder-Struktur.

`BPREQI_ALLOLDFIELDS`\
Initialisieren/Verwenden Sie alle Felder `BP_REQUEST_INFO` für die Struktur.

`BPREQI_VENDOR`\
Initialisieren/Verwenden `guidVendor` des `BP_REQUEST_INFO2` Strukturfelds.

`BPREQI_CONSTRAINT`\
Initialisieren/Verwenden `bstrConstraint` des `BP_REQUEST_INFO2` Strukturfelds.

`BPREQI_TRACEPOINT`\
Initialisieren/Verwenden `bstrTracepoint` des `BP_REQUEST_INFO2` Strukturfelds.

`BPREQI_ALLFIELDS`\
Gibt alle Felder `BP_REQUEST_INFO2` für die Struktur an.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument an die [GetRequestInfo-](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) und [BP_REQUEST_INFO-Methoden,](../../../extensibility/debugger/reference/bp-request-info.md) um anzugeben, welche Felder der [BP_REQUEST_INFO-](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2-Strukturen](../../../extensibility/debugger/reference/bp-request-info2.md) initialisiert werden sollen.

Diese Flags werden auch verwendet, `BP_REQUEST_INFO` um `BP_REQUEST_INFO2` anzugeben, welche Felder der und Strukturen verwendet werden und gültig sind, wenn jede Struktur zurückgegeben wird.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
