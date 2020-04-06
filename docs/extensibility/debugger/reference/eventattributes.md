---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737058"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Gibt die Ereignisattribute an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Felder
`EVENT_ASYNCHRONOUS`\
Gibt an, dass das Ereignis asynchron ist und keine Antwort auf das Ereignis erforderlich ist.

`EVENT_SYNCHRONOUS`\
Gibt an, dass das Ereignis synchron ist. Antwort über [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Gibt an, dass es sich um ein Beenden-Ereignis handelt. Muss mit einem `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`oder kombiniert werden.

`EVENT_ASYNC_STOP`\
Gibt ein asynchrones Stoppereignis an. Ein solches Ereignis gibt es derzeit nicht. Dieses Flag ist nur ein Platzhalter.

`EVENT_SYNC_STOP`\
Gibt ein synchrones Stoppereignis `EVENT_SYNCHRONOUS` (eine Kombination aus und `EVENT_STOPPING`) an. Dieser Wert wird von einem Debugmodul (DE) verwendet, wenn es ein Stoppereignis sendet. Die Antwort erfolgt über einen Aufruf von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)oder [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Gibt ein Ereignis an, das sofort und synchron an die IDE gesendet wird. Dieses Flag wird mit `EVENT_ASYNCHRONOUS`anderen `EVENT_SYNCHRONOUS`Flags `EVENT_SYNC_STOP` wie , oder zur Angabe des Ereignistyps und der Tatsache, dass der Antwortmechanismus (falls vorhanden) bekannt ist, kombiniert.

`EVENT_EXPRESSION_EVALUATION`\
Das Ereignis ist ein Ergebnis der Ausdrucksauswertung.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden `dwAttrib` im Parameter der [Event-Methode](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) übergeben.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
