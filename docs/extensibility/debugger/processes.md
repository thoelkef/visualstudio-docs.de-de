---
title: Prozesse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c45fc70fe61c7221a8042d275dd44d69eb5d11e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351497"
---
# <a name="processes"></a>Prozesse
Architektur der Debugger eine *Prozess*:

- Ist ein Container für einen Satz von Programmen. Er ist eng an einen Windows-Prozess, der ein Container für eine Gruppe von Threads ist.

- Können selbst durch den Namen, Bezeichner oder Bezeichner der physischen identifizieren.

- Können alle ausgeführten Programme (und ihren Threads) auflisten.

- Beschreiben können selbst, den Port an, den er ausgeführt wird und der Computer, der sie enthält.

- Können, erstellen Sie eine oder mehr Programme beenden eines der Programme, die sie erstellt oder dazu führen, dass ein Programm zu beenden.

- Wird durch dargestellt eine [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle, die erstellt wird, wenn der Prozess gestartet wird. Ein Prozess wird gestartet, indem Sie entweder die sitzungsbasierter Debug-Manager (SDM) oder [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Das debugpaket kann eine Debug-Engine (DE) an einen Prozess anfügen, durch den Aufruf [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md), d. h., die die DE anfügt, auf alle möglichen Programme, die Ausführung im Prozess, die er verarbeiten kann. Wenn die common Language Runtime DE an einen Prozess angefügt wurde, fügt es z. B. nur für Programme, die verwalteten Code ausgeführt werden.

## <a name="see-also"></a>Siehe auch
- [Programme](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Paket](../../extensibility/debugger/debug-package.md)
- [Debug-engine](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)