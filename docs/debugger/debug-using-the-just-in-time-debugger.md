---
title: Debuggen mithilfe des Just-in-Time-Debuggers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/06/17
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 99a57f217cc92051f2b85b1b210ce3adf5a189be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058762"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debuggen Sie mithilfe der Just-in-Time-Debugger in Visual Studio
Just-In-Time-Debuggen startet Visual Studio automatisch tritt eine Ausnahme oder ein Absturz in einer Anwendung, die außerhalb von Visual Studio ausgeführt wird. Dadurch können Sie Ihre Anwendung testen, wenn Visual Studio nicht ausgeführt wird, und beginnen mit Visual Studio debuggen, wenn ein Problem auftritt.

Just-In-Time-Debuggen funktioniert für Windows desktop-apps. Es funktioniert nicht für universelle Windows-Apps, und es funktioniert nicht für verwalteten Code, der in einer systemeigenen Anwendung, z. B. in Schnellansichten gehostet wird.

> [!TIP]
> Wenn Sie einfach wissen, zum Reagieren auf die Just-in-Time möchten-debugger (Dialogfeld), finden Sie unter [in diesem Thema](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Aktivieren oder deaktivieren Sie Just-in-Time-Debuggen
Sie können aktivieren oder deaktivieren Sie Just-in-Time-Debuggen von Visual Studio **Tools > Optionen** Dialogfeld.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen

1.  Öffnen Sie Visual Studio mit Administratorberechtigungen aus (mit der rechten Maustaste, und wählen Sie **als Administrator ausführen**).

    Aktivieren oder deaktivieren Just-in-Time-Debuggen wird ein Registrierungsschlüssel, und möglicherweise Administratorrechte zum Ändern dieses Schlüssels erforderlich.

2. Klicken Sie im Menü **Extras** auf **Optionen**.

2.  In der **Optionen** Dialogfeld erweitern Sie die **Debuggen** Knoten.

3.  In der **Debuggen** Knoten **Just-In-Time-**.

    ![Aktivieren oder Deaktivieren der JIT-Debuggen](../debugger/media/dbg-jit-enable-or-disable.png "aktivieren oder Deaktivieren der JIT-Debuggen")

4.  In der **diese Codetypen aktivieren von Just-in-Time-Debuggen** Feld aktivieren bzw. deaktivieren Sie die gewünschten Programmtypen: **verwaltete**, **Native**, oder **Skript**.

5.  Klicken Sie auf **OK**.

Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht installiert ist, können Sie nicht Just-In-Time-Debuggen von Visual Studio deaktivieren **Optionen** Dialogfeld. In diesem Fall können Sie Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung

1.  Auf der **starten** Menüs, suchen und ausführen `regedit.exe`

2.  In der **Registrierungs-Editor** Fenster Suchen und löschen Sie die folgenden Registrierungseinträge:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger

    ![JIT-Registrierungsschlüssel](../debugger/media/dbg-jit-registry.png "JIT-Registrierungsschlüssel")

3.  Wenn Ihr Computer eine 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Löschen oder ändern Sie nicht versehentlich andere Registrierungsschlüssel.

5.  Schließen der **Registrierungs-Editor** Fenster.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>So aktivieren Sie das Just-In-Time-Debuggen für ein Windows Form

1.  Windows Forms-Anwendungen verfügen über einen Ausnahmehandler der obersten Ebene, der dem Programm die weitere Ausführung ermöglicht, wenn eine Wiederherstellung möglich ist. Wenn die Windows Forms-Anwendung eine nicht behandelte Ausnahme auslöst, werden Sie z. B. ein Dialogfeld wie folgt angezeigt:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     So aktivieren Sie Just-In-Time-Debuggen einer Windows Forms-Anwendung, müssen Sie die folgenden zusätzlichen Schritte ausführen:

2.  Legen Sie die `jitDebugging` Wert `true` in die `system.windows.form` Abschnitt der Datei machine.config oder  *\<Anwendungsname >*. exe.config-Datei:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  In einer C++ Windows Form-Anwendung muss auch `DebuggableAttribute` in einer Konfigurationsdatei in Ihrem Code festgelegt werden. Bei der Kompilierung mit ["/ Zi"](/cpp/build/reference/z7-zi-zi-debug-information-format) und ohne ["/ Og"](/cpp/build/reference/og-global-optimizations), legt der Compiler dieses Attribut für Sie. Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, müssen Sie den Wert selbst festlegen. Fügen Sie dazu der Datei "AssemblyInfo.cpp" der Anwendung die folgende Zeile hinzu:

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Verwenden Sie die Just-In-Time-Debuggen
 Dieser Abschnitt zeigt, was geschieht, wenn eine ausführbare Datei eine Ausnahme auslöst.

 Sie benötigen Visual Studio installiert, um die folgenden Schritte ausführen zu können. Wenn Sie Visual Studio nicht haben, können Sie die kostenlose Herunterladen [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 Stellen Sie sicher, dass diese Just-In-Time-Debuggen ist [aktiviert](#BKMK_Enabling).

 Für die Zwecke dieses Artikels, wir erstellen eine C#-Konsolen-app in Visual Studio, das löst eine ["NullReferenceException"](/dotnet/api/system.nullreferenceexception).

 Erstellen Sie in Visual Studio eine C#-Konsolen-app (**Datei > Neu > Projekt > Visual c# > Konsolenanwendung**) mit dem Namen **ThrowsNullException**. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei "Program.cs" ein. Ersetzen der Main()-Methode durch den folgenden Code, der gibt eine Zeile an die Konsole, und klicken Sie dann eine NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  In der Reihenfolge für dieses Verfahren funktioniert einer [Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md), Sie deaktivieren möchten [nur mein Code](../debugger/just-my-code.md). Klicken Sie in Visual Studio auf **Tools > Optionen**. In der **Optionen** wählen Sie im Dialogfeld **Debuggen**. Entfernen Sie das Kontrollkästchen **nur meinen Code aktivieren**.

 Erstellen Sie die Projektmappe (Wählen Sie in Visual Studio **erstellen > Projektmappe neu erstellen**). Sie können das Debuggen oder die Releasekonfiguration auswählen (Wählen Sie **Debuggen** für dem vollständigen Debugvorgang). Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

 Der Buildprozess erstellt eine ausführbare ThrowsNullException.exe. Sie finden es unter dem Ordner, in dem Sie c#-Projekt erstellt haben: **...\ThrowsNullException\ThrowsNullException\bin\Debug** oder **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Doppelklicken Sie auf die ThrowsNullException.exe. Daraufhin sollte ein Befehlsfenster wie folgt:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Nach wenigen Sekunden erscheint eine Fehlermeldung:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Klicken Sie nicht auf **Abbrechen**! Nach wenigen Sekunden sehen Sie zwei Schaltflächen, **Debuggen** und **Programm schließen**. Klicken Sie auf **Debuggen**.

> [!CAUTION]
>  Wenn Ihre Anwendung nicht vertrauenswürdigen Code enthält, wird ein Dialogfeld mit einer sicherheitswarnung angezeigt. In diesem Dialogfeld können Sie festlegen, ob das Debuggen fortgesetzt werden soll. Bevor Sie mit dem Debuggen fortfahren, entscheiden Sie, ob Sie den Code als vertrauenswürdig einstufen. Haben Sie den Code selbst geschrieben? Vertrauen Sie dem Programmierer? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Selbst wenn die Anwendung lokal ausgeführt wird, bedeutet dies nicht unbedingt, dass sie als vertrauenswürdig eingestuft werden kann. Wägen Sie die Wahrscheinlichkeit von schädlichem Code, die auf Ihrem Computer ausgeführt werden soll. Wenn Sie sich entscheiden, dass der Code Sie möchten "Debug" vertrauenswürdig ist, klicken Sie auf **Debuggen**. Klicken Sie anderenfalls auf **nicht Debuggen**.

 Die **Just-in-Time-Debugger von Visual Studio** Fenster wird angezeigt:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Klicken Sie unter **Mögliche Debugger**, sollte angezeigt werden, die **neue Instanz von Microsoft Visual Studio <available version>**  Zeile ausgewählt ist. Wenn sie nicht bereits ausgewählt ist, wählen Sie sie jetzt ein.

 Am unteren Fensterrand unter **möchten Sie mit dem ausgewählten Debugger zu Debuggen?**, klicken Sie auf **Ja**.

 Das Projekt ThrowsNullException öffnet in einer neuen Instanz von Visual Studio, bei der Ausführung beendet wird, in der Zeile, die die Ausnahme auslöst:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Sie können die an diesem Punkt Debuggen starten. Wenn dies eine reale Anwendung wäre, müssten Sie herausfinden, warum der Code die Ausnahme auslöst.

## <a name="just-in-time-debugging-errors"></a>Fehler beim Just-In-Time-Debuggen
 Wenn Sie das Dialogfeld nicht angezeigt wird, wenn die Anwendung abstürzt, kann dies aufgrund von Windows-Fehlerberichterstattung-Einstellungen auf Ihrem Computer. Weitere Informationen finden Sie unter [. WER-Einstellungen](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).

 Möglicherweise werden die folgenden Fehlermeldungen angezeigt, die mit Just-In-Time-Debuggen zusammenhängen.

-   **Anfügen an den abstürzenden Prozess nicht möglich. Das angegebene Programm ist nicht Windows oder MS-DOS-Programm.**

     Dieser Fehler tritt auf, wenn Sie versuchen, Anhängen an einen Prozess als ein anderer Benutzer ausgeführt wird.

     Öffnen Sie zum Umgehen dieses Problems starten Sie Visual Studio die **an den Prozess anhängen** das Dialogfeld die **Debuggen** Menü, und suchen Sie den Prozess Sie debuggen möchten die **verfügbare Prozesse**Liste. Wenn Sie den Namen des Prozesses nicht kennen, sehen Sie sich die **Just-in-Time-Debugger von Visual Studio** Dialogfeld und notieren Sie die Prozess-ID. Wählen Sie den Prozess in der **verfügbare Prozesse** aus, und klicken Sie auf **Anfügen**. In der **Just-in-Time-Debugger von Visual Studio** Dialogfeld klicken Sie auf **keine** um das Dialogfeld zu schließen.

-   **Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**

     Dieser Fehler tritt auf, wenn vom Just-In-Time-Debuggen versucht wird, Visual Studio auf einem Computer zu starten, auf dem kein Benutzer bei der Konsole angemeldet ist. Da kein Benutzer angemeldet ist, existiert keine Benutzersitzung, um das Dialogfeld für Just-In-Time-Debuggen anzuzeigen.

     Um dieses Problem zu beheben, melden Sie sich beim Computer an.

-   **Die Klasse nicht registriert.**

     Dieser Fehler zeigt, dass der Debugger versucht hat, eine nicht registrierte COM-Klasse zu erstellen. Die Ursache ist wahrscheinlich ein Installationsproblem.

     Beheben Sie dieses Problem, indem Sie Visual Studio mithilfe des Installationsdatenträgers neu installieren oder reparieren.

## <a name="see-also"></a>Siehe auch
 [Debuggersicherheit](../debugger/debugger-security.md) [Debugger – Grundlagen](../debugger/debugger-basics.md) [Just-In-Time, Debuggen, Dialogfeld Optionen](../debugger/just-in-time-debugging-options-dialog-box.md) [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann sein gefährlich. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
