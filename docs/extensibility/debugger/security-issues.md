---
title: Sicherheitsprobleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713054"
---
# <a name="security-issues"></a>Sicherheitsprobleme
Zum Debuggen eines Programms mit Visual Studio sind nur die Berechtigungen erforderlich, die ein Entwickler zum Ausführen des Programms benötigt. Dies schließt Remote-Debugging für die meisten Situationen ein. In einigen Situationen, die andere Dienste betreffen, z. B. der Internetinformationsdienst, ist möglicherweise eine höhere Berechtigungsstufe erforderlich.

 Während Visual Studio ausgeführt wird, verfolgt der Prozessdebug-Manager (PDM) Debugprozesse auf dem lokalen Computer. Remote wird ein Programm namens *msvsmon.exe* vom Entwickler gestartet, um Remote-Debugging zu verarbeiten und das PDM verfügbar zu machen. (*msvsmon.exe* ist kein Dienst und muss manuell gestartet werden, um das Remotedebuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder *msvsmon.exe*) nicht ausgeführt wird, werden keine Prozesse zum Debuggen nachverfolgt.

 Ein Entwickler kann Programme debuggen, die er ohne spezielle Berechtigungen gestartet hat. Der Entwickler kann sogar Prozesse debuggen, die von einer anderen Person gestartet wurden, wenn diese andere Person Mitglied derselben Sicherheitsgruppe ist. Und um das Remote-Debuggen zu aktivieren, ist es nur erforderlich, die erforderlichen Dateien auf den Remotecomputer zu kopieren und *msvsmon.exe*zu starten. Weitere Informationen finden Sie unter [Remotedebugging](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
- [Prozess-Debug-Manager](../../extensibility/debugger/process-debug-manager.md)
- [Remotedebuggen](../../debugger/remote-debugging.md)
