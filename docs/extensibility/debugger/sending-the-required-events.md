---
title: Senden der erforderlichen Ereignisse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712997"
---
# <a name="send-the-required-events"></a>Senden der erforderlichen Ereignisse
Verwenden Sie dieses Verfahren zum Senden erforderlicher Ereignisse.

## <a name="process-for-sending-required-events"></a>Prozess zum Senden erforderlicher Ereignisse
 Beim Erstellen eines Debugmoduls (DE) und Anfügen an ein Programm sind in dieser Reihenfolge die folgenden Ereignisse erforderlich:

1. Senden Sie ein [IDebugEngineCreateEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugenginecreateevent2.md) an den Sitzungsdebug-Manager (SDM), wenn die DE zum Debuggen eines oder mehrere Programme in einem Prozess initialisiert wird.

2. Wenn das zu debuggende Programm angefügt ist, senden Sie ein [IDebugProgramCreateEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) an das SDM. Dieses Ereignis kann je nach Motordesign ein Stoppereignis sein.

3. Wenn das Programm beim Starten des Prozesses angefügt wird, senden Sie ein [IDebugThreadCreateEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) an das SDM, um die IDE des neuen Threads zu benachrichtigen. Dieses Ereignis kann je nach Motordesign ein Stoppereignis sein.

4. Senden Sie ein [IDebugLoadCompleteEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) an das SDM, wenn das zu debuggende Programm beendet wird oder wenn das Anfügen an das Programm abgeschlossen ist. Dieses Ereignis muss ein Beenden-Ereignis sein.

5. Wenn die zu debuggende Anwendung gestartet wird, senden Sie ein [IDebugEntryPointEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugentrypointevent2.md) an das SDM, wenn die erste Codeanweisung in der Laufzeitarchitektur ausgeführt wird. Dieses Ereignis ist immer ein Stoppereignis. Beim Einstieg in die Debugsitzung wird die IDE bei diesem Ereignis beendet.

> [!NOTE]
> Viele Sprachen verwenden globale Initialisierer oder externe, vorkompilierte Funktionen (aus der CRT-Bibliothek oder _Main) am Anfang ihres Codes. Wenn die Sprache des Programms, das Sie debuggen, eines dieser Elementtypen vor dem ursprünglichen Einstiegspunkt enthält, wird dieser **main** Code `WinMain`ausgeführt, und das Einstiegspunktereignis wird gesendet, wenn der Benutzereinstiegspunkt erreicht wird, z. B. Main oder .

## <a name="see-also"></a>Weitere Informationen
- [Debuggen eines Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
