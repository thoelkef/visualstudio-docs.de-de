---
title: Remotedebuggen eines C++-Projekts | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301086"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Remotedebuggen eines C++-Projekts in Visual Studio
Um eine Visual Studio-Anwendung auf einem anderen Computer zu debuggen, installieren und führen Sie die Remotetools auf dem Computer aus, auf dem Sie Ihre App bereitstellen, konfigurieren Sie das Projekt so, dass eine Verbindung mit dem Remotecomputer über Visual Studio hergestellt wird, und führen Sie die App aus.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Remotedebug ein C++-Projekt
 In der folgenden Prozedur lautet der Name und der Pfad des Projekts C:-Remotetemp-MyMfc, und der Name des Remotecomputers lautet **MJO-DL**.

1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus. Öffnen Sie die Registerkarte **Debuggen**.

4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:

   |Einstellung|value|
   |-|-|
   |Remote-Befehl|C:\remotetemp\mymfc.exe|
   |Arbeitsverzeichnis|C:\remotetemp|
   |Remoteservername|MJO-DL:*Portnummer*|
   |Verbindung|Remote mit Windows-Authentifizierung|
   |Debuggertyp|Nur systemeigen|
   |Bereitstellungsverzeichnis|C:\remotetemp.|
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|

    Wenn Sie zusätzliche Dateien bereitstellen (optional), muss der Ordner auf beiden Computern vorhanden sein.

6. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Configuration Manager**.

7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Starten Sie das Debuggen (wählen Sie **Debuggen > Debuggen starten** aus, oder drücken Sie **F5**).

9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.

10. Wenn Sie dazu aufgefordert werden, geben Sie Netzwerkanmeldeinformationen ein, um eine Verbindung mit dem Remotecomputer herzustellen.

     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Auf einem Domänencomputer können Sie beispielsweise ein Sicherheitszertifikat auswählen oder Ihren Domänennamen und Ihr Kennwort eingeben. Auf einem Nicht-Domänencomputer können Sie den Computernamen und einen <strong>MJO-DL\name@something.com</strong>gültigen Benutzerkontonamen wie , zusammen mit dem richtigen Kennwort, eingeben.

11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.

    > [!TIP]
    > Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.

    Wenn Sie nicht-Codedateien haben, die von der Anwendung benötigt werden, können Sie sie in **Zusätzliche Dateien** angeben, die auf der **Remote-Windows-Debuggerseite** bereitgestellt werden sollen.

    Alternativ können Sie die Dateien in Ihr Projekt einschließen und die **Content-Eigenschaft** auf die **Eigenschaftenseite** für jede Datei auf **Ja** festlegen. Diese Dateien werden in das **Bereitstellungsverzeichnis** kopiert, das auf der **Seite Remote-Windows-Debugger** angegeben ist. Sie können auch den **Elementtyp** in **Kopierdatei** ändern und dort zusätzliche Eigenschaften angeben, wenn Sie die Dateien in einen Unterordner des **Bereitstellungsverzeichnisses**kopieren möchten.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Weitere Informationen
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)