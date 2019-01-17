---
title: Remotedebuggen eines Visual C++-Projekts | Microsoft-Dokumentation
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: bdbcefe1e0878ef6bf2520edb90ce904e414f211
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269760"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Remotedebuggen von Visual C++-Projekt in Visual Studio
Zum Debuggen einer Visual Studio-Anwendung auf einem anderen Computer, installieren und die Remotetools auf dem Computer ausführen, werden Sie Ihre app bereitstellen, konfigurieren Sie das Projekt, um die Verbindung mit dem Remotecomputer in Visual Studio, und klicken Sie dann bereitstellen und Ausführen Ihrer app.

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

## <a name="remote_cplusplus"></a> Remotedebuggen eines Visual C++-Projekts  
 In der folgenden Prozedur den Namen und Pfad des Projekts C:\remotetemp\MyMfc, und der Name des Remotecomputers ist **MJO-DL**.  
  
1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.  
  
2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.  
  
3. Projektmappen-Explorer mit der Maustaste auf das Projekt, und wählen **Eigenschaften**. Öffnen Sie die Registerkarte **Debuggen**.  
  
4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
   |Einstellung|Wert|
   |-|-|  
   |Remotebefehl|C:\remotetemp\mymfc.exe|  
   |Arbeitsverzeichnis|C:\remotetemp|  
   |Remoteservername|MJO-DL:*Portnumber*|  
   |Verbindung|Remote mit Windows-Authentifizierung|  
   |Debuggertyp|Nur systemeigen|  
   |Bereitstellungsverzeichnis|C:\remotetemp.|  
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|  
  
    Wenn Sie zusätzliche Dateien (optional) bereitstellen, muss der Ordner auf beiden Computern vorhanden sein.  
  
6. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in der Projektmappe, und wählen Sie **Configuration Manager**.  
  
7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Starten Sie das Debuggen (wählen Sie **Debuggen > Debuggen starten** aus, oder drücken Sie **F5**).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Netzwerk eine Verbindung zum Remotecomputer herstellen.  
  
     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Sie können z. B. auf einem Computer, wählen Sie ein Sicherheitszertifikat oder geben Sie Ihren Domänennamen und Kennwort. Auf einem Computer nicht mit der Domäne möglicherweise eingegebenen Namen des Computers und einen gültigen Benutzerkontonamen an, wie z. B. <strong>MJO-DL\name@something.com</strong>, zusammen mit dem richtigen Kennwort.  
  
11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    >  Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.  
  
    Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Neuer Ordner**). Fügen Sie die Dateien anschließend zum Ordner hinzu (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Vorhandenes Element**, und wählen Sie dann die Dateien aus). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)   
 [Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)