---
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737931"
---
# <a name="bp_location"></a>BP_LOCATION
Gibt den Strukturtyp an, der zum Beschreiben der Position des Haltepunkts verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Member
`bpLocationType`\
Ein Wert aus der BP_LOCATION_TYPE-Enumeration, `unionmemberX` die zum Interpretieren der [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) `bpLocation` Union oder der Mitglieder verwendet wird.

`bpLocation`.`bplocCodeFileLine`\
[Nur C++ Enthält [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) die BP_LOCATION_CODE_FILE_LINE `bpLocationType`  =  `BPLT_CODE_FILE_LINE`Struktur, wenn .

`bpLocation.bplocCodeFuncOffset`\
[Nur C++ Enthält [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) die BP_LOCATION_CODE_FUNC_OFFSET `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`Struktur, wenn .

`bpLocation.bplocCodeContext`\
[Nur C++ Enthält [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) die BP_LOCATION_CODE_CONTEXT `bpLocationType`  =  `BPLT_CODE_CONTEXT`Struktur, wenn .

`bpLocation.bplocCodeString`\
[Nur C++ Enthält [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) die BP_LOCATION_CODE_STRING `bpLocationType`  =  `BPLT_CODE_STRING`Struktur, wenn .

`bpLocation.bplocCodeAddress`\
[Nur C++ Enthält [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) die BP_LOCATION_CODE_ADDRESS `bpLocationType`  =  `BPLT_CODE_ADDRESS`Struktur, wenn .

`bpLocation.bplocDataString`\
[Nur C++ Enthält [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) die BP_LOCATION_DATA_STRING `bpLocationType`  =  `BPLT_DATA_STRING`Struktur, wenn .

`bpLocation.bplocResolution`\
[Nur C++ Enthält [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) die BP_LOCATION_RESOLUTION `bpLocationType`  =  `BPLT_RESOLUTION`Struktur, wenn .

`unionmember1`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember2`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember3`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember4`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.

 [Nur C-Code] Die `unionmemberX` Elemente werden gemäß der folgenden Tabelle interpretiert. Schauen Sie in der `bpLocationType` linken Spalte nach dem Wert, `unionmemberX` und suchen `unionmemberX` Sie dann über die anderen Spalten, um zu bestimmen, was jedes Element darstellt, und marshallen Sie die entsprechend. Im Beispiel finden Sie eine Möglichkeit, einen Teil dieser Struktur in C' zu interpretieren.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(ein Kontext)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(ein Kontext)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(ein Kontext)|`string`(bedingter Ausdruck)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(ein Kontext)|`string`(Modul-URL)|`string`(Funktionsname)|`string`(Adresse)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(ein Kontext)|`string`(Datenausdruck)|`uint`(Anzahl der Elemente)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Beispiel
In diesem Beispiel wird `BP_LOCATION` gezeigt, wie `BPLT_DATA_STRING` die Struktur für den Typ in C- und C-Code interpretiert wird. Dieser spezielle Typ zeigt, `unionmemberX` wie alle vier Elemente in allen möglichen Formaten (Objekt, Zeichenfolge und Zahl) interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
