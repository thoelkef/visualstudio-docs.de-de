---
title: 'Vorgehensweise: Anfügen an ein Skript | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6769c4061487dc4b9279ff6ef9dffd36c2614775
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-attach-to-script"></a>Gewusst wie: Anfügen an ein Skript
In diesem Thema wird erläutert, wie der Visual Studio-Debugger zum Debuggen manuell an eine Skriptdatei angefügt wird.  
  
### <a name="to-attach-to-a-running-process"></a>So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1.  Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**. (Wenn kein Projekt geöffnet ist, wählen Sie **an den Prozess anhängen** auf die **Tools** Menü.)  
  
2.  In der **an den Prozess anhängen** Dialogfeld Betrachtung der **verfügbare Prozesse** Liste und suchen Sie den Skriptprozess, die Sie anfügen möchten. Sie können Skriptprozesse identifizieren, durch einen Blick auf die **Typ** Spalte.  
  
    1.  Wenn der zu debuggende Prozess auf einem anderen Computer ausgeführt wird, müssen Sie zunächst diesen Remotecomputer auswählen. Weitere Informationen finden Sie unter [wie: Auswählen eines Remotecomputers](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .  
  
    3.  Wenn Sie über verbunden sind **Remote Desktop Connection**, wählen die **Prozesse in allen Sitzungen anzeigen** Kontrollkästchen.  
  
3.  Klicken Sie auf den Prozess, mit dem eine Verbindung hergestellt werden soll.  
  
4.  In der **zuordnen** Feld sollte eine **Skriptcode** oder **automatische: Skriptcode**. Wenn etwas anderes angezeigt wird, führen Sie die folgenden Schritte aus:  
  
    1.  Klicken Sie auf **Auswählen**.  
  
    2.  In der **Codetyp auswählen** (Dialogfeld), klicken Sie auf **diese Codetypen debuggen** , und wählen Sie **Skript**.  
  
    3.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf **Anfügen**aus.  
  
     Zu diesem Zeitpunkt kann eine Warnung mit dem Hinweis ausgegeben werden, dass das Skriptdebuggen in Internet Explorer deaktiviert ist. Wenn in diesem Fall finden Sie unter [Warnung: Skriptdebugging deaktiviert](../debugger/warning-script-debugging-disabled.md).  
  
 Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Deshalb ist der Inhalt u. U. nicht immer aktuell. Sie können die Liste aktualisieren, jederzeit aufrufen, um die aktuelle Liste der Prozesse durch Drücken von finden Sie unter der **aktualisieren** Schaltfläche.  
  
 Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm in der Symbolleiste Debugspeicherort festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen des aktuellen Prozesses](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Alle **Debuggen** Ausführungsbefehle des Menüs Auswirkungen auf das aktive Programm. Sie können alle gedebuggten Programme aus dem Dialogfeld Prozesse unterbrochen. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Beim Versuch, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess, der im Besitz eines nicht vertrauenswürdigen Benutzers kann riskant sein. Wenn die folgende Informationen verdächtig, oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 In einigen Fällen werden beim Debuggen in einer Terminaldienstesitzung (Remotedesktop) in der Liste Verfügbare Prozesse nicht alle verfügbaren Prozesse angezeigt. Wenn Visual Studio unter [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] oder höher mit einem eingeschränkten Benutzerkonto ausgeführt wird, werden in der Liste Verfügbare Prozesse keine Prozesse in Sitzung 0 angezeigt, die für Dienste und andere Serverprozesse einschließlich w3wp.exe verwendet wird. Sie können dieses Problem beheben, indem Sie Visual Studio unter einem Administratorkonto oder an der Serverkonsole, und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden problemlösungen möglich ist, wird eine dritte Möglichkeit ist, an den Prozess anfügen, indem Sie vsjitdebugger.exe eingeben --p ProcessId in der Windows-Befehlszeile. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um tlist.exe abzurufen, herunterladen und installieren Sie die Debugtools für Windows auf [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von clientseitigem Skript](../debugger/client-side-script-debugging.md)   
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgende Informationen verdächtig, oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)