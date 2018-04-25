---
title: Keine Verbindung zu der Microsoft Visual Studio-Remotedebugmonitor | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5b7af9c41aac0531a9af014a49e9e0a1e71763d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor mit dem Namen "" konnte nicht hergestellt werden
Diese Meldung kann auftreten, da der Remotedebugmonitor nicht ordnungsgemäß auf dem Remotecomputer eingerichtet ist oder der Remotecomputer aufgrund von Netzwerkproblemen bzw. wegen einer Firewall nicht zugegriffen werden ist.
  
> [!IMPORTANT]
>  Wenn Sie glauben, Sie diese Meldung aufgrund eines Produktfehlers erhalten haben dass, wenden [melden Sie dieses Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) zu Visual Studio. Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/talk-to-us.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="specificerrors"></a>Was ist die ausführliche Fehlermeldung?

Die `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Nachricht ist generisch. In der Regel ist eine spezifische Nachricht in die Fehlerzeichenfolge enthalten, und, die können Sie die Ursache des Problems oder Suche für eine genauere Korrektur zu identifizieren. Hier sind einige der häufigsten Fehlermeldungen, die die wichtigsten Fehlermeldung angefügt sind:

- [Der Debugger kann keine Verbindung mit dem Remotecomputer hergestellt werden. Der Debugger konnte den angegebenen Computernamen auflösen](#cannot_connect)
- [Verbindungsanforderung wurde von der Remotedebugger zurückgewiesen.](#rejected)
- [Ungültigen Zugriff auf die Speicheradresse](#invalid_access)
- [Es ist kein Server mit dem angegebenen Namen, die auf dem Remotecomputer ausgeführt wird](#no_server)
- [Name des angeforderten war ungültig, aber es wurde keine Daten des angeforderten Typs gefunden.](#valid_name)
- [Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann nicht erneut mit diesem Computer herstellen.](#cant_connect_back)
- ["Zugriff verweigert"](#access_denied)
- [Eine bestimmte Paketfehler aufgetreten ist](#security_package)

## <a name="cannot_connect"></a> Der Debugger kann keine Verbindung mit dem Remotecomputer hergestellt werden. Der Debugger konnte den angegebenen Computernamen auflösen

Probieren Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie geben Sie einen gültigen Computernamen ein, und die Portnummer in das **an den Prozess anhängen** Dialogfeld oder in den Projekteigenschaften (um Eigenschaften festzulegen, finden Sie unter [Schritte](#server_incorrect)). Der Computername muss das folgende Format:

    `computername:port`

    > [!NOTE]
    > Die Nummer des Ports muss übereinstimmen. die [Portnummer des Remotedebuggers](../debugger/remote-debugger-port-assignments.md), welche *muss ausgeführt werden,* auf dem Zielcomputer.

2. Wenn der Computername nicht funktioniert, versuchen Sie die IP-Adresse und Portnummer stattdessen.

3. Stellen Sie sicher, dass die Version des Remotedebuggers auf dem Zielcomputer ausgeführt wird, Ihre Version von Visual Studio entspricht. Um die richtige Version des Remotedebuggers zu erhalten, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

    > [!TIP]
    > Wenn Sie an den Prozess anfügen und Sie eine Verbindung herstellen erfolgreich, jedoch nicht den gewünschten Prozess angezeigt, wählen Sie die **Prozesse Kontrollkästchen für alle Benutzer anzeigen**. Es werden die Prozesse angezeigt, wenn Sie sich unter einem anderen Benutzerkonto verbunden sind.

4. Wenn diese Schritte nicht diesen Fehler beheben, finden Sie unter [der Remotecomputer ist nicht erreichbar](#dns).

## <a name="rejected"></a> Verbindungsanforderung wurde von der Remotedebugger zurückgewiesen.

In der **an den Prozess anhängen** Dialogfeld Feld oder in den Projekteigenschaften, stellen Sie sicher, dass den Remotecomputernamen und die Portnummer stimmt die Namen und die Portnummer im Remotedebugger-Fenster angezeigt. Wenn falsch ist, zu beheben Sie, und wiederholen Sie den Vorgang.

Wenn diese Werte korrekt sind und die Nachricht erwähnt **Windows-Authentifizierung** Modus, überprüfen Sie, dass der Remotedebugger in der richtigen Authentifizierungsmodus (**Tools > Optionen**).

## <a name="invalid_access"></a> Ungültigen Zugriff auf die Speicheradresse

Interner Fehler. Starten Sie Visual Studio neu, und wiederholen Sie den Vorgang.

## <a name="no_server"></a> Es ist kein Server mit dem angegebenen Namen, die auf dem Remotecomputer ausgeführt wird

Visual Studio konnte nicht mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Finden Sie unter [Schritte](#user_accounts)

- Der Port ist in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [nicht blockiert Ihre Anforderung](#firewall), insbesondere, wenn Sie eine Drittanbieter-Firewall verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Um die richtige Version des Remotedebuggers zu erhalten, finden Sie unter [des Remotedebuggens](../debugger/remote-debugging.md)


## <a name="#valid_name"></a> Name des angeforderten war ungültig, aber es wurde keine Daten des angeforderten Typs gefunden.

Der Remotecomputer ist vorhanden, aber Visual Studio konnte keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Ein DNS-Problem verhindert, dass die Verbindung. Finden Sie unter [Schritte](#dns).

- Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Führen Sie die [Schritte](#user_accounts).

- Der Port ist in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [nicht blockiert Ihre Anforderung](#firewall), insbesondere, wenn Sie eine Drittanbieter-Firewall verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Um die richtige Version des Remotedebuggers zu erhalten, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann nicht erneut mit diesem Computer herstellen.

Der Remotedebugger kann unter einem anderen Benutzerkonto ausgeführt werden. Öffnen Sie den Remotedebugger **Extras > Berechtigungen** beim Hinzufügen des Benutzers, den Remotedebugger-Berechtigungen. Weitere Informationen finden Sie unter [der Remotedebugger unter einem anderen Benutzerkonto ausgeführt wird](#user_accounts).

Wenn die Fehlermeldung auch eine Firewall erwähnt, kann die Firewall auf dem lokalen Computer zurück zu Visual Studio-Kommunikation mit dem Remotecomputer verhindern. Finden Sie unter [Schritte](#firewall).

## <a name="access_denied"></a> "Zugriff verweigert"

Dieser Fehler kann angezeigt werden, wenn Sie versuchen, das Debuggen auf einem 64-Bit-Remotecomputer von einem 32-Bit-Computer (nicht unterstützt).

## <a name="security_package"></a> Eine bestimmte Paketfehler aufgetreten ist

Dies ist möglicherweise eine ältere Problem speziell für Windows XP und Windows 7. Lesen Sie diese [Informationen](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Ursachen und Empfehlungen

### <a name="dns"></a> Der Remotecomputer ist nicht erreichbar 

Wenn Sie mit dem Namen der remote-Computer herstellen können, versuchen Sie es stattdessen mit der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile auf dem Remotecomputer die IPv4-Adresse abrufen. Wenn Sie eine HOSTS-Datei verwenden, stellen Sie sicher, dass er ordnungsgemäß konfiguriert ist.

Wenn dies fehlschlägt, stellen Sie sicher, dass der Remotecomputer im Netzwerk verfügbar ist ([Ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx) Remotecomputer). Remotedebuggen über das Internet wird nicht unterstützt, außer in einigen Szenarien für die Microsoft Azure.
  
### <a name="server_incorrect"></a> Der Servername ist falsch oder Drittanbieter-Software wird der Remotedebugger stören

Klicken Sie in Visual Studio sehen Sie sich die Projekteigenschaften, und stellen Sie sicher, dass der Servername richtig ist. Finden Sie in Themen [(c# und Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) und [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Öffnen Sie für ASP.NET, **Eigenschaften / Web / Server** oder **Eigenschaften / Debug** Abhängigkeit vom Projekttyp.

> [!NOTE]
> Wenn Sie an den Prozess anfügen, werden die Einstellungen des remote in den Projekteigenschaften nicht verwendet.

Wenn der Servername korrekt ist, kann Ihrer Antivirussoftware oder einer Drittanbieter-Firewall, den Remotedebugger blockiert. Beim lokalen Debuggen, kann dies folgende Ursachen Visual Studio eine 32-Bit-Anwendung ist, damit sie die 64-Bit-Version des Remotedebuggers Debuggen von 64-Bit-Anwendungen verwendet. Die 32-Bit und 64-Bit-Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

### <a name="user_accounts"></a> Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt. 

Der Remotedebugger, wird standardmäßig nur akzeptiert Verbindungen von der Benutzer, der dem Remotedebugger und Mitglied der Gruppe "Administratoren" gestartet hat. Zusätzliche Benutzern müssen explizit Berechtigungen erteilt werden. 
 
Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:  

-   Fügen Sie den Visual Studio-Benutzer mit Berechtigungen für den Remotedebugger (Wählen Sie im Remotedebugger-Fenster **Extras > Berechtigungen**).

-   Starten Sie den Remotedebugger unter dem gleichen Benutzerkonto und Kennwort, mit dem Sie auf dem Visual Studio-Computer, neu, auf dem Remotecomputer.

    > [!NOTE]
    > Wenn Sie den Remotedebugger auf einem Remoteserver ausgeführt werden, mit der rechten Maustaste den Remotedebugger-app, und wählen Sie **als Administrator ausführen** (oder Sie können den Remotedebugger als Dienst ausführen). Wenn Sie Sie nicht auf einem Remoteserver ausgeführt werden, starten Sie es normalerweise.
  
-   Sie können den Remotedebugger starten, über die Befehlszeile mit der **/ allow \<Benutzername >** Parameter: `msvsmon /allow <username@computer>`. 
  
-   Alternativ können Sie allen Benutzern das Remotedebuggen erlauben. Wechseln Sie im Remotedebugger-Fenster, um die **Tools > Optionen** Dialogfeld. Bei der Auswahl von   **Keine Authentifizierung**können Sie **Allen Benutzern das Debugging ermöglichen**aktivieren. Allerdings sollten Sie diese Option nur, wenn die anderen Optionen fehl, oder wenn Sie in einem privaten Netzwerk können.

### <a name="firewall"></a> Die Firewall auf dem Remotecomputer zuzulassen keine eingehende Verbindungen mit dem Remotedebugger.  
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers entspricht nicht die Version von Visual Studio  
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Um die richtige Version des Remotedebuggers zu erhalten, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf  
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus ändern. Wechseln Sie im Remotedebugger-Fenster, um die **Tools > Optionen** (Dialogfeld).
  
 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](https://technet.microsoft.com/en-us/library/hh831472.aspx).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert  
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio  
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zu Windows-Netzwerksicherheitsrichtlinie, finden Sie unter [sicherheitsrichtlinieneinstellungen](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen  
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.  
  
## <a name="more-help"></a>Weitere Hilfe  
 Um mehr remote Debugger-Hilfe zu erhalten, öffnen Sie den Remotedebugger-Hilfeseite (**Hilfe > Verwendung** in den Remotedebugger).
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)