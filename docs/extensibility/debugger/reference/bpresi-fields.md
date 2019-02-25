---
title: BPRESI_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fac4c65047c51d1213d8be4352c1b8e6efc35c8e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680567"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Gibt die Informationen über die erfolgreiche Auflösung eines Haltepunkts abgerufen werden sollen.

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

## <a name="members"></a>Member
BPRESI_BPRESLOCATION initialisieren und Verwenden der `bpResLocation` (Position des Haltepunkts Auflösung) Feld der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur.

BPRESI_PROGRAM initialisieren und Verwenden der `pProgram` Feld der `BP_RESOLUTION_INFO` Struktur.

BPRESI_THREAD initialisieren und Verwenden der `pThread` Feld der `BP_RESOLUTION_INFO` Struktur.

BPRESI_ALLFIELDS gibt alle Felder an.

## <a name="remarks"></a>Hinweise
Übergeben der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) Methode an, welche Felder der der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) sind, dass die Struktur initialisiert werden.

Diese Flags werden auch verwendet, welche Felder der an die `BP_RESOLUTION_INFO` -Struktur sind gültig und verwendet, wenn dieser Struktur zurückgegeben wird.

Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
