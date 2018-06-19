---
title: Ausnahmebehandlung (Visual Studio SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 646479184061b093d5d84f81827a4106bd3cda47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100789"
---
# <a name="exception-handling-visual-studio-sdk"></a>Ausnahmebehandlung (Visual Studio SDK)
Im folgenden wird erläutert, das auftritt, wenn Ausnahmen ausgelöst werden.  
  
## <a name="exception-handling-process"></a>Ausnahme behandeln Prozess  
  
1.  Wenn wird zuerst eine Ausnahme ausgelöst, aber bevor er vom Ausnahmehandler in der gedebuggten Anwendung behandelt wird, der Debugging-Modul (DE sendet) eine [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) Sitzung Debug-Manager (SDM) als eine Stopping-Ereignis. Die `IDebugExceptionEvent2` wird gesendet, wenn nur die Einstellungen für die Ausnahme (angegeben in das Dialogfeld "Ausnahmen" in das debugpaket) angeben, dass der Benutzer auf die erste Chance ausnahmebenachrichtigungen beenden möchte.  
  
2.  Ruft die SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) zum Abrufen der Eigenschaft der Ausnahme.  
  
3.  Ruft die Debug-Paket [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) um zu bestimmen, welche Optionen für den Benutzer anzuzeigen.  
  
4.  Das debugpaket wird der Benutzer gefragt, wie die Ausnahme behandelt, durch eine Ausnahme der ersten Chance-Dialogfeld zu öffnen.  
  
5.  Wenn der Benutzer entscheidet, den Vorgang fortzusetzen, ruft die SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Wenn die Methode gibt S_OK zurück, ruft [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         - oder -   
  
         Wenn die Methode gibt "S_FALSE", das Programm zurück, der debuggt wird eine zweite Möglichkeit zur Behandlung von Ausnahmen erhält.  
  
6.  Verfügt das derzeit debuggte Programm kein Handler für eine zweite Chance-Ausnahme, die DE sendet eine `IDebugExceptionEvent2` , das SDM als **EVENT_SYNC_STOP**.  
  
7.  Das debugpaket wird der Benutzer gefragt, wie die Ausnahme behandelt, durch eine Ausnahme der ersten Chance-Dialogfeld zu öffnen.  
  
8.  Ruft die Debug-Paket [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) um zu bestimmen, welche Optionen für den Benutzer anzuzeigen.  
  
9. Das debugpaket fordert den Benutzer wie die Ausnahme behandelt, durch Öffnen einer zweiten Chance Ausnahmedialogfeld an.  
  
10. Wenn die Methode gibt S_OK zurück, ruft `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)