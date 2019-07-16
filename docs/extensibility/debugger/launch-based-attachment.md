---
title: Startbasiertes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 638eaea19b4f21e749fbd3db845f18eb573420f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344150"
---
# <a name="launch-based-attachment"></a>Startbasiertes
Startbasiertes an ein Programm erfolgt automatisch. Wenn der Hostprozess für das Programm durch die SDM gestartet wird, folgt startbasiertes einen Pfad, mit der manuellen Anlage Methode ähnelt. Weitere Informationen finden Sie unter [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Der Prozess anfügen
 Der Hauptunterschied ist die Abfolge der Ereignisse, die nach der **Anfügen** wie folgt aufrufen:

1. Senden einer **IDebugEngineCreateEvent2** Event-Objekt, das SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

2. Rufen Sie die `IDebugProgram2::GetProgramId` Methode für die **IDebugProgram2** Schnittstelle zu übergeben, um die **Anfügen** Methode.

3. Senden einer **IDebugProgramCreateEvent2** Event-Objekt, das SDM zu benachrichtigen, die der lokalen **IDebugProgram2** Objekt wurde erstellt, um die Anwendung für das DE darstellen.

4. Senden einer [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisobjekt, dem SDM benachrichtigen, dass es sich bei ein neuer Thread für den Prozess erstellt wird, die gestartet.

## <a name="see-also"></a>Siehe auch
- [Senden Sie die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)
- [Aktivieren Sie zu debuggenden Programm](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)