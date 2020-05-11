---
title: Direkt es an ein Programm anfügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739262"
---
# <a name="attach-directly-to-a-program"></a>Direkt an ein Programm anhängen
Benutzer, die Programme in einem prozessbereits ausgeführten Prozess debuggen möchten, folgen in der Regel diesem Prozess:

1. Wählen Sie in der IDE den Befehl **"Prozesse debuggen"** aus dem Menü **Extras** aus.

    Das Dialogfeld **Prozesse** wird angezeigt.

2. Wählen Sie einen Prozess aus, und klicken Sie auf die Schaltfläche **Anfügen.**

    Das Dialogfeld **An Prozess anfügen** wird und listet alle auf dem Computer installierten Debugmodule (DEs) auf.

3. Geben Sie die DEs an, die zum Debuggen des ausgewählten Prozesses verwendet werden sollen, und klicken Sie dann auf **OK**.

   Das Debugpaket startet eine Debugsitzung und übergibt die Liste der DEs an sie. Die Debugsitzung übergibt diese Liste zusammen mit einer Rückruffunktion an den ausgewählten Prozess und fordert den Prozess dann auf, die ausgeführten Programme aufzulisten.

   Programmgesteuert instanziiert das Debugpaket als Antwort auf die Benutzeranforderung den Sitzungsdebug-Manager (SDM) und übergibt die Liste der ausgewählten DEs an ihn. Zusammen mit der Liste übergibt das Debugpaket dem SDM eine [IDebugEventCallback2-Schnittstelle.](../../extensibility/debugger/reference/idebugeventcallback2.md) Das Debugpaket übergibt die Liste der DEs an den ausgewählten Prozess, indem [iDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufgerufen wird. Das SDM ruft dann [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf dem Port auf, um die im Prozess ausgeführten Programme aufzuzählen.

   Ab diesem Zeitpunkt wird jedes Debugmodul mit zwei Ausnahmen an ein Programm angeschlossen, das [in Attaching genau](../../extensibility/debugger/attaching-after-a-launch.md)so detailliert ist.

   Aus Gründen der Effizienz werden DEs, die implementiert sind, um einen Adressraum für das SDM gemeinsam zu nutzen, so gruppiert, dass jede DE über eine Reihe von Programmen verfügt, an die sie anfügen. In diesem Fall ruft [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) auf und übergibt ihm ein Array von Programmen, an die angefügt werden soll.

   Die zweite Ausnahme besteht darin, dass die Startereignisse, die von einer DE gesendet werden, die an ein Programm angefügt wird, das bereits ausgeführt wird, in der Regel nicht das Einstiegspunktereignis enthalten.

## <a name="see-also"></a>Weitere Informationen
- [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
