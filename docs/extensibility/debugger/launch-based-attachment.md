---
title: Start-basierte Anlage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738460"
---
# <a name="launch-based-attachment"></a>Start-basierte Anlage
Die Start-basierte Anlage zu einem Programm erfolgt automatisch. Wenn der Prozess, der das Programm hostet, vom SDM gestartet wird, folgt die startbasierte Anlage einem Pfad, der dem der manuellen Anlagemethode ähnelt. Weitere Informationen finden Sie [unter Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Der Ansteckungsprozess
 Der Hauptunterschied ist die Abfolge der Ereignisse nach dem **Attach-Aufruf,** wie folgt:

1. Senden Sie ein **IDebugEngineCreateEvent2-Ereignisobjekt** an das SDM. Weitere Informationen finden Sie unter Senden von [Ereignissen](../../extensibility/debugger/sending-events.md).

2. Rufen `IDebugProgram2::GetProgramId` Sie die Methode auf der **IDebugProgram2-Schnittstelle** auf, die an die **Attach-Methode** übergeben wird.

3. Senden Sie ein **IDebugProgramCreateEvent2-Ereignisobjekt,** um das SDM darüber zu benachrichtigen, dass das lokale **IDebugProgram2-Objekt** erstellt wurde, um das Programm für die DE darzustellen.

4. Senden Sie ein [IDebugThreadCreateEvent2-Ereignisobjekt,](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) um das SDM darüber zu informieren, dass ein neuer Thread für den gestarteten Prozess erstellt wurde.

## <a name="see-also"></a>Weitere Informationen
- [Senden der erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)
- [Aktivieren des Debuggens eines Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
