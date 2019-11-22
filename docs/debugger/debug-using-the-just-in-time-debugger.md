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
ms.openlocfilehash: b842fa4ce7c75e061a58d980cefe5648094c2ef7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188669"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debuggen mit dem Just-in-Time-Debugger in Visual Studio

Just-in-Time-Debuggen kann Visual Studio automatisch starten, wenn eine App außerhalb von Visual Studio-Fehlern oder-Abstürzen ausgeführt wird. Mithilfe des Just-in-Time-Debuggens können Sie apps außerhalb von Visual Studio testen und Visual Studio öffnen, um mit dem Debuggen zu beginnen, wenn ein Problem auftritt.

Just-in-Time-Debuggen funktioniert für Windows-Desktop-Apps. Dies funktioniert nicht für universelle Windows-Apps oder für verwalteten Code, der in einer systemeigenen Anwendung gehostet wird, z. b. in Visualisierungen.

> [!TIP]
> Wenn Sie das Dialogfeld Just-in-Time-Debugger nicht anzeigen möchten, aber Visual Studio nicht installiert ist, finden Sie weitere Informationen unter [Deaktivieren des Just-in-Time-Debuggers](../debugger/just-in-time-debugging-in-visual-studio.md). Wenn Sie Visual Studio installiert haben, müssen Sie möglicherweise [das Just-in-Time-Debuggen aus der Windows-Registrierung deaktivieren](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="BKMK_Enabling"></a>Aktivieren oder Deaktivieren des Just-in-Time-Debuggens in Visual Studio

>[!NOTE]
>Um das Just-in-Time-Debuggen zu aktivieren oder zu deaktivieren, müssen Sie Visual Studio als Administrator ausführen. Durch das Aktivieren oder Deaktivieren des Just-in-Time-Debuggens wird ein Registrierungsschlüssel festgelegt, und möglicherweise sind Administratorrechte erforderlich, um diesen Schlüssel zu ändern Um Visual Studio als Administrator zu öffnen, klicken Sie mit der rechten Maustaste auf die Visual Studio-app, und wählen Sie **als Administrator ausführen**aus.

Sie können das Just-in-Time-Debuggen im Dialogfeld Visual Studio- **Tools** > **Optionen** (oder > **Optionen** **Debuggen** ) konfigurieren.

**So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen:**

1. Wählen Sie **im Menü Extras oder** **Debuggen** die **Option Optionen** > **Debuggen** > **Just-in-Time**aus.

   ![Aktivieren oder Deaktivieren des JIT-Debuggens](../debugger/media/dbg-jit-enable-or-disable.png "Aktivieren oder Deaktivieren des JIT-Debuggens")

1. Wählen Sie im Feld **Just-in-Time-Debuggen für diese Codetypen aktivieren** die Codetypen aus **, die**Sie zum Debuggen von Just-in-Time-Debugging benötigen: **verwaltet**, System eigen und/oder **Skript**.

1. Klicken Sie auf **OK**.

Wenn Sie den Just-in-Time-Debugger aktivieren, jedoch nicht, wenn eine APP einen Absturz oder Fehler verursacht, finden Sie weitere Informationen unter [Beheben von Just-in-Time-Debuggen](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deaktivieren von Just-in-Time-Debuggen aus der Windows-Registrierung

Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht mehr installiert ist, können Sie das Just-in-Time-Debuggen deaktivieren, indem Sie die Windows-Registrierung bearbeiten.

**So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung:**

1. Führen Sie im Windows- **Startmenü** den **Registrierungs-Editor** (*Regedit. exe*) aus.

2. Suchen Sie im Fenster **Registrierungs-Editor** die folgenden Registrierungseinträge, und löschen Sie Sie:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT-Registrierungsschlüssel](../debugger/media/dbg-jit-registry.png "JIT-Registrierungsschlüssel")

3. Wenn auf Ihrem Computer ein 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Stellen Sie sicher, dass Sie keine anderen Registrierungsschlüssel löschen oder ändern.

5. Schließen Sie das Fenster des **Registrierungs-Editors** .

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Just-in-Time-Debuggen für ein Windows Form aktivieren

Standardmäßig verfügen Windows Form-Apps über einen Ausnahmehandler der obersten Ebene, mit dem die APP weiterhin ausgeführt werden kann, wenn Sie wieder hergestellt werden kann. Wenn eine Windows Forms-App eine nicht behandelte Ausnahme auslöst, wird das folgende Dialogfeld angezeigt:

![Nicht behandelte Windows Form-Ausnahme](../debugger/media/windowsformsunhandledexception.png "Nicht behandelte Windows Form-Ausnahme")

Um just-in-Time-Debuggen anstelle der standardmäßigen Windows Form-Fehlerbehandlung zu aktivieren, fügen Sie diese Einstellungen hinzu:

- Legen Sie im `system.windows.forms` Abschnitt der Datei " *Machine. config* " oder " *\<App Name >. exe. config* " den `jitDebugging` Wert auf `true`fest:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Legen Sie C++ in einer Windows Form-Anwendung auch`DebuggableAttribute`auf`true`in einer *config* -Datei oder in Ihrem Code fest. Bei der Kompilierung mit [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) und ohne [/Og](/cpp/build/reference/og-global-optimizations) wird dieses Attribut vom Compiler für Sie festgelegt. Wenn Sie jedoch einen nicht optimierten Releasebuild debuggen möchten, müssen Sie `DebuggableAttribute` festlegen, indem Sie die folgende Zeile in der *AssemblyInfo. cpp* -Datei Ihrer APP hinzufügen:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Just-in-Time-Debuggen verwenden
Dieses Beispiel führt Sie durch das Just-in-Time-Debuggen, wenn eine APP einen Fehler auslöst.

- Sie müssen Visual Studio installiert haben, um die folgenden Schritte ausführen zu können. Wenn Sie nicht über Visual Studio verfügen, können Sie die kostenlose [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)herunterladen.

- Stellen Sie sicher, dass das Just-in-Time-Debuggen in **Tools** > **Optionen** > **Debuggen** > **Just-in-Time** [aktiviert](#BKMK_Enabling) ist.

In diesem Beispiel erstellen Sie eine C# Konsolen-app in Visual Studio, die eine [NullReferenceException](/dotnet/api/system.nullreferenceexception)auslöst.

1. Erstellen Sie in Visual Studio eine C# Konsolen-app (**Datei** > **Neues** > **Projekt** >  **C# Visual** > - **Konsolenanwendung**) namens *throwsnullexception*. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen Anwendung](../get-started/csharp/tutorial-wpf.md).

1. Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei *Program.cs* . Ersetzen Sie die Main ()-Methode durch den folgenden Code, der eine Zeile auf der Konsole ausgibt und dann eine NullReferenceException auslöst:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Wählen Sie zum Erstellen der Projekt Mappe entweder die **Debug** -(Standard) oder die **Releasekonfiguration** aus, und wählen Sie dann **Erstellen** > Projekt Mappe **neu**erstellen aus.

   > [!NOTE]
   > - Wählen Sie **Debugkonfiguration** aus, um die gesamte Suche
   > - Wenn Sie die [Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md) auswählen, müssen Sie [nur eigenen Code](../debugger/just-my-code.md) deaktivieren, damit dieses Verfahren funktioniert. Deaktivieren Sie unter **Extras > ** Optionen > **Debuggen**die **Option** **nur eigenen Code aktivieren**.

   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

1. Öffnen Sie die integrierte app " *throwsnullexception. exe* " in Ihrem C# Projektordner ( *. ..\throwsnullexception\throwsnullexception\bin\debug* oder *. ..\throwsnullexception\throwsnullexception\bin\release*).

   Das folgende Befehlsfenster sollte angezeigt werden:

   ![Throwsnullexceptionconsole](../debugger/media/throwsnullexceptionconsole.png "Throwsnullexceptionconsole")

1. Das Dialogfeld **Just-in-Time-Debugger auswählen** wird geöffnet.

   ![Justintimedialog](../debugger/media/justintimedialog.png "Justintimedialog")

   Wählen Sie unter **Verfügbare Debugger** **die Option neue Instanz von aus, \<Ihre bevorzugte Visual Studio-Version/Edition >** , sofern diese nicht bereits ausgewählt ist.

1. Klicken Sie auf **OK**.

   Das Projekt "throwsnullexception" wird in einer neuen Instanz von Visual Studio geöffnet, wobei die Ausführung in der Zeile angehalten wurde, die die Ausnahme ausgelöst hat:

   ![Nullreferencesecondinstance](../debugger/media/nullreferencesecondinstance.png "Nullreferencesecondinstance")

An dieser Stelle können Sie mit dem Debuggen beginnen. Wenn Sie eine echte App Debuggen, müssen Sie herausfinden, warum der Code die Ausnahme auslöst.

> [!CAUTION]
> Wenn Ihre APP nicht vertrauenswürdigen Code enthält, wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt, in dem Sie entscheiden können, ob das Debugging fortgesetzt werden soll. Bevor Sie das Debuggen fortsetzen, entscheiden Sie, ob Sie dem Code Vertrauen. Haben Sie den Code selbst geschrieben? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Wenn die APP lokal ausgeführt wird, sollten Sie die Möglichkeit der Ausführung von bösartigem Code auf Ihrem Computer berücksichtigen. Wenn Sie festlegen, dass der Code vertrauenswürdig ist, wählen Sie **OK**aus. Wählen Sie andernfalls **Abbrechen** aus.

## <a name="jit_errors"></a>Problembehandlung beim Just-in-Time-Debuggen

Wenn Just-in-Time-Debuggen nicht gestartet wird, wenn eine APP abstürzt, auch wenn Sie in Visual Studio aktiviert ist:

- Windows-Fehlerberichterstattung könnten die Fehlerbehandlung auf dem Computer übernehmen.

  Um dieses Problem zu beheben, fügen Sie mithilfe des Registrierungs-Editors den folgenden Registrierungs Schlüsseln den **DWORD-Wert** " **deaktiviert**" mit dem **Wert** " **1**" hinzu:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows-Fehlerberichterstattung**

  Weitere Informationen finden Sie unter [. Wer-Einstellungen](/windows/desktop/wer/wer-settings).

- Ein bekanntes Windows-Problem kann dazu führen, dass der Just-in-Time-Debugger fehlschlägt.

  Die Korrektur besteht darin, den folgenden Registrierungs Schlüsseln den **DWORD-Wert** " **Auto**" mit dem **Wert** " **1**" hinzuzufügen:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Für 64-Bit-Computer): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Beim Just-in-Time-Debuggen werden möglicherweise die folgenden Fehlermeldungen angezeigt:

- **An den abstürzenden Prozess kann nicht angefügt werden. Das angegebene Programm ist kein Windows-oder MS-DOS-Programm.**

    Der Debugger hat versucht, einen Prozess anzufügen, der unter einem anderen Benutzer ausgeführt wird.

    Um dieses Problem zu umgehen, öffnen Sie in Visual Studio **Debuggen** > **an den Prozess anhängen**, und suchen Sie den Prozess, den Sie debuggen möchten, in der Liste **Verfügbare Prozesse** . Wenn Sie den Namen des Prozesses nicht kennen, finden Sie die Prozess-ID im Dialogfeld **Just-in-Time-Debugger von Visual Studio** . Wählen Sie den Prozess in der Liste **Verfügbare Prozesse** aus, und klicken Sie auf **Anfügen**. Wählen Sie **Nein** aus, um das Dialogfeld Just-in-Time-Debugger zu schließen.

- **Der Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**

    Es ist kein Benutzer an der Konsole angemeldet, daher gibt es keine Benutzersitzung, um das Just-in-Time-debugdialogfeld anzuzeigen.

    Um dieses Problem zu beheben, melden Sie sich beim Computer an.

- **Die Klasse ist nicht registriert.**

    Der Debugger hat versucht, eine COM-Klasse zu erstellen, die nicht registriert ist, wahrscheinlich aufgrund eines Installations Problems.

    Um dieses Problem zu beheben, verwenden Sie die Visual Studio-Installer, um die Installation von Visual Studio neu zu installieren oder zu reparieren.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Optionen, Debuggen, Just-in-time (Dialogfeld)](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Sicherheitswarnung: das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig sind oder Sie sich nicht sicher sind, fügen Sie diesen Vorgang nicht an.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
