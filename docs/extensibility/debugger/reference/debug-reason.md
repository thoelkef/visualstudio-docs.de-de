---
title: DEBUG_REASON | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
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
Ein nicht spezifischer Fehler ist aufgetreten (dies wird als Standardbedingung verwendet, wenn keiner der anderen Gründe passt).

`DEBUG_REASON_USER_LAUNCHED`\
Der Prozess wurde auf Anforderung des Benutzers gestartet.

`DEBUG_REASON_USER_ATTACHED`\
Der bereits ausgeführte Prozess wurde vom Benutzer angefügt.

`DEBUG_REASON_AUTO_ATTACHED`\
Der Prozess wurde automatisch an das Startziel angefügt.

`DEBUG_REASON_CAUSALITY`\
Der Prozess wurde aufgrund eines JIT-Debugging-Ereignisses *(Just-In-Time)* gestartet.

## <a name="remarks"></a>Bemerkungen
Von der [GetDebugReason-Methode](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
