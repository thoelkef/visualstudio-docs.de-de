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
ms.openlocfilehash: bcca366cb06916811a66da9f168684e704c50714
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056002"
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
>  Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.  
  
### <a name="to-open-the-local-security-policy-window"></a>So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"  
  
1. Starten Sie das Microsoft Management Console-Snap-In **secpol.msc**. Geben Sie "secpol.msc" in die Windows-Suche, das Windows-Ausführungsfeld oder in einer Eingabeaufforderung ein.  
  
### <a name="to-add-user-rights-assignments"></a>So fügen Sie Benutzerrechtezuordnungen hinzu  
  
1. Öffnen Sie die Speicherorte  
  
2. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
3. Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
4. Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
5. Doppelklicken Sie in der Spalte **Richtlinie** auf **Debuggen von Programmen**, um die aktuell zugewiesenen Richtlinien der lokalen Gruppe im Dialogfeld **Lokale Sicherheitsrichtlinieneinstellung** anzuzeigen.  
  
     ![Lokalen Benutzerrechte für Richtlinie](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**, um neue Benutzer hinzuzufügen.  
  
### <a name="to-change-the-sharing-and-security-model"></a>So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell  
  
1. Öffnen Sie das Fenster **Lokale Sicherheitsrichtlinie**.  
  
2. Erweitern Sie den Ordner **Lokale Richtlinien**.  
  
3. Klicken Sie auf **Sicherheitsoptionen**.  
  
4. In der **Richtlinie** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
5. In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld ändern den Wert, der **Klassisch - lokale Benutzer authentifizieren sich als Sie selbst** , und klicken Sie auf die **übernehmen** Schaltfläche.  
  
     ![Sicherheitsoptionen für lokale Richtlinie](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
