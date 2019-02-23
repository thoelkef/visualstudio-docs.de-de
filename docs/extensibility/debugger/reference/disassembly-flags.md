---
title: DISASSEMBLY_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c4602fa1b8d30e9119bb39e925cf7768ae1cbcf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682426"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Gibt die Flags für die Disassemblierung.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="members"></a>Member
DF_DOCUMENTCHANGE gibt an, die diese Anweisung in einem anderen Dokument als die vorherige Version.

DF_DISABLED gibt an, dass diese Anweisung nicht ausgeführt wird.

DF_INSTRUCTION_ACTIVE angibt, der diese Anweisung den nächsten Anweisungen ausgeführt werden (möglicherweise mehr als eine).

DF_DATA gibt an, dass diese Anweisung wirklich Daten (nicht Code).

DF_HASSOURCE gibt an, die diese Anweisung Quelle hat. Einige Anweisungen, z. B. profilerstellung oder Garbage Collection-Code, verfügen über keine entsprechende Quelle.

DF_DOCUMENT_CHECKSUM gibt an, dass `bstrDocumentUrl` Feld Prüfsummendaten enthält, nach der Dokument-URL. Finden Sie im Abschnitt "Hinweise" der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur wie die Prüfsummendaten gespeichert werden.

## <a name="remarks"></a>Hinweise
Verwendet als die `dwFlags` Mitglied der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur.

Diese Flags können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
