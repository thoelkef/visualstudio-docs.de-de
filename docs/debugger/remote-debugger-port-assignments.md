---
title: Remotedebugger – Portzuweisungen | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 988731be4376e1d1e402b3722bed157cc9b655d2
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151001"
---
# <a name="remote-debugger-port-assignments"></a>Remotedebugger - Portzuweisungen
Der Visual Studio-Remotedebugger kann als Anwendung oder als Hintergrunddienst ausgeführt werden. Bei der Ausführung als Anwendung wird standardmäßig der folgende Port zugewiesen:  

-   Visual Studio 2017:4022

-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 Die Nummer des Ports, der dem Remotedebugger zugewiesen ist, wird also für jede Version um 2 erhöht. Sie können bei Bedarf eine andere Portnummer festlegen. Das Festlegen von Portnummern wird in einem späteren Abschnitt erläutert.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Remotedebugger-Port bei 32-Bit-Betriebssystemen  
 TCP 4022 (in Visual Studio 2017) ist der Hauptport und für alle Szenarien erforderlich ist. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.  
  
 Klicken Sie im Remotedebugger-Fenster auf **Tools > Optionen**, und legen Sie die Nummer des TCP/IP-Ports.  
  
 In der Befehlszeile, starten Sie den Remotedebugger über die **/a-Station** wechseln: **Msvsmon/Port \<Portnummer >**.  
  
 Sie können alle Remotedebugger Befehlszeilen-Switches finden Sie in der Hilfe zum Remotedebugging (drücken Sie **F1** oder klicken Sie auf **Hilfe > Verwendung** im Remotedebugger-Fenster).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Remotedebugger-Port bei 64-Bit-Betriebssystemen  
 Wenn die 64-Bit-Version des Remotedebuggers gestartet wird, wird standardmäßig den Port 4022 verwendet.  Wenn Sie einen 32-Bit-Prozess debuggen, startet die 64-Bit-Version des Remotedebuggers eine 32-Bit-Version des Remotedebuggers auf Port 4023 an. Wenn Sie die 32-Bit-Remotedebugger ausführen, wird 4022 und 4023 wird nicht verwendet.  
  
 Dieser Port ist über die Befehlszeile konfigurierbar: **"msvsmon" /wow64port \<Portnummer >**.  
  
## <a name="the-discovery-port"></a>Port für die Ermittlung  
 UDP 3702 wird für die Suche nach ausgeführten Instanzen des Remotedebuggers im Netzwerk verwendet (z. B. bei **Suchen** im Dialogfeld **An den Prozess anhängen** ). Er wird nur für die Ermittlung von Computern verwendet, auf denen der Remotedebugger ausgeführt wird, und ist daher optional, wenn Sie den Computernamen oder die IP-Adresse des Zielcomputers auf andere Weise ermitteln können. Da dies der Standardport für die Ermittlung ist, kann die Portnummer nicht konfiguriert werden.  
  
 Wenn Sie die Ermittlung nicht aktivieren möchten, können Sie msvsmon von der Befehlszeile aus mit deaktivierter Ermittlung starten:  **msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Remotedebugger-Ports in Azure  
 Die folgenden Ports werden vom Remotedebugger in Azure verwendet. Die Ports im Clouddienst werden den Ports auf den einzelnen virtuellen Computern zugeordnet. Bei allen Ports handelt es sich um TCP-Ports.  
  
|Verbindung|Port im Clouddienst|Port auf virtuellem Computer|
|-|-|-|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)