---
title: Anfügen an laufende Prozesse mit dem Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 04/08/2019
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
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1a41667592b6965497f9b87514719f7d8a5a442
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75775977"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wurde, wählen Sie **Debuggen** , > **an den Prozess anhängen** , oder drücken Sie **STRG**+**alt**+**P** in Visual Studio, und fügen Sie den Debugger mit dem Dialogfeld an den Prozess **Anhängen** an den Prozess an.

Sie können **Anfügen an den Prozess** verwenden, um die Ausführung von apps auf lokalen Computern oder Remote Computern zu debuggen, mehrere Prozesse gleichzeitig zu debuggen, apps zu debuggen, die nicht in Visual Studio erstellt wurden, oder eine APP zu debuggen, die Sie nicht Wenn Sie z. b. eine APP ohne den Debugger ausführen und eine Ausnahme erreichen, können Sie den Debugger an den Prozess anfügen, der die app ausführen und mit dem Debuggen beginnen.

> [!TIP]
> Sie sind nicht sicher, ob Sie das **Anfügen an den Prozess** für Ihr Debugszenario verwenden Siehe [gängige Debugszenarien](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a>Anfügen an einen laufenden Prozess auf dem lokalen Computer

Informationen zum schnellen erneuten Anfügen an einen Prozess, den Sie zuvor angefügt haben, finden Sie unter [wieder anfügen an einen Prozess](#BKMK_reattach).

Informationen zum Debuggen eines Prozesses auf einem Remote Computer finden Sie unter [Anfügen an einen Prozess auf einem Remote Computer](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Informationen zum Debuggen eines .net Core-Prozesses in einem Linux docker-Container finden Sie unter [Anfügen an einen Linux docker-Container](#BKMK_Docker_Attach).
::: moniker-end

**Anfügen an einen Prozess auf dem lokalen Computer:**

1. Wählen Sie in Visual Studio **Debuggen** > **an den Prozess anfügen** aus (oder drücken Sie **STRG**+**alt**+**P**), um das Dialogfeld **an den Prozess anhängen** zu öffnen.

   Der **Verbindungstyp** sollte auf **default**festgelegt werden. Das **Verbindungs Ziel** sollte der Name des lokalen Computers sein.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, den Sie anfügen möchten.

   - Geben Sie den Namen oder den ersten Buchstaben im Feld **Filter Prozesse** ein, um schnell einen Prozess auszuwählen.

   - Wenn Sie den Prozessnamen nicht kennen, Durchsuchen Sie die Liste, oder sehen Sie sich [häufige Debugszenarien](#BKMK_Scenarios) für einige gängige Prozessnamen an.

   >[!TIP]
   >Prozesse können im Hintergrund gestartet und angehalten werden, während das Dialogfeld **an den Prozess anhängen** geöffnet ist, sodass die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

3. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Die **Automatische** Standardeinstellung funktioniert für die meisten App-Typen.

   So wählen Sie Codetypen manuell aus:
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** die Option **Diese Codetypen debuggen**aus.
   1. Wählen Sie die zu debuggenden Codetypen aus.
   1. Klicken Sie auf **OK**.

4. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können mehrere Apps zum Debuggen anfügen, es ist jedoch jeweils nur eine APP im Debugger aktiv. Sie können die aktive app in der Visual Studio-Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer

Sie können auch im Dialogfeld **an den Prozess anhängen** einen Remote Computer auswählen, eine Liste der verfügbaren Prozesse anzeigen, die auf diesem Computer ausgeführt werden, und einen oder mehrere der Prozesse zum Debuggen anfügen. Der Remote Debugger (*msvsmon. exe*) muss auf dem Remote Computer ausgeführt werden. Weitere Informationen finden Sie unter [Remote Debuggen](../debugger/remote-debugging.md).

Ausführlichere Anweisungen zum Debuggen von ASP.NET-Anwendungen, die in IIS bereitgestellt wurden, finden Sie unter [Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Anfügen an einen laufenden Prozess auf einem Remote Computer:**

1. Wählen Sie in Visual Studio **Debuggen** > **an den Prozess anfügen** aus (oder drücken Sie **STRG**+**alt**+**P**), um das Dialogfeld **an den Prozess anhängen** zu öffnen.

2. Der **Verbindungstyp** sollte in den meisten Fällen **standardmäßig** sein. Wählen Sie im Feld **Verbindungs Ziel** den Remote Computer aus, indem Sie eine der folgenden Methoden verwenden:

   - Wählen Sie den Dropdown Pfeil neben **Verbindungs Ziel**aus, und wählen Sie den Computernamen aus der Dropdown Liste aus.
   - Geben Sie den Computernamen in das Feld **Verbindungs Ziel** ein, und drücken **Sie die Eingabe**Taste.

     Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im folgenden Format angezeigt wird: **\<Remote Computername >:p Ort** .

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Wenn Sie keine Verbindung mit dem Remote Computernamen herstellen können, verwenden Sie die IP-Adresse und die Portadresse (z. b. `123.45.678.9:4022`). 4024 ist der Standardport für den Visual Studio 2019 x64-Remote Debugger. Informationen zu anderen Port Zuweisungen für Remote Debugger finden Sie unter [Port Zuweisungen für Remote Debugger](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Wenn Sie keine Verbindung mit dem Remote Computernamen herstellen können, verwenden Sie die IP-Adresse und die Portadresse (z. b. `123.45.678.9:4022`). 4022 ist der Standardport für den Visual Studio 2017 x64-Remote Debugger. Informationen zu anderen Port Zuweisungen für Remote Debugger finden Sie unter [Port Zuweisungen für Remote Debugger](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Wählen Sie neben dem Feld **Verbindungs Ziel** die Schaltfläche **Suchen** aus, um das Dialogfeld **Remote Verbindungen** zu öffnen. Im Dialogfeld **Remote Verbindungen** werden alle Geräte aufgelistet, die sich in Ihrem lokalen Subnetz befinden oder direkt an den Computer angeschlossen sind. Möglicherweise müssen Sie den [UDP-Port 3702](../debugger/remote-debugger-port-assignments.md) auf dem Server öffnen, um Remote Geräte zu ermitteln. Wählen Sie den gewünschten Computer bzw. das gewünschte Gerät aus, und klicken Sie dann auf **auswählen**.

   > [!NOTE]
   > Die Einstellung für den **Verbindungstyp** bleibt zwischen Debugsitzungen erhalten. Die **Verbindungs Ziel** Einstellung bleibt zwischen Debugsitzungen nur dann erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Ziel aufgetreten ist.

3. Klicken Sie auf aktualisieren, um die Liste **Verfügbare Prozesse** **aufzufüllen** .

    >[!TIP]
    >Prozesse können im Hintergrund gestartet und angehalten werden, während das Dialogfeld **an den Prozess anhängen** geöffnet ist, sodass die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

4. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, den Sie anfügen möchten.

   - Geben Sie den Namen oder den ersten Buchstaben im Feld **Filter Prozesse** ein, um schnell einen Prozess auszuwählen.

   - Wenn Sie den Prozessnamen nicht kennen, Durchsuchen Sie die Liste, oder sehen Sie sich [häufige Debugszenarien](#BKMK_Scenarios) für einige gängige Prozessnamen an.

   - Aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** , um Prozesse zu suchen, die unter allen Benutzerkonten ausgeführt werden.

     >[!NOTE]
     >Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Die **Automatische** Standardeinstellung funktioniert für die meisten App-Typen.

   So wählen Sie Codetypen manuell aus:
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** die Option **Diese Codetypen debuggen**aus.
   1. Wählen Sie die zu debuggenden Codetypen aus.
   1. Klicken Sie auf **OK**.

6. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können mehrere Apps zum Debuggen anfügen, es ist jedoch jeweils nur eine APP im Debugger aktiv. Sie können die aktive app in der Visual Studio-Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen.

In einigen Fällen werden beim Debuggen in einer Remotedesktop Sitzung (Terminal Dienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer mit eingeschränktem Benutzerkonto ausführen, werden in der Liste **Verfügbare Prozesse** keine Prozesse angezeigt, die in Sitzung 0 ausgeführt werden. Sitzung 0 wird für Dienste und andere Server Prozesse einschließlich *w3wp. exe*verwendet. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen.

Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p <ProcessId>` in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit *tlist. exe*ermittelt werden. Laden Sie die Debugtools für Windows unter [WDK and WinDbg downloads (Herunterladen von WDK und WinDbg)](/windows-hardware/drivers/download-the-wdk) herunter, um *tlist.exe* abzurufen.

::: moniker range=">= vs-2019"

## <a name="BKMK_Docker_Attach"></a>Anfügen an einen Prozess, der in einem Linux docker-Container ausgeführt wird

Sie können den Visual Studio-Debugger an einen Prozess anfügen, der in einem Linux .net Core docker-Container auf Ihrem lokalen oder Remote Computer ausgeführt wird. verwenden Sie dazu das Dialogfeld **an den Prozess anhängen** .

> [!IMPORTANT]
> Um dieses Feature verwenden zu können, müssen Sie die Arbeitsauslastung für die plattformübergreifende .net Core-Entwicklung installieren und über lokalen Zugriff auf den Quellcode verfügen.

**So fügen Sie an einen laufenden Prozess in einem Linux docker-Container an:**

1. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen (STRG + ALT + P)** aus, um das Dialogfeld **an den Prozess anhängen** zu öffnen.

![Menü "an den Prozess anhängen"](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Legen Sie den **Verbindungstyp** auf **docker (Linux-Container)** fest.
3. Wählen Sie **suchen...** aus, um das **Verbindungs Ziel** über das Dialogfeld **docker-Container auswählen** festzulegen.

    Sie können einen docker-Container Prozess entweder lokal oder Remote Debuggen.
    
    **So debuggen Sie einen docker-Container Prozess lokal:**
    1. Legen Sie den **docker-CLI-Host** auf **lokaler Computer**fest.
    1. Wählen Sie einen ausgesuchten Container aus der Liste aus, und klicken Sie auf **OK**.
    
    ![Menü "docker-Container auswählen"](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. so Debuggen Sie einen docker-Container Prozess Remote:**
    
    > [!NOTE] 
    > Es gibt zwei Möglichkeiten, eine Remote Verbindung mit einem laufenden Prozess in einem docker-Container herzustellen. Wenn Sie nicht über docker-Tools auf dem lokalen Computer installiert sind, ist die erste Option zum Verwenden von SSH ideal.  Wenn Sie docker-Tools lokal installiert haben und über einen docker-Daemon verfügen, der für die Annahme von Remote Anforderungen konfiguriert ist, verwenden Sie die zweite Option mithilfe eines docker-Daemons.

    1. ***So stellen Sie über ssh eine Verbindung mit einem Remote Computer her:***
        1. Wählen Sie **Hinzufügen** aus, um eine Verbindung mit einem Remote System herzustellen.<br/>
        ![Herstellen einer Verbindung mit einem Remote System](../debugger/media/connect-remote-system.png "Herstellen einer Verbindung mit einem Remote System")
        1. Wählen Sie einen ausgesuchten Container aus, den Sie nach dem erfolgreichen Herstellen einer Verbindung mit dem SSH oder dem Daemon anfügen **möchten.**

    
    1. ***So legen Sie das Ziel auf einen Remote Container fest, der einen Prozess über einen [docker-Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) führt***
        1. Geben Sie die daemonadresse (z. b. über TCP, IP usw.) unter **docker-Host (optional)** an, und klicken Sie auf den Link aktualisieren.
        1. Wählen Sie einen ausgesuchten Container aus, an den Sie nach dem erfolgreichen herstellender Verbindung mit dem Daemon anfügen möchten

4. Wählen Sie den entsprechenden Container Prozess in der Liste der **verfügbaren Prozesse** aus, und wählen Sie C# **Anfügen** aus, um das Debuggen Ihres Container Prozesses in Visual Studio

    ![Vollständiges docker-Anfüge Menü](../debugger/media/docker-attach-complete.png "Vollständiges docker-Anfüge Menü")


::: moniker-end

## <a name="BKMK_reattach"></a>Erneut an einen Prozess anfügen

Sie können schnell erneut an Prozesse anfügen, an die Sie zuvor angefügt waren, indem Sie **Debuggen** > **erneut an den Prozess anfügen** auswählen (**UMSCHALT**+**alt**+**P**). Wenn Sie diesen Befehl auswählen, versucht der Debugger sofort, an die letzten Prozesse anzufügen, an die Sie angefügt haben, indem er zuerst versucht, die vorherige Prozess-ID abzugleichen, wenn dies fehlschlägt, indem er mit dem vorherigen Prozessnamen übereinstimmt. Wenn keine Übereinstimmungen gefunden werden oder mehrere Prozesse denselben Namen aufweisen, wird das Dialogfeld **an den Prozess anhängen** geöffnet, sodass Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Der Befehl **erneut an den Prozess anhängen** ist ab Visual Studio 2017 verfügbar.

## <a name="BKMK_Scenarios"></a>Gängige Debugszenarien

In der folgenden Tabelle finden Sie einige gängige Debuggingszenarios mit Links zu weiteren Anweisungen, sofern verfügbar, um Ihnen zu helfen, zu bestimmen, ob " **an den Prozess anhängen** " und an welchem Prozess angehängt werden soll. (Die Liste ist nicht vollständig.)

Für einige APP-Typen, wie universelle Windows app-apps (UWP), werden Sie nicht direkt an einen Prozessnamen angefügt, sondern die Menüoption " **installiertes App-Paket Debuggen** " in Visual Studio (siehe Tabelle).

Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

Beim Client seitigen Skript Debuggen muss das Skript Debugging im Browser aktiviert werden. Zum Debuggen des Client seitigen Skripts in Chrome wählen Sie **Web Kit** als Codetyp aus. je nach App-Typ müssen Sie möglicherweise alle Chrome-Instanzen schließen und den Browser im Debugmodus starten (geben Sie `chrome.exe --remote-debugging-port=9222` über die Befehlszeile ein).

Wenn Sie schnell einen laufenden Prozess auswählen möchten, der angefügt werden soll, geben Sie in Visual Studio **STRG**+**alt**+**P**ein, und geben Sie dann den ersten Buchstaben des Prozess namens ein.

|Szenario|Debug-Methode|Prozessname|Hinweise und Links|
|-|-|-|-|
|Remote Debuggen ASP.NET 4 oder 4,5 auf einem IIS-Server|Remote Tools verwenden und **an den Prozess anhängen**|*w3wp.exe*|Weitere Informationen finden Sie [unter Remote Debugging ASP.net auf einem Remote Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote Debuggen ASP.net Core auf einem IIS-Server|Remote Tools verwenden und **an den Prozess anhängen**|*dotnet.exe*|Informationen zur Bereitstellung von apps finden [Sie unter Veröffentlichen in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Informationen zum Debuggen finden Sie [unter Remote Debugging ASP.net Core auf einem IIS-Remote Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) .|
|Debuggen des Client seitigen Skripts auf einem lokalen IIS-Server für unterstützte App-Typen |" **An den Prozess anhängen** " verwenden|*chrome.exe*, *MicrosoftEdgeCP.exe* oder *iexplore.exe*|Skript Debugging muss aktiviert sein. Für Chrome müssen Sie auch Chrome im Debugmodus ausführen und im Feld **Anfügen an** den **WebKit-Code** auswählen.|
|Debuggen einer C#-, C++ Visual Basic-oder-App auf dem lokalen Computer|Standard Debuggen (**F5**) oder **an Prozess anhängen** verwenden|*\<appname>.exe*|Verwenden Sie in den meisten Szenarien standardmäßige Debuggen und nicht **an den Prozess anhängen**.|
|Remote Debuggen einer Windows-Desktop-App|Remotetools|Nicht zutreffend| [Remote Debuggen C# einer](../debugger/remote-debugging-csharp.md) [ C++ App](../debugger/remote-debugging-cpp.md) oder einer Visual Basic-App|
|Debuggen einer ASP.net-App auf dem lokalen Computer, nachdem Sie die APP ohne den Debugger gestartet haben|" **An den Prozess anhängen** " verwenden|*iiexpress.exe*|Dies kann hilfreich sein, damit die APP schneller geladen wird, z. b. bei der Profilerstellung (z. b.). |
|Andere unterstützte App-Typen auf einem Server Prozess Debuggen|Wenn der Server Remote ist, Remote Tools verwenden und **an den Prozess anhängen**|*Chrome. exe*, *iexplore. exe*oder andere Prozesse|Verwenden Sie bei Bedarf Ressourcenmonitor, um den Prozess zu identifizieren. Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](../debugger/remote-debugging.md).|
|Remote Debuggen einer universellen Windows-app (UWP), onecore, hololens oder IOT-App|Installiertes App-Paket debuggen|Nicht zutreffend|Siehe [Debuggen eines installierten App-Pakets](debug-installed-app-package.md) anstelle von " **an den Prozess anhängen** "|
|Debuggen Sie eine universelle Windows-app (UWP), onecore, hololens oder IOT-APP, die Sie nicht von Visual Studio aus gestartet haben.|Installiertes App-Paket debuggen|Nicht zutreffend|Siehe [Debuggen eines installierten App-Pakets](debug-installed-app-package.md) anstelle von " **an den Prozess anhängen** "|

## <a name="use-debugger-features"></a>Verwenden von Debugger-Funktionen

Um die vollständigen Funktionen des Visual Studio-Debuggers (z. b. beim erreichen von Haltepunkten) beim Anfügen an einen Prozess zu verwenden, muss die APP genau mit der lokalen Quelle und den Symbolen übereinstimmen Das heißt, der Debugger muss in der Lage sein, die richtigen [Symbol Dateien (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)zu laden. Standardmäßig ist hierfür ein Debugbuild erforderlich.

Für remotedebuggingszenarien muss der Quellcode (oder eine Kopie des Quellcodes) bereits in Visual Studio geöffnet sein. Die kompilierten App-Binärdateien auf dem Remote Computer müssen vom gleichen Build wie auf dem lokalen Computer stammen.

In einigen lokalen debuggingszenarien können Sie in Visual Studio ohne Zugriff auf die Quelle Debuggen, wenn die richtigen Symbol Dateien mit der app vorhanden sind. Standardmäßig ist hierfür ein Debugbuild erforderlich. Weitere Informationen finden Sie unter [Angeben von Symbol-und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.

 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.

 Wenn der Debugger an einige, aber nicht an alle Codetypen angefügt werden kann, wird eine Meldung angezeigt, die angibt, welche Typen nicht angefügt werden konnten.

 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Der nicht angefügte Code im Prozess wird zwar weiterhin ausgeführt, aber Sie können keine Haltepunkte festlegen, Daten anzeigen oder andere debuggingvorgänge für diesen Code ausführen.

 Wenn Sie spezifischere Informationen darüber wünschen, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, an diesen Codetyp anzufügen.

 **So erhalten Sie Informationen darüber, warum ein bestimmter Codetyp nicht angehängt werden konnte:**

1. Trennen Sie den Prozess. Wählen Sie im Menü **Debuggen** die Option **Alle trennen**aus.

1. Fügen Sie den Prozess erneut an, und wählen Sie nur den Codetyp aus, der nicht angefügt werden konnte.

    1. Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.

    2. Wählen Sie **Auswählen** aus.

    3. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Deaktivieren Sie die anderen Codetypen.

    4. Klicken Sie auf **OK**.

    5. Klicken Sie im Dialogfeld **an den Prozess anhängen** auf **Anfügen**.

    Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.

## <a name="see-also"></a>Siehe auch

- [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)
- [Just-In-Time debugging (Just-In-Time-Debuggen)](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Remotedebuggen](../debugger/remote-debugging.md)
