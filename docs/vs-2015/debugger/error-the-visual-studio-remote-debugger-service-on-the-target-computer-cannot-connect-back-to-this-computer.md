---
title: 'Fehler: der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann keine Verbindung mit diesem Computer herstellen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a7de83f118b38d9a3c71f1c7e7febf48e0f5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520509"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Fehler: Der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann die Verbindung mit diesem Computer nicht wiederherstellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler besagt, dass der Visual Studio-Remotedebugdienst unter einem Benutzerkonto ausgeführt wird, das beim Versuch, eine Verbindung zu dem Computer herzustellen, von dem aus Sie debuggen, nicht authentifiziert werden kann.  
  
 Die folgende Tabelle zeigt, welche Konten auf den Computer zugreifen können:  
  
|Szenario|LocalSystem-Konto|Domänenkonto|Lokale Konten mit identischem Benutzernamen und -kennwort auf beiden Computern|  
|-|-|-|-|-|  
|Beide Computer in derselben Domäne|Ja|Ja|Ja|  
|Beide Computer in Domänen mit bidirektionaler Vertrauenswürdigkeit|Nein|Nein|Ja|  
|Einer oder beide Computer in einer Arbeitsgruppe|Nein|Nein|Ja|  
|Computer in einer anderen Domäne|Nein|Nein|Ja|  
  
 Außerdem:  
  
- Das Konto, unter dem Sie den Visual Studio-Remotedebugdienst ausführen, sollte Administratorrechte auf dem Remotecomputer besitzen, damit alle Prozesse gedebuggt werden können.  
  
- Dem Konto muss auf dem Remotecomputer außerdem mithilfe des Verwaltungstools **Lokale Sicherheitsrichtlinie** die Berechtigung `Log on as a service` gewährt werden.  
  
- Bei Verwendung eines lokalen Kontozugriffs auf den Computer müssen Sie den Visual Studio-Remotedebugdienst unter einem lokalen Konto verwenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Stellen Sie sicher, dass der Visual Studio-Remotedebugdienst ordnungsgemäß auf dem Remotecomputer eingerichtet ist. Weitere Informationen finden Sie unter [Einrichten der Remotetools auf dem Gerät](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2. Führen Sie den Remotedebugdienst unter einem Konto aus, über das auf den Hostcomputer des Debuggers zugegriffen werden kann (siehe obige Tabelle).  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>So fügen Sie die Berechtigung "Als Dienst anmelden" hinzu  
  
1. Klicken Sie im Menü **Start** auf **Systemsteuerung**.  
  
2. Wählen Sie in der Systemsteuerung die **Klassische Ansicht** aus (falls erforderlich).  
  
3. Doppelklicken Sie auf **Verwaltung**.  
  
4. Doppelklicken Sie im Fenster „Verwaltung“ auf **Lokale Sicherheitsrichtlinie**.  
  
5. Erweitern Sie im Fenster **Lokale Sicherheitseinstellungen** den Ordner **Lokale Richtlinien**.  
  
6. Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
7. Doppelklicken Sie in der Spalte **Richtlinie** auf **Anmelden als Dienst**, um sich im Dialogfeld **Anmelden als Dienst** die aktuell zugewiesenen lokalen Gruppenrichtlinien anzeigen zu lassen.  
  
8. Klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**, um neue Benutzer hinzuzufügen.  
  
9. Klicken Sie auf **OK**, wenn Sie fertig sind.  
  
### <a name="to-work-around-this-error"></a>So umgehen Sie diesen Fehler  
  
- Führen Sie den Remotedebugmonitor als Anwendung statt als Dienst aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Remote Debugging-Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
