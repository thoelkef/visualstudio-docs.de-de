---
title: "Fehler: Der Visual&#160;Studio-Remotedebugdienst auf dem Zielcomputer kann keine R&#252;ckverbindung mit diesem Computer herstellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.service_access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Visual&#160;Studio-Remotedebugdienst auf dem Zielcomputer kann keine R&#252;ckverbindung mit diesem Computer herstellen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Fehler besagt, dass der Visual Studio\-Remotedebugdienst unter einem Benutzerkonto ausgeführt wird, das beim Versuch, eine Verbindung zu dem Computer herzustellen, von dem aus Sie debuggen, nicht authentifiziert werden kann.  
  
 Die folgende Tabelle zeigt, welche Konten auf den Computer zugreifen können:  
  
|||||  
|-|-|-|-|  
||LocalSystem\-Konto|Domänenkonto|Lokale Konten mit identischem Benutzernamen und \-kennwort auf beiden Computern|  
|Beide Computer in derselben Domäne|Ja|Yes|Yes|  
|Beide Computer in Domänen mit bidirektionaler Vertrauenswürdigkeit|No|No|Yes|  
|Einer oder beide Computer in einer Arbeitsgruppe|No|No|Yes|  
|Computer in einer anderen Domäne|No|No|Yes|  
  
 Außerdem:  
  
-   Das Konto, unter dem Sie den Visual Studio\-Remotedebugdienst ausführen, sollte Administratorrechte auf dem Remotecomputer besitzen, damit alle Prozesse gedebuggt werden können.  
  
-   Dem Konto muss auf dem Remotecomputer außerdem mithilfe des Verwaltungstools **Lokale Sicherheitsrichtlinie** die Berechtigung `Log on as a service` gewährt werden.  
  
-   Bei Verwendung eines lokalen Kontozugriffs auf den Computer müssen Sie den Visual Studio\-Remotedebugdienst unter einem lokalen Konto verwenden.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Visual Studio\-Remotedebugdienst ordnungsgemäß auf dem Remotecomputer eingerichtet ist.  Weitere Informationen finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
2.  Führen Sie den Remotedebugdienst unter einem Konto aus, über das auf den Hostcomputer des Debuggers zugegriffen werden kann \(siehe obige Tabelle\).  
  
### So fügen Sie die Berechtigung "Als Dienst anmelden" hinzu  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**.  
  
2.  Wählen Sie in der Systemsteuerung die **Klassische Ansicht**.  
  
3.  Doppelklicken Sie auf **Verwaltung**.  
  
4.  Doppelklicken Sie im Fenster Verwaltung auf **Lokale Sicherheitsrichtlinie**.  
  
5.  Erweitern Sie im Fenster **Lokale Sicherheitseinstellungen** den Ordner **Lokale Richtlinien**.  
  
6.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
7.  Doppelklicken Sie in der Spalte **Richtlinie** auf **Anmelden als Dienst**, um die aktuell zugewiesenen Richtlinien der lokalen Gruppe im Dialogfeld **Anmelden als Dienst** anzuzeigen.  
  
8.  Um neue Benutzer hinzuzufügen, klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**.  
  
9. Wenn Sie keine weiteren Benutzer hinzufügen möchten, klicken Sie auf **OK**.  
  
### So umgehen Sie diesen Fehler  
  
-   Führen Sie den Remotedebugmonitor als Anwendung statt als Dienst aus.  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)