---
title: Remote Debuggen eines C++ Projekts | Microsoft-Dokumentation
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730321"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Remote Debuggen eines C++ Projekts in Visual Studio
Zum Debuggen einer Visual Studio-Anwendung auf einem anderen Computer installieren und führen Sie die Remote Tools auf dem Computer aus, auf dem Sie die APP bereitstellen möchten, konfigurieren Sie das Projekt für die Verbindung mit dem Remote Computer über Visual Studio, und stellen Sie die APP bereit, und führen Sie Sie aus.

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

## <a name="remote_cplusplus"></a>Remote Debuggen eines C++ Projekts
 In der folgenden Prozedur ist der Name und der Pfad des Projekts "c:\remotetemp\mymfc", und der Name des Remote Computers lautet " **mjo-DL**".

1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.

3. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus. Öffnen Sie die Registerkarte **Debuggen**.

4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.

    ![Remotedebuggingcplus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:

   |Einstellung|Wert|
   |-|-|
   |Remote-Befehl|C:\remotetemp\mymfc.exe|
   |Arbeitsverzeichnis|C:\remotetemp|
   |Remoteservername|Mjo-DL:*PortNumber*|
   |Verbindung|Remote mit Windows-Authentifizierung|
   |Debuggertyp|Nur systemeigen|
   |Bereitstellungsverzeichnis|C:\remotetemp.|
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|

    Wenn Sie zusätzliche Dateien (optional) bereitstellen, muss der Ordner auf beiden Computern vorhanden sein.

6. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **Configuration Manager**.

7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.

    ![Remotedebugcplusbereitstellung](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Starten Sie das Debuggen (wählen Sie **Debuggen > Debuggen starten** aus, oder drücken Sie **F5**).

9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.

10. Geben Sie bei entsprechender Aufforderung Netzwerk Anmelde Informationen ein, um eine Verbindung mit dem Remote Computer herzustellen.

     Die erforderlichen Anmelde Informationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Beispielsweise können Sie auf einem Domänen Computer ein Sicherheitszertifikat auswählen oder den Domänen Namen und das Kennwort eingeben. Auf einem Computer, der nicht der Domäne ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen, wie z. b. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort eingeben.

11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.

    > [!TIP]
    > Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.

    Wenn Sie nicht-Code Dateien haben, die für die Anwendung erforderlich sind, können Sie Sie in **zusätzlichen** bereit zustellenden Dateien auf der Seite **Windows-Remote Debugger** angeben.

    Alternativ dazu können Sie die Dateien in Ihr Projekt einschließen und die **Content** -Eigenschaft auf der Seite **Eigenschaften** für jede Datei auf **Ja** festlegen. Diese Dateien werden in das **Bereitstellungs Verzeichnis** kopiert, das auf der Seite **Remote-Windows-Debugger** angegeben ist. Sie können auch den **Elementtyp** in **Datei kopieren** ändern und zusätzliche Eigenschaften angeben, wenn Sie möchten, dass die Dateien in einen Unterordner des **Bereitstellungs Verzeichnisses**kopiert werden.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)