---
title: Remote-Debuggen eines C-Oder-VB-Projekts | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301074"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Remotedebuggen eines C- oder Visual Basic-Projekts in Visual Studio
Um eine Visual Studio-Anwendung zu debuggen, die auf einem anderen Computer bereitgestellt wurde, installieren und führen Sie die Remotetools auf dem Computer aus, auf dem Sie Ihre App bereitgestellt haben, konfigurieren Sie das Projekt so, dass eine Verbindung mit dem Remotecomputer über Visual Studio hergestellt wird, und führen Sie dann die App aus.

![Remote-Debuggerkomponenten](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Weitere Informationen zum Remotedebugging von Universellen Windows-Apps (UWP) finden Sie unter [Debuggen eines installierten App-Pakets](debug-installed-app-package.md).

## <a name="requirements"></a>Requirements (Anforderungen)

Der Remotedebugger wird unter Windows 7 und neueren (nicht Telefon) und Versionen von Windows Server ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Das Debuggen zwischen zwei Computern, die über einen Proxy verbunden sind, wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder geringer Bandbreite, z. B. DFÜ-Internet, oder über das Internet zwischen Ländern wird nicht empfohlen und kann fehlschlagen oder unannehmbar langsam sein.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten sein, den Remotedebugger von einer Dateifreigabe aus auszuführen. Weitere Informationen finden Sie unter [Ausführen des Remotedebuggers aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen müssen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Remote-Debug-Debug-Projekt
Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Bei der folgenden Vorgehensweise wird davon ausgegangen, dass Sie es auf einem Computer mit dem Namen **MJO-DL**debuggen möchten, wie in der Abbildung unten gezeigt.

1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.

    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Öffnen Sie dazu MainWindow.xaml, und fügen Sie ein Schaltflächensteuerelement aus der Toolbox hinzu, und doppelklicken Sie dann auf die Schaltfläche, um den Handler zu öffnen.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**.

4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.

6. Wählen Sie **Remotecomputer verwenden**, und geben Sie **yourmachinename:port** in das Textfeld ein. (Die Portnummer wird im Remote-Debuggerfenster angezeigt. Die Portnummer erhöht sich in jeder Version von Visual Studio um 2).

    Verwenden Sie in diesem Beispiel:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** auf Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** auf Visual Studio 2017
    ::: moniker-end

7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.

8. Erstellen Sie das Projekt.

9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**-Ordner auf Ihrem Visual Studio-Computer: **\<Quellpfad>\MyWPF\MyWPF\bin\Debug**.

10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.

    > [!CAUTION]
    > Nehmen Sie keine Änderungen am Code vor oder erstellen Sie ihn neu (oder wiederholen Sie diesen Schritt). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren, Xcopy, Robocopy, Powershell oder andere Optionen verwenden.

11. Stellen Sie sicher, dass der Remote-Debugger auf dem Zielcomputer ausgeführt wird (Wenn dies nicht der Fall ist, suchen Sie im **Startmenü** nach **Remote-Debugger).** Das Remote-Debuggerfenster sieht wie folgt aus.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Starten Sie das Debuggen in Visual Studio (**Debuggen > Debuggen starten** oder **F5**).

13. Wenn Sie dazu aufgefordert werden, geben Sie Netzwerkanmeldeinformationen ein, um eine Verbindung mit dem Remotecomputer herzustellen.

     Die erforderlichen Anmeldeinformationen variieren je nach Sicherheitskonfiguration Ihres Netzwerks. Auf einem Domänencomputer können Sie beispielsweise Ihren Domänennamen und Ihr Kennwort eingeben. Auf einem Nicht-Domänencomputer können Sie den Computernamen und einen <strong>MJO-DL\name@something.com</strong>gültigen Benutzerkontonamen wie , zusammen mit dem richtigen Kennwort, eingeben.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.

14. Falls erforderlich, ergreifen Sie Maßnahmen, um den Haltepunkt zu treffen. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die Symbole für die Anwendung nicht geladen. Wiederholen Sie den Vorgang, und wenn dies nicht funktioniert, erhalten Sie Informationen zum Laden von Symbolen und zur Problembehandlung unter Grundlegendes zu [Symboldateien und Symboleinstellungen von Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.

    Wenn Sie nicht codefreie Dateien haben, die von der Anwendung verwendet werden müssen, müssen Sie sie in das Visual Studio-Projekt einschließen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (im **Projektmappen-Explorer**auf **> neuen Ordner**hinzufügen ). Fügen Sie die Dateien anschließend zum Ordner hinzu (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Vorhandenes Element**, und wählen Sie dann die Dateien aus). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Weitere Informationen
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)