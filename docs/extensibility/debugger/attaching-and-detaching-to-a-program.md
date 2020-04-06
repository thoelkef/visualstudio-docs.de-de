---
title: Anfügen und Trennen an ein Programm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739268"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen und Trennen an einem Programm
Das Anfügen des Debuggers erfordert das Senden der richtigen Reihenfolge von Methoden und Ereignissen mit den richtigen Attributen.

## <a name="sequence-of-methods-and-events"></a>Reihenfolge der Methoden und Ereignisse

1. Der Sitzungsdebug-Manager (SDM) ruft die [OnAttach-Methode](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) auf.

    Basierend auf dem Debugmodul (DE)-Prozessmodell gibt die `IDebugProgramNodeAttach2::OnAttach` Methode eine der folgenden Methoden zurück, die bestimmt, wie es weitergeht.

    Wenn `S_FALSE` zurückgegeben wird, wurde das Debugmodul erfolgreich an das Programm angefügt. Andernfalls wird die [Attach-Methode](../../extensibility/debugger/reference/idebugengine2-attach.md) aufgerufen, um den Attach-Prozess abzuschließen.

    Wenn `S_OK` die DE zurückgegeben wird, wird die DE im gleichen Prozess wie das SDM geladen. Das SDM führt die folgenden Aufgaben aus:

   1. Ruft [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) auf, um die Motorinformationen der DE abzubekommen.

   2. Erstellt die DE mit.

   3. Anrufe [attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Die DE sendet ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

3. Die DE sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) an `EVENT_SYNC` das SDM mit einem Attribut.

4. Die DE sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) an `EVENT_SYNC_STOP` das SDM mit einem Attribut.

   Das Trennen von einem Programm ist ein einfacher, zweistufiger Prozess wie folgt:

5. Das SDM ruft [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md)auf.

6. Die DE sendet ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
