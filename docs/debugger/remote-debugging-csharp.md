---
title: Remote Debuggen eines C# -oder VB-Projekts | Microsoft-Dokumentation
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730254"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Remote Debuggen eines C# -oder Visual Basic-Projekts in Visual Studio
Zum Debuggen einer Visual Studio-Anwendung, die auf einem anderen Computer bereitgestellt wurde, installieren und führen Sie die Remote Tools auf dem Computer aus, auf dem Sie die APP bereitgestellt haben, konfigurieren Sie das Projekt für die Verbindung mit dem Remote Computer von Visual Studio, und führen Sie die APP aus.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Weitere Informationen zum Remote Debuggen von universellen Windows-Apps (UWP) finden Sie unter [Debuggen eines installierten App-Pakets](debug-installed-app-package.md).

## <a name="requirements"></a>Anforderungen

Der Remote Debugger wird unter Windows 7 und höher (nicht telefonisch) und Windows Server-Versionen ab Windows Server 2008 Service Pack 2 unterstützt. Eine umfassende Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Das Debuggen zwischen zwei mit einem Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, wie z. b. ddas Internet oder über das Internet über das Internet hinweg, wird nicht empfohlen und schlägt möglicherweise fehl oder ist nicht akzeptabel.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten sein, den Remote Debugger von einer Dateifreigabe aus auszuführen. Weitere Informationen finden Sie unter [Ausführen des Remote Debuggers aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a>Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remote Debugger ändern müssen, finden Sie weitere Informationen unter [configure the Remote Debugger](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Remote Debuggen des Projekts
Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Bei der folgenden Prozedur wird davon ausgegangen, dass Sie Sie auf einem Computer mit dem Namen **mjo-DL Debuggen**möchten, wie in der folgenden Abbildung dargestellt.

1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.

    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Öffnen Sie hierzu die Datei "MainWindow. XAML", und fügen Sie ein Schaltflächen-Steuerelement aus der Toolbox hinzu, und doppelklicken Sie dann auf die Schaltfläche, um den Handler zu öffnen.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**.

4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.

    ![Remotedebuggercsharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.

6. Wählen Sie **Remote Computer verwenden**aus, und geben Sie **yourmachinename: Port** in das Textfeld ein. (Die Portnummer wird im Fenster Remote Debugger angezeigt. Die Portnummer wird in jeder Version von Visual Studio auf 2 erhöht.)

    Verwenden Sie in diesem Beispiel Folgendes:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** in Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Mjo-DL: 4022** in Visual Studio 2017
    ::: moniker-end

7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.

8. Erstellen Sie das Projekt.

9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**-Ordner auf Ihrem Visual Studio-Computer: **\<Quellpfad>\MyWPF\MyWPF\bin\Debug**.

10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.

    > [!CAUTION]
    > Nehmen Sie keine Änderungen am Code vor, oder erstellen Sie keine Neuerstellung (oder Sie müssen diesen Schritt wiederholen). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren und xcopy, Robocopy, PowerShell oder andere Optionen verwenden.

11. Stellen Sie sicher, dass der Remote Debugger auf dem Zielcomputer ausgeführt wird (wenn dies nicht der Fall ist, suchen Sie im **Startmenü** nach **Remote Debugger** ). Das Fenster Remote Debugger sieht wie folgt aus.

     ![Remotedebuggerwindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Starten Sie das Debuggen in Visual Studio (**Debuggen > Debuggen starten** oder **F5**).

13. Geben Sie bei entsprechender Aufforderung Netzwerk Anmelde Informationen ein, um eine Verbindung mit dem Remote Computer herzustellen.

     Die erforderlichen Anmelde Informationen variieren abhängig von der Sicherheitskonfiguration Ihres Netzwerks. Auf einem Domänen Computer können Sie z. b. den Domänen Namen und das Kennwort eingeben. Auf einem Computer, der nicht der Domäne ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen, wie z. b. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort eingeben.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.

14. Nehmen Sie ggf. Maßnahmen zum Erreichen des Breakpoints vor. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die Symbole für die Anwendung nicht geladen. Versuchen Sie es erneut, und wenn dies nicht funktioniert, erhalten Sie Informationen zum Laden von Symbolen und zur Problembehandlung in [den Symbol Dateien und in den Symbol Einstellungen von Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.

    Wenn Sie nicht-Code Dateien haben, die von der Anwendung verwendet werden müssen, müssen Sie Sie in das Visual Studio-Projekt einschließen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Neuer Ordner**.) Fügen Sie die Dateien anschließend zum Ordner hinzu (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Vorhandenes Element**, und wählen Sie dann die Dateien aus). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)