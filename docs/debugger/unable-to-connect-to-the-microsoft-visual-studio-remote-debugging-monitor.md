---
title: Es kann keine Verbindung mit dem Microsoft Visual Studio Remote-Debuggingmonitor hergestellt werden | Microsoft Docs
ms.date: 04/14/2020
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
ms.openlocfilehash: d6173d6b3525a1bd723bc859d34b889b3796d295
ms.sourcegitcommit: c3b92a9912a5816f16c6059d1738dbc833851346
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81397375"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
Diese Meldung kann auftreten, weil der Remote-Debuggingmonitor auf dem Remotecomputer nicht ordnungsgemäß eingerichtet ist oder auf den Remotecomputer aufgrund von Netzwerkproblemen oder dem Vorhandensein einer Firewall nicht zugegriffen werden kann.

> [!IMPORTANT]
> Wenn Sie der Meinung sind, dass Sie diese Meldung aufgrund eines Produktfehlers erhalten haben, melden Sie [dieses Problem](../ide/how-to-report-a-problem-with-visual-studio.md) an Visual Studio. Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/feedback-options.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Was ist die detaillierte Fehlermeldung?

Die `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Nachricht ist generisch. In der Regel ist eine spezifischere Meldung in der Fehlerzeichenfolge enthalten, die Ihnen helfen kann, die Ursache des Problems zu identifizieren oder nach einer genaueren Lösung zu suchen. Hier sind einige der häufigsten Fehlermeldungen, die an die Hauptfehlermeldung angehängt werden:

- [Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen.](#cannot_connect)
- [Die Verbindungsanforderung wurde vom Remotedebugger abgelehnt.](#rejected)
- [Die Verbindung mit dem Remoteendpunkt wurde beendet.](#connection_terminated)
- [Ungültiger Zugriff auf den Speicherort](#invalid_access)
- [Es gibt keinen Server mit dem angegebenen Namen, der auf dem Remotecomputer ausgeführt wird.](#no_server)
- [Der angeforderte Name war gültig, es wurden jedoch keine Daten des angeforderten Typs gefunden.](#valid_name)
- [Der Visual Studio Remote-Debugger auf dem Zielcomputer kann keine Verbindung zu diesem Computer herstellen.](#cant_connect_back)
- [Zugriff verweigert](#access_denied)
- [Ein Sicherheitspaket-spezifischer Fehler ist aufgetreten.](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen.

Führen Sie die folgenden Schritte aus:

1. Stellen Sie sicher, dass Sie einen gültigen Computernamen und eine gültige Portnummer im Dialogfeld **An Prozess anfügen** oder in den Projekteigenschaften eingeben (Um Eigenschaften festzulegen, lesen Sie [diese Schritte](#server_incorrect)). Der Computername muss das folgende Format haben:

    `computername:port`

    > [!NOTE]
    > Die Portnummer muss mit der [Portnummer des Remotedebuggers](../debugger/remote-debugger-port-assignments.md)übereinstimmen, der auf dem Zielcomputer *ausgeführt werden muss.*

2. Wenn der Computername nicht funktioniert, versuchen Sie stattdessen die IP-Adresse und die Portnummer.

3. Stellen Sie sicher, dass die Version des Remotedebuggers, der auf dem Zielcomputer ausgeführt wird, mit Ihrer Version von Visual Studio übereinstimmt. Informationen zur richtigen Version des Remotedebuggers finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).

    > [!TIP]
    > Wenn Sie eine Verbindung zum Prozess herstellen und eine verbindung erfolgreich herstellen, aber den gewünschten Prozess nicht sehen, aktivieren Sie das **Kontrollkästchen Prozesse aller Benutzer anzeigen**. Dadurch werden Prozesse angezeigt, wenn Sie unter einem anderen Benutzerkonto verbunden sind.

4. Wenn dieser Fehler durch diese Schritte nicht behoben wird, finden Sie weitere Informationen unter [Der Remotecomputer ist nicht erreichbar.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>Die Verbindungsanforderung wurde vom Remotedebugger abgelehnt.

Stellen Sie im Dialogfeld **"An Prozess anfügen"** oder in den Projekteigenschaften sicher, dass der Name des Remotecomputers und die Portnummer mit dem Namen und der Portnummer übereinstimmen, die im Remotedebuggerfenster angezeigt werden. Wenn falsch, beheben Sie, und versuchen Sie es erneut.

Wenn diese Werte korrekt sind und die Meldung den **Windows-Authentifizierungsmodus** erwähnt, überprüfen Sie, ob sich der Remotedebugger im richtigen Authentifizierungsmodus befindet (**Tools > Options**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>Die Verbindung mit dem Remoteendpunkt wurde beendet.

Wenn Sie eine Azure App Service-App debuggen, verwenden Sie den Befehl [Debugger anfügen](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) aus Cloud Explorer oder Server Explorer anstelle von **Anfügen an den Prozess**.

Wenn Sie **zum Debuggen an den Prozess anfügen** verwenden:

- Stellen Sie im Dialogfeld **"An Prozess anfügen"** oder in den Projekteigenschaften sicher, dass der Name des Remotecomputers und die Portnummer mit dem Namen und der Portnummer übereinstimmen, die im Remotedebuggerfenster angezeigt werden. Wenn falsch, beheben Sie, und versuchen Sie es erneut.

- Wenn Sie versuchen, eine Verbindung mit einem Hostnamen herzustellen, versuchen Sie es stattdessen mit einer IP-Adresse.

- Überprüfen Sie das Anwendungsprotokoll auf dem Server (Ereignisanzeige unter Windows), um detailliertere Informationen zu erhalten, um das Problem zu beheben.

- Versuchen Sie andernfalls, Visual Studio mit Administratorrechten neu zu starten, und versuchen Sie es dann erneut.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Ungültiger Zugriff auf den Speicherort

Ein interner Fehler ist aufgetreten. Starten Sie Visual Studio neu, und wiederholen Sie den Vorgang.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Es gibt keinen Server mit dem angegebenen Namen, der auf dem Remotecomputer ausgeführt wird.

Visual Studio konnte keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus mehreren Gründen auftreten:

- Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Sehen Sie [sich diese Schritte an](#user_accounts)

- Der Port ist auf der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert,](#firewall)insbesondere wenn Sie eine Firewall eines Drittanbieters verwenden.

- Die Remotedebuggerversion stimmt nicht mit Visual Studio überein. Informationen zur richtigen Version des Remotedebuggers finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>Der angeforderte Name war gültig, es wurden jedoch keine Daten des angeforderten Typs gefunden.

Der Remotecomputer ist vorhanden, Visual Studio konnte jedoch keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus mehreren Gründen auftreten:

- Ein DNS-Problem verhindert die Verbindung. Sehen Sie sich [diese Schritte an.](#dns)

- Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Führen Sie [die folgenden Schritte aus.](#user_accounts)

- Der Port ist auf der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert,](#firewall)insbesondere wenn Sie eine Firewall eines Drittanbieters verwenden.

- Die Remotedebuggerversion stimmt nicht mit Visual Studio überein. Informationen zur richtigen Version des Remotedebuggers finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Der Visual Studio Remote-Debugger auf dem Zielcomputer kann keine Verbindung zu diesem Computer herstellen.

Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Öffnen Sie im Remotedebugger **Tools > Berechtigungen,** um den Benutzer zu den Berechtigungen des Remotedebuggers hinzuzufügen. Weitere Informationen finden Sie unter [Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt.](#user_accounts)

Wenn in der Fehlermeldung auch eine Firewall erwähnt wird, verhindert die Firewall auf dem lokalen Computer möglicherweise die Kommunikation vom Remotecomputer zurück zu Visual Studio. Sehen Sie sich [diese Schritte an.](#firewall)

## <a name="access-denied"></a><a name="access_denied"></a>Zugriff verweigert

Dieser Fehler wird möglicherweise angezeigt, wenn Sie versuchen, auf einem 64-Bit-Remotecomputer von einem 32-Bit-Computer (nicht unterstützt) zu debuggen.

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Ein Sicherheitspaket-spezifischer Fehler ist aufgetreten.

Dies kann ein älteres Problem sein, das speziell für Windows XP und Windows 7 gilt. Siehe diese [Informationen](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Ursachen und Empfehlungen

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>Die Remote-Maschine ist nicht erreichbar

Wenn Sie keine Verbindung mit dem Namen des Remotecomputers herstellen können, verwenden Sie stattdessen die IP-Adresse. Sie können `ipconfig` in einer Befehlszeile auf dem Remotecomputer die IPv4-Adresse abrufen. Wenn Sie eine HOSTS-Datei verwenden, stellen Sie sicher, dass sie richtig konfiguriert ist.

Wenn dies fehlschlägt, stellen Sie sicher, dass auf den Remotecomputer im Netzwerk zugegriffen werden kann[(Ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) des Remotecomputers). Remote-Debugging über das Internet wird nicht unterstützt, außer in einigen Microsoft Azure-Szenarien.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>Der Servername ist falsch, oder Software von Drittanbietern stört den Remotedebugger

Sehen Sie sich in Visual Studio die Projekteigenschaften an, und stellen Sie sicher, dass der Servername korrekt ist. Weitere Informationen finden Sie unter Themen für [C- und Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) und [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Öffnen Sie für ASP.NET **Eigenschaften / Web / Server** oder Eigenschaften / **Debug,** abhängig von Ihrem Projekttyp.

> [!NOTE]
> Wenn Sie an den Prozess anfügen, werden die Remoteeinstellungen in den Projekteigenschaften nicht verwendet.

Wenn der Servername korrekt ist, blockiert die Antivirensoftware oder eine Firewall eines Drittanbieters möglicherweise den Remotedebugger. Beim lokalen Debuggen kann dies passieren, da Visual Studio eine 32-Bit-Anwendung ist, sodass die 64-Bit-Version des Remotedebuggers zum Debuggen von 64-Bit-Anwendungen verwendet wird. Die 32-Bit- und 64-Bit-Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt.

Der Remotedebugger akzeptiert standardmäßig nur Verbindungen von dem Benutzer, der den Remotedebugger gestartet hat, und Mitgliedern der Gruppe Administratoren. Zusätzlichen Benutzern müssen explizit Berechtigungen erteilt werden.

Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:

- Fügen Sie den Visual Studio-Benutzer den Berechtigungen des Remote-Debuggers hinzu (wählen Sie im Remotedebuggerfenster **Tools > Permissions**aus).

- Starten Sie auf dem Remotecomputer den Remotedebugger unter demselben Benutzerkonto und Kennwort neu, das Sie auf dem Visual Studio-Computer verwenden.

    > [!NOTE]
    > Wenn Sie den Remotedebugger auf einem Remoteserver ausführen, klicken Sie mit der rechten Maustaste auf die Remote-Debugger-App, und wählen Sie **Als Administrator ausführen** (oder Sie können den Remotedebugger als Dienst ausführen). Wenn Sie es nicht auf einem Remoteserver ausführen, starten Sie es einfach normal.

- Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<Benutzername>** starten: `msvsmon /allow <username@computer>`.

- Alternativ können Sie jedem Benutzer Remote-Debugging erlauben. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**. Bei der Auswahl von   **Keine Authentifizierung**können Sie **Allen Benutzern das Debugging ermöglichen**aktivieren. Sie sollten diese Option jedoch nur ausprobieren, wenn die anderen Optionen fehlschlagen oder wenn Sie sich in einem privaten Netzwerk befinden.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Informationen zur richtigen Version des Remotedebuggers finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus ändern. Wechseln Sie im Fenster des Remote-Debuggers zum Dialogfeld **Tools > Options.**

 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Windows-Netzwerksicherheitsrichtlinie finden Sie unter [Sicherheitsrichtlinieneinstellungen](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.

## <a name="more-help"></a>Weitere Hilfe
 Um weitere Hilfe für Remotedebugger zu erhalten, öffnen Sie die Hilfeseite des Remotedebuggers **(Hilfe > Verwendung** im Remotedebugger).

## <a name="see-also"></a>Weitere Informationen
- [Remote-Debugging](../debugger/remote-debugging.md)
