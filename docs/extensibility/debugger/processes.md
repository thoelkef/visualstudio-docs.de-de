---
title: Prozesse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738249"
---
# <a name="processes"></a>Prozesse
In der Debuggerarchitektur wird ein *Prozess*:

- Ist ein Container für eine Reihe von Programmen. Es ist eng mit einem Windows-Prozess vergleichbar, der ein Container für eine Reihe von Threads ist.

- Kann sich durch Namen, Bezeichner oder physischen Bezeichner identifizieren.

- Kann alle ausgeführten Programme (und deren Threads) aufzählen.

- Kann sich selbst beschreiben, den Port, in dem er läuft, und den Computer, der ihn enthält.

- Kann ein oder mehrere Programme erstellen, eines der von ihm erstellten Programme beenden oder dazu führen, dass ein Programm beendet wird.

- Wird durch eine [IDebugProcess2-Schnittstelle](../../extensibility/debugger/reference/idebugprocess2.md) dargestellt, die beim Starten des Prozesses erstellt wird. Ein Prozess wird entweder vom Session Debug Manager (SDM) oder [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)gestartet.

  Das Debugpaket kann ein Debugmodul (DE) an einen Prozess anfügen, indem [es Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufruft, was bedeutet, dass die DE an alle möglichen Programme anfügt, die in dem Prozess ausgeführt werden, den es verarbeiten kann. Wenn z. B. die Common Language Runtime DE an einen Prozess angefügt wird, wird sie nur an Programme angefügt, die verwalteten Code ausführen.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Paket](../../extensibility/debugger/debug-package.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)
