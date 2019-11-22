---
title: Attach to Running Processes with the Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299517"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. After the process is running, click **Debug / Attach to Process** (or press **CTRL+ALT+P**) to open the **Attach to Process** dialog box.

You can use this capability to debug apps that are running on a local or remote computer, debug multiple processes simultaneously, or debug an application that was not created in Visual Studio. It is often useful when you want to debug an app, but (for whatever reason) you did not start the app from Visual Studio with the debugger attached. For example, if you are running the app without the debugger and hit an exception, you might then attach to the process running the app to begin debugging.

> [!TIP]
> Not sure whether you need to use **Attach to Process** for your debugging scenario? See [Common debugging scenarios](#BKMK_Scenarios). If you want to debug ASP.NET applications that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Attach to a running process on the local machine
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names).

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

     To quickly select the process you want, type the first letter of the process name. If you don't know the process name, see [Common debugging scenarios](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .

3. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Bei Verwendung der Standardeinstellung **Automatisch** wird versucht, den zu debuggenden Codetyp zu ermitteln. Führen Sie die folgenden Schritte aus, um den Codetyp manuell festzulegen:

    1. Klicken Sie neben dem Feld **Anfügen an:** auf **Auswählen...** .

    2. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie die zu debuggenden Codetypen aus.

    3. Klicken Sie auf **OK**.

4. Klicken Sie auf **Anfügen**aus.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names). For more complete guidance for ASP.NET apps that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Bei anderen Anwendungen finden Sie den Namen des Prozesses möglicherweise im Task-Manager.

 Wenn Sie das Dialogfeld **An den Prozess anhängen** verwenden, können Sie einen anderen Computer auswählen, der für das Remotedebuggen eingerichtet wurde. For more information, see [Remote Debugging](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Nach dem Auswählen eines Remotecomputers können Sie über eine Liste, in der alle verfügbaren laufenden Prozesse des Remotecomputers enthalten sind, den Debugger an einen oder mehrere Prozesse anhängen.

 **To select a remote computer:**

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. Wählen Sie im Dialogfeld **An den Prozess anhängen** die entsprechende Verbindungsart aus der Liste **Transport** aus. **Standard** ist für die meisten Programme die richtige Einstellung.

   Die Einstellung **Transport** bleibt zwischen Debugsitzungen erhalten.

3. Verwenden Sie das Listenfeld **Qualifizierer** , um den Remotecomputernamen mithilfe einer der folgenden Methoden auszuwählen:

   1. Geben Sie im Listenfeld **Qualifizierer** den Namen ein.

      > [!NOTE]
      > If, in later steps, you can't connect using the remote computer name, use the IP address. (The port number may appear automatically after selecting the process. You can also enter it manually. In the illustration below, 4020 is the default port for the remote debugger.)

   2. Klicken Sie auf den Dropdownpfeil neben dem Listenfeld **Qualifizierer** , und wählen Sie den Computernamen aus der Dropdownliste aus.

   3. Click the **Find** button next to the **Qualifier** list to open the **Select Remote Debugger Connection** dialog box. Im Dialogfeld **Remotedebuggerverbindung auswählen** werden alle Geräte aufgeführt, die sich auf dem lokalen Subnetz befinden, sowie sämtliche Geräte, die über ein Ethernetkabel direkt mit dem Computer verbunden sind. Klicken Sie auf den gewünschten Computer bzw. das gewünschte Gerät, und klicken Sie dann auf **Auswählen**.

      Die Einstellung **Qualifizierer** bleibt nur zwischen Debugsitzungen erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Qualifizierer auftritt.

4. Klicken Sie auf **Aktualisieren**.

     Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Der Inhalt ist jedoch nicht immer aktuell. Sie können die Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf **Aktualisieren**.

5. Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

    Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .

6. Klicken Sie auf **Anfügen**aus.

## <a name="additional-info"></a>Additional info

Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen. Weitere Informationen finden Sie unter [Gewusst wie: Festlegen des aktuellen Programms](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, der nur über ein eingeschränktes Benutzerkonto verfügt, enthält die Liste **Verfügbare Prozesse** keine Prozesse, die in Sitzung 0 laufen. Sie wird für Dienste und andere Serverprozesse verwendet, wie z.B. „w3wp.exe“. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p` *ProzessID* in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um die Datei "tlist.exe" abzurufen, laden Sie die Debugtools für Windows von der Seite  [WDK- und WinDbg-Downloads](https://go.microsoft.com/fwlink/?LinkId=168279)herunter, und installieren Sie diese.

## <a name="BKMK_Scenarios"></a> Common debugging scenarios

To help you identify whether you need to use **Attach to process** and what process to attach to, a few common debugging scenarios are shown here (the list is not exhaustive). Where more instructions are available, we provide links.

For some app types (like Windows Store apps), you don't attach directly to a process name, but use the **Debug Installed App Package** menu option instead (see table).

> [!NOTE]
> For information about basic debugging in Visual Studio, see [Getting started with the debugger](../debugger/getting-started-with-the-debugger.md).

|Szenario|Debug Method|Prozessname|Notes and Links|
|-|-|-|-|
|Debug a managed or native app on the local machine|Use attach to process or [standard debugging](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|To quickly access the dialog box, use **CTRL+ALT+P** and then type the first letter of the process name.|
|Debug ASP.NET apps on the local machine after starting the app without the debugger|Use attach to process|iiexpress.exe|This may be helpful to make your app load faster, such as (for example) when profiling. |
|Remote debug ASP.NET 4 or 4.5 on an IIS server|Use remote tools and attach to process|w3wp.exe|See [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote debug ASP.NET Core on an IIS server|Use remote tools and attach to process|dnx.exe|For app deployment, see [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html). For debugging, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug other supported app types on a server process|Use remote tools (if server is remote) and attach to process|iexplore.exe or other processes|If necessary, use Task Manager to help identify the process. See [Remote Debugging](../debugger/remote-debugging.md) and later sections in this topic|
|Remote debug a Windows desktop app|Remote Tools and F5|Nicht zutreffend| See [Remote Debugging](../debugger/remote-debugging.md)|
|Remote debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app|Installiertes App-Paket debuggen|Nicht zutreffend|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|
|Debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app that you didn't start from Visual Studio|Installiertes App-Paket debuggen|Nicht zutreffend|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|

> [!WARNING]
> Zum Anhängen an eine in JavaScript geschriebene universelle Windows-App müssen Sie zuerst das Debuggen für die App aktivieren. Weitere Informationen hierzu finden Sie unter [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) im Windows Developer Center.

> [!NOTE]
> Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) -Linkeroption herstellen.

## <a name="what-debugger-features-can-i-use"></a>What debugger features can I use?

To use the full features of the Visual Studio debugger (like hitting breakpoints) when attaching to a process, the executable must exactly match your local source and symbols (that is, the debugger must be able to load the correct [symbol (.pbd) files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). By default, this requires a debug build.

For remote debugging scenarios, you must have the source code (or a copy of the source code) already open in Visual Studio. The compiled app binaries on the remote machine must come from the same build as on the local machine.

In some local debugging scenarios, you can debug in Visual Studio with no access to the source if the correct symbol files are present with the app (by default, this requires a debug build). For more info, see [Specify Symbol and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.

 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.

 Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.

 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die vorherige Beispielmeldung weist darauf hin, dass der Skriptcodetyp nicht angefügt werden konnte. Deshalb wäre es nicht möglich, den Skriptcode innerhalb des Prozesses zu debuggen. Der Skriptcode im Prozess würde zwar weiterhin ausgeführt werden, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen im Skript durchzuführen.

 Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.

 **To obtain specific information about why a code type failed to attach**

1. Trennen Sie den Prozess. Klicken Sie im Menü **Debuggen** auf **Alle trennen**.

2. Fügen Sie den Prozess erneut an, und wählen Sie hierbei nur einen Codetyp aus.

   1. Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.

   2. Klicken Sie auf **Auswählen**.

   3. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Löschen Sie allen übrigen Code.

   4. Klicken Sie auf **OK**. Das Dialogfeld **Codetyp auswählen** wird geschlossen.

   5. Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Anhängen**.

      Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.

## <a name="see-also"></a>Siehe auch
 [Debug Multiple Processes](../debugger/debug-multiple-processes.md) [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) [Remote Debugging](../debugger/remote-debugging.md)
