---
title: DEBUG_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03b2db1fd58af6a8b2f8a57846e7753cdbc82352
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707262"
---
# <a name="debugreason"></a>DEBUG_REASON
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

#### <a name="parameters"></a>Parameter
DEBUG_REASON_ERROR ein nicht-spezifischen Fehler aufgetreten ist (Dies wird verwendet, als eine standardbedingung Wenn keine der anderen Lösung Gründe).

DEBUG_REASON_USER_LAUNCHED der Prozess wurde auf Anforderung des Benutzers gestartet.

DEBUG_REASON_USER_ATTACHED den bereits ausgeführten Prozess wurde vom Benutzer zugeordnet.

DEBUG_REASON_AUTO_ATTACHED wurde der Prozess automatisch an angefügt, wenn sie gestartet wurde.

DEBUG_REASON_CAUSALITY, die der Prozess, aufgrund gestartet wurde einer *Just-In-Time-* Debuggen (JIT)-Ereignis.

## <a name="remarks"></a>Hinweise
Zurückgegeben von der [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
