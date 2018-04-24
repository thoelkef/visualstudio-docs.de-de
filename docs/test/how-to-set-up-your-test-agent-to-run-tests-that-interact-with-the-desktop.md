---
title: Konfigurieren eines Visual Studio-Test-Agents zum Ausführen von Tests, die mit dem Desktop interagieren | Microsoft-Dokumentation
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 27b1024c1384e70f7b49765b5d079a72a3726818
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>How to: Set Up Your Test Agent to Run Tests that Interact with the Desktop

Wenn Sie automatisierte Tests ausführen möchten, die mit dem Desktop interagieren, müssen Sie den Agent für die Ausführung als Prozess statt als Dienst konfigurieren. Wenn Sie z. B. einen Test der programmierten UI mithilfe eines Testcontrollers und eines Test-Agents remote ausführen möchten oder einen Test ausführen und während der Ausführung eine Videoaufzeichnung erfassen möchten, müssen Sie den Agent für die Ausführung als Prozess einrichten. Wenn Sie mithilfe von Microsoft Test Manager in den Testeinstellungen oder mithilfe von Visual Studio in der Umgebung den Rollen Agents zuweisen, müssen Sie die Einrichtung für alle Agents ändern, die Rollen zugewiesen sind, die mit dem Desktop interagieren.

> [!WARNING]
> Wenn Sie Microsoft Test Manager zum Einrichten einer Laborumgebung verwenden, wird der Test-Agent installiert. Sie können im Assistenten für die Umgebungserstellung angeben, dass Sie eine der Rollen zur Ausführung von Tests der programmierten UI konfigurieren möchten.

> [!IMPORTANT]
> Der Computer mit dem Agent, auf dem Sie Tests der programmierten UI ausführen möchten, darf nicht gesperrt sein und über keinen aktiven Bildschirmschoner verfügen.

Wenn Sie Tests der codierten UI ausführen, die einen Browser starten, wird zum Starten des Browsers das Dienstkonto für den Test-Agent verwendet. Dieses Dienstkonto muss mit dem Benutzerkonto des aktiven Benutzers auf diesem Computer identisch sein. Wenn es sich nicht um das gleiche Benutzerkonto handelt, wird der Browser nicht gestartet.

> [!IMPORTANT]
> Wenn Sie einen Test der codierten UI ausführen, der einen Browser als Teil einer Builddefnition startet, wird zum Starten dieses Browsers das Dienstkonto für den Builddienst verwendet. Dieses Dienstkonto muss mit dem Benutzerkonto des aktiven Benutzers auf diesem Computer identisch sein. Wenn es sich nicht um das gleiche Benutzerkonto handelt, wird der Browser nicht gestartet.

 Gehen Sie wie folgt vor, um Agents einzurichten, die einer Rolle zugewiesen sind, die eine Interaktion mit dem Desktop erfordernde Aufgabe ausführt.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>So richten Sie einen Agent für die Ausführung als Prozess ein

1.  Navigieren Sie zum Konfigurieren des von Ihnen installierten Test-Agents, damit er als Prozess ausgeführt wird, zu **Start**, **Alle Programme**, **Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent-Konfigurationstool**.

     Das Dialogfeld **Test-Agent konfigurieren** wird angezeigt.

2.  Zum Anzeigen der Seite, auf der Sie die Ausführung als Prozess auswählen können, Klicken Sie auf **Ausführungsoptionen**.

     Die Seite wird angezeigt, auf der Sie auswählen können, ob der Agent als Prozess oder Dienst ausgeführt wird.

3.  Wählen Sie **Interaktiver Prozess** aus. Der Test-Agent wird als Prozess statt als Dienst gestartet. Wählen Sie **Weiter** aus.

     Sie können jetzt die Details für den Benutzer, der beim Starten des Test-Agents als Prozess verwendet werden soll, und für weitere Optionen eingeben.

    > [!NOTE]
    > Der Benutzer, den Sie zum Starten des Prozesses hinzufügen, muss auch als Mitglied der Gruppe TeamTestAgentService auf dem Computer des Testcontrollers für diesen Agent hinzugefügt werden. Wenn dieser Benutzer der aktuelle Benutzer ist und Sie dem Testcontrollercomputer diesen Benutzer hinzufügen, müssen Sie sich abmelden oder diesen Computer neu starten.

4.  Geben Sie in **Benutzername** den Namen ein.

5.  Geben Sie in **Kennwort** das Kennwort ein.

     **Wichtige Benutzerkontoinformationen:**

    -   NULL-Kennwörter werden für Benutzerkonten nicht unterstützt.

    -   Wenn Sie den Datenadapter und Adapter für diagnostische Daten für IntelliTrace oder die Netzwerkemulation verwenden möchten, muss das Benutzerkonto Mitglied der Gruppe "Administratoren" sein. Wenn der Computer, auf dem der Test-Agent ausgeführt wird, ein Betriebssystem verwendet, das ein Benutzerkonto mit den geringsten Berechtigungen hat, müssen Sie es ebenfalls als Administrator (erhöht) ausführen. Wenn der Agent-Benutzername nicht im Agent-Dienst vorhanden ist, wird er hinzugefügt. Dafür sind Berechtigungen für den Testcontroller erforderlich.

    -   Der Benutzer, der den Testcontroller verwenden möchte, muss im Benutzerkonto des Testcontrollers angemeldet sein. Andernfalls können die Tests nicht anhand des Controllers ausgeführt werden.

6.  Um sicherzustellen, dass ein Computer mit einem Test-Agent nach dem Neustart Tests ausführen kann, können Sie den Computer für die automatische Anmeldung als Test-Agent-Benutzer einrichten. Klicken Sie auf **Automatisch anmelden**. Dadurch werden der Benutzername und das Kennwort in verschlüsselter Form in der Registrierung gespeichert.

    > [!NOTE]
    > Wenn Sie die Verbindung mit der Lab-Umgebung über einen Remotedesktop oder eine Gast-basierte Verbindung hergestellt haben, ist es möglich, dass diese häufig und unerwartet getrennt wird. Eine mögliche Ursache des Verbindungsverlusts besteht darin, dass der Computer für die automatische Anmeldung am Netzwerk konfiguriert ist.

7.  Um sicherzustellen, dass der Bildschirmschoner deaktiviert ist, wählen Sie **Sicherstellen, dass Bildschirmschoner deaktiviert ist**aus, da andernfalls automatisierte Tests, die mit dem Desktop interagieren müssen, behindert werden können.

    > [!WARNING]
    > Durch die automatische Anmeldung und das Deaktivieren des Bildschirmschoners entstehen Sicherheitsrisiken. Wenn Sie die automatische Anmeldung aktivieren, ermöglichen Sie es anderen Benutzern, den betreffenden Computer zu starten und das Konto zu verwenden, das automatisch angemeldet wird. Wenn Sie den Bildschirmschoner deaktivieren, wird der Benutzer möglicherweise nicht aufgefordert, sich anzumelden, um die Sperre des Computers aufzuheben. So kann jede Person mit physischem Zugang zum Computer auf den Computer zugreifen. Wenn Sie diese Funktionen auf einem Computer aktivieren, sollten Sie sicherstellen, dass der Computer physikalisch sicher ist. Ein solcher Computer befindet sich z. B. in einem physikalisch sicheren Labor. Durch Deaktivieren des Kontrollkästchens **Sicherstellen, dass der Bildschirmschoner deaktiviert ist** wird der Bildschirmschoner nicht aktiviert.

     Zum Ausführen des Agents als Dient, können Sie dieses Tool verwenden und **Dienst** auswählen.

8.  Klicken Sie auf **Einstellungen übernehmen**, um die Änderungen zu übernehmen.

     Das Dialogfeld **Konfigurationszusammenfassung** wird angezeigt, in dem der Status der einzelnen Schritte zum Konfigurieren des Test-Agents angezeigt wird.

9. Klicken Sie zum Schließen des Dialogfelds **Konfigurationszusammenfassung** auf **Schließen**. Klicken Sie dann erneut auf **Schließen**, um das Test Agent-Konfigurationstool zu schließen.

    > [!NOTE]
    > Auf dem Computer wird ein Infobereichssymbol für einen als Prozess ausgeführten Test-Agent angezeigt. Es zeigt den Status des Test-Agents an. Sie können mit diesem Tool den Agent starten, beenden oder neu starten, wenn er als Prozess ausgeführt wird. Zum Starten des Test-Agents als Prozess, wenn er nicht ausgeführt wird, wählen Sie **Start**, **Alle Programme**, **Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent** aus.

     Wenn der Testcontroller für diesen Test-Agent bei Team Foundation Server registriert ist, wird der Status eines Test-Agents, der als interaktiver Prozess ausgeführt wird, in der Ansicht **Controller** im **Lab-Center** für Microsoft Test Manager angezeigt. Er wird mit einem vorangestellten Sternchen gekennzeichnet, das angibt, dass er als interaktiver Prozess ausgeführt wird. Verwenden Sie zum Neustarten dieses Test-Agents das Tool, das auf dem Computer mit dem Test-Agent ausgeführt wird, und nicht die Ansicht **Controller**.

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)