---
title: Mithilfe der Just-in-Time-Debugger debuggen | Microsoft Docs
ms.custom: ''
ms.date: 07/06/17
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bfaed6a788d61f239fb8fb69095549fe5c20d6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debuggen Sie mithilfe der Just-in-Time-Debugger in Visual Studio
Just-in-Time-Debuggen Visual Studio wird automatisch gestartet, wenn eine Ausnahme oder ein Absturz in einer Anwendung ausgeführt wird, die außerhalb von Visual Studio ausgeführt wird. Dadurch können Sie die Anwendung testen, wenn Visual Studio nicht ausgeführt wird, und beginnen mit Visual Studio debuggen, wenn ein Problem auftritt.

Just-in-Time-Debuggen funktioniert für Windows desktop-apps. Es funktioniert nicht für universelle Windows-Apps, und es funktioniert nicht für verwalteten Code, der in einer systemeigenen Anwendung, z. B. in Schnellansichten gehostet wird.

> [!TIP] 
> Wenn Sie nur wissen, reagieren auf das Just-in-Time möchten-debugger (Dialogfeld), finden Sie unter [in diesem Thema](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Aktivieren oder deaktivieren Sie Just-in-Time-Debuggen  
Sie aktivieren oder deaktivieren Sie Just-in-Time-Debuggen von Visual Studio **Tools > Optionen** (Dialogfeld).
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen  
  
1.  Öffnen Sie Visual Studio mit Administratorberechtigungen aus (mit der rechten Maustaste, und wählen Sie **als Administrator ausführen**).

    Aktivieren oder deaktivieren Just-in-Time-Debuggen wird ein Registrierungsschlüssel und zum Ändern dieses Schlüssels möglicherweise Administratorrechte erforderlich.
    
2. Klicken Sie im Menü **Extras** auf **Optionen**.
  
2.  In der **Optionen** Dialogfeld erweitern Sie die **Debuggen** Knoten.  
  
3.  In der **Debuggen** Knoten **Just-in-Time**.

    ![Aktivieren oder Deaktivieren von JIT-Debuggen](../debugger/media/dbg-jit-enable-or-disable.png "aktivieren oder Deaktivieren von JIT-Debuggen") 
  
4.  In der **Aktivieren von Just-in-Time-Debuggen für diese Codetypen** Feld aktivieren bzw. deaktivieren Sie die Programmtypen: **verwaltet**, **Native**, oder **Skript**.    
  
5.  Klicken Sie auf **OK**.  
  
Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht installiert ist, kann nicht, deaktivieren Sie Just-in-Time-Debuggen von Visual Studio **Optionen** (Dialogfeld). In diesem Fall können Sie Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung  
  
1.  Auf der **starten** Menü, suchen und ausführen `regedit.exe`  
  
2.  In der **Registrierungs-Editor** Fenster Suchen und löschen Sie die folgenden Registrierungseinträge:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\DbgManagedDebugger  

    ![JIT-Registrierungsschlüssel](../debugger/media/dbg-jit-registry.png "JIT-Registrierungsschlüssel") 
  
3.  Wenn Ihr Computer eine 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Löschen oder ändern Sie nicht versehentlich andere Registrierungsschlüssel.  
  
5.  Schließen der **Registrierungs-Editor** Fenster.   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>So aktivieren Sie das Just-In-Time-Debuggen für ein Windows Form  
  
1.  Windows Forms-Anwendungen verfügen über einen Ausnahmehandler der obersten Ebene, der dem Programm die weitere Ausführung ermöglicht, wenn eine Wiederherstellung möglich ist. Wenn Ihre Windows Forms-Anwendung eine nicht behandelte Ausnahme auslöst, werden Sie z. B. ein Dialogfeld folgendermaßen angezeigt:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Zum Aktivieren von Just-in-Time-Debuggen einer Windows Forms-Anwendung, müssen Sie die folgenden zusätzlichen Schritte ausführen:  
  
2.  Legen Sie die `jitDebugging` Wert `true` in der `system.windows.form` Abschnitt der Datei machine.config oder  *\<Anwendungsname >*. exe.config-Datei:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  In einer C++ Windows Form-Anwendung muss auch `DebuggableAttribute` in einer Konfigurationsdatei in Ihrem Code festgelegt werden. Beim Kompilieren mit [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) und ohne [/Og](/cpp/build/reference/og-global-optimizations), legt der Compiler dieses Attribut für Sie. Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, müssen Sie den Wert selbst festlegen. Fügen Sie dazu der Datei "AssemblyInfo.cpp" der Anwendung die folgende Zeile hinzu:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Verwenden Sie Just-in-Time-Debuggen  
 In diesem Abschnitt wird gezeigt, was geschieht, wenn eine ausführbare Datei eine Ausnahme auslöst.  
  
 Sie benötigen Visual Studio installiert, um die folgenden Schritte ausführen zu können. Wenn Sie Visual Studio nicht haben, können Sie die kostenlose Herunterladen [Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).  
  
 Stellen Sie sicher, dass diese Just-in-Time-Debuggen ist [aktiviert](#BKMK_Enabling).
  
 Für die Zwecke dieses Abschnitts können wir eine C#-Konsolenanwendung in Visual Studio, die auslöst, stellen eine [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a).  
  
 In Visual Studio, erstellen Sie eine C#-Konsolenanwendung (**Datei > Neu > Projekt > c# > Konsolenanwendung**) mit dem Namen **ThrowsNullException**. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei "Program.cs". Ersetzen Sie die Main()-Methode durch den folgenden Code, der gibt eine Zeile an die Konsole, und klicken Sie dann eine NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  In der Reihenfolge für diese Prozedur in der Sie arbeiten ein [Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md), müssen Sie deaktivieren [nur mein Code](../debugger/just-my-code.md). Klicken Sie in Visual Studio auf **Tools > Optionen**. In der **Optionen** wählen Sie im Dialogfeld **Debuggen**. Entfernen Sie die Überprüfung von **nur meinen Code aktivieren**.  
  
 Erstellen Sie die Projektmappe (Wählen Sie in Visual Studio **erstellen > Projektmappe neu erstellen**). Sie können das Debuggen oder die Releasekonfiguration auswählen (Wählen Sie **Debuggen** für die vollständige Debugvorgänge). Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
 Während des Erstellungsprozesses wird eine ausführbare ThrowsNullException.exe erstellt. Sie finden sie unter dem Ordner, in dem Sie das C#-Projekt erstellt haben: **...\ThrowsNullException\ThrowsNullException\bin\Debug** oder **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Doppelklicken Sie auf die ThrowsNullException.exe. Daraufhin sollte ein Befehlsfenster, das wie folgt:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Nach wenigen Sekunden angezeigt wird ein Fenster aus:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Klicken Sie nicht auf **"Abbrechen"**! Nach wenigen Sekunden sehen Sie zwei Schaltflächen **Debuggen** und **Programm schließen**. Klicken Sie auf **Debuggen**.  
  
> [!CAUTION]
>  Wenn Ihre Anwendung nicht vertrauenswürdigen Code enthält, wird ein Dialogfeld mit einer sicherheitswarnung angezeigt. In diesem Dialogfeld können Sie festlegen, ob das Debuggen fortgesetzt werden soll. Bevor Sie mit dem Debuggen fortfahren, entscheiden Sie, ob Sie den Code als vertrauenswürdig einstufen. Haben Sie den Code selbst geschrieben? Vertrauen Sie dem Programmierer? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Selbst wenn die Anwendung lokal ausgeführt wird, bedeutet dies nicht unbedingt, dass sie als vertrauenswürdig eingestuft werden kann. Wägen Sie die Wahrscheinlichkeit von bösartigem Code auf Ihrem Computer ausgeführt wird. Wenn Sie sich dazu entschließen, die den Code Sie möchten Debug vertrauenswürdig ist, klicken Sie auf **Debuggen**. Klicken Sie andernfalls auf **nicht Debuggen**.  
  
 Die **Just-in-Time-Debugger von Visual Studio** Fenster wird angezeigt:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 Klicken Sie unter **Mögliche Debugger**, sollte angezeigt werden, die **neue Instanz von Microsoft Visual Studio <available version>**  Zeile ausgewählt ist. Wenn es nicht bereits ausgewählt ist, wählen Sie diese jetzt ein.  
  
 Am unteren Rand des Fensters unter **möchten Sie mit dem ausgewählten Debugger Debuggen?**, klicken Sie auf **Ja**.  
  
 Das Projekt ThrowsNullException öffnet in einer neuen Instanz von Visual Studio mit der Ausführung beendet wird, in der Zeile, die die Ausnahme auslöst:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Sie können das Debuggen zu diesem Zeitpunkt starten. Wenn dies einer echten Anwendung würden, müssten Sie herauszufinden, warum der Code die Ausnahme auslöst.  
  
## <a name="just-in-time-debugging-errors"></a>Fehler beim Just-In-Time-Debuggen  
 Wenn das Dialogfeld nicht angezeigt wird, wenn das Programm abstürzt haben, kann dies aufgrund von Windows-Fehlerberichterstattung-Einstellungen auf Ihrem Computer. Weitere Informationen finden Sie unter [. WER Settings](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).  
  
 Möglicherweise werden die folgenden Fehlermeldungen angezeigt, die mit Just-In-Time-Debuggen zusammenhängen.  
  
-   **Anfügen an den abstürzenden Prozess nicht möglich. Die angegebene ProgID ist nicht Windows oder MS-DOS-Programm.**  
  
     Dieser Fehler tritt auf, wenn Sie versuchen, Anfügen an einen Prozess als ein anderer Benutzer ausgeführt.  
  
     Zum Umgehen dieses Problems starten Sie Visual Studio, öffnen Sie die **an den Prozess anhängen** (Dialogfeld), aus der **Debuggen** Menü, und suchen Sie den Prozess Sie debuggen möchten die **verfügbare Prozesse**Liste. Wenn Sie den Namen des Prozesses nicht kennen, sehen Sie sich die **Just-in-Time-Debugger von Visual Studio** Dialogfeld, und beachten Sie die Prozess-ID Wählen Sie den Prozess in den **verfügbare Prozesse** aus, und klicken Sie auf **Anfügen**. In der **Just-in-Time-Debugger von Visual Studio** Dialogfeld klicken Sie auf **keine** um das Dialogfeld zu schließen.  
  
-   **Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**  
  
     Dieser Fehler tritt auf, wenn vom Just-In-Time-Debuggen versucht wird, Visual Studio auf einem Computer zu starten, auf dem kein Benutzer bei der Konsole angemeldet ist. Da kein Benutzer angemeldet ist, existiert keine Benutzersitzung, um das Dialogfeld für Just-In-Time-Debuggen anzuzeigen.  
  
     Um dieses Problem zu beheben, melden Sie sich beim Computer an.  
  
-   **Die Klasse nicht registriert.**  
  
     Dieser Fehler zeigt, dass der Debugger versucht hat, eine nicht registrierte COM-Klasse zu erstellen. Die Ursache ist wahrscheinlich ein Installationsproblem.  
  
     Beheben Sie dieses Problem, indem Sie Visual Studio mithilfe des Installationsdatenträgers neu installieren oder reparieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Just-In-Time, Debuggen, Dialogfeld "Optionen"](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)