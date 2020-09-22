---
title: 'Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09f018982b81535ae23eafe7158aa88c0b6b08a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840983"
---
# <a name="error-workgroup-remote-logon-failure"></a>Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inhalt dieses Fehlers:  
  
 Fehler bei der Anmeldung: Unbekannter Benutzername oder ungültiges Kennwort.  
  
 **Ursache**  
  
 Dieser Fehler kann auftreten, wenn Sie von einem Computer in einer Arbeitsgruppe debuggen und versuchen, eine Verbindung mit einem Remotecomputer herzustellen. Mögliche Ursachen sind:  
  
- Es gibt kein Konto auf dem Remotecomputer mit übereinstimmendem Namen und Kennwort.  
  
- Wenn der Visual Studio-Computer und der Remotecomputer sich beide in Arbeitsgruppen befinden, wird dieser Fehler u.U. aufgrund der Standardeinstellung für die **Lokale Sicherheitsrichtlinie** auf dem Remotecomputer ausgelöst. Die Standardeinstellung für die **Lokale Sicherheitsrichtlinie** ist **Nur Gast – lokale Benutzer authentifizieren sich als Gast**. Um in diesem Setup zu debuggen, müssen Sie die Einstellung auf dem Remotecomputer in **Klassisch – lokale Benutzer authentifizieren sich als sie selbst** ändern.  
  
> [!NOTE]
> Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.  
  
### <a name="to-open-the-local-security-policy-window"></a>So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"  
  
1. Starten Sie das Microsoft Management Console-Snap-In **secpol.msc**. Geben Sie "secpol.msc" in die Windows-Suche, das Windows-Ausführungsfeld oder in einer Eingabeaufforderung ein.  
  
### <a name="to-add-user-rights-assignments"></a>So fügen Sie Benutzerrechtezuordnungen hinzu  
  
1. Öffnen Sie die Speicherorte  
  
2. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
3. Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
4. Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
5. Doppelklicken Sie in der Spalte **Richtlinie** auf **Debuggen von Programmen**, um die aktuell zugewiesenen Richtlinien der lokalen Gruppe im Dialogfeld **Lokale Sicherheitsrichtlinieneinstellung** anzuzeigen.  
  
     ![Benutzerrechte für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**, um neue Benutzer hinzuzufügen.  
  
### <a name="to-change-the-sharing-and-security-model"></a>So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell  
  
1. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
2. Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
3. Klicken Sie auf **Sicherheitsoptionen**.  
  
4. Doppelklicken Sie in der Spalte **Richtlinie** auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
5. Ändern Sie im Dialogfeld **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** den Wert in **Klassisch – lokale Benutzer authentifizieren sich als sie selbst**, und klicken Sie auf **Übernehmen**.  
  
     ![Sicherheitsoptionen für Richtlinie zur lokalen Sicherheit](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Remote Debugging-Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
