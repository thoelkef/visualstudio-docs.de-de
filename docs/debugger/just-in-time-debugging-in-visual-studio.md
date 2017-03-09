---
title: "Just-In-Time-Debuggen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Just-In-Time"
  - "Just-In-Time-Debuggen"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Just-In-Time-Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Just\-In\-Time\-Debuggen wird Visual Studio automatisch gestartet, wenn eine Ausnahme oder ein Absturz in einer Anwendung auftreten, die außerhalb von Visual Studio ausgeführt wird.  Auf diese Weise können Sie die Anwendung testen, wenn Visual Studio nicht ausgeführt wird und Debuggen mit Visual Studio beginnen, wenn ein Problem auftritt.  
  
 Just\-In\-Time\-Debugging funktioniert nicht für Windows Store\-Apps.  Just\-In\-Time\-Debuggen funktioniert nicht für verwalteten Code, der in einer systemeigenen Anwendung gehostet wird, z. B. in Schnellansichten.  
  
## Verwenden von Just\-In\-Time\-Debuggen  
 Wenn Sie Visual Studio installieren, wird das Just\-In\-Time\-Debuggen standardmäßig aktiviert.  Wenn Sie Just\-In\-Time\-Debugging deaktivieren oder erneut aktivieren müssen, finden Sie weitere Informationen hierzu unter [Schrittweises Durchlaufen für "Nur mein Code" beschränken](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Wenn Just\-In\-Time\-Debuggen aktiviert ist, können Sie die Anwendung außerhalb von Visual Studio testen.  Wenn ein Absturz oder eine Ausnahme auftritt, wird ein Dialogfeld mit einer Meldung angezeigt, die ungefähr folgendermaßen aussieht:  
  
 Unbehandelte Ausnahme \("System.TypeInitializationException"\) in terrarium.exe\[3384\]  
  
 Wenn das Dialogfeld angezeigt wird, können Sie das Debuggen mit der folgenden Prozedur beginnen.  
  
#### So starten Sie Just\-In\-Time\-Debuggen beim Auftreten eines Fehlers  
  
1.  Klicken Sie im Dialogfeld „Just\-In\-Time\-Debugging“ in der Liste **Mögliche Debugger** auf **Neue Instanz von Visual Studio 2015** oder auf eine Instanz von Visual Studio, die bereits ausgeführt wird.  
  
2.  Wenn Visual Studio automatisch für alle zukünftigen Abstürze verwendet werden soll, klicken Sie auf **Der aktuell ausgewählte Debugger wird als Standard festgelegt**.  
  
3.  Wenn Sie selbst die Codetypen bestimmen wollen, die gedebuggt werden sollen, klicken Sie auf **Debugmodule manuell auswählen**.  Wenn Sie diese Option nicht wählen, wählt Visual Studio automatisch die entsprechenden Debugmodule für den Codetyp im Programm.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Wenn die Anwendung eine Assembly mit nicht vertrauenswürdigem Code enthält, wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt.  In diesem Dialogfeld können Sie festlegen, ob das Debuggen fortgesetzt werden soll.  Bevor Sie mit dem Debuggen fortfahren, entscheiden Sie, ob Sie den Code als vertrauenswürdig einstufen.  Haben Sie den Code selbst geschrieben?  Vertrauen Sie dem Programmierer?  Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses?  Selbst wenn die Anwendung lokal ausgeführt wird, bedeutet dies nicht unbedingt, dass sie als vertrauenswürdig eingestuft werden kann.  In Internet Explorer könnte zum Beispiel ein schädliches ActiveX\-Steuerelement ausgeführt werden.  Wägen Sie die Wahrscheinlichkeit ab, mit der solcher bösartiger Code auf Ihrem Computer ausgeführt wird.  Wenn Sie zu dem Urteil kommen, dass der Code, den Sie debuggen möchten, vertrauenswürdig ist, klicken Sie auf **Debuggen**.  Klicken Sie andernfalls auf **Nicht debuggen**.  
  
##  <a name="BKMK_Enabling"></a> Deaktivieren oder Aktivieren von Just\-In\-Time\-Debuggen  
 Sie können Just\-In\-Time\-Debuggen im Dialogfeld **Optionen** aktivieren oder deaktivieren.  
  
#### So aktivieren oder deaktivieren Sie Just\-In\-Time\-Debuggen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Wählen Sie im Dialogfeld **Optionen** den Ordner **Debuggen** aus.  
  
3.  Wählen Sie im Ordner **Debuggen** die Kategorie **Just\-In\-Time** aus.  
  
4.  Wählen Sie im Feld **Just\-In\-Time\-Debuggen für diese Codetypen aktivieren** die gewünschten Programmtypen aus, bzw. heben Sie die Auswahl auf. Die Optionen sind **Verwaltet**, **Systemeigen** und **Skript**.  
  
     Nach dem Aktivieren von Just\-In\-Time\-Debuggen müssen Sie über Administratorrechte verfügen, um es wieder zu deaktivieren.  Beim Aktivieren von Just\-In\-Time\-Debuggen wird ein Registrierungsschlüssel festgelegt, und zum Ändern dieses Schlüssels sind Administratorrechte erforderlich.  
  
5.  Klicken Sie auf **OK**.  
  
 Windows Forms\-Anwendungen verfügen über einen Ausnahmehandler der obersten Ebene, der dem Programm die weitere Ausführung ermöglicht, wenn eine Wiederherstellung möglich ist.  Daher müssen Sie die folgenden zusätzlichen Schritte ausführen, um das Just\-In\-Time\-Debuggen einer Windows Forms\-Anwendung zu ermöglichen.  
  
#### So aktivieren Sie das Just\-In\-Time\-Debuggen für ein Windows Form  
  
1.  Legen Sie den `jitDebugging`\-Wert im `true`\-Abschnitt der Datei "machine.config" oder in der Datei "`system.windows.form`Anwendung.exe.config" auf  *fest:*  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  In einer C\+\+ Windows Form\-Anwendung muss auch `DebuggableAttribute` in einer Konfigurationsdatei in Ihrem Code festgelegt werden.  Bei der Kompilierung mit [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) und ohne [\/Og](/visual-cpp/build/reference/og-global-optimizations) wird dieses Attribut vom Compiler für Sie festgelegt.  Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, müssen Sie den Wert selbst festlegen.  Fügen Sie dazu der Datei "AssemblyInfo.cpp" der Anwendung die folgende Zeile hinzu:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.  
  
 Just\-In\-Time\-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist.  Wenn Visual Studio nicht installiert ist, können Sie das Just\-In\-Time\-Debuggen im Dialogfeld **Optionen** in Visual Studio nicht deaktivieren.  In diesem Fall können Sie Just\-In\-Time\-Debuggen durch Bearbeiten der Windows\-Registrierung deaktivieren.  
  
#### So deaktivieren Sie Just\-In\-Time\-Debuggen durch Bearbeiten der Registrierung  
  
1.  Suchen Sie im Menü **Start** nach der Datei `regedit.exe`, und führen Sie sie aus.  
  
2.  Suchen Sie im Fenster **Registrierungs\-Editor** die folgenden Registrierungsschlüssel, und löschen Sie sie:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  Wenn auf Ihrem Computer ein 64\-Bit\-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungsschlüssel:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  Löschen oder ändern Sie nicht versehentlich andere Registrierungsschlüssel.  
  
5.  Schließen Sie das Fenster **Registrierungs\-Editor**.  
  
## Fehler beim Just\-In\-Time\-Debuggen  
 Möglicherweise werden die folgenden Fehlermeldungen angezeigt, die mit Just\-In\-Time\-Debuggen zusammenhängen.  
  
-   **An den abstürzenden Prozess kann nicht angehängt werden.  Das angegebene Programm ist keine MS\-DOS\- oder Windows\-Anwendung.**  
  
     Dieser Fehler tritt auf, wenn Sie versuchen, einen Prozess unter einem anderen Benutzerkonto unter Windows 2000 auszuführen.  
  
     Um dieses Problem zu umgehen, starten Sie Visual Studio, öffnen Sie das Dialogfeld **An den Prozess anhängen** vom Menü **Debuggen** aus, und suchen Sie den Prozess, den Sie in der Liste **Verfügbare Prozesse** debuggen möchten.  Falls Sie den Namen des Prozesses nicht kennen, sehen Sie im Dialogfeld **Just\-In\-Time\-Debugger von Visual Studio** nach, und notieren Sie die Prozess\-ID.  Wählen Sie den Prozess in der Liste **Verfügbare Prozesse** aus, und klicken Sie auf **Anfügen**.  Klicken Sie im Dialogfeld **Just\-In\-Time\-Debugger von Visual Studio** auf **Nein**, um das Dialogfeld zu schließen.  
  
-   **Der Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**  
  
     Dieser Fehler tritt auf, wenn vom Just\-In\-Time\-Debuggen versucht wird, Visual Studio auf einem Computer zu starten, auf dem kein Benutzer bei der Konsole angemeldet ist.  Da kein Benutzer angemeldet ist, existiert keine Benutzersitzung, um das Dialogfeld für Just\-In\-Time\-Debuggen anzuzeigen.  
  
     Um dieses Problem zu beheben, melden Sie sich beim Computer an.  
  
-   **Die Klasse ist nicht registriert.**  
  
     Dieser Fehler zeigt, dass der Debugger versucht hat, eine nicht registrierte COM\-Klasse zu erstellen. Die Ursache ist wahrscheinlich ein Installationsproblem.  
  
     Beheben Sie dieses Problem, indem Sie Visual Studio mithilfe des Installationsdatenträgers neu installieren oder reparieren.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Just\-In\-Time, Debuggen, Dialogfeld "Optionen"](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)