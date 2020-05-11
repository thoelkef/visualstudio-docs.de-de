---
title: Senden von Startereignissen nach einem Start | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713014"
---
# <a name="send-startup-events-after-a-launch"></a>Senden von Startereignissen nach einem Start
Sobald das Debugmodul (DE) an das Programm angeschlossen ist, sendet es eine Reihe von Startereignissen zurück an die Debugsitzung.

 Zu den Startereignissen, die an die Debugsitzung zurückgesendet werden, gehören:

- Ein Engine-Erstellungsereignis.

- Ein Programmerstellungsereignis.

- Threaderstellungs- und Modulladeereignisse.

- Ein vollständiges Load-Ereignis, das gesendet wird, wenn der Code geladen wird und ausgeführt werden kann, aber bevor Code ausgeführt wird.

  > [!NOTE]
  > Wenn dieses Ereignis fortgesetzt wird, werden globale Variablen initialisiert und Startroutinen ausgeführt.

- Mögliche andere Threaderstellungs- und Modulladeereignisse.

- Ein Einstiegspunktereignis, das signalisiert, dass das Programm **Main** seinen `WinMain`Haupteinstiegspunkt erreicht hat, z. B. Main oder . Dieses Ereignis wird in der Regel nicht gesendet, wenn die DE an ein Programm anfügt, das bereits ausgeführt wird.

  Programmgesteuert sendet die DE zuerst den Session Debug Manager (SDM) eine [IDebugEngineCreateEvent2-Schnittstelle,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) die ein Modulerstellungsereignis darstellt, gefolgt von einem [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), das ein Programmerstellungsereignis darstellt.

  Auf diese Ereignisse folgen in der Regel ein oder mehrere [IDebugThreadCreateEvent2-Threaderstellungsereignisse](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) und [IDebugModuleLoadEvent2-Modulladeereignisse.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Wenn der Code geladen und ausgeführt werden kann, aber bevor Code ausgeführt wird, sendet die DE dem SDM ein [vollständiges IDebugLoadCompleteEvent2-Ladeereignis.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Wenn das Programm noch nicht ausgeführt wird, sendet die DE ein [IDebugEntryPointEvent2-Einstiegspunktereignis,](../../extensibility/debugger/reference/idebugentrypointevent2.md) das signalisiert, dass das Programm seinen Haupteinstiegspunkt erreicht hat und zum Debuggen bereit ist.

## <a name="see-also"></a>Weitere Informationen
- [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md)
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
