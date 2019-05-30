---
title: Threads | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9759536e1b27018a3361bbb723b4cde0f88269e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333657"
---
# <a name="threads"></a>Threads
Architektur der Debugger eine *Thread*:

- Ist die grundlegende Einheit für die Berechnung an. Ein Thread führt nacheinander die Anweisungen innerhalb des Kontexts von einer einzigen Aufrufliste, die aus einem Codekontext mit dem nächsten fortgefahren.

- Erkennen sich selbst und das Programm, das er ausgeführt wird. Threads können mit dem Namen, angehalten und fortgesetzt werden. Ein Thread kann auch der zugeordnete Stapelrahmen aufzählen und unter bestimmten Umständen kann in einen anderen Stapelrahmen verschoben werden. Im Rahmen einen Stapelrahmen kann, ein Thread seine zugeordneten logischen Thread auf, ggf. zurück. Ein Thread verfügt über Eigenschaften, z. B. dem Unterbrechungszähler, die in angezeigt werden, kann die **Threads** Fenster der IDE.

- Wird durch dargestellt eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Schnittstelle, die in der Regel von einer Debug-Engine (DE) oder die virtuelle Maschine, daher das Ausführen eines Programms erstellt.

## <a name="see-also"></a>Siehe auch
- [Programme](../../extensibility/debugger/programs.md)
- [Stapelrahmen](../../extensibility/debugger/stack-frames.md)
- [Debug-engine](../../extensibility/debugger/debug-engine.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Sitzungsbasierter Debug-manager](../../extensibility/debugger/session-debug-manager.md)