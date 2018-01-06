---
title: 'Fehler: Arbeitsgruppe Fehler bei Remoteanmeldung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38ec2de37279e1f383751c9652aeeac74473c50f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-workgroup-remote-logon-failure"></a>Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe
Inhalt dieses Fehlers:  
  
 Fehler bei der Anmeldung: Unbekannter Benutzername oder ungültiges Kennwort.  
  
 **Ursache**  
  
 Dieser Fehler kann auftreten, wenn Sie von einem Computer in einer Arbeitsgruppe debuggen und versuchen, eine Verbindung mit einem Remotecomputer herzustellen. Mögliche Ursachen sind:  
  
-   Es gibt kein Konto auf dem Remotecomputer mit übereinstimmendem Namen und Kennwort.  
  
-   Wenn der Visual Studio-Computer und dem Remotecomputer in Arbeitsgruppen befinden, kann dieser Fehler auftreten, aufgrund der Standardeinstellung **lokale Sicherheitsrichtlinie** auf dem Remotecomputer festlegen. Die Standardeinstellung für die **lokale Sicherheitsrichtlinie** Einstellung **nur Gast - lokale Benutzer authentifizieren sich als Gast**. Um in diesem Setup zu debuggen, müssen Sie die Einstellung auf dem Remotecomputer zu ändern **Klassisch - lokale Benutzer authentifizieren sich als Sie selbst**.  
  
> [!NOTE]
>  Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.  
  
### <a name="to-open-the-local-security-policy-window"></a>So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"  
  
1.  Starten Sie die **secpol.msc** Microsoft Management Console-Snap-in. Geben Sie "secpol.msc" in die Windows-Suche, das Windows-Ausführungsfeld oder in einer Eingabeaufforderung ein.  
  
### <a name="to-add-user-rights-assignments"></a>So fügen Sie Benutzerrechtezuordnungen hinzu  
  
1.  Öffnen der **lokale Sicherheitsrichtlinie** Fenster.  
  
2.  Erweitern Sie die **lokale Richtlinien** Ordner.  
  
3.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
4.  In der **Richtlinie** Spalte doppelklicken Sie auf **Debuggen von Programmen** zum Anzeigen der aktuellen richtlinienzuweisungen der lokalen Gruppe "in der **lokale Sicherheitsrichtlinie einstellen** (Dialogfeld).  
  
     ![Lokale Richtlinie Benutzerrechten](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  Um neue Benutzer hinzuzufügen, klicken Sie auf die **Benutzer oder Gruppe hinzufügen** Schaltfläche.  
  
### <a name="to-change-the-sharing-and-security-model"></a>So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell  
  
1.  Öffnen der **lokale Sicherheitsrichtlinie** Fenster.  
  
2.  Erweitern Sie die **lokale Richtlinien** Ordner.  
  
3.  Klicken Sie auf **Sicherheitsoptionen**.  
  
4.  In der **Richtlinie** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
5.  In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld Feld, ändern Sie den Wert auf **Klassisch - lokale Benutzer authentifizieren sich als Sie selbst** , und klicken Sie auf die **übernehmen**Schaltfläche.  
  
     ![Sicherheitsoptionen für Richtlinie lokalen Sicherheitsgruppe](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)