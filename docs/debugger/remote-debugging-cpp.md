---
title: Remotedebuggen eines Visual C++-Projekts | Microsoft-Dokumentation
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 334a0b964033282458c211d69af30aad20dbd6bc
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781944"
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
  
1.  Erstellen eine MFC-Anwendung, die mit dem Namen **Mymfc.**  
  
2.  Legen Sie einen Haltepunkt an einer beliebigen Stelle in der Anwendung, die leicht, z. B. in erreicht wird **"MainFrm.cpp"**, am Anfang des `CMainFrame::OnCreate`.  
  
3.  Projektmappen-Explorer mit der Maustaste auf das Projekt, und wählen **Eigenschaften**. Öffnen der **Debuggen** Registerkarte.  
  
4.  Legen Sie die **zu startender Debugger** zu **Remote-Windows-Debugger**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:  
  
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
  
6.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in der Projektmappe, und wählen Sie **Configuration Manager**.  
  
7.  Für die **Debuggen** Konfiguration der **bereitstellen** Kontrollkästchen.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Mit dem Debuggen beginnen (**Debuggen > Debuggen starten**, oder **F5**).  
  
9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.  
  
10. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Netzwerk eine Verbindung zum Remotecomputer herstellen.  
  
     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Sie können z. B. auf einem Computer, wählen Sie ein Sicherheitszertifikat oder geben Sie Ihren Domänennamen und Kennwort. Auf einem Computer nicht mit der Domäne möglicherweise eingegebenen Namen des Computers und einen gültigen Benutzerkontonamen an, wie z. B. **MJO-DL\name@something.com**, zusammen mit dem richtigen Kennwort.  
  
11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.  
  
    > [!TIP]
    >  Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. In der **Projektmappen-Explorer** mit der rechten Maustaste die **Mymfc** Knoten und wählen Sie dann **bereitstellen**.  
  
 Wenn bestimmte Dateien ohne Code von der Anwendung benötigt werden, müssen Sie diese zum Visual Studio-Projekt hinzufügen. Erstellen einen Projektordner für die zusätzlichen Dateien (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen > Neuer Ordner**.) Fügen Sie dann die Dateien in den Ordner hinzu (in der **Projektmappen-Explorer**, klicken Sie auf **hinzufügen > Vorhandenes Element**, wählen Sie die Dateien). Auf der **Eigenschaften** Seite für jede Datei **in Ausgabeverzeichnis kopieren** zu **immer kopieren**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)   
 [Konfigurieren der Windows-Firewalls für Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)   
 [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)