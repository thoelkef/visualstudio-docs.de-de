---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737734"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Zählt die gültigen Werte auf, die die Informationen angeben, die zu einer Haltepunktanforderung abgerufen werden sollen. Diese Enumeration erweitert [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) die BPREQI_FIELDS-Enumeration.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Felder
`BPREQI90_BPLOCATION`\
Initialisieren oder `bpLocation` verwenden Sie das Feld (Haltepunktposition) der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) oder [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.

`BPREQI90_LANGUAGE`\
Initialisieren oder `guidLanguage` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_PROGRAM`\
Initialisieren oder `pProgram` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_PROGRAMNAME`\
Initialisieren oder `bstrProgramName` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_THREAD`\
Initialisieren oder `pThread` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_THREADNAME`\
Initialisieren oder `bstrThreadName` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_PASSCOUNT`\
Initialisieren oder `bpPassCount` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_CONDITION`\
Initialisieren oder `bpCondition` verwenden Sie das Feld `BP_REQUEST_INFO` (Breakpoint-Bedingung) der oder-Struktur. `BP_REQUEST_INFO2`

`BPREQI90_FLAGS`\
Initialisieren oder `dwFlags` verwenden Sie `BP_REQUEST_INFO` `BP_REQUEST_INFO2` das Feld der oder-Struktur.

`BPREQI90_ALLOLDFIELDS`\
Initialisieren oder verwenden Sie alle `BP_REQUEST_INFO` Felder für die Struktur.

`BPREQI90_VENDOR`\
Initialisieren oder `guidVendor` verwenden `BP_REQUEST_INFO2` Sie das Strukturfeld.

`BPREQI90_CONSTRAINT`\
Initialisieren oder `bstrConstraint` verwenden `BP_REQUEST_INFO2` Sie das Strukturfeld.

`BPREQI90_TRACEPOINT`\
Initialisieren oder `bstrTracepoint` verwenden `BP_REQUEST_INFO2` Sie das Strukturfeld.

`BPREQI90_MACROTRACEPOINT`\
Initialisieren oder `bstrMacroTracepoint` verwenden `BP_REQUEST_INFO2` Sie das Strukturfeld. BPREQI_ALLFIELDS enthält dieses Feld nicht.

`BPREQI90_ALLFIELDS`\
Gibt alle Felder `BP_REQUEST_INFO2` für die Struktur an.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
