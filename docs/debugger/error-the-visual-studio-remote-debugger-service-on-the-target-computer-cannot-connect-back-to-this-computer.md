---
title: 'Fehler: Der Visual Studio-Remotedebugger-Dienst auf dem Zielcomputer kann keine Verbindung hergestellt wieder auf diesen Computer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd2db1e4bf5b87d12eb5d5ffcf94d06e142516
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471751"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Fehler: Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann keine Rückverbindung mit diesem Computer herstellen
Dieser Fehler besagt, dass der Visual Studio-Remotedebugdienst unter einem Benutzerkonto ausgeführt wird, das beim Versuch, eine Verbindung zu dem Computer herzustellen, von dem aus Sie debuggen, nicht authentifiziert werden kann.  
  
 Die folgende Tabelle zeigt, welche Konten auf den Computer zugreifen können:  
  
|||||  
|-|-|-|-|  
||LocalSystem-Konto|Domänenkonto|Lokale Konten mit identischem Benutzernamen und -kennwort auf beiden Computern|  
|Beide Computer in derselben Domäne|Ja|Ja|Ja|  
|Beide Computer in Domänen mit bidirektionaler Vertrauenswürdigkeit|Nein|Nein|Ja|  
|Einer oder beide Computer in einer Arbeitsgruppe|Nein|Nein|Ja|  
|Computer in einer anderen Domäne|Nein|Nein|Ja|  
  
 Außerdem:  
  
-   Das Konto, unter dem Sie den Visual Studio-Remotedebugdienst ausführen, sollte Administratorrechte auf dem Remotecomputer besitzen, damit alle Prozesse gedebuggt werden können.  
  
-   Das Konto muss außerdem erteilt werden die `Log on as a service` Berechtigung auf dem Remotecomputer, die verwendet die **lokale Sicherheitsrichtlinie** Verwaltungstool.  
  
-   Bei Verwendung eines lokalen Kontozugriffs auf den Computer müssen Sie den Visual Studio-Remotedebugdienst unter einem lokalen Konto verwenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Visual Studio-Remotedebugdienst ordnungsgemäß auf dem Remotecomputer eingerichtet ist. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
2.  Führen Sie den Remotedebugdienst unter einem Konto aus, über das auf den Hostcomputer des Debuggers zugegriffen werden kann (siehe obige Tabelle).  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>So fügen Sie die Berechtigung "Als Dienst anmelden" hinzu  
  
1.  Auf der **starten** Menü wählen **Systemsteuerung**.  
  
2.  Wählen Sie in der Systemsteuerung **klassische Ansicht**, falls erforderlich.  
  
3.  Doppelklicken Sie auf **Verwaltung**.  
  
4.  Doppelklicken Sie im Fenster Verwaltung auf **lokale Sicherheitsrichtlinie**.  
  
5.  In der **lokale Sicherheitseinstellungen** Fenster, erweitern Sie die **lokale Richtlinien** Ordner.  
  
6.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
7.  In der **Richtlinie** Spalte doppelklicken Sie auf **Anmelden als Dienst** zum Anzeigen der aktuellen lokaler Gruppenrichtlinien-Zuweisungen in der **Anmelden als Dienst** (Dialogfeld).  
  
8.  Um neue Benutzer hinzuzufügen, klicken Sie auf die **Benutzer oder Gruppe hinzufügen** Schaltfläche.  
  
9. Wenn Sie das Hinzufügen von Benutzern fertig sind, klicken Sie auf **OK**.  
  
### <a name="to-work-around-this-error"></a>So umgehen Sie diesen Fehler  
  
-   Führen Sie den Remotedebugmonitor als Anwendung statt als Dienst aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)