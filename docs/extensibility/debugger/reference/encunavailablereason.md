---
title: EncUnavailableReason | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717038"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Stellt die Gründe, **bearbeiten und Fortfahren** ist nicht verfügbar.

## <a name="syntax"></a>Syntax

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

#### <a name="parameters"></a>Parameter
ENCUN_NONE keine bestimmten Grund für bearbeiten und Fortfahren nicht verfügbar.

ENCUN_INTEROP bearbeiten und Fortfahren ist während eines Interop-Aufrufs nicht verfügbar.

ENCUN_SQLCLR bearbeiten und Fortfahren ist während eines Aufrufs der SQL-Prozedur, das die Common Language Runtime (CLR) wird verwendet, nicht verfügbar.

ENCUN_MINIDUMP bearbeiten und Fortfahren ist während der Verarbeitung eines Minidump nicht verfügbar.

Bei der Verarbeitung von eingebetteten Codes ist ENCUN_EMBEDDED bearbeiten und Fortfahren nicht verfügbar.

ENCUN_ATTACH bearbeiten und Fortfahren ist nicht verfügbar, da die Sitzung an angefügt wurde, nicht vom Debugger gestartet.

ENCUN_WIN64 bearbeiten und Fortfahren ist während der Verarbeitung von 64-Bit-Windows-Code nicht verfügbar.

## <a name="remarks"></a>Hinweise
Diese Enumeration ist für die interne Verwendung nur durch [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. Die [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) und [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) Methoden wie von einem benutzerdefinierten Port Lieferanten implementiert, sollte immer zurückgeben `E_NOTIMPL`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.idl

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
