---
title: Starten des Debuggers | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ffe0405b1e07bfb7825607e17088f0f75796197
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059720"
---
# <a name="launch-the-debugger"></a>Starten des Debuggers
Starten des Debuggers gesendet werden müssen, der richtigen Sequenz von Methoden und Ereignisse mit ihren entsprechenden Attributen.

## <a name="sequences-of-methods-and-events"></a>Sequenzen von Methoden und Ereignisse

1. Sitzungsbasierter Debug-Manager (SDM) wird aufgerufen, durch Auswählen der **Debuggen** Menü auswählen und dann **starten**. Weitere Informationen finden Sie unter [ein Programm starten](../../extensibility/debugger/launching-a-program.md).

2. Die SDM-Aufrufe [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.

3. Basierend auf der Debug-Engine (DE)-Prozessmodell der `IDebugProgramNodeAttach2::OnAttach` Methode gibt einen der folgenden Methoden, die bestimmt, was als Nächstes geschieht zurück.

     Wenn `S_FALSE` zurückgibt, die Debug-Engine (DE) wird dabei den virtuellen Computer geladen werden.

     - oder - 

     Wenn `S_OK` zurückgegeben wird, ist der DE geladen werden von der SDM in-Process. Das SDM führt dann die folgenden Aufgaben aus:

    1. Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) zum Abrufen der Engine Informationen des DE.

    2. Gemeinsam erstellt die DE.

    3. Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Der DE sendet eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.

5. Der DE sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.

6. Der DE sendet eine [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.

7. Der DE sendet eine [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.

8. Der DE sendet eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
- [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)