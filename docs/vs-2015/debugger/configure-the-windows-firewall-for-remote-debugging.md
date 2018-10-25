---
title: Die Windows-Firewall für Remotedebuggen konfigurieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96b4e4cc929dc7941fac5e8a7f090e701fe2810f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935392"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurieren der Windows-Firewall für das Remotedebuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird die Konfiguration der Firewall für das Remotedebuggen auf Computern mit folgenden Betriebssystemen beschrieben:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Wenn das Netzwerk, in dem Sie debuggen, nicht durch eine Firewall geschützt ist, ist diese Konfiguration nicht erforderlich. Andernfalls müssen auf dem Computer, auf dem Visual Studio gehostet wird, und auf dem Remotecomputer, auf dem das Debuggen erfolgen soll, Änderungen an der Konfiguration der Firewall vorgenommen werden.  
  
  **IPSec** Wenn Ihr Netzwerk eine Kommunikation mit IPSec erfordert, müssen Sie auf dem Visual Studio-Hostcomputer und dem Remotecomputer zusätzliche Ports öffnen.  
  
  **Webserver** Wenn Sie einen Remotewebserver debuggen, müssen Sie auf dem Remotecomputer einen zusätzlichen Port öffnen.  
  
  Auf den beiden Computern muss nicht das gleiche Betriebssystem ausgeführt werden. Auf dem Visual Studio-Computer kann beispielsweise Windows 10 und auf dem Remotecomputer Windows Server 2012 R2 ausgeführt werden.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>So konfigurieren Sie die Windows-Firewall auf dem Visual Studio-Computer  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Bei Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet, bei Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **App** verwendet.  In den folgenden Schritten verwenden wir das Wort **App**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  Suchen Sie in der Liste **Zugelassene Apps und Features** nach **Visual Studio - Remotedebuggerermittlung**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio - Remotedebuggerermittlung** nicht aufgeführt ist, klicken Sie auf **Andere App zulassen**. Wenn Sie noch, dass es in sehen der **fügen Sie eine app** Fenster klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  Wählen Sie in der Liste **Zugelassene Apps und Features** den Eintrag **Visual Studio - Remotedebugmonitor**aus. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>So öffnen Sie einen Port auf dem Visual Studio-Computer, um die Ermittlung zu aktivieren  
 Sie müssen UDP-Port 3702 für eingehende Anforderungen zulassen, um die Ermittlung der Computer zu ermöglichen, auf denen der Remotedebugger ausgeführt wird. Das Hinzufügen dieses Ports wird unter "Konfigurieren von Ports in einer Firewall" beschrieben.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>So konfigurieren Sie die Windows-Firewall des Remotecomputers für das Remotedebuggen  
 Die Komponenten für das Remotedebuggen können auf dem Remotecomputer installiert sein oder aus einem freigegebenen Verzeichnis ausgeführt werden. In beiden Fällen muss die Firewall des Remotecomputers konfiguriert werden. Die Komponenten für das Remotedebuggen befinden sich an folgendem Speicherort:  
  
 **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**  
  
 Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig bei den verschiedenen Betriebssystemen. Bei Windows 7 oder Windows Server 2008 wird das Wort **Programm** verwendet, bei Windows 8/8.1, Windows 10 und Windows Server 2012 wird das Wort **App** verwendet.  In den folgenden Schritten verwenden wir das Wort **App**.  
  
1.  Öffnen Sie die Windows-Firewall. (Geben Sie im Menü **Start** im Suchfeld **Windows-Firewall**ein.)  
  
2.  Klicken Sie auf **Eine App oder ein Feature durch die Windows-Firewall zulassen**.  
  
3.  Suchen Sie in der Liste **Zugelassene Apps und Features** nach **Visual Studio - Remotedebugmonitor**. Vergewissern Sie sich, dass diese Option (sofern aufgeführt) und mindestens ein Netzwerktyp ausgewählt sind.  
  
4.  Wenn **Visual Studio - Remotedebugmonitor** nicht aufgeführt ist, klicken Sie auf **Andere App zulassen**. Wenn Sie noch, dass es in sehen der **ein app-Fenster "hinzufügen"**, klicken Sie auf **Durchsuchen** und navigieren Sie zu  **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger**. Suchen Sie den entsprechenden Ordner für die Anwendung (x86, x64, Appx), und wählen Sie dann **msvsmon.exe**aus. Klicken Sie anschließend auf **Hinzufügen**.  
  
5.  Wählen Sie in der Liste **Zugelassene Apps** den Eintrag **Visual Studio - Remotedebugmonitor**aus. Wählen Sie einen oder mehrere Netzwerktypen (**Domäne, Heim/Arbeitsplatz (Privat), Öffentlich**) für die Kommunikation mit dem Remotedebugmonitor aus. Ein Typ muss das Netzwerk beinhalten, mit dem der Visual Studio-Computer verbunden ist.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports auf dem Remotecomputer, die das Remotedebuggen ermöglichen  
  
|||||  
|-|-|-|-|  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|  
|3702|Ausgehend|UDP|Erforderlich für die Remotedebuggerermittlung.|  
|4020||TCP|Für VS 2015. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter "Visual Studio-Remotedebugger – Portzuweisungen".|  
|4021||TCP|Für VS 2015. Die Portnummer wird für jede Visual Studio-Version um 2 erhöht. Weitere Informationen finden Sie unter "Visual Studio-Remotedebugger – Portzuweisungen".|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Ports auf dem Remotecomputer, die das Remotedebuggen im verwalteten oder systemeigenen Kompatibilitätsmodus zulassen  
  
|||||  
|-|-|-|-|  
|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|  
|135, 139, 445|Ausgehend|TCP|Erforderlich.|  
|137, 138|Ausgehend|UDP|Erforderlich.|  
|500, 4500|Ausgehend|UDP|Erforderlich, wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec vorschreibt.|  
|80|Ausgehend|TCP|Erforderlich für das Webserverdebuggen.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Konfigurieren von Ports in der Windows-Firewall  
  
1.  Suchen Sie im Menü **Start** nach **Windows-Firewall mit erweiterter Sicherheit**.  
  
2.  Klicken Sie auf **Eingehende Regeln** oder **Ausgehende Regeln** , und klicken Sie dann in der Liste **Aktionen** auf **Neue Regel** .  
  
3.  Wählen Sie auf der Seite **Regeltyp** die Option **Port** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Protokoll und Ports** das Protokoll für den Port (TCP oder UDP) aus. Wählen Sie **Bestimmte lokale Ports** aus,  und geben Sie eine oder mehrere Portnummern ein, die Sie für das Protokoll aktivieren möchten. Trennen Sie die einzelnen Nummern durch Kommas. Klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Aktion** die Option **Verbindung zulassen** aus, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Profil** einen oder mehrere Netzwerktypen aus, die für den Port aktiviert werden sollen. Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist. Klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie auf der Seite **Name** einen Namen für die Regel ein, und klicken Sie dann auf **Fertig stellen**.  
  
8.  Daraufhin sollte die neue Regel in der Liste **Eingehende Regeln** bzw. **Ausgehende Regeln** angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging](../debugger/remote-debugging.md)



