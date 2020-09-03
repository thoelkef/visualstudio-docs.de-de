---
title: Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477064"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Fehlermeldung wird angezeigt, wenn Sie im Dialogfeld **An den Prozess anhängen** einen ungültigen Namen des Visual Studio-Remotedebugmonitors eingeben. Der Remotedebugmonitor-Name entspricht gewöhnlich dem Namen des Computers, zu dem Sie für das Remotedebuggen eine Verbindung herstellen möchten. Diese Fehlermeldung kann verschiedene Ursachen haben: Entweder der Remotecomputer ist im Netzwerk nicht vorhanden, der Remotedebugmonitor ist auf dem Remotecomputer nicht ordnungsgemäß eingerichtet, oder auf den Remotecomputer kann aufgrund von Netzwerkproblemen bzw. wegen einer Firewall nicht zugegriffen werden.  
  
> [!IMPORTANT]
> Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/talk-to-us.md) , wie Sie Kontakt mit Microsoft aufnehmen.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Ich habe diese Meldung beim lokalen Debuggen erhalten  
 Wenn Sie diese Meldung beim lokalen Debuggen erhalten, kann dies an Ihrer Antivirussoftware oder einer Drittanbieter-Firewall liegen. Visual Studio ist eine 32-Bit-Anwendung, die zum Debuggen von 64-Bit-Anwendungen die 64-Bit-Version des Remotedebuggers verwendet. Die beiden Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.  
  
 In den folgenden Abschnitten sind einige andere Gründe aufgelistet, warum Sie diese Meldung erhalten haben und wie Sie das Problem beheben können.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass der Visual Studio-Remotedebugmonitor auf dem Remotecomputer installiert ist und ausgeführt wird. Weitere Informationen zum Remote Debugger und dessen Installation finden Sie unter [Remote Debugging](../debugger/remote-debugging.md).  
  
- Zeigen Sie in Visual Studio die Projekteigenschaften an (**Projekt / Eigenschaften / Debugging**). Stellen Sie sicher, dass der **Remoteservername** richtig ist.  
  
- Überprüfen Sie, ob der Remotecomputer im Netzwerk erreichbar ist.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Der Remotecomputer ist nicht erreichbar.  
 Versuchen Sie, eine [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) -Anforderung an den Remotecomputer zu senden. Wenn Sie keine Antwort auf die ping-Anforderung erhalten, können auch die Remotetools keine Verbindung herstellen. Versuchen Sie, den Remotecomputer neu zu starten, und stellen Sie sicher, dass er ordnungsgemäß im Netzwerk konfiguriert ist.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein  
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Wechseln Sie zu [Visual Studio-Abonnements](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) , um die richtige Version des Remote Debuggers für Ihre Version von Visual Studio zu finden.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf  

 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus für den Remotedebugger im Dialogfeld **Extras / Optionen** ändern.  
  
 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt  
 Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:  
  
- Sie können den Remotedebugger beenden und unter dem Konto, das Sie auf dem lokalen Computer verwenden, erneut starten.  
  
- Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<username>** starten: `msvsmon /allow <username@computer>`.  
  
- Sie können den Benutzer den Remote Debugger-Berechtigungen hinzufügen (im Fenster Remote Debugger, Extras **/Berechtigungen**).  
  
- Wenn Sie die Methoden in den vorangehenden Schritten nicht verwenden können, können Sie allen Benutzern das Remotedebuggen erlauben. Öffnen Sie im Remotedebugger-Fenster das Dialogfeld **Extras/Optionen** . Bei der Auswahl von   **Keine Authentifizierung**können Sie **Allen Benutzern das Debugging ermöglichen**aktivieren. Sie sollten diese Option jedoch nur verwenden, wenn es keine andere Möglichkeit gibt oder Sie sich in einem privaten Netzwerk befinden.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu  
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert  
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio  
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Sicherheitsrichtlinie für Windows-Netzwerke finden Sie unter [Sicherheitsverwaltung](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen  
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.  
  
## <a name="more-help"></a>Weitere Hilfe  
 Weitere Informationen zum Remotedebugger, einschließlich Befehlzeilenoptionen, finden Sie unter:  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Remote Debugging](../debugger/remote-debugging.md)
