---
title: Remotedebugger-Portzuweisungen | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3872f11dff614e8fae4deeace7cdf301cd9b5e1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="remote-debugger-port-assignments"></a>Remotedebugger - Portzuweisungen
Der Visual Studio-Remotedebugger kann als Anwendung oder als Hintergrunddienst ausgeführt werden. Bei der Ausführung als Anwendung wird standardmäßig der folgende Port zugewiesen:  

-   Visual Studio 2017:4022

-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 Die Nummer des Ports, der dem Remotedebugger zugewiesen ist, wird also für jede Version um 2 erhöht. Sie können bei Bedarf eine andere Portnummer festlegen. Das Festlegen von Portnummern wird in einem späteren Abschnitt erläutert.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Remotedebugger-Port bei 32-Bit-Betriebssystemen  
 TCP-4022 (in Visual Studio-2017) ist der Hauptport und für alle Szenarien erforderlich ist. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.  
  
 Klicken Sie im Remotedebugger-Fenster auf **Tools > Optionen**, und legen Sie die TCP/IP-Portnummer.  
  
 In der Befehlszeile starten Sie den Remotedebugger über die **/a-Station** wechseln: **Msvsmon/Port \<Portnummer >**.  
  
 Sie können den Remotedebugger Befehlszeilenschalter finden, in der Hilfe zum Remotedebugging (drücken Sie **F1** oder klicken Sie auf **Hilfe > Verwendung** im Remotedebugger-Fenster).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Remotedebugger-Port bei 64-Bit-Betriebssystemen  
 Wenn die 64-Bit-Version des Remotedebuggers gestartet wird, wird standardmäßig den Port 4022 verwendet.  Wenn Sie einen 32-Bit-Prozess zu debuggen, startet die 64-Bit-Version des Remotedebuggers eine 32-Bit-Version des Remotedebuggers auf Port 4023 an. Wenn Sie die 32-Bit-Remotedebugger ausführen, 4022 verwendet, und 4023 wird nicht verwendet.  
  
 Dieser Port ist über die Befehlszeile konfigurierbar: **Msvsmon /wow64port \<Portnummer >**.  
  
## <a name="the-discovery-port"></a>Port für die Ermittlung  
 UDP 3702 wird für die Suche nach ausgeführten Instanzen des Remotedebuggers im Netzwerk verwendet (z. B. bei **Suchen** im Dialogfeld **An den Prozess anhängen** ). Er wird nur für die Ermittlung von Computern verwendet, auf denen der Remotedebugger ausgeführt wird, und ist daher optional, wenn Sie den Computernamen oder die IP-Adresse des Zielcomputers auf andere Weise ermitteln können. Da dies der Standardport für die Ermittlung ist, kann die Portnummer nicht konfiguriert werden.  
  
 Wenn Sie die Ermittlung nicht aktivieren möchten, können Sie msvsmon von der Befehlszeile aus mit deaktivierter Ermittlung starten:  **msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Remotedebugger-Ports in Azure  
 Die folgenden Ports werden vom Remotedebugger in Azure verwendet. Die Ports im Clouddienst werden den Ports auf den einzelnen virtuellen Computern zugeordnet. Bei allen Ports handelt es sich um TCP-Ports.  
  
||||  
|-|-|-|  
|**Verbindung**|**Port im Clouddienst**|**Port auf virtuellem Computer**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)