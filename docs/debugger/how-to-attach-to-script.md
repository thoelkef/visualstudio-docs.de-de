---
title: "Gewusst wie: Anf&#252;gen an ein Skript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Prozesse, Anfügen an ein Skript"
  - "Remotedebuggen, Anfügen an ein Skript"
  - "Skriptdebuggen, Anfügen an ein Skript"
  - "Skript, Anhängen an"
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Anf&#252;gen an ein Skript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie der Visual Studio\-Debugger zum Debuggen manuell an eine Skriptdatei angefügt wird.  
  
### So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1.  Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**. \(Wenn kein Projekt geöffnet ist, wählen Sie den Befehl **An den Prozess anhängen** über das Menü **Extras**.\)  
  
2.  Überprüfen Sie im Dialogfeld **An den Prozess anhängen** die Liste **Verfügbare Prozesse**, und suchen Sie den Skriptprozess, mit dem Sie eine Verbindung herstellen möchten.  Sie können Skriptprozesse anhand der Spalte **Typ** identifizieren.  
  
    1.  Wenn der zu debuggende Prozess auf einem anderen Computer ausgeführt wird, müssen Sie zunächst diesen Remotecomputer auswählen.  Weitere Informationen finden Sie unter [How to: Select a Remote Computer](http://msdn.microsoft.com/de-de/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen**.  
  
    3.  Wenn Sie über eine **Remotedesktopverbindung** verbunden sind, aktivieren Sie das Kontrollkästchen **Prozesse in allen Sitzungen anzeigen**.  
  
3.  Klicken Sie auf den Prozess, mit dem eine Verbindung hergestellt werden soll.  
  
4.  Im Feld **Anfügen an** sollte **Skriptcode** oder **Automatisch: Skriptcode** angezeigt werden.  Wenn etwas anderes angezeigt wird, führen Sie die folgenden Schritte aus:  
  
    1.  Klicken Sie auf **Auswählen**.  
  
    2.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen**, und wählen Sie **Skript** aus.  
  
    3.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf **Anfügen**.  
  
     Zu diesem Zeitpunkt kann eine Warnung mit dem Hinweis ausgegeben werden, dass das Skriptdebuggen in Internet Explorer deaktiviert ist.  In diesem Fall informieren Sie sich unter [Warnung: Skriptdebuggen deaktiviert](../debugger/warning-script-debugging-disabled.md).  
  
 Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt.  Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden.  Deshalb ist der Inhalt u. U. nicht immer aktuell.  Sie können diese Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf die Schaltfläche **Aktualisieren**.  
  
 Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv.  Sie können das aktive Programm in der Symbolleiste **Debugspeicherort** festlegen.  Weitere Informationen finden Sie unter [How to: Set the Current Process](http://msdn.microsoft.com/de-de/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Alle Ausführungsbefehle des Menüs **Debuggen** wirken sich auf das aktive Programm aus.  Sie können jedes debuggte Programm über das Dialogfeld "Prozesse" unterbrechen. Weitere Informationen hierzu finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Beim Versuch, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt.  Weitere Informationen finden Sie unter [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 In einigen Fällen werden beim Debuggen in einer Terminaldienstesitzung \(Remotedesktop\) in der Liste Verfügbare Prozesse nicht alle verfügbaren Prozesse angezeigt.  Wenn Visual Studio unter [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] oder höher mit einem eingeschränkten Benutzerkonto ausgeführt wird, werden in der Liste Verfügbare Prozesse keine Prozesse in Sitzung 0 angezeigt, die für Dienste und andere Serverprozesse einschließlich w3wp.exe verwendet wird.  Sie können dieses Problem beheben, indem Sie Visual Studio unter einem Administratorkonto oder an der Serverkonsole, und nicht in einer Terminaldienstesitzung ausführen.  Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit eine Verbindung mit dem Prozess herstellen, indem Sie vsjitdebugger.exe \-p ProcessId in der Windows\-Befehlszeile eingeben.  Die Prozess\-ID kann mit tlist.exe ermittelt werden.  Um die Datei "tlist.exe" abzurufen, laden Sie die Debugtools für Windows von [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651) herunter und installieren diese.  
  
## Siehe auch  
 [Debuggen von clientseitigen Skripts](../debugger/client-side-script-debugging.md)   
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)