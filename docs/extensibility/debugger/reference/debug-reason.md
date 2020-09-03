---
title: DEBUG_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737420"
---
# <a name="debug_reason"></a>DEBUG_REASON
Gibt an, warum der Prozess zum Debuggen gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Felder
`DEBUG_REASON_ERROR`\
Ein nicht spezifischer Fehler ist aufgetreten (Dies wird als Standard Bedingung verwendet, wenn keiner der anderen Gründe passt).

`DEBUG_REASON_USER_LAUNCHED`\
Der Prozess wurde bei der Anforderung des Benutzers gestartet.

`DEBUG_REASON_USER_ATTACHED`\
Der Benutzer hat den bereits laufenden Prozess angefügt.

`DEBUG_REASON_AUTO_ATTACHED`\
Der Prozess wurde beim Starten automatisch an angefügt.

`DEBUG_REASON_CAUSALITY`\
Der Prozess wurde aufgrund eines JIT-Debugereignisses ( *Just-in-Time* ) gestartet.

## <a name="remarks"></a>Bemerkungen
Wird von der [getdebugreason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
