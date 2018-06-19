---
title: Die Windows-Firewall für Remotedebuggen konfigurieren | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9fdd6db229bf1aa6f607e096715ea485ec5c5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465199"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurieren der Windows-Firewall für das Remotedebuggen
In diesem Thema wird die Konfiguration der Firewall für das Remotedebuggen auf Computern mit folgenden Betriebssystemen beschrieben:  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 Wenn das Netzwerk, in dem Sie debuggen, nicht durch eine Firewall geschützt ist, ist diese Konfiguration nicht erforderlich. Andernfalls müssen auf dem Computer, auf dem Visual Studio gehostet wird, und auf dem Remotecomputer, auf dem das Debuggen erfolgen soll, Änderungen an der Konfiguration der Firewall vorgenommen werden.  
  
 **IPSec** Wenn Ihr Netzwerk eine Kommunikation mit IPSec erfordert, müssen Sie auf dem Visual Studio-Hostcomputer und dem Remotecomputer zusätzliche Ports öffnen.  
  
 **Webserver** Wenn Sie einen Remotewebserver debuggen, müssen Sie auf dem Remotecomputer einen zusätzlichen Port öffnen. (Für IIS, muss Port 80 geöffnet sein.)  
  
 Auf den beiden Computern muss nicht das gleiche Betriebssystem ausgeführt werden. Auf dem Visual Studio-Computer kann beispielsweise Windows 10 und auf dem Remotecomputer Windows Server 2012 R2 ausgeführt werden.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports auf dem Remotecomputer, die das Remotedebuggen ermöglichen  
  
|||||  
|-|-|-|-|  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|   
|4022|eingehende|TCP|Für VS 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter [Visual Studio Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md).|  
|4023|eingehende|TCP|Für VS 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. (Nur zur remote Debuggen von 64-Bit-Version des Remotedebuggers eine 32-Bit-Prozess.) Weitere Informationen finden Sie unter [Visual Studio Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md).| 
|3702|Ausgehend|UDP|(Optional) Erforderlich für die remotedebuggerermittlung.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Konfigurieren von Ports in der Windows-Firewall  

Bei der Installation von Visual Studio oder der Remotedebugger wird die Software versuchen, um die richtigen Ports zu öffnen. In einigen Szenarien (z. B. das Verwenden einer Drittanbieter-Firewall), müssen Sie jedoch manuell einen Port zu öffnen. Sie müssen sicherstellen, dass die Ports geöffnet sind, finden Sie unter [Problembehandlung](#troubleshooting). Einige Anweisungen zum Öffnen eines Ports kann auf älteren Versionen von Windows abweichen.

Zum Öffnen eines Ports:
  
1. Öffnen der **starten** Menü, suchen Sie nach **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **eingehende Regeln > neue Regel > Port**, und klicken Sie dann auf **Weiter**. (Wählen Sie für ausgehende Regeln **ausgehende Regeln** stattdessen.)

3. Wählen Sie entweder **TCP** oder **UDP**, je nachdem, auf die Portnummer an.

4. Klicken Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer an, klicken Sie auf **Weiter**.

5. Klicken Sie auf **Allow the Connection** , und klicken Sie dann in der Liste **Weiter**.

6. Wählen Sie eine oder mehrere Netzwerktypen für den Port zu aktivieren, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
7. Fügen Sie den Namen (z. B. **Msvsmon**, **IIS**, oder **Web Deploy**) für die Regel, und klicken Sie auf **Fertig stellen**.

    Die neue Regel in der Liste eingehende oder ausgehende Regeln sollte angezeigt werden.

## <a name="troubleshooting"></a>Problembehandlung bei

Wenn Sie Probleme beim Anfügen an Ihre app mit dem remote Debugger sind, müssen Sie möglicherweise stellen Sie sicher, dass die richtigen Ports geöffnet sind.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Stellen Sie sicher, dass die Ports in der Windows-Firewall auf dem Visual Studio-Computer geöffnet sind.  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Auf Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **app** verwendet wird, unter Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet wird.  In den folgenden Schritten verwenden wir das Wort **app**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  Suchen Sie in der Liste **Zugelassene Apps und Features** nach **Visual Studio - Remotedebuggerermittlung**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio - Remotedebuggerermittlung** nicht aufgeführt ist, klicken Sie auf **Andere App zulassen**. Wenn Sie weiterhin, dass es in sehen der **app hinzufügen** Fenster, klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  In der **apps und Funktionen zulässig** Liste **Visual Studio Remote Debugger**. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Stellen Sie sicher, dass die Ports in der Windows-Firewall auf dem Remotecomputer geöffnet sind.  
 Die Komponenten für das Remotedebuggen können auf dem Remotecomputer installiert sein oder aus einem freigegebenen Verzeichnis ausgeführt werden. In beiden Fällen muss die Firewall des Remotecomputers konfiguriert werden. Die Komponenten für das Remotedebuggen befinden sich an folgendem Speicherort:  
  
 **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**  
  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Auf Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **app** verwendet wird, unter Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet wird.  In den folgenden Schritten verwenden wir das Wort **app**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  In der **apps und Funktionen zulässig** auflisten, suchen Sie nach **Visual Studio Remote Debugger**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio Remote Debugger** ist nicht aufgeführt ist, klicken Sie auf **andere app zulassen**. Wenn Sie weiterhin, dass es in sehen der **fügen Sie ein app-Fenster**, klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  In der **zulässige apps** Liste **Visual Studio Remote Debugger**. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Verwalteten oder systemeigenen Kompatibilitätsmodus zulassen) Öffnen zusätzlicher Ports auf dem Remotecomputer

Bei Verwendung von Kompatibilitätsmodus für den Debugger (**Extras > Optionen > Debugging**), müssen zusätzliche Ports geöffnet werden. Kompatibilitätsmodus aktiviert eine ältere Version des Debuggers und unterschiedliche Ports sind erforderlich.

> [!NOTE]
> Die ältere Version des Debuggers wird der Debugger von Visual Studio 2010.
  
|||||  
|-|-|-|-|  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|  
|135, 139, 445|Ausgehend|TCP|Erforderlich.|  
|137, 138|Ausgehend|UDP|Erforderlich.|  
|500, 4500|Ausgehend|UDP|Erforderlich, wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec vorschreibt.|  
|80|Ausgehend|TCP|Erforderlich für das Webserverdebuggen.|
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)