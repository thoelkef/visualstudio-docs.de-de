---
title: Timeouts für Adapter für diagnostische Daten in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 61572a323fa29892096c963ad94a5e201dd61ec9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>How to: Prevent Time-Outs for Diagnostic Data Adapters

Wenn Sie Adapter für diagnostische Daten in den Testeinstellungen verwenden, kann beim Starten des Testlaufs aus folgenden Gründen ein Timeout auftreten:

-   Der Testcontrollerdienst wird nicht auf dem Testcontrollercomputer ausgeführt. Sie müssen den Dienst möglicherweise neu starten. Weitere Informationen finden Sie unter [Managing Test Controllers and Test Agents with Visual Studio (Verwalten von Testcontrollern und Test-Agents mit Visual Studio)](../test/manage-test-controllers-and-test-agents.md).

-   Wenn Sie Daten auf einem Remotecomputer erfassen, könnte die Firewall Microsoft Test Manager blockieren. Der Computer, der Microsoft Test Manager ausführt, muss eingehende Verbindungen vom Testcontroller akzeptieren. Ein Timeout tritt auf, wenn Microsoft Test Manager keine Meldung vom Controller empfängt, weil er von der Firewall blockiert wird. Sie müssen die Firewalleinstellungen auf dem Computer überprüfen, der Microsoft Test Manager ausführt. Weitere Informationen zu Firewalleinstellungen erhalten Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkId=184980).

-   Der Testcontroller kann den Namen des Computers nicht auflösen, der Microsoft Test Manager ausführt. Das kann passieren, wenn DNS die falsche Adresse für diesen Computer bereitstellt. Möglicherweise müssen Sie sich an den Netzwerkadministrator wenden, um dieses Problem zu beheben.

 Wenn Sie einen langen Test ausführen, der viele Daten erfassen muss, kann bei der Datenerfassung ein Timeout auftreten. Sie können dieses Problem mithilfe der folgenden Prozedur beheben:

 Sie können das Timeout verlängern, indem Sie die Konfigurationsdatei von Microsoft Test Manager oder die Konfigurationsdatei vom Test-Agent, bei dem das Timeout auftritt, aktualisieren.

 Die Konfigurationsdatei von Microsoft Test Manager heißt **mtm.exe.config**. Die Datei befindet sich im folgenden Verzeichnis: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

 Zum Aktualisieren eines Test-Agents müssen Sie die folgenden Konfigurationsdateien auf dem Test-Agent-Computer aktualisieren. Diese Dateien befinden sich alle im gleichen Verzeichnis auf dem Test-Agent-Computer: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 Wenn Sie manuelle Tests ausführen und Daten aus einer Umgebung erfassen, wenn ein Fehler erstellt oder der Testfall abgeschlossen wird, werden alle von Adaptern für diagnostische Daten erfasste Daten auf den Computer übertragen, der die manuellen Tests ausführt. Wenn Sie viele Daten erfasst haben oder eine langsame Netzwerkverbindung vorliegt, könnte es länger als der Standardwert von 60 Sekunden dauern. Wenn Sie z. B. den IntelliTrace-Adapter konfiguriert haben, um IntelliTrace-Ereignisse und Aufrufinformationen für viele Prozesse zu sammeln, könnte die Übertragung dieser Daten das Standardtimeout überschreiten. Sie können die folgende Prozedur zum Aktualisieren der Datei **mtm.exe.config** verwenden, um diesen Wert zu vergrößern.

 Wenn für die Test Runner-Aktivität oder einen Test-Agent ein Timeout auftritt, wird eine Fehlermeldung angezeigt. Die Fehlermeldung für den Test-Agent enthält Informationen zu dem Test-Agent-Computer, auf dem das Timeout aufgetreten ist. Gehen Sie wie im Folgenden beschrieben vor, um die Konfigurationsdateien zu aktualisieren (je nach angezeigter Fehlermeldung).

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>So erhöhen Sie die Timeouts für die Adapter für diagnostische Daten

1.  Öffnen Sie ein Fenster im Windows-Explorer (oder im Datei-Explorer).

     Klicken Sie dazu mit der rechten Maustaste auf **Start** und dann auf **Windows-Explorer öffnen**.

    > [!NOTE]
    > Zum Aktualisieren der Datei sind möglicherweise Administratorrechte erforderlich.

2.  Suchen Sie auf dem Computer nach dem Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*, das die zu aktualisierende Datei enthält.

3.  Klicken Sie mit der rechten Maustaste auf die Datei, und klicken Sie auf **Öffnen mit**. Wählen Sie einen Editor aus.

     Die Datei wird im Editor angezeigt. In dieser Datei werden viele Einstellungen gespeichert. Die meisten dieser Einstellungen können mit Microsoft Test Manager geändert werden. Die Timeouteinstellungen müssen jedoch wie in den folgenden Schritten beschrieben manuell geändert werden.

4.  Zum Erhöhen der Timeoutwerte müssen Sie den Abschnitt mit den Testausführungseinstellungen ändern. Dieser Abschnitt hat das folgende Format:

    ```
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Erhöhen Sie den Wert des **DataCollectorEventTimeoutInSeconds**-Schlüssels, um die Zeit zu verlängern, während der Adapter für diagnostische Daten auf den Abschluss von Ereignissen warten.

6.  Wenn die Timeoutfehlermeldung die Test Runner-Aktivität betrifft, müssen Sie den Wert des **RunOperationTimeoutInSeconds**-Schlüssels erhöhen.

7.  Sie müssen zum Verlängern des Timeouts für das Übertragen der für einen Fehler oder am Ende eines Tests gesammelten Daten auf den Computer, auf dem die Tests ausgeführt werden, das folgende Timeout zu **mtm.exe.config** im appSettings-Abschnitt der Datei hinzufügen:

    ```
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > Der Timeoutwert wird in Sekunden angegeben.

8.  Speichern Sie die Änderungen an der Datei, und führen Sie die Tests, bei denen zuvor ein Timeout aufgetreten ist, erneut aus.

## <a name="see-also"></a>Siehe auch

- [Collect Diagnostic Information Using Test Settings (Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)