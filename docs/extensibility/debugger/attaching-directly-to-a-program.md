---
title: Direktes Anfügen an ein Programm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70e8caea5cb15f614f20faafc92785e9a2da8fae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926041"
---
# <a name="attach-directly-to-a-program"></a>Fügen Sie direkt an ein Programm
Gehen Sie Benutzer, die beim Debuggen von Programmen in einem Prozess, der bereits, in der Regel ausgeführt wird möchten:

1. Wählen Sie in der IDE die **Debugprozesse** Befehl die **Tools** Menü.

    Das Dialogfeld **Prozesse** wird angezeigt.

2. Wählen Sie einen Prozess aus, und klicken Sie auf die **Anfügen** Schaltfläche.

    Die **an den Prozess anhängen** im angezeigten Dialogfeld auflisten alle Debug-Engines (DEs), auf dem Computer installiert.

3. Geben Sie die DEs zu verwenden, um den ausgewählten Prozess debuggen, und klicken Sie dann auf **OK**.

   Das debugpaket startet eine Debugsitzung, und die Liste der DEs übergeben. Die Debugsitzung wiederum übergibt diese Liste zusammen mit der eine Callback-Funktion, um den ausgewählten Prozess, und fordert dann der Vorgang zum Auflisten von seinen Programmen ausgeführten.

   Programmgesteuert, wird als Antwort auf Anforderung des Benutzers, ein das debugpaket sitzungsbasierter Debug-Manager (SDM) instanziiert und die Liste der ausgewählten DEs übergeben. Zusammen mit der Liste aus, übergibt das debugpaket das SDM ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle. Das debugpaket übergibt die Liste der DEs an den ausgewählten Prozess, durch den Aufruf [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Klicken Sie dann aufruft, das SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf den Port an, die im Prozess ausgeführten Programme aufgelistet werden.

   Ab diesem Zeitpunkt auf jede Debug-Engine angefügt ist, an ein Programm genau wie im [anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md), mit zwei Ausnahmen.

   Aus Effizienzgründen DEs, die implementiert werden, wenn Sie einen Adressraum für das SDM freigeben werden so gruppiert, sodass jede DE enthält eine Reihe von Programmen, die sie beim Hinzufügen. In diesem Fall [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) Aufrufe [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) und übergibt ein Array von Programmen für das Anfügen an.

   Die zweite Ausnahme ist, dass die Startereignisse, die per einer bereitgestellten Kompatibilitätsrichtlinie Anfügen an ein Programm, das bereits ausgeführt wird nicht in der Regel das punktereignis Eintrag enthalten.

## <a name="see-also"></a>Siehe auch
- [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)