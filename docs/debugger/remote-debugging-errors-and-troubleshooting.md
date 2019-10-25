---
title: Remote Debuggen von Fehlern und Problembehandlung | Microsoft-Dokumentation
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
ms.openlocfilehash: f41292c22de1d9c76007ca44cb7accbf82359b3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730022"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Remotedebuggen – Fehler und Problembehandlung

Wenn Sie versuchen, Remote zu debuggen, treten möglicherweise die folgenden Fehler auf.

- [Error: Unable to Automatically Step Into the Server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Remote Debugger als Administrator ausführen

Möglicherweise treten Probleme auf, wenn Sie den Remote Debugger nicht als Administrator ausführen. Beispielsweise wird möglicherweise der folgende Fehler angezeigt: "die Visual Studio Remote Debugger (msvsmon). EXE) verfügt nicht über ausreichende Berechtigungen, um diesen Prozess zu debuggen. Wenn Sie den Remote Debugger als Anwendung (nicht als Dienst) ausführen, wird möglicherweise der [andere Benutzerkonto](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) Fehler angezeigt.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Beim Ausführen des Remote Debuggers als Dienst

Wenn Sie den Remote Debugger als s-Dienst ausführen, empfiehlt es sich, ihn aus verschiedenen Gründen als Administrator zu ausführen:

- Der Remote Debugger-Dienst lässt nur Verbindungen von Administratoren zu, sodass **keine** neuen Sicherheitsrisiken entstehen, indem er als Administrator ausgeführt wird.

- Dadurch können Fehler verhindert werden, die auftreten, wenn der Visual Studio-Benutzer mehr Berechtigungen zum Debuggen eines Prozesses hat, als der Remote Debugger selbst tut.

- Vereinfachen der Einrichtung und Konfiguration des Remote Debuggers.

Obwohl es möglich ist, einen Debugvorgang auszuführen, ohne den Remote Debugger als Administrator auszuführen, müssen verschiedene Anforderungen erfüllt werden, damit diese Aufgabe ordnungsgemäß funktioniert und häufig erweiterte Dienst Konfigurationsschritte erforderlich sind.

- Das Konto, das Sie auf dem Remote Computer verwenden, muss über die Berechtigung " **Anmelden als Dienst** " verfügen. Weitere Informationen finden Sie in den Schritten unter "So fügen Sie LOGON-as-a-Service hinzu" im Artikel " [keine Verbindung zurück](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) "

- Das Konto muss über Rechte zum Debuggen des Ziel Prozesses verfügen. Um diese Rechte zu erhalten, müssen Sie den Remote Debugger unter demselben Konto wie den zu debuggenden Prozess ausführen. (Die einfachere Alternative besteht darin, den Dienst als Administrator auszuführen.) 

- Das Konto muss in der Lage sein, eine Verbindung mit dem Visual Studio-Computer über das Netzwerk herzustellen (d. h. Authentifizieren mit). In einer Domäne ist es einfacher, eine Verbindung herzustellen, wenn der Remote Debugger unter dem integrierten lokalen System oder den Netzwerkdienst Konten oder einem Domänen Konto ausgeführt wird. Die integrierten Konten verfügen über erhöhte Sicherheits Berechtigungen, die ein Sicherheitsrisiko darstellen können.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Beim Ausführen des Remote Debuggers als Anwendung (normaler Modus)

Wenn Sie versuchen, an Ihren eigenen Prozess ohne erhöhte Rechte (z. b. eine normale Anwendung) anzufügen, ist es unerheblich, ob Sie den Remote Debugger als Administrator ausführen.

Sie möchten den Remote Debugger in verschiedenen Szenarien als Administrator ausführen:

- Sie möchten an Prozesse anfügen, die als anderer Benutzer ausgeführt werden (z. b. beim Debuggen von IIS).

- Sie versuchen, einen anderen Prozess zu starten, und der Prozess, den Sie starten möchten, ist ein Administrator.

Sie möchten **nicht** als Administrator ausgeführt werden, wenn Sie Prozesse starten möchten, und der Prozess, den Sie starten möchten, sollte **kein** Administrator sein.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)