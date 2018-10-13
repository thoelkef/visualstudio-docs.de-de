---
title: Just-In-Time-Debuggen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 606f0129d49e8d5b8f07e6c8fac60fa5029a4828
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294046"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Just-In-Time-Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Just-In-Time-Debuggen startet Visual Studio automatisch tritt eine Ausnahme oder ein Absturz in einer Anwendung, die außerhalb von Visual Studio ausgeführt wird. Dadurch können Sie Ihre Anwendung testen, wenn Visual Studio nicht ausgeführt wird, und beginnen mit Visual Studio debuggen, wenn ein Problem auftritt.

Just-In-Time-Debuggen funktioniert für Windows desktop-apps. Es funktioniert nicht für universelle Windows-apps, und es funktioniert nicht für verwalteten Code, der in einer systemeigenen Anwendung, z. B. in Schnellansichten gehostet wird.

## <a name="BKMK_Scenario"></a> Haben Sie die Just-in-Time-Debugger-Dialogfeld angezeigt, wenn Sie versuchen, die zum Ausführen einer app?

Die Aktionen, die Sie abwartet, wenn Sie sehen, dass die Visual Studio Just-in-Time Debugger Dialogfeld abhängig sind, auf was Sie tun möchten:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Führen Sie die app sollten Sie das Dialogfeld zu entfernen und einfach wie gewohnt

1. (Fortgeschrittene Benutzer) Wenn Sie Visual Studio installiert haben (oder Sie es zuvor installiert hatten, und entfernt sie), [deaktivieren Sie Just-in-Time-Debuggen](#BKMK_Enabling) und führen Sie die app erneut aus.

2. Wenn Sie eine Web-app in Internet Explorer ausgeführt werden, deaktivieren Sie das Skriptdebuggen.

    Deaktivieren Sie das Skriptdebuggen in das Dialogfeld "Internetoptionen". Sie erreichen dies über die **Systemsteuerung** / **Netzwerk und Internet** / **Internetoptionen** (die genauen Schritte hängen Ihre Version von Windows und InternetExplorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Öffnen Sie erneut die Webseite, in dem Sie den Fehler gefunden. Wenn dies das Problem nicht behebt, wenden Sie sich an den Besitzer der Web-app, um das Problem zu beheben.

4. Wenn Sie eine andere Art von Windows-app ausführen, müssen Sie wenden Sie sich an den Besitzer der app, um den Fehler beheben, und klicken Sie dann erneut die korrigierten Version der app zu installieren.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Wenn Sie möchten zu beheben oder Debuggen des Fehlers (fortgeschrittene Benutzer)

- Sie benötigen [Visual Studio installiert](https://www.microsoft.com/download/details.aspx?id=48146) um die ausführliche Informationen zum Fehler anzuzeigen und zu debuggen. Finden Sie unter [mithilfe von JIT-Kompilierung](#BKMK_Using_JIT) ausführliche Anweisungen. Wenn Sie nicht den Fehler beheben, und beheben Sie die app, wenden Sie sich an den Besitzer der app, um den Fehler zu beheben.
  
##  <a name="BKMK_Enabling"></a> Aktivieren oder deaktivieren Sie Just-in-Time-Debuggen  
 Sie können aktivieren oder deaktivieren Sie Just-in-Time-Debuggen von Visual Studio **Extras / Optionen** Dialogfeld.  
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>So aktivieren oder deaktivieren Sie Just-In-Time-Debuggen  
  
1.  Öffnen Sie Visual Studio. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** wählen Sie im Dialogfeld die **Debuggen** Ordner.  
  
3.  In der **Debuggen** Ordner, wählen die **Just-In-Time-** Seite.  
  
4.  In der **diese Codetypen aktivieren von Just-in-Time-Debuggen** Feld aktivieren bzw. deaktivieren Sie die gewünschten Programmtypen: **verwaltete**, **Native**, oder **Skript**.  
  
     Nach dem Aktivieren von Just-In-Time-Debuggen müssen Sie über Administratorrechte verfügen, um es wieder zu deaktivieren. Beim Aktivieren von Just-In-Time-Debuggen wird ein Registrierungsschlüssel festgelegt, und zum Ändern dieses Schlüssels sind Administratorrechte erforderlich.  
  
5.  Klicken Sie auf **OK**.  
  
 Just-In-Time-Debuggen ist möglicherweise immer noch aktiviert, auch wenn Visual Studio nicht mehr auf dem Computer installiert ist. Wenn Visual Studio nicht installiert ist, können Sie nicht Just-In-Time-Debuggen von Visual Studio deaktivieren **Optionen** Dialogfeld. In diesem Fall können Sie Just-In-Time-Debuggen durch Bearbeiten der Windows-Registrierung deaktivieren.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>So deaktivieren Sie Just-In-Time-Debuggen durch Bearbeiten der Registrierung  
  
1.  Auf der **starten** Menüs, suchen und ausführen `regedit.exe`  
  
2.  In der **Registrierungs-Editor** Fenster Suchen und löschen Sie die Registrierungseinträge gehen Sie folgendermaßen vor:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger  
  
3.  Wenn Ihr Computer eine 64-Bit-Betriebssystem ausgeführt wird, löschen Sie auch die folgenden Registrierungseinträge:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Löschen oder ändern Sie nicht versehentlich andere Registrierungsschlüssel.  
  
5.  Schließen der **Registrierungs-Editor** Fenster.  
  
> [!NOTE]
>  Wenn Sie versuchen, das Just-In-Time-Debuggen für eine serverseitige app zu deaktivieren und diese Schritte das Problem nicht beheben kann, serverseitige debugging in den Einstellungen des IIS-Anwendung deaktivieren Sie, und wiederholen Sie.  
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>So aktivieren Sie das Just-In-Time-Debuggen für ein Windows Form  
  
1.  Windows Forms-Anwendungen verfügen über einen Ausnahmehandler der obersten Ebene, der dem Programm die weitere Ausführung ermöglicht, wenn eine Wiederherstellung möglich ist. Wenn die Windows Forms-Anwendung eine nicht behandelte Ausnahme auslöst, werden Sie z. B. ein Dialogfeld wie folgt angezeigt:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     So aktivieren Sie Just-In-Time-Debuggen einer Windows Forms-Anwendung, müssen Sie die folgenden zusätzlichen Schritte ausführen:  
  
2.  Legen Sie die `jitDebugging` Wert `true` in die `system.windows.form` Abschnitt der Datei machine.config oder  *\<Anwendungsname >*. exe.config-Datei:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  In einer C++ Windows Form-Anwendung muss auch `DebuggableAttribute` in einer Konfigurationsdatei in Ihrem Code festgelegt werden. Bei der Kompilierung mit ["/ Zi"](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) und ohne ["/ Og"](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), legt der Compiler dieses Attribut für Sie. Wenn Sie einen nicht optimierten Releasebuild debuggen möchten, müssen Sie den Wert selbst festlegen. Fügen Sie dazu der Datei "AssemblyInfo.cpp" der Anwendung die folgende Zeile hinzu:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Weitere Informationen finden Sie unter <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Verwenden Sie die Just-In-Time-Debuggen  
 Dieser Abschnitt zeigt, was geschieht, wenn eine ausführbare Datei eine Ausnahme auslöst.  
  
 Sie benötigen Visual Studio installiert, um die folgenden Schritte ausführen zu können. Wenn Sie Visual Studio nicht haben, können Sie die kostenlose Herunterladen [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146).  
  
 Wenn Sie Visual Studio installieren, wird das Just-In-Time-Debuggen standardmäßig aktiviert.  
  
 Für die Zwecke dieses Artikels, wir erstellen eine C#-Konsolen-app in Visual Studio, das löst eine <xref:System.NullReferenceException>.  
  
 Erstellen Sie in Visual Studio eine C#-Konsolen-app (**Datei / neu / Projekt / Visual C#-/ Konsolenanwendung**) mit dem Namen **ThrowsNullException**. Weitere Informationen zum Erstellen von Projekten in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Wenn das Projekt in Visual Studio geöffnet wird, öffnen Sie die Datei "Program.cs" ein. Ersetzen der Main()-Methode durch den folgenden Code, der gibt eine Zeile an die Konsole, und klicken Sie dann eine NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  In der Reihenfolge für dieses Verfahren funktioniert einer [Releasekonfiguration](../debugger/how-to-set-debug-and-release-configurations.md), Sie deaktivieren möchten [nur mein Code](../debugger/just-my-code.md). Klicken Sie in Visual Studio auf **Extras / Optionen**. In der **Optionen** wählen Sie im Dialogfeld **Debuggen**. Entfernen Sie das Kontrollkästchen **nur meinen Code aktivieren**.  
  
 Erstellen Sie die Projektmappe (Wählen Sie in Visual Studio **Build / Jektmappe**). Sie können entweder das Debuggen oder der Release-Konfiguration auswählen. Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
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
  
 Klicken Sie unter **Mögliche Debugger**, sollte angezeigt werden, die **neue Instanz von Microsoft Visual Studio 2015** Zeile ausgewählt ist. Wenn sie nicht bereits ausgewählt ist, wählen Sie sie jetzt ein.  
  
 Am unteren Fensterrand unter **möchten Sie mit dem ausgewählten Debugger zu Debuggen?**, klicken Sie auf **Ja**.  
  
 Das Projekt ThrowsNullException öffnet in einer neuen Instanz von Visual Studio, bei der Ausführung beendet wird, in der Zeile, die die Ausnahme auslöst:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Sie können die an diesem Punkt Debuggen starten. Wenn dies eine reale Anwendung wäre, müssten Sie herausfinden, warum der Code die Ausnahme auslöst.  
  
## <a name="just-in-time-debugging-errors"></a>Fehler beim Just-In-Time-Debuggen  
 Wenn Sie das Dialogfeld nicht angezeigt wird, wenn die Anwendung abstürzt, kann dies aufgrund von Windows-Fehlerberichterstattung-Einstellungen auf Ihrem Computer. Weitere Informationen finden Sie unter [. WER-Einstellungen](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).  
  
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
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Just-In-Time, Debuggen, Dialogfeld "Optionen"](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)



