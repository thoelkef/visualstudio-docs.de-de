---
title: Die Windows-Firewall für Remotedebuggen konfigurieren | Microsoft-Dokumentation
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
ms.openlocfilehash: 7f6904313ff585b8099c993f83e90bacb91a4ba2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847954"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurieren der Windows-Firewall für das Remotedebuggen
In diesem Thema wird die Konfiguration der Firewall für das Remotedebuggen auf Computern mit folgenden Betriebssystemen beschrieben:  
  
- Windows 10  
  
- Windows 8/8.1  
  
- Windows 7   
  
- Windows Server 2012 R2  

- Windows Server 2012
  
- Windows Server 2008 R2 
  
  Wenn das Netzwerk, in dem Sie debuggen, nicht durch eine Firewall geschützt ist, ist diese Konfiguration nicht erforderlich. Andernfalls müssen auf dem Computer, auf dem Visual Studio gehostet wird, und auf dem Remotecomputer, auf dem das Debuggen erfolgen soll, Änderungen an der Konfiguration der Firewall vorgenommen werden.  
  
  **IPSec** Wenn Ihr Netzwerk eine Kommunikation mit IPSec erfordert, müssen Sie auf dem Visual Studio-Hostcomputer und dem Remotecomputer zusätzliche Ports öffnen.  
  
  **Webserver** Wenn Sie einen Remotewebserver debuggen, müssen Sie auf dem Remotecomputer einen zusätzlichen Port öffnen. (Für IIS, muss Port 80 geöffnet sein.)  
  
  Auf den beiden Computern muss nicht das gleiche Betriebssystem ausgeführt werden. Auf dem Visual Studio-Computer kann beispielsweise Windows 10 und auf dem Remotecomputer Windows Server 2012 R2 ausgeführt werden.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports auf dem Remotecomputer, die das Remotedebuggen ermöglichen  
  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|   
|-|-|-|-|  
|4022|Eingehende|TCP|Für Visual Studio 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter [Visual Studio Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).|  
|4023|Eingehende|TCP|Für Visual Studio 2017. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. (Nur verwendet, um remote Debuggen von 64-Bit-Version des Remotedebuggers eine 32-Bit-Prozess.) Weitere Informationen finden Sie unter [Visual Studio Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).| 
|3702|Ausgehend|UDP|(Optional) Erforderlich für die remotedebuggerermittlung.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Konfigurieren von Ports in der Windows-Firewall  

Bei der Installation von Visual Studio oder der Remotedebugger versucht die Software, die richtigen Ports öffnen. Aber in einigen Szenarios (z. B. mit einer Drittanbieter-Firewall), müssen Sie manuell einen Port zu öffnen. Um sicherzustellen, dass die Ports geöffnet sind, finden Sie unter [Problembehandlung](#troubleshooting). Einige Anweisungen zum Öffnen eines Ports können bei älteren Versionen von Windows unterschiedlich sein.

Zum Öffnen eines Ports:
  
1. Öffnen der **starten** Menü, und suchen Sie **Windows-Firewall mit erweiterter Sicherheit**.

2. Wählen Sie dann **Eingangsregeln > neue Regel > Port**, und klicken Sie dann auf **Weiter**. (Wählen Sie für ausgehende Regeln **Ausgangsregeln** stattdessen.)

3. Wählen Sie entweder **TCP** oder **UDP**, je nachdem, auf die Portnummer an.

4. Klicken Sie unter **bestimmte lokale Ports**, geben Sie die Portnummer, und klicken Sie auf **Weiter**.

5. Klicken Sie auf **Allow the Connection** , und klicken Sie dann in der Liste **Weiter**.

6. Wählen Sie eine oder mehrere Netzwerktypen für den Port zu aktivieren, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
7. Fügen Sie den Namen (z. B. **"msvsmon"**, **IIS**, oder **Web Deploy**) für die Regel und auf **Fertig stellen**.

    Daraufhin sollte die neue Regel in der Liste von Regeln für eingehende oder ausgehende Regeln.

## <a name="troubleshooting"></a>Problembehandlung bei

Wenn Sie Probleme beim Anfügen an Ihre app mit dem Remotedebugger haben, müssen Sie möglicherweise um sicherzustellen, dass die richtigen Ports geöffnet sind.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Stellen Sie sicher, dass die Ports in der Windows-Firewall auf dem Visual Studio-Computer geöffnet sind  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Auf Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **app** verwendet wird, auf Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet wird.  In den folgenden Schritten verwenden wir das Wort **app**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  Suchen Sie in der Liste **Zugelassene Apps und Features** nach **Visual Studio - Remotedebuggerermittlung**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio - Remotedebuggerermittlung** nicht aufgeführt ist, klicken Sie auf **Andere App zulassen**. Wenn Sie noch, dass es in sehen der **fügen Sie eine app** Fenster klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  In der **zugelassene apps und Features** Liste **Visual Studio Remote Debugger**. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Stellen Sie sicher, dass die Ports in der Windows-Firewall auf dem Remotecomputer geöffnet sind  
 Die Komponenten für das Remotedebuggen können auf dem Remotecomputer installiert sein oder aus einem freigegebenen Verzeichnis ausgeführt werden. In beiden Fällen muss die Firewall des Remotecomputers konfiguriert werden. Die Komponenten für das Remotedebuggen befinden sich an folgendem Speicherort:  
  
 **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**  
  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Auf Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **app** verwendet wird, auf Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet wird.  In den folgenden Schritten verwenden wir das Wort **app**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  In der **zugelassene apps und Features** auflisten, suchen Sie nach **Visual Studio Remote Debugger**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio Remote Debugger** ist nicht aufgeführt ist, klicken Sie auf **andere app zulassen**. Wenn Sie noch, dass es in sehen der **ein app-Fenster "hinzufügen"**, klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  In der **zulässige apps** Liste **Visual Studio Remote Debugger**. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Verwalteten oder systemeigenen Kompatibilitätsmodus) Klicken Sie auf dem Remotecomputer zusätzliche Ports öffnen

Wenn Sie für den Debugger im Kompatibilitätsmodus verwenden (**Tools > Optionen > Debugging**), müssen zusätzliche Ports geöffnet werden. Kompatibilitätsmodus kann eine ältere Version des Debuggers, und verschiedene Ports sind erforderlich.

> [!NOTE]
> Die ältere Version des Debuggers wird der Debugger von Visual Studio 2010.
  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|  
|-|-|-|-|  
|135, 139, 445|Ausgehend|TCP|Erforderlich.|  
|137, 138|Ausgehend|UDP|Erforderlich.|  
|500, 4500|Ausgehend|UDP|Erforderlich, wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec vorschreibt.|  
|80|Ausgehend|TCP|Erforderlich für das Webserverdebuggen.|
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging](../debugger/remote-debugging.md)