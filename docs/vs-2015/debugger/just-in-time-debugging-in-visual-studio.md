---
title: Just-In-Time-Debuggen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690598"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Just-In-Time-Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Just-in-Time-Debuggen starten von Visual Studio automatisch, wenn in einer Anwendung, die außerhalb von Visual Studio ausgeführt wird, eine Ausnahme oder ein Absturz auftritt. Dies ermöglicht es Ihnen, Ihre Anwendung zu testen, wenn Visual Studio nicht ausgeführt wird, und mit dem Debuggen mit Visual Studio zu beginnen, wenn ein Problem auftritt.

Just-in-Time-Debuggen funktioniert für Windows-Desktop-Apps. Dies funktioniert nicht für universelle Windows-apps und funktioniert nicht für verwalteten Code, der in einer systemeigenen Anwendung gehostet wird, z. b. in Visualisierungen.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> Hat das Dialogfeld Just-in-Time-Debugger angezeigt, wenn Sie versuchen, eine APP auszuführen?

Die Aktionen, die Sie durchführen sollten, wenn das Dialogfeld Just-in-Time-Debugger von Visual Studio angezeigt wird, hängt davon ab, was Sie versuchen:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Wenn Sie das Dialogfeld entfernen und die app nur normal ausführen möchten.

1. (Erweiterte Benutzer) Wenn Sie Visual Studio installiert haben (oder zuvor installiert und entfernt wurde), [Deaktivieren Sie Just-in-Time-Debuggen](#BKMK_Enabling) , und versuchen Sie, die APP erneut auszuführen.

2. Wenn Sie eine Web-App in Internet Explorer ausführen, deaktivieren Sie das Skript Debugging.

    Deaktivieren Sie das Skript Debuggen im Dialogfeld Internet Optionen. Sie können auf diese Option über die **Systemsteuerung**  /  **Netzwerk-und Internet**  /  **Optionen** zugreifen (die genauen Schritte hängen von Ihrer Windows-Version und Internet Explorer ab).

    ![Jitinternetoptions](../debugger/media/jitinternetoptions.png "Jitinternetoptions")

3. Öffnen Sie die Webseite erneut, auf der Sie den Fehler gefunden haben. Wenn das Problem hierdurch nicht behoben wird, wenden Sie sich an den Besitzer der Web-App, um das Problem zu beheben.

4. Wenn Sie einen anderen Typ von Windows-app ausführen, müssen Sie sich an den Besitzer der APP wenden, um den Fehler zu beheben, und dann die feste Version der APP erneut installieren.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Wenn Sie den Fehler beheben oder debuggen möchten (Erweiterte Benutzer)

- Sie müssen [Visual Studio installiert](https://visualstudio.microsoft.com/vs/older-downloads/) haben, um ausführliche Informationen zum Fehler anzuzeigen und zu debuggen. Ausführliche Anweisungen finden [Sie unter Verwenden von JIT](#BKMK_Using_JIT) . Wenn Sie den Fehler nicht beheben und die APP nicht beheben können, wenden Sie sich an den Besitzer der APP, um den Fehler zu beheben.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Just-in-Time-Debuggen aktivieren oder deaktivieren
 Sie können das Just-in-Time-Debuggen im Dialogfeld Visual Studio **-Tools/-Optionen** aktivieren oder deaktivieren.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen

1. Öffnen Sie Visual Studio. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Wählen Sie im Dialogfeld **Optionen** den Ordner **Debuggen** aus.

3. Wählen Sie im Ordner **Debuggen** die **Just-in-Time-** Seite aus.

4. Wählen Sie im Feld **Just-in-Time-Debugging für diese Codetypen aktivieren** die relevanten Programmtypen **aus, oder**löschen Sie Sie: **verwaltet**, System eigen oder **Skript**.

    Nach dem Aktivieren von Just-In-Time-Debuggen müssen Sie über Administratorrechte verfügen, um es wieder zu deaktivieren. Beim Aktivieren von Just-In-Time-Debuggen wird ein Registrierungsschlüssel festgelegt, und zum Ändern dieses Schlüssels sind Administratorrechte erforderlich.

5. Klicken Sie auf **OK**.

   Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht installiert ist, können Sie das Just-in-Time-Debugging nicht über das Visual Studio-Dialogfeld **Optionen** deaktivieren. In diesem Fall können Sie Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung

1. Suchen Sie im **Startmenü** nach, und führen Sie es aus. `regedit.exe`

2. Suchen und löschen Sie die folgenden Registrierungseinträge im Fenster des **Registrierungs-Editors** :

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Wenn auf Ihrem Computer ein 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Löschen oder ändern Sie nicht versehentlich andere Registrierungsschlüssel.

5. Schließen Sie das Fenster **Registrierungs-Editor**.

> [!NOTE]
> Wenn Sie versuchen, das Just-in-Time-Debuggen für eine serverseitige APP zu deaktivieren, und diese Schritte das Problem nicht beheben, deaktivieren Sie das serverseitige Debuggen in den IIS-Anwendungseinstellungen, und wiederholen Sie den Vorgang.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>So aktivieren Sie das Just-In-Time-Debuggen für ein Windows Form

1. Windows Forms-Anwendungen verfügen über einen Ausnahmehandler der obersten Ebene, der dem Programm die weitere Ausführung ermöglicht, wenn eine Wiederherstellung möglich ist. Wenn Ihre Windows Forms Anwendung z. b. eine nicht behandelte Ausnahme auslöst, wird ein Dialogfeld wie das folgende angezeigt:

     ![Windowsformsunchdexception](../debugger/media/windowsformsunhandledexception.png "Windowsformsunchdexception")

     Um das Just-in-Time-Debuggen einer Windows Forms Anwendung zu aktivieren, müssen Sie die folgenden zusätzlichen Schritte ausführen:

2. Legen `jitDebugging` Sie den Wert `true` im- `system.windows.form` Abschnitt der Datei machine.config oder *\<application name>*.exe.config auf fest:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. In einer C++ Windows Form-Anwendung muss auch `DebuggableAttribute` in einer Konfigurationsdatei in Ihrem Code festgelegt werden. Bei der Kompilierung mit [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) und ohne [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435) wird dieses Attribut vom Compiler für Sie festgelegt. Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, müssen Sie den Wert selbst festlegen. Fügen Sie dazu der Datei "AssemblyInfo.cpp" der Anwendung die folgende Zeile hinzu:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Just-in-Time-Debuggen verwenden
 In diesem Abschnitt wird gezeigt, was geschieht, wenn eine ausführbare Datei eine Ausnahme auslöst.

 Zum Durchführen dieser Schritte muss Visual Studio installiert sein. Wenn Sie nicht über Visual Studio verfügen, können Sie die kostenlose [Visual Studio 2015 Community-Edition](https://visualstudio.microsoft.com/vs/older-downloads/)herunterladen.

 Wenn Sie Visual Studio installieren, wird das Just-In-Time-Debuggen standardmäßig aktiviert.

 Im Rahmen dieses Abschnitts erstellen wir eine c#-Konsolen-app in Visual Studio, die eine auslöst <xref:System.NullReferenceException> .

 Erstellen Sie in Visual Studio eine c#-Konsolen-app (**Datei/neu/Projekt/Visual c#/Konsolenanwendung**) namens **throwsnullexception**. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei Program.cs. Ersetzen Sie die Main()-Methode durch den folgenden Code, durch den eine Zeile in der Konsole ausgegeben und dann eine „NullReferenceException“ ausgelöst wird:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Damit dieses Verfahren in einer [Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md)funktioniert, müssen Sie [nur eigenen Code](../debugger/just-my-code.md)deaktivieren. Klicken Sie in Visual Studio auf Extras > **Optionen**. Wählen Sie **Options** im Dialogfeld Optionen **Debuggen**aus. Entfernen Sie die Überprüfung aus **nur eigenen Code aktivieren**.

 Erstellen Sie die Projekt Mappe (Klicken Sie in Visual Studio auf Projekt Mappe **erstellen/neu**erstellen). Sie können entweder die Debug-oder die Releasekonfiguration auswählen. Weitere Informationen zu Buildkonfigurationen finden Sie Untergrund Legendes zu [Buildkonfigurationen](../ide/understanding-build-configurations.md).

 Der Buildprozess erstellt eine ausführbare Datei ThrowsNullException.exe. Sie finden ihn unter dem Ordner, in dem Sie das c#-Projekt erstellt haben: **. ..\throwsnullexception\throwsnullexception\bin\debug** oder **. ..\throwsnullexception\throwsnullexception\bin\release**.

 Doppelklicken Sie auf den ThrowsNullException.exe. Ein Befehlsfenster sollte wie folgt angezeigt werden:

 ![ThrowsNullException – Konsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullException – Konsole")

 Nach einigen Sekunden wird ein Fehler Fenster angezeigt:

 ![Throwsnullexceptionerror](../debugger/media/throwsnullexceptionerror.png "Throwsnullexceptionerror")

 Klicken Sie nicht auf **Abbrechen**! Nach wenigen Sekunden sollten zwei Schaltflächen angezeigt werden: **Debuggen** und **Programm schließen**. Klicken Sie auf **Debug**.

> [!CAUTION]
> Wenn die Anwendung nicht vertrauenswürdigen Code enthält, wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt. In diesem Dialogfeld können Sie festlegen, ob das Debuggen fortgesetzt werden soll. Bevor Sie mit dem Debuggen fortfahren, entscheiden Sie, ob Sie den Code als vertrauenswürdig einstufen. Haben Sie den Code selbst geschrieben? Vertrauen Sie dem Programmierer? Wenn die Anwendung auf einem Remotecomputer ausgeführt wird, erkennen Sie den Namen des Prozesses? Selbst wenn die Anwendung lokal ausgeführt wird, bedeutet dies nicht unbedingt, dass sie als vertrauenswürdig eingestuft werden kann. Berücksichtigen Sie die Möglichkeit, dass bösartiger Code auf Ihrem Computer ausgeführt wird. Wenn Sie entscheiden, dass der Code, den Sie Debuggen, vertrauenswürdig ist, klicken Sie auf **Debuggen** Andernfalls klicken Sie auf **nicht Debuggen**.

 Das Fenster **Just-in-Time-Debugger von Visual Studio** wird angezeigt:

 ![Just-In-Time-Debugger – Dialogfeld](../debugger/media/justintimedialog.png "Just-In-Time-Debugger – Dialogfeld")

 Unter **möglichen**Debug-Elementen sollten Sie sehen, dass die **neue Instanz von Microsoft Visual Studio Zeile 2015** ausgewählt ist. Wenn es nicht bereits ausgewählt ist, wählen Sie es jetzt aus.

 Klicken Sie am unteren Rand des Fensters unter möchten **Sie mit dem ausgewählten Debugger Debuggen?** auf **Ja**.

 Das Projekt "throwsnullexception" wird in einer neuen Instanz von Visual Studio geöffnet, wobei die Ausführung in der Zeile angehalten wird, die die Ausnahme auslöst:

 ![Nullverweis – zweite Instanz](../debugger/media/nullreferencesecondinstance.png "Nullverweis – zweite Instanz")

 Sie können an dieser Stelle mit dem Debuggen beginnen. Wenn dies eine echte Anwendung wäre, müssten Sie herausfinden, warum der Code die Ausnahme auslöst.

## <a name="just-in-time-debugging-errors"></a>Fehler beim Just-In-Time-Debuggen
 Wenn das Dialogfeld nicht angezeigt wird, wenn das Programm abstürzt, kann dies auf Windows-Fehlerberichterstattung Einstellungen auf Ihrem Computer zurückzuführen sein. Weitere Informationen finden Sie unter [. Wer-Einstellungen](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Möglicherweise werden die folgenden Fehlermeldungen angezeigt, die mit Just-In-Time-Debuggen zusammenhängen.

- **An den abstürzenden Prozess kann nicht angehängt werden. Das angegebene Programm ist keine MS-DOS- oder Windows-Anwendung.**

     Dieser Fehler tritt auf, wenn Sie versuchen, einen Prozess anzufügen, der als anderer Benutzer ausgeführt wird.

     Um dieses Problem zu umgehen, starten Sie Visual Studio, öffnen Sie das Dialogfeld **an den Prozess anhängen** im Menü **Debuggen** , und suchen Sie in der Liste **Verfügbare Prozesse** den Prozess, den Sie debuggen möchten. Wenn Sie den Namen des Prozesses nicht kennen, sehen Sie sich das **Visual Studio-Dialogfeld Just-in-Time-Debugger** an, und notieren Sie sich die Prozess-ID. Wählen Sie den Prozess in der Liste **Verfügbare Prozesse** aus, und klicken Sie auf **Anhängen**. Klicken Sie im Dialogfeld **Just-in-Time-Debugger von Visual Studio** auf **Nein** , um das Dialogfeld zu schließen.

- **Der Debugger konnte nicht gestartet werden, da kein Benutzer angemeldet ist.**

     Dieser Fehler tritt auf, wenn vom Just-In-Time-Debuggen versucht wird, Visual Studio auf einem Computer zu starten, auf dem kein Benutzer bei der Konsole angemeldet ist. Da kein Benutzer angemeldet ist, existiert keine Benutzersitzung, um das Dialogfeld für Just-In-Time-Debuggen anzuzeigen.

     Um dieses Problem zu beheben, melden Sie sich beim Computer an.

- **Die Klasse ist nicht registriert.**

     Dieser Fehler zeigt, dass der Debugger versucht hat, eine nicht registrierte COM-Klasse zu erstellen. Die Ursache ist wahrscheinlich ein Installationsproblem.

     Beheben Sie dieses Problem, indem Sie Visual Studio mithilfe des Installationsdatenträgers neu installieren oder reparieren.

## <a name="see-also"></a>Weitere Informationen
 [Debuggersicherheitsdebugger](../debugger/debugger-security.md) [Grundlagen](../debugger/debugger-basics.md) [Just-in-Time, Debugging, Dialog Feld "Optionen](../debugger/just-in-time-debugging-options-dialog-box.md) " [Sicherheitswarnung: das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig sind oder Sie sich nicht sicher sind, fügen Sie diesen Vorgang nicht an](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015) .
