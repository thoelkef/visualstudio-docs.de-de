---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737722"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Gibt die Informationen an, die über die erfolgreiche Auflösung eines Haltepunkts abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Felder
`BPRESI_BPRESLOCATION`\
Initialisieren/verwenden `bpResLocation` Sie das Feld (Breakpoint-Auflösungsposition) der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur.

`BPRESI_PROGRAM`\
Initialisieren/verwenden `pProgram` Sie das `BP_RESOLUTION_INFO` Feld der Struktur.

`BPRESI_THREAD`\
Initialisieren/verwenden `pThread` Sie das `BP_RESOLUTION_INFO` Feld der Struktur.

`BPRESI_ALLFIELDS`\
Gibt alle Felder an.

## <a name="remarks"></a>Bemerkungen
Wird an die [GetResolutionInfo-Methode](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) übergeben, um anzugeben, welche Felder der [BP_RESOLUTION_INFO-Struktur](../../../extensibility/debugger/reference/bp-resolution-info.md) initialisiert werden sollen.

Diese Flags werden auch verwendet, `BP_RESOLUTION_INFO` um anzugeben, welche Felder der Struktur verwendet werden und gültig sind, wenn diese Struktur zurückgegeben wird.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
