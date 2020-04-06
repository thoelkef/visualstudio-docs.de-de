---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737814"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Gibt die Struktur der Position der Haltepunktauflösung an.

## <a name="syntax"></a>Syntax

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Member
`bpType`\
Ein Wert aus der BP_TYPE-Enumeration, `bpResLocation` der `unionmemberX` angibt, wie die Union oder die Mitglieder interpretiert werden sollen. [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)

`bpResLocation.bpresCode`\
[Nur C++ Enthält [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) die BP_RESOLUTION_CODE `bpType`  =  `BPT_CODE`Struktur, wenn .

`bpResLocation.bpresData`\
[Nur C++ Enthält [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) die BP_RESOLUTION_DATA `bpType`  =  `BPT_DATA`Struktur, wenn .

`bpResLocation.unused`\
[Nur C++ Ein Platzhalter.

`unionmember1`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember2`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember3`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

`unionmember4`\
[Nur C-Code] Siehe Hinweise zur Interpretation.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Mitglied der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) und [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Strukturen.

 [Nur C-Code] Die `unionmemberX` Elemente werden gemäß der folgenden Tabelle interpretiert. Schauen Sie in der `bpType` linken Spalte nach `unionmemberX` dem Wert, `unionmemberX` um zu bestimmen, was jedes Element darstellt, und marshallen Sie den wertentsprechend. Eine Möglichkeit, diese Struktur in C- zu interpretieren, finden Sie im Beispiel.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(Datenausdruck)|`string`(Funktionsname)|`string`(Bildname)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Beispiel
In diesem Beispiel wird `BP_RESOLUTION_LOCATION` gezeigt, wie die Struktur in C- interpretiert wird.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
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
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
