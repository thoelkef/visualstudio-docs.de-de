---
title: 'Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723666"
---
# <a name="error-workgroup-remote-logon-failure"></a>Fehler: Fehler bei Remoteanmeldung von Arbeitsgruppe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inhalt dieses Fehlers:  
  
 Fehler bei der Anmeldung: Unbekannter Benutzername oder ungültiges Kennwort.  
  
 **Ursache**  
  
 Dieser Fehler kann auftreten, wenn Sie von einem Computer in einer Arbeitsgruppe debuggen und versuchen, eine Verbindung mit einem Remotecomputer herzustellen. Mögliche Ursachen sind:  
  
-   Es gibt kein Konto auf dem Remotecomputer mit übereinstimmendem Namen und Kennwort.  
  
-   Wenn es sich bei dem Visual Studio-Computer und dem remote-Computer in Arbeitsgruppen befinden, kann dieser Fehler auftreten, aufgrund der Standardeinstellung **Local Security Policy** festlegen, auf dem Remotecomputer. Die Standardeinstellung für die **Local Security Policy** Einstellung **nur Gast - lokale Benutzer authentifizieren sich als Gast**. Um in diesem Setup zu debuggen, müssen Sie die Einstellung auf dem Remotecomputer zu ändern **Klassisch - lokale Benutzer authentifizieren sich als Sie selbst**.  
  
> [!NOTE]
>  Sie müssen Administrator sein, um die folgenden Aufgaben ausführen zu können.  
  
### <a name="to-open-the-local-security-policy-window"></a>So öffnen Sie das Fenster "Lokale Sicherheitsrichtlinie"  
  
1.  Starten Sie den **secpol.msc** Microsoft Management Console-Snap-in. Geben Sie "secpol.msc" in die Windows-Suche, das Windows-Ausführungsfeld oder in einer Eingabeaufforderung ein.  
  
### <a name="to-add-user-rights-assignments"></a>So fügen Sie Benutzerrechtezuordnungen hinzu  
  
1.  Öffnen Sie die Speicherorte  
  
2.  Öffnen der **Local Security Policy** Fenster.  
  
3.  Erweitern Sie die **lokale Richtlinien** Ordner.  
  
4.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
5.  In der **Richtlinie** Spalte doppelklicken Sie auf **Debuggen von Programmen** aktuell lokale Gruppe zugewiesenen Richtlinien an die **lokale Sicherheitsrichtlinie einstellen** im Dialogfeld.  
  
     ![Lokalen Benutzerrechte für Richtlinie](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Um neue Benutzer hinzuzufügen, klicken Sie auf die **Benutzer oder Gruppe hinzufügen** Schaltfläche.  
  
### <a name="to-change-the-sharing-and-security-model"></a>So ändern Sie das Modell für gemeinsame Nutzung und das Sicherheitsmodell  
  
1.  Öffnen der **Local Security Policy** Fenster.  
  
2.  Erweitern Sie die **lokale Richtlinien** Ordner.  
  
3.  Klicken Sie auf **Sicherheitsoptionen**.  
  
4.  In der **Richtlinie** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
5.  In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld ändern den Wert, der **Klassisch - lokale Benutzer authentifizieren sich als Sie selbst** , und klicken Sie auf die **übernehmen**Schaltfläche.  
  
     ![Sicherheitsoptionen für lokale Richtlinie](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



