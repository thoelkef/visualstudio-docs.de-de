---
title: Es kann keine Verbindung mit dem Microsoft Visual Studio Remotedebugmonitor hergestellt werden | Microsoft-Dokumentation
ms.date: 08/24/2017
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872f7c594344af2c59ebe7f8d1fbd1a640dd2190
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728830"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
Diese Meldung kann auftreten, wenn der Remotedebugmonitor auf dem Remote Computer nicht ordnungsgemäß eingerichtet ist oder der Remote Computer aufgrund von Netzwerkproblemen oder dem vorhanden sein einer Firewall nicht zugänglich ist.

> [!IMPORTANT]
> Wenn Sie der Meinung sind, dass Sie diese Meldung aufgrund eines Produktfehlers erhalten haben, [melden Sie dieses Problem](../ide/how-to-report-a-problem-with-visual-studio.md) in Visual Studio. Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/talk-to-us.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Nachricht ist generisch. In der Regel ist eine spezifischere Nachricht in der Fehler Zeichenfolge enthalten, die Ihnen helfen kann, die Ursache des Problems zu identifizieren oder nach einer genaueren Korrektur zu suchen. Im folgenden finden Sie einige der häufigsten Fehlermeldungen, die an die Haupt Fehlermeldung angehängt werden:

- [Der Debugger kann keine Verbindung mit dem Remote Computer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen.](#cannot_connect)
- [Die Verbindungsanforderung wurde vom Remote Debugger abgelehnt.](#rejected)
- [Ungültiger Zugriff auf Speicherort des Speichers](#invalid_access)
- [Auf dem Remote Computer ist kein Server mit dem angegebenen Namen vorhanden.](#no_server)
- [Der angeforderte Name war gültig, aber es wurden keine Daten vom angeforderten Typ gefunden.](#valid_name)
- [Die Visual Studio Remote Debugger auf dem Zielcomputer kann keine Verbindung mit diesem Computer herstellen.](#cant_connect_back)
- [Zugriff verweigert](#access_denied)
- [Ein Sicherheitspaket spezifischer Fehler ist aufgetreten.](#security_package)

## <a name="cannot_connect"></a>Der Debugger kann keine Verbindung mit dem Remote Computer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen.

Führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass Sie einen gültigen Computernamen und eine gültige Portnummer im Dialogfeld **an den Prozess anhängen** oder in den Projekteigenschaften eingeben (Informationen zum Festlegen von Eigenschaften finden Sie in den folgenden [Schritten](#server_incorrect)). Der Computername muss das folgende Format aufweisen:

    `computername:port`

    > [!NOTE]
    > Die Portnummer muss mit der [Portnummer des Remote Debuggers](../debugger/remote-debugger-port-assignments.md)identisch sein, der auf dem Zielcomputer *ausgeführt werden muss* .

2. Wenn der Computername nicht funktioniert, versuchen Sie es stattdessen mit der IP-Adresse und der Portnummer.

3. Stellen Sie sicher, dass die Version des Remote Debuggers, der auf dem Zielcomputer ausgeführt wird, mit Ihrer Version von Visual Studio übereinstimmt. Informationen zum Ermitteln der richtigen Version des Remote [Debuggers](../debugger/remote-debugging.md)finden Sie unter Remote Debugging.

    > [!TIP]
    > Wenn Sie an den Prozess anhängen und eine Verbindung hergestellt haben, der gewünschte Prozess jedoch nicht angezeigt wird, aktivieren Sie das **Kontrollkästchen Prozesse aller Benutzer anzeigen**. Dadurch werden Prozesse angezeigt, wenn eine Verbindung mit einem anderen Benutzerkonto besteht.

4. Wenn dieser Fehler durch diese Schritte nicht behoben werden kann, [ist der Remote Computer nicht erreichbar](#dns).

## <a name="rejected"></a>Die Verbindungsanforderung wurde vom Remote Debugger abgelehnt.

Stellen Sie im Dialogfeld **an den Prozess anhängen** oder in den Projekteigenschaften sicher, dass der Name des Remote Computers und die Portnummer mit dem Namen und der Portnummer übereinstimmen, die im Remote Debugger-Fenster angezeigt werden. Wenn falsch, korrigieren Sie, und versuchen Sie es erneut.

Wenn diese Werte richtig sind und in der Meldung der **Windows-Authentifizierungs** Modus erwähnt wird, überprüfen Sie, ob sich der Remote Debugger im richtigen Authentifizierungsmodus befindet (**Tools > Optionen**).

## <a name="invalid_access"></a>Ungültiger Zugriff auf Speicherort des Speichers

Interner Fehler. Starten Sie Visual Studio neu, und versuchen Sie es erneut.

## <a name="no_server"></a>Auf dem Remote Computer ist kein Server mit dem angegebenen Namen vorhanden.

Visual Studio konnte keine Verbindung mit dem Remote Debugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Der Remote Debugger kann unter einem anderen Benutzerkonto ausgeführt werden. Siehe [die folgenden Schritte](#user_accounts) .

- Der Port wird in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert](#firewall), insbesondere, wenn Sie eine Drittanbieter-Firewall verwenden.

- Die remotedebuggerversion stimmt nicht mit Visual Studio. Informationen zum Ermitteln der richtigen Version des Remote [Debuggers](../debugger/remote-debugging.md)finden Sie unter Remote Debugging.

## <a name="valid_name"></a>Der angeforderte Name war gültig, aber es wurden keine Daten vom angeforderten Typ gefunden.

Der Remote Computer ist vorhanden, aber Visual Studio konnte keine Verbindung mit dem Remote Debugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Ein DNS-Problem verhindert die Verbindung. Weitere [Informationen](#dns)finden Sie hier.

- Der Remote Debugger kann unter einem anderen Benutzerkonto ausgeführt werden. Führen Sie [folgende Schritte](#user_accounts) aus.

- Der Port wird in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert](#firewall), insbesondere, wenn Sie eine Drittanbieter-Firewall verwenden.

- Die remotedebuggerversion stimmt nicht mit Visual Studio. Informationen zum Ermitteln der richtigen Version des Remote [Debuggers](../debugger/remote-debugging.md)finden Sie unter Remote Debugging.

## <a name="cant_connect_back"></a>Die Visual Studio Remote Debugger auf dem Zielcomputer kann keine Verbindung mit diesem Computer herstellen.

Der Remote Debugger kann unter einem anderen Benutzerkonto ausgeführt werden. Öffnen Sie im Remote Debugger **Tools > Berechtigungen** , um den Benutzer den Berechtigungen des Remote Debuggers hinzuzufügen. Weitere Informationen finden Sie [unter unter einem anderen Benutzerkonto wird der Remote Debugger ausgeführt](#user_accounts).

Wenn in der Fehlermeldung auch eine Firewall erwähnt wird, verhindert die Firewall auf dem lokalen Computer möglicherweise die Kommunikation zwischen dem Remote Computer und Visual Studio. Weitere [Informationen](#firewall)finden Sie hier.

## <a name="access_denied"></a> Zugriff verweigert

Dieser Fehler wird möglicherweise angezeigt, wenn Sie versuchen, auf einem Remote Computer mit 64 Bit von einem 32-Bit-Computer zu Debuggen (nicht unterstützt).

## <a name="security_package"></a>Ein Sicherheitspaket spezifischer Fehler ist aufgetreten.

Hierbei kann es sich um ein Legacy Problem handeln, das für Windows XP und Windows 7 spezifisch ist. Weitere [Informationen](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)finden Sie unter.

## <a name="causes-and-recommendations"></a>Gründe und Empfehlungen

### <a name="dns"></a> Der Remotecomputer ist nicht erreichbar

Wenn Sie keine Verbindung mit dem Remote Computernamen herstellen können, versuchen Sie es stattdessen mit der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile auf dem Remote Computer verwenden, um die IPv4-Adresse zu erhalten. Wenn Sie eine Hostdatei verwenden, überprüfen Sie, ob Sie ordnungsgemäß konfiguriert ist.

Wenn dies nicht möglich ist, überprüfen Sie, ob der Remote Computer im Netzwerk erreichbar ist ([Ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) -Befehl an den Remote Computer). Remote Debugging über das Internet wird nicht unterstützt, außer in einigen Microsoft Azure Szenarien.

### <a name="server_incorrect"></a>Der Servername ist falsch, oder die Software von Drittanbietern beeinträchtigt den Remote Debugger.

Überprüfen Sie in Visual Studio die Projekteigenschaften, und stellen Sie sicher, dass der Servername richtig ist. Weitere Informationen finden Sie in den [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)Themen zu [ C# und Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) und. Öffnen Sie für ASP.net abhängig vom Projekttyp **Eigenschaften/Web/Server** oder **Eigenschaften/Debuggen** .

> [!NOTE]
> Wenn Sie an den Prozess anhängen, werden die Remote Einstellungen in den Projekteigenschaften nicht verwendet.

Wenn der Servername richtig ist, blockiert die Antivirensoftware oder eine Drittanbieter-Firewall möglicherweise den Remote Debugger. Beim lokalen Debuggen kann dies passieren, da Visual Studio eine 32-Bit-Anwendung ist. Daher wird die 64-Bit-Version des Remote Debuggers verwendet, um 64-Bit-Anwendungen zu debuggen. Die 32-Bit-und 64-Bit-Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

### <a name="user_accounts"></a> Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt

Der Remote Debugger akzeptiert standardmäßig nur Verbindungen von dem Benutzer, der den Remote Debugger gestartet hat, und die Mitglieder der Gruppe "Administratoren". Zusätzlichen Benutzern müssen explizit Berechtigungen erteilt werden.

Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:

- Fügen Sie den Visual Studio-Benutzer den Berechtigungen des Remote Debuggers hinzu (Klicken Sie im Fenster Remote Debugger auf Extras **> Berechtigungen**).

- Starten Sie den Remote Debugger auf dem Remote Computer unter demselben Benutzerkonto und Kennwort neu, das Sie auf dem Visual Studio-Computer verwenden.

    > [!NOTE]
    > Wenn Sie den Remote Debugger auf einem Remote Server ausführen, klicken Sie mit der rechten Maustaste auf die Remote Debugger-APP, und wählen Sie **als Administrator ausführen** (oder Sie können den Remote Debugger als Dienst ausführen). Wenn Sie Sie nicht auf einem Remote Server ausführen, starten Sie Sie einfach.

- Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<Benutzername>** starten: `msvsmon /allow <username@computer>`.

- Alternativ können Sie allen Benutzern das Remote Debuggen erlauben. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**. Bei der Auswahl von   **Keine Authentifizierung**können Sie **Allen Benutzern das Debugging ermöglichen**aktivieren. Sie sollten diese Option jedoch nur dann ausprobieren, wenn die anderen Optionen fehlschlagen oder wenn Sie sich in einem privaten Netzwerk befinden.

### <a name="firewall"></a> Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Informationen zum Ermitteln der richtigen Version des Remote [Debuggers](../debugger/remote-debugging.md)finden Sie unter Remote Debugging.

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus ändern. Wechseln Sie im Fenster Remote Debugger zum Dialogfeld **Tools > Optionen** .

 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Windows-Netzwerk Sicherheitsrichtlinie finden Sie unter [Sicherheitsrichtlinien Einstellungen](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.

## <a name="more-help"></a>Weitere Hilfe
 Wenn Sie weitere Hilfe zum Remote Debugger benötigen, öffnen Sie die Hilfeseite des Remotedebuggers (**Hilfe >** im Remote Debugger).

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
