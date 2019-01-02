---
title: 'Fehler: Der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann nicht an diesem Computer herstellen | Microsoft-Dokumentation'
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
manager: ghogen
ms.openlocfilehash: 7f1e457829f7b6ab5050a02bd8f20e1c51d5df14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798468"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Fehler: Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann keine Rückverbindung mit diesem Computer herstellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
-   Das Konto muss auch erteilt werden die `Log on as a service` Berechtigungen auf dem Remotecomputer, der verwendet die **Local Security Policy** Verwaltungstool.  
  
-   Bei Verwendung eines lokalen Kontozugriffs auf den Computer müssen Sie den Visual Studio-Remotedebugdienst unter einem lokalen Konto verwenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Visual Studio-Remotedebugdienst ordnungsgemäß auf dem Remotecomputer eingerichtet ist. Weitere Informationen finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2.  Führen Sie den Remotedebugdienst unter einem Konto aus, über das auf den Hostcomputer des Debuggers zugegriffen werden kann (siehe obige Tabelle).  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>So fügen Sie die Berechtigung "Als Dienst anmelden" hinzu  
  
1.  Auf der **starten** Menü wählen **Systemsteuerung**.  
  
2.  Wählen Sie in der Systemsteuerung **klassische Ansicht**, falls erforderlich.  
  
3.  Doppelklicken Sie auf **Verwaltung**.  
  
4.  Doppelklicken Sie im Fenster Verwaltung auf **Local Security Policy**.  
  
5.  In der **lokale Sicherheitseinstellungen** Fenster, erweitern Sie die **lokale Richtlinien** Ordner.  
  
6.  Klicken Sie auf **Zuweisen von Benutzerrechten**.  
  
7.  In der **Richtlinie** Spalte doppelklicken Sie auf **Anmelden als Dienst** an der aktuellen lokalen Gruppenrichtlinien-Zuweisungen in der **Anmelden als Dienst** Dialogfeld.  
  
8.  Um neue Benutzer hinzuzufügen, klicken Sie auf die **Benutzer oder Gruppe hinzufügen** Schaltfläche.  
  
9. Wenn Sie nach dem Hinzufügen der Benutzer sind, klicken Sie auf **OK**.  
  
### <a name="to-work-around-this-error"></a>So umgehen Sie diesen Fehler  
  
-   Führen Sie den Remotedebugmonitor als Anwendung statt als Dienst aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



