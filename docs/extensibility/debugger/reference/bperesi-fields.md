---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737768"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Gibt die Informationen an, die über eine fehlgeschlagene Auflösung eines Haltepunkts abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Felder
`PERESI_BPRESLOCATION`\
Initialisieren/Verwenden `bpResLocation` des Feldes (Breakpoint-Auflösungsposition) der [BP_ERROR_RESOLUTION_INFO-Struktur.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Initialisieren/verwenden `pProgram` Sie das `BP_ERROR_RESOLUTION_INFO` Feld der Struktur.

`BPERESI_THREAD`\
Initialisieren/verwenden `pThread` Sie das `BP_ERROR_RESOLUTION_INFO` Feld der Struktur.

`BPERESI_MESSAGE`\
Initialisieren/verwenden `bstrMessage` Sie das `BP_ERROR_RESOLUTION_INFO` Feld der Struktur.

`BPERESI_TYPE`\
Initialisieren/verwenden `dwType` Sie das Feld (Breakpoint-Typ) der `BP_ERROR_RESOLUTION_INFO` Struktur.

`BPERESI_ALLFIELDS`\
Initialisieren/Verwenden aller Felder `BP_ERROR_RESOLUTION_INFO` der Struktur.

## <a name="remarks"></a>Bemerkungen
Wird als Parameter an die [GetResolutionInfo-Methode](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) übergeben, um anzugeben, welche Felder der [BP_ERROR_RESOLUTION_INFO-Struktur](../../../extensibility/debugger/reference/bp-error-resolution-info.md) initialisiert werden sollen.

Diese Werte werden auch verwendet, `BP_ERROR_RESOLUTION_INFO` um anzugeben, welche Felder in der Struktur verwendet werden und gültig sind, wenn diese Struktur zurückgegeben wird.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
