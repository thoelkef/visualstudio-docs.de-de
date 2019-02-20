---
title: BPRESI_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 0784d26f4d5ae6bd8edd9b6565644a6cd513db78
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413058"
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
BPRESI_BPRESLOCATION  
Initialisieren und Verwenden der `bpResLocation` (Position des Haltepunkts Auflösung) Feld der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur.

BPRESI_PROGRAM  
Initialisieren und Verwenden der `pProgram` Feld der `BP_RESOLUTION_INFO` Struktur.

BPRESI_THREAD  
Initialisieren und Verwenden der `pThread` Feld der `BP_RESOLUTION_INFO` Struktur.

BPRESI_ALLFIELDS  
Gibt alle Felder an.

## <a name="remarks"></a>Hinweise
Übergeben der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) Methode an, welche Felder der der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) sind, dass die Struktur initialisiert werden.

Diese Flags werden auch verwendet, welche Felder der an die `BP_RESOLUTION_INFO` -Struktur sind gültig und verwendet, wenn dieser Struktur zurückgegeben wird.

Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
