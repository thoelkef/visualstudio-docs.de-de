---
title: "Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgef&#252;hrt. | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgef&#252;hrt.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Fehlermeldung bedeutet, dass Visual Studio auf dem Remotecomputer keine passende Instanz des Visual Studio\-Remotedebugmonitors finden konnte. Der Visual Studio\-Remotedebugmonitor muss installiert werden, damit das Remotedebuggen funktioniert. Informationen zum Herunterladen und zum Einrichten des Remotedebuggers finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
> [!IMPORTANT]
>  Wenn Sie der Ansicht sind, dass Sie diese Meldung aufgrund eines Produktfehlers erhalten haben, melden Sie das Problem bitte an Visual Studio [Lächeln senden](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md). Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Sprechen Sie mit uns](../ide/talk-to-us.md), wie Sie Kontakt mit Microsoft aufnehmen.  
  
## Ich habe diese Meldung beim Debuggen in Visual Studio 2010 oder einer früheren Version erhalten  
 Wenn Sie Visual Studio 2010 oder eine frühere Version von Visual Studio verwenden, kann dieser Fehler auch darauf hinweisen, dass die Datei\- und Druckerfreigabe nicht aktiviert ist. Weitere Informationen zu diesem Problem finden Sie in der Visual Studio 2010\-Version dieser Dokumentation: [Fehler: Der Microsoft Visual Studio\-Remotedebugmonitor \(MSVSMON.EXE\) wird anscheinend auf dem Remotecomputer nicht ausgeführt – Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx).  
  
## Ich habe diese Meldung beim lokalen Debuggen erhalten  
 Wenn Sie diese Meldung beim lokalen Debuggen erhalten, kann dies an Ihrer Antivirussoftware oder einer Drittanbieter\-Firewall liegen. Visual Studio ist eine 32\-Bit\-Anwendung, die zum Debuggen von 64\-Bit\-Anwendungen die 64\-Bit\-Version des Remotedebuggers verwendet. Die beiden Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Datenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter\-Sicherheitssoftware die Kommunikation blockiert.  
  
 In den folgenden Abschnitten sind einige andere Gründe aufgelistet, warum Sie diese Meldung erhalten haben und wie Sie das Problem beheben können.  
  
## Der Remotecomputer ist nicht erreichbar.  
 Versuchen Sie, eine [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx)\-Anforderung an den Remotecomputer zu senden. Wenn Sie keine Antwort auf die ping\-Anforderung erhalten, können auch die Remotetools keine Verbindung herstellen. Versuchen Sie, den Remotecomputer neu zu starten, und stellen Sie sicher, dass er ordnungsgemäß im Netzwerk konfiguriert ist.  
  
## Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein  
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Wechseln Sie zum [Download Center](http://www.microsoft.com/en-us/download), um die richtige Version des Remotedebuggers zu finden.  
  
## Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf  
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows\-Authentifizierung](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt  
 Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:  
  
-   Sie können den Remotedebugger beenden und unter dem Konto, das Sie auf dem lokalen Computer verwenden, erneut starten.  
  
-   Sie können den Remotedebugger über die Befehlszeile mit dem **\/allow \<Benutzername\>**\-Parameter erneut starten: `msvsmon /allow <username@computer>`  
  
-   Sie können dem Benutzer Remotedebuggerberechtigungen \(im Remotedebugger\-Fenster **Extras\/Berechtigungen**\) hinzufügen.  
  
-   Wenn Sie die Methoden in den vorangehenden Schritten nicht verwenden können, können Sie allen Benutzern das Remotedebuggen erlauben. Öffnen Sie im Remotedebugger\-Fenster das Dialogfeld **Extras\/Optionen**. Bei der Auswahl von **Keine Authentifizierung** können Sie **Allen Benutzern das Debugging ermöglichen** aktivieren. Sie sollten diese Option jedoch nur verwenden, wenn es keine andere Möglichkeit gibt oder Sie sich in einem privaten Netzwerk befinden.  
  
## Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu  
 Die Firewalls auf dem Visual Studio\-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remotedebugger \- Portzuweisungen](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows\-Firewall finden Sie unter [Konfigurieren der Windows\-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## Verbindungen werden durch Antivirussoftware blockiert  
 Die Windows\-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter\-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.  
  
## Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio  
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Sicherheitsrichtlinie für Windows\-Netzwerke finden Sie unter [Sicherheitsverwaltung](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen  
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.  
  
## Weitere Hilfe  
 Weitere Informationen zum Remotedebugger, einschließlich Befehlzeilenoptionen, finden Sie unter:  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)