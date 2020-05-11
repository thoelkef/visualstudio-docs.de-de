---
title: Remote-Debugging-Fehler und Fehlerbehebung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301068"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Remotedebuggen – Fehler und Problembehandlung

Beim Remote-Debugversuch können die folgenden Fehler auftreten.

- [Fehler: Der Schritt in den Server kann nicht automatisch ausgeführt werden.](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ausführen des Remotedebuggers als Administrator

Es können Probleme auftreten, wenn Sie den Remotedebugger nicht als Administrator ausführen. Beispielsweise wird möglicherweise der folgende Fehler angezeigt: "Der Visual Studio Remote Debugger (MSVSMON. EXE) verfügt nicht über ausreichende Berechtigungen, um diesen Prozess zu debuggen." Wenn Sie den Remotedebugger als Anwendung (nicht als Dienst) ausführen, wird möglicherweise der [unterschiedliche Benutzerkontofehler](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) angezeigt.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Beim Ausführen des Remote-Debuggers als Dienst

Wenn Sie den Remotedebugger als s-Dienst ausführen, empfehlen wir, ihn aus mehreren Gründen als Administrator auszuführen:

- Der Remotedebuggerdienst lässt nur Verbindungen von Administratoren zu, sodass **keine** neuen Sicherheitsrisiken durch die Ausführung als Administrator entstehen.

- Es kann Fehler verhindern, die auftreten, wenn der Visual Studio-Benutzer über mehr Rechte zum Debuggen eines Prozesses verfügt als der Remotedebugger selbst.

- So vereinfachen Sie die Einrichtung und Konfiguration des Remote-Debuggers.

Obwohl es möglich ist, zu debuggen, ohne den Remotedebugger als Administrator auszuführen, gibt es mehrere Anforderungen, damit dies ordnungsgemäß funktioniert, und sie erfordern häufig erweiterte Dienstkonfigurationsschritte.

- Das Konto, das Sie auf dem Remotecomputer verwenden, muss über die **Anmeldeberechtigung als Dienst** verfügen. Weitere Informationen finden Sie in den Schritten unter "Anmelden als Dienst hinzufügen" im Artikel ["Fehler kann keine Verbindung herstellen" zurück.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

- Das Konto muss über Rechte zum Debuggen des Zielprozesses verfügen. Um diese Rechte zu erhalten, müssen Sie den Remotedebugger unter demselben Konto wie der zu debuggende Prozess ausführen. (Die einfachere Alternative besteht darin, den Dienst als Administrator auszuführen.) 

- Das Konto muss in der Lage sein, über das Netzwerk eine Verbindung mit dem Visual Studio-Computer herzustellen (d. h. sich mit ihm zu authentifizieren). In einer Domäne ist es einfacher, eine Verbindung herzustellen, wenn der Remotedebugger unter den integrierten lokalen System- oder Netzwerkdienstkonten oder einem Domänenkonto ausgeführt wird. Die integrierten Konten verfügen über erhöhte Sicherheitsberechtigungen, die ein Sicherheitsrisiko darstellen können.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Beim Ausführen des Remote-Debuggers als Anwendung (Normalmodus)

Wenn Sie versuchen, einen eigenen, nicht erhöhten Prozess (z. B. eine normale Anwendung) anzufügen, spielt es keine Rolle, ob Sie den Remotedebugger als Administrator ausführen.

Sie möchten den Remotedebugger als Administrator in mehreren Szenarien ausführen:

- Sie möchten an Prozesse anfügen, die als anderer Benutzer ausgeführt werden (z. B. beim Debuggen von IIS) oder

- Sie versuchen, einen anderen Prozess zu starten, und der Prozess, den Sie starten möchten, ist ein Administrator.

Sie möchten **nicht** als Administrator ausgeführt werden, wenn Sie Prozesse starten möchten, und der Prozess, den Sie starten möchten, sollte **kein** Administrator sein.

## <a name="see-also"></a>Weitere Informationen
- [Remotedebugging](../debugger/remote-debugging.md)