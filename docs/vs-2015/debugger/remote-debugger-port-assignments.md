---
title: Remotedebugger-Portzuweisungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542102"
---
# <a name="remote-debugger-port-assignments"></a>Remotedebugger - Portzuweisungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Remotedebugger kann als Anwendung oder als Hintergrunddienst ausgeführt werden. Bei der Ausführung als Anwendung wird standardmäßig der folgende Port zugewiesen:  
  
- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  Die Nummer des Ports, der dem Remotedebugger zugewiesen ist, wird also für jede Version um 2 erhöht. Sie können bei Bedarf eine andere Portnummer festlegen. Das Festlegen von Portnummern wird in einem späteren Abschnitt erläutert.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Remotedebugger-Port bei 32-Bit-Betriebssystemen  
 TCP 4020 (Visual Studio 2015) ist der Hauptport und für alle Szenarien erforderlich. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.  
  
 Klicken Sie im Fenster Remote Debugger auf Extras > **Optionen**, und legen Sie die TCP/IP-Portnummer fest.  
  
 Starten Sie den Remote Debugger in der Befehlszeile mit dem **/Port** -Schalter: **msvsmon \<port number> /Port **.  
  
 Alle Remote Debugger-Befehls Zeilenschalter finden Sie in der Hilfe zum Remote Debugging (drücken Sie **F1** , oder klicken Sie im Fenster "Remote Debugger" auf **Hilfe/Verwendung** ).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Remotedebugger-Port bei 64-Bit-Betriebssystemen  
 Beim Starten der 64-Bit-Version des Remotedebuggers wird standardmäßig Port 4020 verwendet.  Wenn Sie einen 32-Bit-Prozess debuggen, startet die 64-Bit-Version des Remotedebuggers eine 32-Bit-Remotedebuggerversion auf Port 4021. Wenn Sie den 32-Bit-Remotedebugger ausführen, wird Port 4020 und nicht Port 4021 verwendet.  
  
 Dieser Port kann über die Befehlszeile konfiguriert werden: **msvsmon \<port number> /wow64port **.  
  
## <a name="the-discovery-port"></a>Port für die Ermittlung  
 UDP 3702 wird für die Suche nach ausgeführten Instanzen des Remotedebuggers im Netzwerk verwendet (z. B. bei **Suchen** im Dialogfeld **An den Prozess anhängen** ). Er wird nur für die Ermittlung von Computern verwendet, auf denen der Remotedebugger ausgeführt wird, und ist daher optional, wenn Sie den Computernamen oder die IP-Adresse des Zielcomputers auf andere Weise ermitteln können. Da dies der Standardport für die Ermittlung ist, kann die Portnummer nicht konfiguriert werden.  
  
 Wenn Sie die Ermittlung nicht aktivieren möchten, können Sie msvsmon von der Befehlszeile aus mit deaktivierter Ermittlung starten:  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Remotedebugger-Ports in Azure  
 Die folgenden Ports werden vom Remotedebugger in Azure verwendet. Die Ports im Clouddienst werden den Ports auf den einzelnen virtuellen Computern zugeordnet. Bei allen Ports handelt es sich um TCP-Ports.  

|**Connection**|**Port im Clouddienst**|**Port auf virtuellem Computer**|  
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Remote Debugging](../debugger/remote-debugging.md)
