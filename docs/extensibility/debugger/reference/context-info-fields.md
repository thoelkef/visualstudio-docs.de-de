---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737590"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Gibt an, welche Informationen zu einem Speicherkontext abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Felder
`CIF_MODULEURL`\
Initialisieren/verwenden `bstrModuleUrl` Sie das Feld der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur.

`CIF_FUNCTION`\
Initialisieren/verwenden `bstrFunction` Sie das `CONTEXT_INFO` Feld der Struktur.

`CIF_FUNCTIONOFFSET`\
Initialisieren/verwenden `posFunctionOffset` Sie das `CONTEXT_INFO` Feld der Struktur.

`CIF_ADDRESS`\
Initialisieren/verwenden `bstrAddress` Sie das `CONTEXT_INFO` Feld der Struktur.

`CIF_ADDRESSOFFSET`\
Initialisieren/verwenden `bstrAddressOffset` Sie das `CONTEXT_INFO` Feld der Struktur.

`CIF_ALLFIELDS`\
Initialisieren/Verwenden aller Felder `CONTEXT_INFO` der Struktur.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) übergeben, um anzugeben, welche Felder der [CONTEXT_INFO-Struktur](../../../extensibility/debugger/reference/context-info.md) initialisiert werden sollen.

Diese Flags werden auch verwendet, `CONTEXT_INFO` um anzugeben, welche Felder der Struktur verwendet werden und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen ODER kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
