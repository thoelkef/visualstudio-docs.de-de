---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737374"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Gibt die Flags für die Demontage an.

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

## <a name="fields"></a>Felder
`DF_DOCUMENTCHANGE`\
Gibt an, dass sich diese Anweisung in einem anderen Dokument als dem vorherigen befindet.

`DF_DISABLED`\
Gibt an, dass diese Anweisung nicht ausgeführt wird.

`DF_INSTRUCTION_ACTIVE`\
Gibt an, dass diese Anweisung eine der nächsten auszuführenden Anweisungen ist (es kann mehr als eine sein).

`DF_DATA`\
Gibt an, dass es sich bei dieser Anweisung wirklich um Daten (nicht um Code) handelt.

`DF_HASSOURCE`\
Gibt an, dass diese Anweisung über eine Quelle verfügt. Einige Anweisungen, z. B. Profilerstellung oder Garbage Collection-Code, haben keine entsprechende Quelle.

`DF_DOCUMENT_CHECKSUM`\
Gibt `bstrDocumentUrl` an, dass das Feld Prüfsummendaten nach der Dokument-URL enthält. Im Abschnitt Hinweise finden Sie die [DisassemblyData-Struktur,](../../../extensibility/debugger/reference/disassemblydata.md) um zu erfahren, wie die Prüfsummendaten gespeichert werden.

## <a name="remarks"></a>Bemerkungen
Wird als `dwFlags` Member der [DisassemblyData-Struktur](../../../extensibility/debugger/reference/disassemblydata.md) verwendet.

Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
