---
title: Anlaufende Prozesse mit dem Debugger | Microsoft Docs
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
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233026"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wurde, wählen Sie > **Debug-Anschleifen an Prozess** aus, oder drücken Sie **Strg**+**Alt**+**P** in Visual Studio, und verwenden Sie das Dialogfeld **An Prozess anfügen,** um den Debugger an den Prozess anzuhängen. **Debug**

Sie können **An Prozess anfügen** verwenden, um ausgeführte Apps auf lokalen oder Remotecomputern zu debuggen, mehrere Prozesse gleichzeitig zu debuggen, Apps zu debuggen, die nicht in Visual Studio erstellt wurden, oder eine App zu debuggen, die Sie nicht von Visual Studio gestartet haben, wobei der Debugger angefügt ist. Wenn Sie beispielsweise eine App ohne den Debugger ausführen und eine Ausnahme treffen, können Sie den Debugger an den Prozess anfügen, der die App ausführt, und mit dem Debuggen beginnen.

> [!TIP]
> Sie sind sich nicht sicher, ob **Sie Attach to Process** für Ihr Debugszenario verwenden sollen? Siehe [Allgemeine Debugging-Szenarien](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>An einen laufenden Prozess auf Ihrem lokalen Computer anfügen

Informationen zum schnellen erneuten Anfügen an einen Prozess, dem Sie zuvor zugeordnet waren, finden Sie unter [Erneutes Anfügen an einen Prozess](#BKMK_reattach).

Informationen zum Debuggen eines Prozesses auf einem Remotecomputer finden Sie unter [Anfügen an einen Prozess auf einem Remotecomputer](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Informationen zum Debuggen eines .NET Core-Prozesses in einem Linux Docker-Container finden Sie unter [Anfügen an einen Linux Docker-Container](#BKMK_Linux_Docker_Attach).
::: moniker-end

**So schließen Sie einen Vorgang auf Ihrem lokalen Computer an:**

1. Wählen Sie in Visual Studio **Debuggen** > **an Prozess** anfügen (oder drücken Sie **Strg**+**Alt**+**P**), um das Dialogfeld An Prozess **anfügen zu** öffnen.

   **Der Verbindungstyp** sollte auf **Standard**festgelegt werden. **Das Verbindungsziel** sollte Ihr lokaler Computername sein.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, denen Bzw. Die Prozesse anfügen sollen.

   - Um einen Prozess schnell auszuwählen, geben Sie den Namen oder den ersten Buchstaben in das Feld **Prozesse filtern** ein.

   - Wenn Sie den Prozessnamen nicht kennen, durchsuchen Sie die Liste, oder sehen Sie [allgemeine Debugszenarios](#BKMK_Scenarios) für einige allgemeine Prozessnamen.

   >[!TIP]
   >Prozesse können im Hintergrund gestartet und beendet werden, während das Dialogfeld **An Prozess anfügen** geöffnet ist, sodass die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

3. Stellen Sie im Feld **Anfügen** an sicher, dass der Codetyp aufgeführt ist, den Sie debuggen möchten. Die Standardeinstellung **Automatisch** funktioniert für die meisten App-Typen.

   So wählen Sie Codetypen manuell aus:
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** diese **Codetypen debuggen**aus.
   1. Wählen Sie die Codetypen aus, die Sie debuggen möchten.
   1. Wählen Sie **OK** aus.

4. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können zum Debuggen an mehrere Apps angefügt werden, aber jeweils ist nur eine App im Debugger aktiv. Sie können die aktive App in der Visual Studio **Debug-Positionssymbolleiste** oder im Fenster **Prozesse** festlegen.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer

Sie können auch einen Remotecomputer im Dialogfeld **An Prozess anfügen** auswählen, eine Liste der verfügbaren Prozesse anzeigen, die auf diesem Computer ausgeführt werden, und an einen oder mehrere Prozesse zum Debuggen anfügen. Der Remotedebugger (*msvsmon.exe*) muss auf dem Remotecomputer ausgeführt werden. Weitere Informationen finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).

Weitere vollständige Anweisungen zum Debuggen ASP.NET Anwendungen, die auf IIS bereitgestellt wurden, finden Sie unter [Remotedebugging ASP.NET auf einem Remote-IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**So schließen Sie einen Vorgang an, der auf einem Remotecomputer ausgeführt wird:**

1. Wählen Sie in Visual Studio **Debuggen** > **an Prozess** anfügen (oder drücken Sie **Strg**+**Alt**+**P**), um das Dialogfeld An Prozess **anfügen zu** öffnen.

2. **Der Verbindungstyp** sollte in den meisten Fällen **Standard** sein. Wählen Sie im **Feld Verbindungsziel** den Remotecomputer mit einer der folgenden Methoden aus:

   - Wählen Sie den Dropdown-Pfeil neben **Verbindungsziel**aus, und wählen Sie den Computernamen aus der Dropdownliste aus.
   - Geben Sie den Computernamen in das Feld **Verbindungsziel** ein, und drücken **Sie die Eingabetaste**.

     Stellen Sie sicher, dass Visual Studio dem Computernamen den erforderlichen Port hinzufügt, der im Format angezeigt wird: ** \<Remotecomputername>:Port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Wenn Sie keine Verbindung mit dem Namen des Remotecomputers herstellen können, `123.45.678.9:4022`verwenden Sie die IP- und Portadresse (z. B. ). 4024 ist der Standardport für den Visual Studio 2019 x64 Remote-Debugger. Weitere Zuweisungen von Remote-Debugger-Ports finden Sie unter [Remote-Debuggerportzuweisungen](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Wenn Sie keine Verbindung mit dem Namen des Remotecomputers herstellen können, `123.45.678.9:4022`verwenden Sie die IP- und Portadresse (z. B. ). 4022 ist der Standardport für den Visual Studio 2017 x64-Remotedebugger. Weitere Zuweisungen von Remote-Debugger-Ports finden Sie unter [Remote-Debuggerportzuweisungen](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Wählen Sie die Schaltfläche **Suchen** neben dem Feld **Verbindungsziel** aus, um das Dialogfeld **Remoteverbindungen** zu öffnen. Im Dialogfeld **Remoteverbindungen** werden alle Geräte aufgelistet, die sich in Ihrem lokalen Subnetz befinden oder direkt an Ihren Computer angeschlossen sind. Möglicherweise müssen Sie [udP-Port 3702](../debugger/remote-debugger-port-assignments.md) auf dem Server öffnen, um Remotegeräte zu ermitteln. Wählen Sie den gewünschten Computer oder das gewünschte Gerät aus, und klicken Sie dann auf **Auswählen**.

   > [!NOTE]
   > Die **Einstellung Verbindungstyp** bleibt zwischen Debugsitzungen bestehen. Die **Verbindungszieleinstellung** bleibt zwischen Debugsitzungen nur bestehen, wenn eine erfolgreiche Debugverbindung mit diesem Ziel aufgetreten ist.

3. Klicken Sie auf **Aktualisieren,** um die Liste **Verfügbare Prozesse** aufzufüllen.

    >[!TIP]
    >Prozesse können im Hintergrund gestartet und beendet werden, während das Dialogfeld **An Prozess anfügen** geöffnet ist, sodass die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuell ist. Sie können jederzeit **Aktualisieren** auswählen, um die aktuelle Liste anzuzeigen.

4. Suchen und wählen Sie in der Liste **Verfügbare Prozesse** den Prozess oder die Prozesse aus, denen Bzw. Die Prozesse anfügen sollen.

   - Um einen Prozess schnell auszuwählen, geben Sie den Namen oder den ersten Buchstaben in das Feld **Prozesse filtern** ein.

   - Wenn Sie den Prozessnamen nicht kennen, durchsuchen Sie die Liste, oder sehen Sie [allgemeine Debugszenarios](#BKMK_Scenarios) für einige allgemeine Prozessnamen.

   - Um Prozesse zu suchen, die unter allen Benutzerkonten ausgeführt werden, aktivieren Sie das Kontrollkästchen **Prozesse von allen Benutzern anzeigen.**

     >[!NOTE]
     >Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Stellen Sie im Feld **Anfügen** an sicher, dass der Codetyp aufgeführt ist, den Sie debuggen möchten. Die Standardeinstellung **Automatisch** funktioniert für die meisten App-Typen.

   So wählen Sie Codetypen manuell aus:
   1. Klicken Sie auf **Auswählen**.
   1. Wählen Sie im Dialogfeld **Codetyp auswählen** diese **Codetypen debuggen**aus.
   1. Wählen Sie die Codetypen aus, die Sie debuggen möchten.
   1. Wählen Sie **OK** aus.

6. Wählen Sie **Anfügen** aus.

>[!NOTE]
>Sie können zum Debuggen an mehrere Apps angefügt werden, aber jeweils ist nur eine App im Debugger aktiv. Sie können die aktive App in der Visual Studio **Debug-Positionssymbolleiste** oder im Fenster **Prozesse** festlegen.

In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) nicht alle verfügbaren Prozesse in der Liste **Verfügbare Prozesse** angezeigt. Wenn Sie Visual Studio als Benutzer mit einem eingeschränkten Benutzerkonto ausführen, werden in der Liste **Verfügbare Prozesse** keine Prozesse angezeigt, die in Sitzung 0 ausgeführt werden. Sitzung 0 wird für Dienste und andere Serverprozesse verwendet, einschließlich *w3wp.exe*. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen.

Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p <ProcessId>` in der Windows-Befehlszeile ausführen. Sie können die Prozess-ID mit *tlist.exe*bestimmen. Laden Sie die Debugtools für Windows unter [WDK and WinDbg downloads (Herunterladen von WDK und WinDbg)](/windows-hardware/drivers/download-the-wdk) herunter, um *tlist.exe* abzurufen.

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>An einen .NET Core-Prozess anfügen, der unter Linux mit SSH ausgeführt wird

Weitere Informationen finden Sie unter [Remote-Debug -.NET-Kern](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)unter Linux mit SSH .

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>An einen Prozess anfügen, der auf einem Linux Docker-Container ausgeführt wird

Sie können den Visual Studio-Debugger mithilfe des Dialogfelds **An prozessanfügen** an einen Prozess anfügen, der in einem Linux .NET Core Docker-Container auf Ihrem lokalen oder Remotecomputer ausgeführt wird.

> [!IMPORTANT]
> Um diese Funktion verwenden zu können, müssen Sie die .NET Core Cross-Platform Development-Workload installieren und über lokalen Zugriff auf den Quellcode verfügen.

**So fügen Sie einen laufenden Prozess in einem Linux Docker-Container an:**

1. Wählen Sie in Visual Studio **> An Prozess anfügen (CTRL+ALT+P),** um das Dialogfeld **An Prozess anfügen** zu öffnen.

![An das Prozessmenü anfügen](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Legen Sie den **Verbindungstyp** auf **Docker (Linux Container)** fest.
3. Wählen Sie **Suchen...,** um das **Verbindungsziel** über das Dialogfeld **Docker Container auswählen** festzulegen.

    Sie können einen Docker-Containerprozess entweder lokal oder remote debuggen.
    
    **So debuggen Sie einen Docker-Containerprozess lokal:**
    1. Legen Sie **docker CLI-Host** auf **Lokalen Computer**fest.
    1. Wählen Sie einen laufenden Container aus, an den Sie aus der Liste anfügen möchten, und klicken Sie auf **OK**.
    
    ![Docker Container Menü auswählen](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. So debuggen Sie einen Docker-Containerprozess remote:**
    
    > [!NOTE] 
    > Es gibt zwei Optionen für die Remoteverbindung mit einem laufenden Prozess in einem Docker-Container. Die erste Option zur Verwendung von SSH ist ideal, wenn Docker-Tools nicht auf Ihrem lokalen Computer installiert sind.  Wenn Docker-Tools lokal installiert sind und sie einen Docker-Daemon haben, der für die Annahme von Remoteanforderungen konfiguriert ist, versuchen Sie die zweite Option mit einem Docker-Daemon.

    1. ***So verbinden Sie sich über SSH mit einem Remote-Rechner:***
        1. Wählen Sie **Hinzufügen...,** um eine Verbindung mit einem Remotesystem herzustellen.<br/>
        ![Herstellen einer Verbindung mit einem Remotesystem](../debugger/media/connect-remote-system.png "Herstellen einer Verbindung mit einem Remotesystem")
        1. Wählen Sie einen laufenden Container aus, an den Sie nach dem erfolgreichen Herstellen einer Verbindung mit dem SSH oder Daemon anfügen möchten, und klicken Sie auf **OK**.

    
    1. ***So legen Sie das Ziel auf einen Remotecontainer fest, der einen Prozess über einen [Docker-Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) ausführt***
        1. Geben Sie die Daemon-Adresse (d. h. über TCP, IP usw.) unter **Docker-Host (Optional)** an und klicken Sie auf den Aktualisierungslink.
        1. Wählen Sie einen laufenden Container aus, an den Sie nach dem erfolgreichen Herstellen einer Verbindung mit dem Daemon anfügen möchten, und klicken Sie auf **OK**.

4. Wählen Sie den entsprechenden Containerprozess aus der Liste der **verfügbaren Prozesse** aus, und wählen Sie **Anfügen** aus, um mit dem Debuggen des C-Containerprozesses in Visual Studio zu beginnen!

    ![Abgeschlossenes Docker-Anfügen-Menü](../debugger/media/docker-attach-complete.png "Abgeschlossenes Linux Docker Attach Menü")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>An einen Prozess anfügen, der in einem Windows Docker-Container ausgeführt wird

Sie können den Visual Studio-Debugger mithilfe des Dialogfelds An **prozessanfügen** an einen Prozess anfügen, der in einem Windows Docker-Container auf dem lokalen Computer ausgeführt wird.

> [!IMPORTANT]
> Um diese Funktion für einen .NET Core-Prozess verwenden zu können, müssen Sie die .NET Core Cross-Platform Development-Workload installieren und über lokalen Zugriff auf den Quellcode verfügen.

**So fügen Sie einen laufenden Prozess in einem Windows Docker-Container an:**

1. Wählen Sie in Visual Studio **> an Prozess anfügen** (oder **STRG+ALT+P**), um das Dialogfeld **An Prozess anfügen** zu öffnen.

   ![An das Prozessmenü anfügen](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Legen Sie den **Verbindungstyp** auf **Docker (Windows Container)** fest.
3. Wählen Sie **Suchen...,** um das **Verbindungsziel** mithilfe des Dialogfelds **Docker Container auswählen** festzulegen.

    > [!IMPORTANT]
    > Der Zielprozess muss über dieselbe Prozessorarchitektur wie der Docker Windows-Container verfügen, auf dem er ausgeführt wird.
    
   Das Festlegen des Ziels auf einen Remotecontainer über SSH ist derzeit nicht verfügbar und kann nur mit einem Docker-Daemon durchgeführt werden.
    
    ***So legen Sie das Ziel auf einen Remotecontainer fest, der einen Prozess über einen [Docker-Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) ausführt***
    1. Geben Sie die Daemon-Adresse (d. h. über TCP, IP usw.) unter **Docker-Host (Optional)** an und klicken Sie auf den Aktualisierungslink. 

    1. Wählen Sie einen laufenden Container aus, an den Sie nach dem erfolgreichen Herstellen einer Verbindung mit dem Daemon anfügen möchten, und wählen Sie OK aus.
    
4. Wählen Sie den entsprechenden Containerprozess aus der Liste der **verfügbaren Prozesse** aus, und wählen Sie **Anfügen** aus, um mit dem Debuggen des C-Containerprozesses zu beginnen.

    ![Abgeschlossenes Docker-Anfügen-Menü](../debugger/media/docker-attach-complete-windows.png "Abgeschlossenes Windows Docker-Anfügen-Menü")
    

5.  Wählen Sie den entsprechenden Containerprozess aus der Liste der verfügbaren Prozesse aus, und wählen Sie **Anfügen** aus, um mit dem Debuggen des C-Containerprozesses zu beginnen.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Erneutes Anfügen an einen Prozess

Sie können Prozesse, denen Sie zuvor angefügt wurden, schnell wieder anfügen, indem Sie **Debug** > **Reattach to Process** (**Shift**+**Alt**+**P**) auswählen. Wenn Sie diesen Befehl auswählen, versucht der Debugger sofort, die letzten Prozesse anzufügen, die Sie angefügt haben, indem er zuerst versucht, die vorherige Prozess-ID abzugleichen, und wenn dies fehlschlägt, indem er mit dem vorherigen Prozessnamen übereinstimmt. Wenn keine Übereinstimmungen gefunden werden oder mehrere Prozesse denselben Namen haben, wird das Dialogfeld **An Prozess anfügen** geöffnet, sodass Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Der Befehl **"An Prozess anfügen"** ist ab Visual Studio 2017 verfügbar.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Häufige Debugging-Szenarien

In der folgenden Tabelle finden Sie einige gängige Debugszenarios mit Links zu weiteren Anweisungen, sofern verfügbar, um zu bestimmen, ob **An Den Prozess angefügt** werden soll. (Die Liste ist nicht erschöpfend.)

Bei einigen App-Typen, z. B. UWP-Apps (Universelle Windows-App), werden Sie nicht direkt an einen Prozessnamen angefügt, sondern verwenden stattdessen die Menüoption **"Installiertes App-Paket debuggen"** in Visual Studio (siehe Tabelle).

Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

Für das clientseitige Skriptdebuggen muss das Skriptdebuggen im Browser aktiviert sein. Wählen Sie zum Debuggen von clientseitigem Skript in Chrome **Webkit** als Codetyp aus, und je nach App-Typ müssen `chrome.exe --remote-debugging-port=9222` Sie möglicherweise alle Chrome-Instanzen schließen und den Browser im Debugmodus starten (geben Sie über eine Befehlszeile ein).

Um schnell einen laufenden Prozess auszuwählen, an den sie angefügt werden soll, geben Sie in Visual Studio **Strg**+**Alt**+**P**ein, und geben Sie dann den ersten Buchstaben des Prozessnamens ein.

|Szenario|Debug-Methode|Prozessname|Hinweise und Links|
|-|-|-|-|
|Remote-Debug-ASP.NET 4 oder 4.5 auf einem IIS-Server|Verwenden von Remote-Tools und **Anfügen an den Prozess**|*w3wp.exe*|Siehe [Remote-Debugging ASP.NET auf einem Remote-IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote-Debug-ASP.NET Core auf einem IIS-Server|Verwenden von Remote-Tools und **Anfügen an den Prozess**|*dotnet.exe* oder *appname.exe*|Informationen zur App-Bereitstellung finden Sie unter [Veröffentlichen in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Informationen zum Debuggen finden Sie unter [Remotedebugging ASP.NET Core auf einem Remote-IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debugen von clientseitigem Skript auf einem lokalen IIS-Server für unterstützte App-Typen |Verwenden **von Anfügen an den Prozess**|*chrome.exe*, *MicrosoftEdgeCP.exe* oder *iexplore.exe*|Das Skriptdebuggen muss aktiviert sein. Für Chrome müssen Sie Chrome auch im Debugmodus ausführen und **Webkit-Code** im Feld **Anfügen** auswählen.|
|Debuggen einer C-, Visual Basic- oder C++-App auf dem lokalen Computer|Verwenden Sie entweder Standard-Debugging (**F5**) oder **An Prozess anfügen**|*\<Appname>.exe*|Verwenden Sie in den meisten Szenarien das Standarddebugging und nicht **das Anfügen an den Prozess**.|
|Remotedebug einer Windows-Desktop-App|Remotetools|–| Siehe [Remote-Debug-Debug-A- oder Visual Basic-App](../debugger/remote-debugging-csharp.md) oder [Remote-Debugeiner einer C++-App](../debugger/remote-debugging-cpp.md)|
|Debuggen von .NET Core unter Linux|Verwenden **von Anfügen an den Prozess**|*dotnet.exe*|Informationen zur Verwendung von SSH finden Sie unter [Remote-Debug -.NET-Kern, das unter Linux mit SSH ausgeführt wird.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) |
|Debuggen einer ASP.NET-App auf dem lokalen Computer, nachdem Sie die App ohne debugger gestartet haben|Verwenden **von Anfügen an den Prozess**|*iiexpress.exe*|Dies kann hilfreich sein, um das Laden Ihrer App zu beschleunigen, z. B. bei der Profilerstellung. |
|Debuggen anderer unterstützter App-Typen auf einem Serverprozess|Wenn der Server remote ist, verwenden Sie Remote-Tools, und **an den Prozess anfügen**|*chrome.exe*, *iexplore.exe*oder andere Prozesse|Verwenden Sie ggf. Resource Monitor, um den Prozess zu identifizieren. Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](../debugger/remote-debugging.md).|
|Remote-Debug-Debug-App (UWP), OneCore, HoloLens oder IoT-App|Installiertes App-Paket debuggen|–|Siehe [Debuggen eines installierten App-Pakets](debug-installed-app-package.md) anstelle von **Anfügen an den Prozess**|
|Debuggen einer universellen Windows-App (UWP), OneCore, HoloLens oder IoT-App, die Sie nicht von Visual Studio gestartet haben|Installiertes App-Paket debuggen|–|Siehe [Debuggen eines installierten App-Pakets](debug-installed-app-package.md) anstelle von **Anfügen an den Prozess**|

## <a name="use-debugger-features"></a>Debugger-Features verwenden

Um beim Anfügen an einen Prozess die vollständigen Funktionen des Visual Studio-Debuggers (z. B. das Anfügen von Haltepunkten) zu verwenden, muss die App genau mit der lokalen Quelle und den Symbolen übereinstimmen. Das heißt, der Debugger muss in der Lage sein, die richtigen [Symboldateien (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)zu laden. Standardmäßig ist dafür ein Debugbuild erforderlich.

Für Remote-Debugging-Szenarien muss der Quellcode (oder eine Kopie des Quellcodes) bereits in Visual Studio geöffnet sein. Die kompilierten App-Binärdateien auf dem Remotecomputer müssen aus demselben Build wie auf dem lokalen Computer stammen.

In einigen lokalen Debugszenarios können Sie in Visual Studio ohne Zugriff auf die Quelle debuggen, wenn die richtigen Symboldateien in der App vorhanden sind. Standardmäßig ist dafür ein Debugbuild erforderlich. Weitere Informationen finden Sie unter [Symbol- und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.

 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.

 Wenn der Debugger in der Lage ist, Codetypen an einige, aber nicht an alle Codetypen anzufügen, wird eine Meldung angezeigt, die identifiziert, welche Typen nicht angefügt werden konnten.

 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Der nicht angefügte Code im Prozess wird weiterhin ausgeführt, aber Sie können keine Haltepunkte festlegen, Daten anzeigen oder andere Debugvorgänge für diesen Code ausführen.

 Wenn Sie genauere Informationen darüber erhalten möchten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie, nur diesem Codetyp erneut das Anfügen zuzufügen.

 **So erhalten Sie Informationen darüber, warum ein bestimmter Codetyp nicht angehängt werden konnte:**

1. Trennen Sie den Prozess. Wählen Sie im **Menü Debuggen** **alle trennen**aus.

1. Fügen Sie den Vorgang erneut an, und wählen Sie nur den Codetyp aus, der nicht angefügt werden konnte.

    1. Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.

    2. Wählen Sie **Auswählen**aus .

    3. Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Deaktivieren Sie die anderen Codetypen.

    4. Wählen Sie **OK** aus.

    5. Wählen Sie im Dialogfeld **An Prozess anfügen** die Option **Anfügen**aus.

    Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.

## <a name="see-also"></a>Siehe auch

- [Debug multiple processes (Debuggen mehrerer Prozesse)](../debugger/debug-multiple-processes.md)
- [Just-In-Time-Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Remote-Debugging](../debugger/remote-debugging.md)
