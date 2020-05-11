---
title: Ausnahmebehandlung (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738763"
---
# <a name="exception-handling-visual-studio-sdk"></a>Ausnahmebehandlung (Visual Studio SDK)
Im Folgenden wird der Prozess beschrieben, der auftritt, wenn Ausnahmen ausgelöst werden.

## <a name="exception-handling-process"></a>Ausnahmebehandlungsprozess

1. Wenn eine Ausnahme zum ersten Mal ausgelöst wird, aber bevor sie vom Ausnahmehandler in dem zu debuggenden Programm behandelt wird, sendet das Debugmodul (DE) ein [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) als Stoppereignis an den Sitzungsdebug-Manager (SDM). Der `IDebugExceptionEvent2` wird gesendet, wenn nur die Einstellungen für die Ausnahme (im Dialogfeld Ausnahmen im Debugpaket angegeben) angeben, dass der Benutzer Bei Ausnahmebenachrichtigungen der ersten Chance beenden möchte.

2. Das SDM ruft [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) auf, um die Eigenschaft exception abzuruft.

3. Das Debugpaket ruft [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) auf, um zu bestimmen, welche Optionen dem Benutzer angezeigt werden sollen.

4. Das Debugpaket fragt den Benutzer, wie die Ausnahme zu behandeln ist, indem ein Ausnahmedialogfeld der ersten Chance geöffnet wird.

5. Wenn der Benutzer den Vorgang fortsetzt, ruft das SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)auf.

    - Wenn die Methode S_OK zurückgibt, ruft [iDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)auf.

         - oder -

         Wenn die Methode S_FALSE zurückgibt, erhält das zu debuggende Programm eine zweite Chance, die Ausnahme zu behandeln.

6. Wenn das zu debuggende Programm keinen Handler für eine Ausnahme `IDebugExceptionEvent2` der zweiten Chance hat, sendet die DE eine an das SDM als **EVENT_SYNC_STOP**.

7. Das Debugpaket fragt den Benutzer, wie die Ausnahme zu behandeln ist, indem ein Ausnahmedialogfeld der ersten Chance geöffnet wird.

8. Das Debugpaket ruft [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) auf, um zu bestimmen, welche Optionen dem Benutzer angezeigt werden sollen.

9. Das Debugpaket fragt den Benutzer, wie die Ausnahme zu behandeln ist, indem ein Dialogfeld für die zweite Chance geöffnet wird.

10. Wenn die Methode S_OK `IDebugExceptionEvent2::PassToDebuggee`zurückgibt, ruft .

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
