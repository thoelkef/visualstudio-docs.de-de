---
title: Remotedebuggen einer C# oder VB-Projekt | Microsoft-Dokumentation
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2017
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
ms.openlocfilehash: 470212f3b6dc4151b793dcd62b9ff1d39fc2e55b
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316222"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Remotedebuggen einer C# oder Visual Basic-Projekt in Visual Studio
Um eine Visual Studio-Anwendung zu debuggen, die auf einem anderen Computer bereitgestellt wurde, installieren Sie und führen Sie der Remotetools auf dem Computer aus, in dem Sie Ihre app bereitgestellt haben, konfigurieren Sie das Projekt in Visual Studio eine Verbindung mit dem Remotecomputer und führen Sie die app.

![Remote Debugger-Komponenten](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Weitere Informationen zu universellen Windows-Apps (UWP) für das Remotedebuggen, finden Sie unter [ein installiertes App-Paket Debuggen](debug-installed-app-package.md).

## <a name="requirements"></a>Anforderungen

Der Remotedebugger ist nur unter Windows 7 und höher (nicht "phone") und Versionen von Windows Server mit Windows Server 2008 Service Pack 2 ab. Eine vollständige Liste der Anforderungen, finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debuggen zwischen zwei Computern über einen Proxy verbunden sind, wird nicht unterstützt. Debuggen über eine hohe Latenz oder niedriger Bandbreite, wie z. B. DFÜ, Internet oder über das Internet in Ländern wird nicht empfohlen und möglicherweise fehl oder unzumutbar langsam werden.
  
## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten zum auszuführen des Remotedebuggers aus einer Dateifreigabe sein. Weitere Informationen finden Sie unter [Ausführen des Remotedebuggers aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie zum Hinzufügen von Berechtigungen für weitere Benutzer: des Authentifizierungsmodus ändern oder Portnummer für den Remotedebugger, finden Sie unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> Remotedebuggen des Projekts
Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Das folgende Verfahren wird davon ausgegangen, dass Sie auf dem Computer debuggen möchten **MJO-DL**, wie in der Abbildung unten gezeigt.
  
1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.  
  
    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Zu diesem Zweck öffnen Sie "MainWindow.xaml" aus der Toolbox fügen Sie ein Button-Steuerelement hinzu, und doppelklicken Sie auf die Schaltfläche, um deren Ereignishandler zu öffnen.
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.  
  
4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.  
  
6. Wählen Sie **Remotecomputer**, und geben **MJO-DL:4022** in das Textfeld ein. (4022 ist die Portnummer im Remotedebugger-Fenster angezeigt. Die Nummer des Ports erhöht die 2 in jeder Version von Visual Studio).
  
7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.  
  
8. Erstellen Sie das Projekt.  
  
9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**-Ordner auf Ihrem Visual Studio-Computer: **\<Quellpfad>\MyWPF\MyWPF\bin\Debug**.  
  
10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.
  
    > [!CAUTION]
    >  Nehmen Sie keine Änderungen an den Code oder neu erstellen (oder Sie müssen diesen Schritt wiederholen). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren, verwenden von Xcopy, Robocopy, Powershell oder andere Optionen.
  
11. Stellen Sie sicher, dass der Remotedebugger auf dem Zielcomputer ausgeführt wird (wenn es nicht der Fall ist, suchen Sie nach **Remote Debugger** in die **starten** Menü). Remotedebugger-Fenster sieht wie folgt aus.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Starten Sie das Debuggen in Visual Studio (**Debuggen > Debuggen starten** oder **F5**).  
  
13. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Netzwerk eine Verbindung zum Remotecomputer herstellen.  
  
     Die erforderlichen Anmeldeinformationen variieren je nach Sicherheitskonfiguration Ihres Netzwerks. Auf einem Computer, können Sie beispielsweise Ihren Domänennamen und ein Kennwort eingeben. Auf einem Computer nicht mit der Domäne möglicherweise eingegebenen Namen des Computers und einen gültigen Benutzerkontonamen an, wie z. B. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.
  
14. Führen Sie gegebenenfalls die Aktion, die der Haltepunkt erreicht. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, noch nicht dazu führen, dass die Symbole für die Anwendung geladen wurden. Wiederholen Sie dann, und wenn dies nicht funktioniert, erhalten Sie Informationen zum Laden von Symbolen und wie sie auf Probleme bei [Grundlegendes zu Symboldateien und Visual Studio symboleinstellungen](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.
  
    Wenn Sie alle Dateien ohne Code, die von der Anwendung verwendet werden müssen verfügen, müssen Sie sie in Visual Studio-Projekt einzuschließen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Neuer Ordner**.) Fügen Sie die Dateien anschließend zum Ordner hinzu (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Vorhandenes Element**, und wählen Sie dann die Dateien aus). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)   
 [Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)