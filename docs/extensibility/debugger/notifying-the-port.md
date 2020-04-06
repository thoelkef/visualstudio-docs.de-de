---
title: Benachrichtigung über den Hafen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738327"
---
# <a name="notify-the-port"></a>Benachrichtigen des Ports
Nach dem Starten eines Programms muss der Port wie folgt benachrichtigt werden:

1. Wenn ein Port einen neuen Programmknoten empfängt, sendet er ein Programmerstellungsereignis zurück an die Debugsitzung. Das Ereignis enthält eine Schnittstelle, die das Programm darstellt.

2. Die Debugsitzung fragt das Programm nach dem Bezeichner eines Debugmoduls (DE), das an das Modul angefügt werden kann.

3. Die Debugsitzung überprüft, ob die DE in der Liste der zulässigen DEs für dieses Programm aufgeführt ist. Die Debugsitzung ruft diese Liste aus den aktiven Programmeinstellungen der Lösung ab, die ursprünglich vom Debugpaket an sie übergeben wurden.

    Die DE muss in der zulässigen Liste stehen, sonst wird die DE nicht an das Programm angefügt.

   Wenn ein Port zum ersten Mal einen neuen Programmknoten empfängt, erstellt er programmgesteuert eine [IDebugProgram2-Schnittstelle,](../../extensibility/debugger/reference/idebugprogram2.md) um das Programm darzustellen.

> [!NOTE]
> Dies sollte nicht `IDebugProgram2` mit der Schnittstelle verwechselt werden, die später vom Debugmodul (DE) erstellt wird.

 Der Port sendet ein [IDebugProgramCreateEvent2-Programmerstellungsereignis](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) über eine COM-Schnittstelle `IConnectionPoint` an den Session Debug Manager (SDM).

> [!NOTE]
> Dies sollte nicht `IDebugProgramCreateEvent2` mit der Schnittstelle verwechselt werden, die später von der DE gesendet wird.

 Zusammen mit der Ereignisschnittstelle selbst sendet der Port die Schnittstellen [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)und [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) die den Port, den Prozess und das Programm darstellen. Das SDM ruft [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) auf, um die GUID der DE abzubekommen, die das Programm debuggen kann. Die GUID wurde ursprünglich von der [IDebugProgramNode2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramnode2.md) abgerufen.

 Das SDM prüft, ob die DE in der Liste der zulässigen DEs steht. Das SDM ruft diese Liste aus den aktiven Programmeinstellungen der Lösung ab, die ursprünglich vom Debugpaket an sie übergeben wurden. Die DE muss in der zulässigen Liste stehen, sonst wird sie nicht an das Programm angehängt.

 Sobald die Identität der DE bekannt ist, ist das SDM bereit, es an das Programm anzuhängen.

## <a name="see-also"></a>Weitere Informationen
- [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
- [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md)
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
