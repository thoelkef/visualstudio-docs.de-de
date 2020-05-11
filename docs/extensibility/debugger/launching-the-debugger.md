---
title: Starten des Debuggers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738458"
---
# <a name="launch-the-debugger"></a>Starten des Debuggers
Beim Starten des Debuggers muss die richtige Reihenfolge von Methoden und Ereignissen mit den richtigen Attributen gesendet werden.

## <a name="sequences-of-methods-and-events"></a>Sequenzen von Methoden und Ereignissen

1. Der Sitzungsdebug-Manager (SDM) wird aufgerufen, indem Sie das **Debugmenü** auswählen und dann **Start**auswählen. Weitere Informationen finden Sie unter [Starten eines Programms](../../extensibility/debugger/launching-a-program.md).

2. Die SDM ruft die [OnAttach-Methode](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) auf.

3. Basierend auf dem Debugmodul (DE)-Prozessmodell gibt die `IDebugProgramNodeAttach2::OnAttach` Methode eine der folgenden Methoden zurück, die bestimmt, wie es weitergeht.

     Wenn `S_FALSE` es zurückgegeben wird, wird das Debugmodul (DE) in der Version der virtuellen Maschine geladen.

     - oder -

     Wenn `S_OK` die SDM zurückgegeben wird, wird die DE im Prozess des SDM geladen. Das SDM führt dann die folgenden Aufgaben aus:

    1. Ruft [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) auf, um die Motorinformationen der DE abzubekommen.

    2. Erstellt die DE mit.

    3. Anrufe [attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Die DE sendet ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

5. Die DE sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

6. Die DE sendet ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

7. Die DE sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

8. Die DE sendet ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
- [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
