---
title: "Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe | Microsoft Docs"
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
  - "vs.debug.error.workgroup_remote_logon_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Fehler bei der Anmeldung, Remotedebuggen"
  - "Remotedebuggen, Fehler bei der Anmeldung"
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inhalt dieses Fehlers:  
  
 Fehler bei der Anmeldung: Unbekannter Benutzername oder ungültiges Kennwort.  
  
 **Ursache**  
  
 Dieser Fehler kann auftreten, wenn Sie von einem Computer in einer Arbeitsgruppe debuggen und versuchen, eine Verbindung mit einem Remotecomputer herzustellen.  Mögliche Ursachen sind:  
  
-   Es gibt kein Konto auf dem Remotecomputer mit übereinstimmendem Namen und Kennwort.  
  
-   Wenn der Visual Studio\-Computer und der Remotecomputer sich beide in Arbeitsgruppen befinden, wird dieser Fehler u. U. aufgrund der Standardeinstellung für die **Lokale Sicherheitsrichtlinie** auf dem Remotecomputer ausgelöst.  Die Standardeinstellung für die **Lokale Sicherheitsrichtlinie** ist **Nur Gast \- lokale Benutzer authentifizieren sich als Gast**.  Um in diesem Setup zu debuggen, müssen Sie die Einstellung auf dem Remotecomputer in **Klassisch \- lokale Benutzer authentifizieren sich als sie selbst** ändern.  
  
> [!NOTE]
>  Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.  
  
### So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"  
  
1.  Starten Sie das Microsoft Management Console\-Snap\-In **secpol.msc**.  Geben Sie "secpol.msc" in die Windows\-Suche, das Windows\-Ausführungsfeld oder in einer Eingabeaufforderung ein.  
  
### So fügen Sie Benutzerrechtezuordnungen hinzu  
  
1.  Öffnen Sie die Speicherorte  
  
2.  Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
3.  Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
4.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
5.  Doppelklicken Sie in der Spalte **Richtlinie** auf **Debuggen von Programmen**, um die aktuell zugewiesenen Richtlinien der lokalen Gruppe im Dialogfeld **Lokale Sicherheitsrichtlinie** anzuzeigen.  
  
     ![Benutzerrechte für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG\_ERR\_LocalSecurityPolicy\_UserRightsDebugPrograms")  
  
6.  Um neue Benutzer hinzuzufügen, klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**.  
  
### So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell  
  
1.  Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
2.  Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
3.  Klicken Sie auf **Sicherheitsoptionen**.  
  
4.  Doppelklicken Sie in der Spalte **Richtlinie** auf die Option **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
5.  Ändern Sie im Dialogfeld **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** den Wert in **Klassisch \- lokale Benutzer authentifizieren sich als sie selbst**, und klicken Sie auf **Übernehmen**.  
  
     ![Sicherheitsoptionen für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG\_ERR\_LocalSecurityPolicy\_SecurityOptions\_NetworkAccess")  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)