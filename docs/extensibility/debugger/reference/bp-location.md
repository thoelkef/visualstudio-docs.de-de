---
title: BP_LOCATION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85f8c915f5c0d6d81214220f78c7db0544777cda
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663322"
---
# <a name="bplocation"></a>BP_LOCATION
Gibt den Typ der Struktur verwendet, um den Speicherort des Haltepunkts zu beschreiben.

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
`bpLocationType` Ein Wert aus der [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) Enumeration, die zum Interpretieren von der `bpLocation` Union oder `unionmemberX` Member.

`bpLocation`.`bplocCodeFileLine`

 [C++ nur] Enthält die [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_FILE_LINE`.

`bpLocation.bplocCodeFuncOffset`

 [C++ nur] Enthält die [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`.

`bpLocation.bplocCodeContext`

 [C++ nur] Enthält die [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_CONTEXT`.

`bpLocation.bplocCodeString`

 [C++ nur] Enthält die [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_STRING`.

`bpLocation.bplocCodeAddress`

 [C++ nur] Enthält die [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_ADDRESS`.

`bpLocation.bplocDataString`

 [C++ nur] Enthält die [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Struktur, wenn `bpLocationType`  =  `BPLT_DATA_STRING`.

`bpLocation.bplocResolution`

 [C++ nur] Enthält die [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Struktur, wenn `bpLocationType`  =  `BPLT_RESOLUTION`.

`unionmember1`

 [C# nur] Siehe Hinweise zum interpretieren.

`unionmember2`

 [C# nur] Siehe Hinweise zum interpretieren.

`unionmember3`

 [C# nur] Siehe Hinweise zum interpretieren.

`unionmember4`

 [C# nur] Siehe Hinweise zum interpretieren.

## <a name="remarks"></a>Hinweise
Diese Struktur ist ein Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.

 [C# nur] Die `unionmemberX` Elemente werden gemäß der folgenden Tabelle interpretiert. Suchen Sie in der linken Spalte für die `bpLocationType` Wert ein, und suchen Sie in den anderen Spalten, um zu bestimmen, was von den einzelnen `unionmemberX` Member darstellt und Marshal-Argument der `unionmemberX` entsprechend. Siehe das Beispiel für eine Methode zur Interpretation von eines Teils dieser Struktur in C# geschrieben.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (ein Kontext)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (ein Kontext)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (ein Kontext)|`string` (bedingter Ausdruck)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (ein Kontext)|`string` (Modul-URL)|`string` (Funktionsnamen)|`string` (Adresse)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (ein Kontext)|`string` (Data-Ausdruck)|`uint` (Anzahl der Elemente)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie zum Interpretieren der `BP_LOCATION` Struktur in c# für die `BPLT_DATA_STRING` Typ. Dieses bestimmten Typs zeigt, wie alle vier interpretieren `unionmemberX` Elemente in allen möglichen Formaten (Object, String und Anzahl).

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

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
