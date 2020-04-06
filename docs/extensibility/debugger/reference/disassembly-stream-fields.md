---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737366"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Gibt an, welche Informationen zu einem Demontagefeld abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Felder
`DSF_ADDRESS`\
Initialisieren/verwenden `bstrAddress` Sie das Feld.

`DSF_ADDRESSOFFSET`\
Initialisieren/verwenden `bstrAddressOffset` Sie das Feld.

`DSF_CODEBYTES`\
Initialisieren/verwenden `bstrCodeBytes` Sie das Feld.

`DSF_OPCODE`\
Initialisieren/verwenden `bstrOpCode` Sie das Feld.

`DSF_OPERANDS`\
Initialisieren/verwenden `bstrOperands` Sie das Feld.

`DSF_SYMBOL`\
Initialisieren/verwenden `bstrSymbol` Sie das Feld.

`DSF_CODELOCATIONID`\
Initialisieren/verwenden `uCodeLocationId` Sie das Feld.

`DSF_POSITION`\
Initialisieren/verwenden `posBeg` Sie `posEnd` die Felder und.

`DSF_DOCUMENTURL`\
Initialisieren/verwenden `bstrDocumentUrl` Sie das Feld.

`DSF_BYTEOFFSET`\
Initialisieren/verwenden `dwByteOffset` Sie das Feld.

`DSF_FLAGS`\
Initialisieren/verwenden `dwFlags` Sie das Feld ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Fügen Sie Symbolnamen in das Feld ein. `bstrOperands`

`DSF_ALL`\
Gibt alle Felder für den Demontagestream an.

## <a name="remarks"></a>Bemerkungen
Wird als Parameter an die [Read-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) übergeben, um anzugeben, welche Felder der [DisassemblyData-Struktur](../../../extensibility/debugger/reference/disassemblydata.md) initialisiert werden sollen.

Wird für `dwFields` das `DisassemblyData` Element der Struktur verwendet, um anzugeben, welche Felder verwendet werden und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
