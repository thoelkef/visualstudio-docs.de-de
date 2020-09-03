---
title: Anfügen an laufende Prozesse mit dem Debugger | Microsoft-Dokumentation
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
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918946"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wurde, klicken Sie auf **Debuggen/an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**), um das Dialogfeld **an den Prozess anhängen** zu öffnen.

Mit dieser Funktion können Sie apps Debuggen, die auf einem lokalen oder Remote Computer ausgeführt werden, mehrere Prozesse gleichzeitig Debuggen oder eine Anwendung debuggen, die nicht in Visual Studio erstellt wurde. Dies ist oft hilfreich, wenn Sie eine APP debuggen möchten, aber (aus irgendeinem Grund) haben Sie die APP nicht aus Visual Studio gestartet, und der Debugger ist angefügt. Wenn Sie z. b. die APP ohne den Debugger ausführen und eine Ausnahme ausgelöst haben, können Sie den Prozess, der die app ausführen soll, anfügen, um mit dem Debuggen zu beginnen.

> [!TIP]
> Sie sind nicht sicher, ob Sie das **Anfügen an den Prozess** für Ihr Debugszenario verwenden müssen? Weitere Informationen finden Sie unter [Allgemeine Debugszenarien](#BKMK_Scenarios). Wenn Sie ASP.NET-Anwendungen debuggen möchten, die in IIS bereitgestellt wurden, finden Sie weitere Informationen unter [Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Anfügen an einen laufenden Prozess auf dem lokalen Computer
 Um an einen Prozess anzufügen, müssen Sie den Namen des Prozesses kennen (Weitere Informationen finden Sie unter [häufige Debugszenarien](#BKMK_Scenarios) für einige gängige Prozessnamen).

1. Wählen Sie in Visual Studio **Debuggen/an den Prozess anhängen** aus (oder drücken Sie **STRG + ALT + P**).

2. Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

     Geben Sie den ersten Buchstaben des Prozess namens ein, um den gewünschten Prozess schnell auszuwählen. Wenn Sie den Prozessnamen nicht kennen, finden Sie weitere Informationen unter [häufige Debugszenarien](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .

3. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Bei Verwendung der Standardeinstellung **Automatisch** wird versucht, den zu debuggenden Codetyp zu ermitteln. Führen Sie die folgenden Schritte aus, um den Codetyp manuell festzulegen:

    1. Klicken Sie neben dem Feld **Anfügen an:** auf **Auswählen...**.

    2. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie die zu debuggenden Codetypen aus.

    3. Klicken Sie auf **OK**.

4. Klicken Sie auf **Anfügen**aus.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer
 Um an einen Prozess anzufügen, müssen Sie den Namen des Prozesses kennen (Weitere Informationen finden Sie unter [häufige Debugszenarien](#BKMK_Scenarios) für einige gängige Prozessnamen). Eine ausführlichere Anleitung für ASP.net-apps, die in IIS bereitgestellt wurden, finden Sie unter [Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Bei anderen Anwendungen finden Sie den Namen des Prozesses möglicherweise im Task-Manager.

 Wenn Sie das Dialogfeld **An den Prozess anhängen** verwenden, können Sie einen anderen Computer auswählen, der für das Remotedebuggen eingerichtet wurde. Weitere Informationen finden Sie unter [Remotedebuggen](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Nach dem Auswählen eines Remotecomputers können Sie über eine Liste, in der alle verfügbaren laufenden Prozesse des Remotecomputers enthalten sind, den Debugger an einen oder mehrere Prozesse anhängen.

 **So wählen Sie einen Remotecomputer aus:**

1. Wählen Sie in Visual Studio **Debuggen/an den Prozess anhängen** aus (oder drücken Sie **STRG + ALT + P**).

2. Wählen Sie im Dialogfeld **An den Prozess anhängen** die entsprechende Verbindungsart aus der Liste **Transport** aus. **Standard** ist für die meisten Programme die richtige Einstellung.

   Die Einstellung **Transport** bleibt zwischen Debugsitzungen erhalten.

3. Verwenden Sie das Listenfeld **Qualifizierer** , um den Remotecomputernamen mithilfe einer der folgenden Methoden auszuwählen:

   1. Geben Sie im Listenfeld **Qualifizierer** den Namen ein.

      > [!NOTE]
      > Wenn Sie in späteren Schritten keine Verbindung mit dem Remote Computernamen herstellen können, verwenden Sie die IP-Adresse. (Die Portnummer wird möglicherweise automatisch angezeigt, nachdem Sie den Prozess ausgewählt haben. Sie können Sie auch manuell eingeben. In der Abbildung unten ist 4020 der Standardport für den Remote Debugger.)

   2. Klicken Sie auf den Dropdownpfeil neben dem Listenfeld **Qualifizierer** , und wählen Sie den Computernamen aus der Dropdownliste aus.

   3. Klicken Sie neben der Liste **Qualifizierer** auf die Schaltfläche **Suchen** , um das Dialogfeld remotedebuggerverbindung **auswählen** zu öffnen. Im Dialogfeld **Remotedebuggerverbindung auswählen** werden alle Geräte aufgeführt, die sich auf dem lokalen Subnetz befinden, sowie sämtliche Geräte, die über ein Ethernetkabel direkt mit dem Computer verbunden sind. Klicken Sie auf den gewünschten Computer bzw. das gewünschte Gerät, und klicken Sie dann auf **Auswählen**.

      Die Einstellung **Qualifizierer** bleibt nur zwischen Debugsitzungen erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Qualifizierer auftritt.

4. Klicken Sie auf **Aktualisieren**.

     Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Der Inhalt ist jedoch nicht immer aktuell. Sie können die Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf **Aktualisieren**.

5. Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

    Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .

6. Klicken Sie auf **Anfügen**aus.

## <a name="additional-info"></a>Zusätzliche Informationen

Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen. Weitere Informationen finden Sie unter [Gewusst wie: Festlegen des aktuellen Programms](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, der nur über ein eingeschränktes Benutzerkonto verfügt, enthält die Liste **Verfügbare Prozesse** keine Prozesse, die in Sitzung 0 laufen. Sie wird für Dienste und andere Serverprozesse verwendet, wie z.B. „w3wp.exe“. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p` *ProzessID* in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit tlist.exe ermittelt werden. Zum Abrufen tlist.exe können Sie die Debugtools für Windows herunterladen und installieren, die unter  [WDK-und WinDbg-Downloads](/windows-hardware/drivers/dashboard/)verfügbar sind.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Allgemeine Debugszenarien

Um Ihnen zu helfen, zu ermitteln, ob Sie " **an den Prozess anhängen** " und den Prozess zum Anfügen verwenden müssen, werden hier einige gängige Debugszenarien angezeigt (die Liste ist nicht vollständig). Wenn weitere Anweisungen verfügbar sind, bieten wir Links.

Bei einigen App-Typen (wie Windows Store-Apps) fügen Sie nicht direkt an einen Prozessnamen an, sondern verwenden stattdessen die Menüoption " **installiertes App-Paket Debuggen** " (siehe Tabelle).

> [!NOTE]
> Informationen zum grundlegenden Debuggen in Visual Studio finden Sie unter [Getting Started with the Debugger](../debugger/getting-started-with-the-debugger.md).

|Szenario|Debug-Methode|Prozessname|Hinweise und Links|
|-|-|-|-|
|Debuggen einer verwalteten oder nativen App auf dem lokalen Computer|Verwenden von Anhängen an den Prozess oder [Standard-Debuggen](../debugger/getting-started-with-the-debugger.md)|*appname*. exe|Um schnell auf das Dialogfeld zuzugreifen, verwenden Sie **STRG + ALT + P** , und geben Sie dann den ersten Buchstaben des Prozess namens ein.|
|Debuggen von ASP.net-apps auf dem lokalen Computer nach dem Starten der APP ohne den Debugger|"An den Prozess anhängen" verwenden|iiexpress.exe|Dies kann hilfreich sein, damit Ihre App schneller geladen wird, z. B. bei der Profilerstellung. |
|Remotedebuggen von ASP.NET 4 oder 4.5 auf einem IIS-Server|Remote Tools verwenden und an den Prozess anhängen|w3wp.exe|Weitere Informationen finden Sie [unter Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebuggen von ASP.NET Core auf einem IIS-Server|Remote Tools verwenden und an den Prozess anhängen|dnx.exe|Informationen zur Bereitstellung von Apps finden Sie unter [Veröffentlichen in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Informationen zum Debuggen finden Sie [unter Remote Debugging ASP.net auf einem IIS-Remote Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Debuggen anderer unterstützter App-Typen für einen Serverprozess|Remote Tools verwenden (wenn der Server Remote ist) und an den Prozess anhängen|iexplore.exe oder andere Prozesse|Verwenden Sie ggf. den Task-Manager, um den Prozess zu identifizieren. Weitere Informationen finden Sie unter [Remote Debugging](../debugger/remote-debugging.md) und spätere Abschnitte in diesem Thema.|
|Remotedebuggen einer Windows-Desktop-App|Remotetools und F5|–| Siehe [Remote Debuggen](../debugger/remote-debugging.md)|
|Remote Debuggen einer universellen Windows-app (UWP), onecore, hololens oder IOT-App|Installiertes App-Paket debuggen|Nicht zutreffend|**Debug/andere debugziele verwenden/installiertes App-Paket Debuggen** **, anstatt an den Prozess anhängen**|
|Debuggen Sie eine Windows Universal (UWP)-, onecore-, hololens-oder IOT-APP, die Sie nicht von Visual Studio aus gestartet haben.|Installiertes App-Paket debuggen|Nicht zutreffend|**Debug/andere debugziele verwenden/installiertes App-Paket Debuggen** **, anstatt an den Prozess anhängen**|

> [!WARNING]
> Zum Anhängen an eine in JavaScript geschriebene universelle Windows-App müssen Sie zuerst das Debuggen für die App aktivieren. Weitere Informationen hierzu finden Sie unter [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) im Windows Developer Center.

> [!NOTE]
> Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) -Linkeroption herstellen.

## <a name="what-debugger-features-can-i-use"></a>Welche Debuggerfunktionen kann ich verwenden?

Um die vollständigen Funktionen des Visual Studio-Debuggers (z. b. das erreichen von Haltepunkten) beim Anfügen an einen Prozess zu verwenden, muss die ausführbare Datei genau mit der lokalen Quelle und den Symbolen übereinstimmen (d. h., der Debugger muss die richtigen [Symbol Dateien (. PBD)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)laden können). Standardmäßig ist hierfür ein Debugbuild erforderlich.

Für Remotedebuggingszenarien müssen Sie den Quellcode (oder eine Kopie des Quellcodes) bereits in Visual Studio geöffnet haben. Die kompilierten Binärdateien der App auf dem Remotecomputer müssen vom gleichen Build wie auf dem lokalen Computer stammen.

In einigen lokalen debuggingszenarien können Sie in Visual Studio ohne Zugriff auf die Quelle Debuggen, wenn die richtigen Symbol Dateien mit der app vorhanden sind (Standardmäßig ist hierfür ein Debugbuild erforderlich). Weitere Informationen finden Sie unter [Angeben von Symbol-und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.

 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.

 Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.

 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die vorherige Beispielmeldung weist darauf hin, dass der Skriptcodetyp nicht angefügt werden konnte. Deshalb wäre es nicht möglich, den Skriptcode innerhalb des Prozesses zu debuggen. Der Skriptcode im Prozess würde zwar weiterhin ausgeführt werden, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen im Skript durchzuführen.

 Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.

 **So erhalten Sie spezifische Informationen dazu, warum ein Codetyp nicht angefügt werden konnte**

1. Trennen Sie den Prozess. Klicken Sie im Menü **Debuggen** auf **Alle trennen**.

2. Fügen Sie den Prozess erneut an, und wählen Sie hierbei nur einen Codetyp aus.

   1. Wählen Sie im Dialogfeld **an den Prozess anhängen** in der Liste **Verfügbare Prozesse** den Prozess aus.

   2. Klicken Sie auf **Auswählen**.

   3. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Löschen Sie allen übrigen Code.

   4. Klicken Sie auf **OK**. Das Dialogfeld **Codetyp auswählen** wird geschlossen.

   5. Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Anhängen**.

      Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.

## <a name="see-also"></a>Weitere Informationen
 Debuggen [mehrerer Prozesse](../debugger/debug-multiple-processes.md) [Just-in-Time-Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) für [Remote Debugging](../debugger/remote-debugging.md)
