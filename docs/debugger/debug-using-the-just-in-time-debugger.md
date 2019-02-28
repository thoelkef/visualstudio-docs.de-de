---
title: Debuggen mithilfe des Just-in-Time-Debuggers | Microsoft-Dokumentation
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8a9661673adf6cdab2d9a880ce27197a4e53127
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796555"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debuggen Sie mithilfe der Just-in-Time-Debugger in Visual Studio

Just-In-Time-Debuggen kann Visual Studio automatisch bei einer app ausgeführt wird, außerhalb von Visual Studio-Fehler oder Abstürze zu starten. Sie können mit Just-In-Time-Debuggen Testen von apps, die außerhalb von Visual Studio und öffnen Sie Visual Studio, um zu beginnen, Debuggen, wenn ein Problem auftritt.

Just-In-Time-Debuggen funktioniert für Windows desktop-apps. Es funktioniert nicht für universelle Windows-Apps oder für verwalteten Code, der in einer systemeigenen Anwendung, z. B. in Schnellansichten gehostet wird.

> [!TIP]
> Wenn Sie nur möchten, beenden das Dialogfeld "Just-in-Time-Debugger" angezeigt werden, jedoch keine Visual Studio installiert haben, finden Sie unter [deaktivieren Sie Just-in-Time-Debugger](../debugger/just-in-time-debugging-in-visual-studio.md). Wenn Sie einmal Visual Studio installiert haben, müssen Sie möglicherweise auf [deaktivieren Sie Just-in-Time-Debuggen aus der Windows-Registrierung](#disable-just-in-time-debugging-from-the-windows-registry).

##  <a name="BKMK_Enabling"></a> Aktivieren oder deaktivieren Sie Just-in-Time-Debuggen in Visual Studio

>[!NOTE]
>Zum Aktivieren oder deaktivieren Just-in-Time-Debuggen, müssen Sie Visual Studio als Administrator ausführen. Aktivieren oder deaktivieren Just-in-Time-Debuggen wird ein Registrierungsschlüssel, und möglicherweise Administratorrechte zum Ändern dieses Schlüssels erforderlich. Klicken Sie zum Öffnen von Visual Studio als Administrator mit der rechten Maustaste in der Visual Studio-app, und wählen Sie **als Administrator ausführen**.

Sie können konfigurieren, Just-In-Time-Debuggen von Visual Studio **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) Das Dialogfeld.

**So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen:**

1. Auf der **Tools** oder **Debuggen** , wählen Sie im Menü **Optionen** > **Debuggen**  >   **Just-In-Time**.

   ![Aktivieren oder Deaktivieren der JIT-Debuggen](../debugger/media/dbg-jit-enable-or-disable.png "aktivieren oder Deaktivieren der JIT-Debuggen")

1. In der **Aktivieren von Just-in-Time-Debuggen für diese Arten von Code** wählen die Codetypen Just-In-Time-Debuggen zum Debuggen angezeigt werden sollen: **verwaltete**, **Native**, und/oder  **Skript**.

1. Klicken Sie auf **OK**.

Aktivieren der Just-In-Time-Debugger, aber es nicht geöffnet werden, wenn eine app abstürzt oder Fehler auftreten, finden Sie unter [Problembehandlung Just-in-Time-Debuggen](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deaktivieren Sie Just-in-Time-Debuggen aus der Windows-Registrierung

Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht mehr installiert ist, können Sie die Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.

**So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung:**

1.  Von der Windows **starten** führen die **Registrierungs-Editor** (*regedit.exe*).

2.  In der **Registrierungs-Editor** Fenster Suchen und löschen Sie die folgenden Registrierungseinträge:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT-Registrierungsschlüssel](../debugger/media/dbg-jit-registry.png "JIT-Registrierungsschlüssel")

3.  Wenn Ihr Computer eine 64-Bit-Betriebssystem ausgeführt wird, können auch löschen Sie die folgenden Registrierungseinträge:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Stellen Sie sicher, dass nicht löschen oder ändern andere Registrierungsschlüssel.

5.  Schließen der **Registrierungs-Editor** Fenster.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Aktivieren der Just-In-Time-Debuggen eines Windows Forms

Standardmäßig haben die Windows-formularanwendungen einen Ausnahmehandler der obersten Ebene, mit dem die app weiterhin ausgeführt, wenn eine Wiederherstellung möglich. Wenn es sich bei eine Windows Forms-app eine nicht behandelte Ausnahme auslöst, wird das folgende Dialogfeld angezeigt:

![Windows-Formular nicht behandelte Ausnahme](../debugger/media/windowsformsunhandledexception.png "Windows Form-Ausnahmefehler")

Um Just-In-Time-Debuggen, anstelle der standardmäßigen Windows-Formular für die Fehlerbehandlung zu aktivieren, fügen Sie diese Einstellungen:

-  In der `system.windows.forms` Teil der *"Machine.config"* oder  *\<app-Name >. exe.config* Datei die `jitDebugging` Wert `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

-  Legen Sie auch in einer C++ Windows Form-Anwendung `DebuggableAttribute` zu `true` in eine *config* Datei oder in Ihrem Code. Bei der Kompilierung mit [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) und ohne [/Og](/cpp/build/reference/og-global-optimizations) wird dieses Attribut vom Compiler für Sie festgelegt. Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, jedoch müssen Sie festlegen `DebuggableAttribute` durch Hinzufügen der folgenden Zeile in Ihrer app *AssemblyInfo.cpp* Datei:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Verwenden von Just-in-Time-Debuggen
 In diesem Beispiel führt Sie durch Just-In-Time-Debuggen, wenn eine app, einen Fehler verursacht.

 - Sie benötigen Visual Studio installiert, um die folgenden Schritte ausführen zu können. Wenn Sie Visual Studio nicht haben, können Sie die kostenlose Herunterladen [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 - Stellen Sie sicher, dass Just-In-Time-Debuggen ist [aktiviert](#BKMK_Enabling) in **Tools** > **Optionen** > **Debuggen**  >  **Just-In-Time**.

In diesem Beispiel erstellen Sie eine C# Konsolen-app in Visual Studio, das löst eine ["NullReferenceException"](/dotnet/api/system.nullreferenceexception).

1. Erstellen Sie in Visual Studio eine C# Konsolen-app (**Datei** > **neu** > **Projekt** > **Visual C#**   >  **Konsolenanwendung**) mit dem Namen *ThrowsNullException*. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](/visualstudio/get-started/csharp/tutorial-wpf).

1. Wenn Sie das Projekt in Visual Studio geöffnet wird, öffnen Sie die *"Program.cs"* Datei. Ersetzen der Main()-Methode durch den folgenden Code, der gibt eine Zeile an die Konsole, und klicken Sie dann eine NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Um die Projektmappe zu erstellen, wählen Sie entweder die **Debuggen** (Standard) oder **Version** Konfiguration, und wählen Sie dann **erstellen** > **Projektmappe neu erstellen** .

   > [!NOTE]
   > - Wählen Sie **Debuggen** Konfiguration für den vollständigen Debugvorgang.
   > - Bei Auswahl von [Version](../debugger/how-to-set-debug-and-release-configurations.md) Konfiguration müssen Sie deaktivieren [nur mein Code](../debugger/just-my-code.md) für dieses Verfahren funktioniert. Klicken Sie unter **Tools** > **Optionen** > **Debuggen**, deaktivieren Sie **nur meinen Code aktivieren**.

   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

1. Öffnen Sie die erstellte app *ThrowsNullException.exe* in Ihre C# Projektordner (*...\ThrowsNullException\ThrowsNullException\bin\Debug* oder *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   Das folgende Befehlsfenster sollte angezeigt werden:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Die **Just-in-Time-Debugger auswählen** Dialogfeld wird geöffnet.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   Klicken Sie unter **verfügbarer Debugger**Option **neue Instanz der \<Ihrer bevorzugten Visual Studio-Version/Edition >**, sofern nicht bereits ausgewählt.

1. Klicken Sie auf **OK**.

   Das ThrowsNullException-Projekt wird in einer neuen Instanz von Visual Studio geöffnet, bei der Ausführung beendet wird, in der Zeile, die die Ausnahme ausgelöst hat:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Sie können die an diesem Punkt Debuggen starten. Wenn Sie eine echte app Debuggen wurden, müssen Sie würden Sie herausfinden, warum der Code die Ausnahme auslöst.

> [!CAUTION]
> Wenn Ihre app nicht vertrauenswürdigen Code enthält, wird ein Sicherheitsdialogfeld für die Warnung angezeigt, sodass Sie entscheiden, ob Sie mit dem Debuggen fortfahren. Bevor Sie fortfahren, Debuggen, entscheiden Sie, ob Sie dem Code vertrauen. Haben Sie den Code selbst geschrieben? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Wenn die app lokal ausgeführt wird, sollten Sie die Möglichkeit der Ausführung bösartigen Codes auf Ihrem Computer. Wenn Sie sich entscheiden, der Code vertrauenswürdig ist, wählen Sie **OK**. Wählen Sie andernfalls **Abbrechen** aus.

## <a name="jit_errors"></a> Problembehandlung bei der Just-In-Time-Debuggen

Wenn Just-in-Time-Debuggen nicht gestartet, wenn eine app abstürzt, auch wenn es in Visual Studio aktiviert ist:

- Windows-Fehlerberichterstattung kann über die Fehlerbehandlung auf Ihrem Computer übernommen werden.

  Um dieses Problem zu beheben, verwenden Sie Registrierungs-Editor zum Hinzufügen einer **DWORD-Wert** von **deaktiviert**, mit **Wertdaten** von **1**, auf die folgenden Registrierungsschlüssel:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows-Fehlerberichterstattung**

  Weitere Informationen finden Sie unter [. WER-Einstellungen](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

- Ein bekanntes Problem von Windows verursacht möglicherweise den Just-In-Time-Debugger fehlschlagen.

  Die Korrektur besteht darin, Hinzufügen einer **DWORD-Wert** von **automatisch**, mit **Wertdaten** von **1**, auf die folgenden Registrierungsschlüssel:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Sie können die folgenden Fehlermeldungen angezeigt, während der Just-in-Time-Debuggen:

- **An den abstürzenden Prozess kann nicht angehängt werden. Das angegebene Programm ist keine MS-DOS- oder Windows-Anwendung.**

    Der Debugger hat versucht, Anhängen an einen Prozess unter einem anderen Benutzer ausgeführt wird.

    Öffnen Sie zum Umgehen dieses Problems in Visual Studio **Debuggen** > **an den Prozess anhängen**, und suchen Sie den Prozess, die Sie debuggen möchten die **verfügbare Prozesse** Liste. Wenn Sie den Namen des Prozesses nicht kennen, finden Sie die Prozess-ID in der **Just-in-Time-Debugger von Visual Studio** Dialogfeld. Wählen Sie den Prozess in der **verfügbare Prozesse** aus, und wählen Sie **Anfügen**. Wählen Sie **keine** zu schließen, die Just-In-Time-Debugger-Dialogfeld.

- **Der Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**

    Es ist kein Benutzer in der Konsole protokolliert werden, es gibt also keine benutzersitzung, zum Anzeigen der Just-In-Time-Debuggen-Dialogfeld.

    Um dieses Problem zu beheben, melden Sie sich beim Computer an.

- **Die Klasse ist nicht registriert.**

    Der Debugger versucht hat, eine COM-Klasse zu erstellen, die nicht, wahrscheinlich aufgrund eines Problems Installation registriert ist.

    Um dieses Problem zu beheben, verwenden Sie Visual Studio-Installer, um eine Neuinstallation oder Reparatur von Visual Studio-Installation.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Optionen, Debugging, Just-In-Time-Dialogfeld](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
