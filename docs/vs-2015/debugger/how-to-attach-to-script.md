---
title: 'Vorgehensweise: Anfügen an ein Skript | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 76418913aa725a7858f292d625cb7584b62694e5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001515"
---
# <a name="how-to-attach-to-script"></a>Vorgehensweise: Anfügen an ein Skript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie der Visual Studio-Debugger zum Debuggen manuell an eine Skriptdatei angefügt wird.  
  
### <a name="to-attach-to-a-running-process"></a>So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1. Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**. (Wenn kein Projekt geöffnet ist, wählen Sie den Befehl **An den Prozess anhängen** über das Menü **Extras**.)  
  
2. Überprüfen Sie im Dialogfeld **An den Prozess anhängen** die Liste **Verfügbare Prozesse**, und suchen Sie den Skriptprozess, mit dem Sie eine Verbindung herstellen möchten. Sie können Skriptprozesse anhand der Spalte **Typ** identifizieren.  
  
   1.  Wenn der zu debuggende Prozess auf einem anderen Computer ausgeführt wird, müssen Sie zunächst diesen Remotecomputer auswählen. Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen eines Remotecomputers](http://msdn.microsoft.com/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2.  Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .  
  
   3.  Wenn Sie über eine **Remotedesktopverbindung** verbunden sind, aktivieren Sie das Kontrollkästchen **Prozesse in allen Sitzungen anzeigen**.  
  
3. Klicken Sie auf den Prozess, mit dem eine Verbindung hergestellt werden soll.  
  
4. In der **Anfügen an** Feld sollte **Skriptcode** oder **automatische: Skriptcode**. Wenn etwas anderes angezeigt wird, führen Sie die folgenden Schritte aus:  
  
   1.  Klicken Sie auf **Auswählen**.  
  
   2.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen**, und wählen Sie **Skript** aus.  
  
   3.  Klicken Sie auf **OK**.  
  
5. Klicken Sie auf **Anfügen**aus.  
  
    Zu diesem Zeitpunkt kann eine Warnung mit dem Hinweis ausgegeben werden, dass das Skriptdebuggen in Internet Explorer deaktiviert ist. In diesem Fall finden Sie unter [Warnung: Skriptdebuggen deaktiviert](../debugger/warning-script-debugging-disabled.md).  
  
   Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Deshalb ist der Inhalt u. U. nicht immer aktuell. Sie können diese Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf die Schaltfläche **Aktualisieren**.  
  
   Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm in der Symbolleiste Debugspeicherort festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen des aktuellen Prozesses](http://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Alle Ausführungsbefehle des Menüs **Debuggen** wirken sich auf das aktive Programm aus. Sie können jedes debuggte Programm über das Dialogfeld "Prozesse" unterbrechen. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Beim Versuch, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
 In einigen Fällen werden beim Debuggen in einer Terminaldienstesitzung (Remotedesktop) in der Liste Verfügbare Prozesse nicht alle verfügbaren Prozesse angezeigt. Wenn Visual Studio unter [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] oder höher mit einem eingeschränkten Benutzerkonto ausgeführt wird, werden in der Liste Verfügbare Prozesse keine Prozesse in Sitzung 0 angezeigt, die für Dienste und andere Serverprozesse einschließlich w3wp.exe verwendet wird. Sie können dieses Problem beheben, indem Sie Visual Studio unter einem Administratorkonto oder an der Serverkonsole, und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit eine Verbindung mit dem Prozess herstellen, indem Sie „vsjitdebugger.exe -p ProcessId“ in der Windows-Befehlszeile eingeben. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um die Datei „tlist.exe“ abzurufen, laden Sie die Debugtools für Windows von [Windows Hardware Developer Central](https://developer.microsoft.com/windows/hardware) herunter und installieren diese.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von clientseitigen Skripts](../debugger/client-side-script-debugging.md)   
 [Attach to running processes (Anfügen an laufende Prozesse)](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Debuggersicherheit](../debugger/debugger-security.md)
