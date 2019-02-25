---
title: Sicherheitsprobleme | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f68db1a4c6fb3ea2a7f9542c1a9d2d313359554
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689212"
---
# <a name="security-issues"></a>Sicherheitsprobleme
Um ein Programm mit Visual Studio zu debuggen, werden nur die erforderlichen Berechtigungen identisch ein Entwickler benötigt, um das Programm auszuführen. Dies schließt die Remotedebugging-Funktionen für die meisten Situationen. Einige Situationen, die im Zusammenhang mit anderen Diensten, z. B. das Internet Information Service, möglicherweise ein höheres Maß an Berechtigungen.

 Während Visual Studio ausgeführt wird, verfolgt der Prozess-Manager (PDM) Debuggen auf dem lokalen Computer. Remote, ein Programm namens *msvsmon.exe* wird gestartet, indem der Entwickler zu behandeln, Remotedebuggen und das PDM verfügbar zu machen. (*msvsmon.exe* ist kein Dienst und muss manuell gestartet werden, um das Remotedebuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder *msvsmon.exe*) wird nicht ausgeführt wird, werden keine Prozesse für das Debuggen nachverfolgt.

 Entwickler kann Programme debuggen, die sie ohne spezielle Berechtigungen gestartet werden. Entwickler kann auch Debuggen, Prozesse, die von einem anderen Benutzer gestartet werden, wenn diese andere Person die gleiche Sicherheitsgruppe angehört. Und, um Remotedebuggen zu aktivieren, ist es erforderlich, um die erforderlichen Dateien auf den Remotecomputer kopieren und starten *msvsmon.exe*. Weitere Informationen finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Siehe auch
- [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
- [Prozessbasierter Debug-manager](../../extensibility/debugger/process-debug-manager.md)
- [Remotedebuggen](../../debugger/remote-debugging.md)
