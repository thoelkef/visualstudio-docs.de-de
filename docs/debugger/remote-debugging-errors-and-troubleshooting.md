---
title: Remotedebuggen – Fehler und Problembehandlung | Microsoft-Dokumentation
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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043350"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Remotedebuggen – Fehler und Problembehandlung

Möglicherweise stoßen Sie auf die folgenden Fehler beim Versuch, Remote zu debuggen.

- [Fehler: Automatischer Einzelschritt auf dem Server nicht möglich](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Den Remotedebugger als Administrator ausführen.

Sie können auf Probleme stoßen, wenn Sie nicht den Remotedebugger als Administrator ausführen. Beispielsweise können Sie die folgende Fehlermeldung angezeigt: "Visual Studio Remote Debugger (MSVSMON. EXE-Datei) besitzt keine ausreichenden Berechtigungen, die diesen Prozess zu debuggen." Wenn Sie den Remotedebugger als Anwendung (nicht um einen Dienst) ausführen, können Sie sehen die [anderes Benutzerkonto](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) Fehler.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Wenn der Remotedebugger als Dienst ausgeführt.

Bei Ausführung des Remotedebuggers als Dienst s empfehlen wir die Ausführung als Administrator für verschiedene Gründe haben:

- Der Remotedebugdienst ermöglicht Verbindungen nur von Administratoren, daher gibt es **keine** neue Sicherheitsrisiken, die eingeführt werden, indem Sie sie als Administrator ausführen.

- Es kann Fehler vermeiden, die Ergebnis, wenn der Visual Studio-Benutzer weitere Rechte zum Debuggen eines Prozesses als den Remotedebugger selbst verfügt.

- Um die Einrichtung und Konfiguration des Remotedebuggers zu vereinfachen.

Es ist, zwar möglich, Debuggen, ohne den Remotedebugger als Administrator ausführen bestehen mehrere Anforderungen an, damit dies funktioniert ordnungsgemäß, und häufig erfordern erweiterte Dienst Konfigurationsschritte.

- Das Konto, das Sie, auf dem Remotecomputer verwenden werden müssen die **Anmelden als Dienst** Berechtigungen. Die Schritte unter "Hinzufügen Anmeldung als Dienst" finden Sie der [kann keine Verbindung wieder hergestellt.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) Artikel.

- Das Konto muss Berechtigungen zum Debuggen des Zielprozess verfügen. Um diese Rechte zu erhalten, müssen Sie den Remotedebugger unter demselben Konto als das zu debuggende Prozess ausführen. (Die einfachere Alternative ist zum Ausführen des Diensts als Administrator.) 

- Das Konto muss in der Lage, Herstellen einer Verbindung mit zurück (d. h. mit authentifizieren) Visual Studio-Computer über das Netzwerk. In einer Domäne ist es einfacher, eine Verbindung herstellen, wenn der Remotedebugger unter den integrierten lokalen System oder Network Service-Konten oder einem Domänenkonto ausgeführt wird. Die Standardkonten erhöhten Sicherheitsberechtigungen, die ein Sicherheitsrisiko darstellen können.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Wenn der Remotedebugger ausgeführt, wie eine Anwendung (normaler Modus)

Wenn Sie versuchen, Verbindung mit Ihrem eigenen Prozess ohne erhöhte Rechte (z. B. eine normale Anwendung), ist es unerheblich, ob Sie den Remotedebugger als Administrator ausführen.

Der Remotedebugger als Administrator in verschiedenen Szenarios ausgeführt werden sollen:

- Zum Anfügen an Prozesse, die als ein anderer Benutzer ausgeführt werden sollen (z. B. beim Debuggen von IIS), oder

- Sie versuchen, einen anderen Prozess zu starten, und der Prozess, den Sie starten möchten, ist ein Administrator.

Sie **nicht** möchten Sie sich als Administrator ausführen, wenn Prozesse gestartet werden soll, und der Prozess, die Sie starten möchten, sollten **nicht** Administrator sein.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)