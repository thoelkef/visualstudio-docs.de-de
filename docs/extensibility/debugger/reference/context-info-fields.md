---
title: CONTEXT_INFO_FIELDS | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737590"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Gibt an, welche Informationen über einen Speicher Kontext abgerufen werden sollen.

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
Initialisieren Sie das- `bstrModuleUrl` Feld der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur, und verwenden Sie es.

`CIF_FUNCTION`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrFunction` `CONTEXT_INFO` .

`CIF_FUNCTIONOFFSET`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `posFunctionOffset` `CONTEXT_INFO` .

`CIF_ADDRESS`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrAddress` `CONTEXT_INFO` .

`CIF_ADDRESSOFFSET`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrAddressOffset` `CONTEXT_INFO` .

`CIF_ALLFIELDS`\
Initialisieren/verwenden Sie alle Felder der- `CONTEXT_INFO` Struktur.

## <a name="remarks"></a>Bemerkungen
Diesen Werten wird ein Parameter an die [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) -Methode übergeben, um anzugeben, welche Felder der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur initialisiert werden sollen.

Diese Flags werden auch verwendet, um anzugeben, welche Felder der `CONTEXT_INFO` Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
