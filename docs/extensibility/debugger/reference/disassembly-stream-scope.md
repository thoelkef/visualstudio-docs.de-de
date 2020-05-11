---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737271"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Gibt den Bereich des Demontagestreams an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Felder
`DSS_HUGE`\
Gibt an, dass die Demontage des Codekontexts mehr Ausgabe generiert, als ein Client normalerweise in einem einzelnen Aufruf abrufen möchte.

`DSS_FUNCTION`\
Gibt an, dass die im Codekontext enthaltene Funktion demontiert werden soll. Gibt an, dass der Demontagestream eine Funktion darstellt, wenn er von der [GetScope-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) zurückgegeben wird.

`DSS_MODULE`\
Wenn die `IDebugDisassemblyStream2::GetScope` Methode zurückgegeben wird, gibt sie an, dass der Demontagestream ein Modul darstellt.

`DSS_ALL`\
Gibt die Demontage für den gesamten Adressraum an.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument an die [GetDisassemblyStream-Methode](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) und wird von der [GetScope-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) zurückgegeben.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
