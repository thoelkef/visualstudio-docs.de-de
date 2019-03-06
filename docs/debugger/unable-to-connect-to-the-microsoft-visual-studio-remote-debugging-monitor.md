---
title: Keine Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor | Microsoft-Dokumentation
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
ms.openlocfilehash: 95a438c6776e468611a99691c0a4bfea2e4203a5
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953653"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
Diese Meldung kann auftreten, weil der Remotedebugmonitor nicht ordnungsgemäß auf dem Remotecomputer eingerichtet ist oder der Remotecomputer aufgrund von Netzwerkproblemen oder das Vorhandensein einer Firewall nicht mehr verfügbar ist.

> [!IMPORTANT]
>  Wenn Sie glauben, Sie diese Meldung aufgrund eines Produktfehlers erhalten haben dass, wenden Sie [melden Sie das Problem](../ide/how-to-report-a-problem-with-visual-studio.md) zu Visual Studio. Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/talk-to-us.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Nachricht ist generisch. In der Regel eine spezifische Nachricht ist in die Zeichenfolge enthalten, und kann, mit denen Sie die Ursache des Problems oder Suche für eine genauere Problembehebung zu identifizieren. Hier sind einige der häufigeren Fehlermeldungen, die die wichtigsten Fehlermeldung angefügt sind:

- [Der Debugger Verbindung keine mit dem Remotecomputer. Der Debugger konnte der vorgegebene Computername an auflösen](#cannot_connect)
- [Die verbindungsanforderung wurde vom Remotedebugger abgelehnt.](#rejected)
- [Ungültiger Zugriff auf die Speicheradresse](#invalid_access)
- [Es ist kein Server mit dem angegebenen Namen, die auf dem Remotecomputer ausgeführt wird](#no_server)
- [Der angeforderte Name ist gültig, aber keine Daten vom angeforderten Typ gefunden](#valid_name)
- [Visual Studio Remote Debugger auf dem Zielcomputer kann keine rückverbindung mit diesem Computer Verbindung herstellen.](#cant_connect_back)
- [Zugriff verweigert](#access_denied)
- [Ein Paket Fehler aufgetreten ist.](#security_package)

## <a name="cannot_connect"></a> Der Debugger Verbindung keine mit dem Remotecomputer. Der Debugger konnte der vorgegebene Computername an auflösen

Versuchen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie einen gültigen Computernamen eingeben und die Portnummer in das **an den Prozess anhängen** Dialogfeld oder in den Projekteigenschaften (um Eigenschaften festzulegen, finden Sie unter [folgendermaßen](#server_incorrect)). Den Namen des Computers muss das folgende Format:

    `computername:port`

    > [!NOTE]
    > Die Nummer des Ports muss übereinstimmen. die [Portnummer des Remotedebuggers](../debugger/remote-debugger-port-assignments.md), *muss ausgeführt werden,* auf dem Zielcomputer.

2. Wenn Sie den Namen des Computers nicht funktioniert, versuchen Sie die IP-Adresse und Portnummer stattdessen.

3. Stellen Sie sicher, dass die Version des Remotedebuggers auf dem Zielcomputer ausgeführt wird, Ihre Version von Visual Studio entspricht. Rufen Sie die richtige Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

    > [!TIP]
    > Wenn Sie an den Prozess anfügen, und Sie erfolgreich verbinden können jedoch nicht den gewünschten Prozess angezeigt, wählen Sie die **Prozesse Kontrollkästchen für alle Benutzer anzeigen**. Dadurch werden die Prozesse angezeigt, wenn Sie sich unter einem anderen Benutzerkonto verbunden sind.

4. Wenn dieser Fehler mit diesen Schritten nicht beheben lässt, finden Sie unter [der Remotecomputer ist nicht erreichbar](#dns).

## <a name="rejected"></a> Die verbindungsanforderung wurde vom Remotedebugger abgelehnt.

In der **an den Prozess anhängen** Dialogfeld ein, oder in den Projekteigenschaften, stellen Sie sicher, dass die Namen des Remotecomputers ein, und die Nummer des Ports eine Übereinstimmung mit den Namen und die Portnummer Zahl im Remotedebugger-Fenster angezeigt. Wenn falsch ist, zu beheben, und versuchen Sie es erneut.

Wenn diese Werte korrekt sind und die Nachricht wird **Windows-Authentifizierung** Modus, überprüfen Sie, ob der Remotedebugger im Modus erforderliche Authentifizierung (**Tools > Optionen**).

## <a name="invalid_access"></a> Ungültiger Zugriff auf die Speicheradresse

Interner Fehler. Visual Studio neu starten, und versuchen Sie es noch mal.

## <a name="no_server"></a> Es ist kein Server mit dem angegebenen Namen, die auf dem Remotecomputer ausgeführt wird

Visual Studio konnte keine mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Finden Sie unter [Schritten](#user_accounts)

- Der Port ist in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [nicht blockiert Ihre Anforderung](#firewall), insbesondere, wenn Sie eine Drittanbieter Firewall verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Rufen Sie die richtige Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md)


## <a name="valid_name"></a> Der angeforderte Name ist gültig, aber keine Daten vom angeforderten Typ gefunden

Der Remotecomputer vorhanden ist, aber Visual Studio konnte keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Ein DNS-Problem verhindert, dass die Verbindung. Finden Sie unter [folgendermaßen](#dns).

- Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Führen Sie [folgende Schritte](#user_accounts) aus.

- Der Port ist in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [nicht blockiert Ihre Anforderung](#firewall), insbesondere, wenn Sie eine Drittanbieter Firewall verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Rufen Sie die richtige Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Visual Studio Remote Debugger auf dem Zielcomputer kann keine rückverbindung mit diesem Computer Verbindung herstellen.

Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Öffnen Sie in dem Remotedebugger **Extras > Berechtigungen** der Benutzer den remotedebuggerberechtigungen hinzu. Weitere Informationen finden Sie unter [der Remotedebugger unter einem anderen Benutzerkonto ausgeführt wird](#user_accounts).

Wenn die Fehlermeldung auch eine Firewall erwähnt, kann die Firewall auf dem lokalen Computer vom Remotecomputer zurück zu Visual Studio verhindert die Kommunikation. Finden Sie unter [folgendermaßen](#firewall).

## <a name="access_denied"></a> Zugriff verweigert

Dieser Fehler kann angezeigt werden, wenn Sie versuchen, das Debuggen auf einem 64-Bit-Remotecomputer von einem 32-Bit-Computer (nicht unterstützt).

## <a name="security_package"></a> Ein Paket Fehler aufgetreten ist.

Dies ist möglicherweise eine ältere Problem, das speziell für Windows XP und Windows 7. Finden Sie in diesem [Informationen](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Ursachen und Empfehlungen

### <a name="dns"></a> Der Remotecomputer ist nicht erreichbar

Wenn Sie eine Verbindung nicht mit dem Namen des Remotecomputers herstellen können, versuchen Sie es stattdessen mit der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile auf dem Remotecomputer, um die IPv4-Adresse zu erhalten. Wenn Sie eine Datei "HOSTS" verwenden, stellen Sie sicher, dass er richtig konfiguriert ist.

Wenn dies fehlschlägt, stellen Sie sicher, dass der Remotecomputer im Netzwerk verfügbar ist ([Ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) den Remotecomputer). Remotedebuggen über das Internet wird nicht unterstützt, außer in einigen Szenarien für Microsoft Azure.

### <a name="server_incorrect"></a> Der Servername ist falsch oder Drittanbieter-Software beeinträchtigt wird, mit dem Remotedebugger

Sehen Sie in Visual Studio sich die Projekteigenschaften, und stellen Sie sicher, dass der Servername richtig ist. Finden Sie in Themen [ C# und Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) und [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Öffnen Sie für ASP.NET **Eigenschaften / Web / Servern** oder **Eigenschaften / Debug** je nach Projekttyp.

> [!NOTE]
> Wenn Sie an den Prozess anfügen, werden die Einstellungen des remote in den Projekteigenschaften nicht verwendet werden.

Wenn der Servername richtig ist, kann Ihre Antivirensoftware oder einer Drittanbieter-Firewall des Remotedebuggers blockieren. Wenn Sie lokal debuggen, kann dies passieren, wenn Visual Studio eine 32-Bit-Anwendung ist, und die 64-Bit-Version des Remotedebuggers zum Debuggen von 64-Bit-Anwendungen verwendet. Die 32-Bit- und 64-Bit-Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

### <a name="user_accounts"></a> Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt

Der Remotedebugger, in der Standardeinstellung nur akzeptiert Verbindungen von der Benutzer, der dem Remotedebugger und den Mitgliedern der Gruppe "Administratoren" gestartet hat. Zusätzliche Benutzern müssen explizit Berechtigungen gewährt werden.

Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:

-   Fügen Sie den Visual Studio-Benutzer, die Berechtigungen des Remotedebuggers (Wählen Sie im Remotedebugger-Fenster, **Extras > Berechtigungen**).

-   Auf dem Remotecomputer neu starten des Remotedebuggers unter dem gleichen Benutzerkonto und Kennwort, das Sie auf dem Visual Studio-Computer verwenden.

    > [!NOTE]
    > Wenn Sie den Remotedebugger auf einem Remoteserver ausführen, mit der rechten Maustaste in der Remote Debugger-app, und wählen Sie **als Administrator ausführen** (oder Sie können den Remotedebugger als Dienst ausführen). Wenn Sie Sie nicht auf einem Remoteserver ausgeführt werden, starten Sie es normalerweise.

-   Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<Benutzername>** starten: `msvsmon /allow <username@computer>`.

-   Alternativ können Sie allen Benutzern das Remotedebuggen erlauben. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**. Bei der Auswahl von   **Keine Authentifizierung**können Sie **Allen Benutzern das Debugging ermöglichen**aktivieren. Allerdings sollten Sie diese Option nur, wenn die anderen Optionen fehlschlagen oder wenn Sie sich in einem privaten Netzwerk befinden.

### <a name="firewall"></a> Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Rufen Sie die richtige Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus ändern. Navigieren Sie im Remotedebugger-Fenster, zu der **Tools > Optionen** Dialogfeld.

 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Sicherheitsrichtlinie für Windows-Netzwerke finden Sie unter [sicherheitsrichtlinieneinstellungen](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.

## <a name="more-help"></a>Weitere Hilfe
 Um mehr remote Debugger-Hilfe zu erhalten, öffnen Sie den Remotedebugger-Hilfeseite (**Hilfe > Verwendung** in den Remotedebugger).

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
