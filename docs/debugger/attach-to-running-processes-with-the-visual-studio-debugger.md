---
title: Anfügen an laufende Prozesse mit dem Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 09/27/2018
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d2609c76c39924794e2a9623e9e70c037c20415
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "53899612"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wird, wählen Sie **Debuggen** > **an den Prozess anhängen** , oder drücken Sie **STRG**+**Alt** + **P** in Visual Studio, und die Verwendung der **an den Prozess anhängen** Dialogfeld, um den Debugger an den Prozess anzuhängen.

Sie können **an den Prozess anhängen** zum Debuggen von ausgeführten apps auf lokalen Computern oder Remotecomputern gleichzeitig Debuggen mehrerer Prozesse, Debuggen von apps, die in Visual Studio erstellt wurden nicht oder Debuggen eine app, die Sie nicht starten von Visual Studio mit der der Debugger angefügt. Z. B., wenn Sie eine app ohne den Debugger ausführen und einen Ausnahmefehler, können Sie dann fügen Sie den Debugger an den Prozess, der die app ausgeführt wird und mit dem Debuggen beginnen.

Weitere Informationen zu den Grundlagen des Debuggens in Visual Studio, finden Sie unter [ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md).

> [!TIP]
> Nicht sicher, ob verwendet **an den Prozess anhängen** für Ihr Szenario Debuggen? Finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios). 

##  <a name="BKMK_Attach_to_a_running_process"></a> Fügen Sie an einen laufenden Prozess auf dem lokalen Computer an  

Um schnell zu einem Prozess anfügen zuvor anhangsanker, finden Sie unter [Anfügen an einen Prozess](#BKMK_reattach). 

Um einen Prozess auf einem Remotecomputer zu debuggen, finden Sie unter [Anfügen an einen Prozess auf einem Remotecomputer](#BKMK_Attach_to_a_process_on_a_remote_computer).

**So fügen Sie an einen Prozess auf dem lokalen Computer an:**  

1. Wählen Sie in Visual Studio **Debuggen** > **an den Prozess anhängen** (oder drücken Sie **STRG**+**Alt** + **P**) zum Öffnen der **an den Prozess anhängen** Dialogfeld.
  
   **Verbindungstyp** sollte festgelegt werden, um **Standard**. **Verbindungsziel** muss Name des lokalen Computers. 
  
   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
2. In der **verfügbare Prozesse** auflisten, suchen und wählen Sie Prozesse, die Sie anfügen möchten.  

   - Um schnell einen Prozess auswählen, geben Sie den Namen oder die ersten Buchstaben der **Filterprozesse** Feld. 
  
   - Wenn Sie den Namen des Prozesses nicht kennen, Durchsuchen Sie die Liste oder finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen. 
  
   >[!TIP]
   >Prozesse können starten und beenden, die im Hintergrund, während die **an den Prozess anhängen** Dialogfeld geöffnet ist, damit die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuelle. Sie können auswählen, **aktualisieren** jederzeit auf die aktuelle Liste anzuzeigen. 
  
3. In der **Anfügen an** Feld, stellen Sie sicher, dass der Code, die Sie debuggen möchten aufgeführt ist. Der Standardwert **automatische** funktioniert für die meisten app-Typen festlegen. 
  
   Codetypen manuell auswählen:
   1. Klicken Sie auf **Auswählen**. 
   1. In der **Codetyp auswählen** wählen Sie im Dialogfeld **diese Codetypen debuggen**.
   1. Wählen Sie die Codetypen, die Sie debuggen möchten.
   1. Klicken Sie auf **OK**.
  
4. Wählen Sie **Anfügen**.
  
>[!NOTE]
>Sie können mehrere apps für das Debuggen angefügt sein, aber nur eine app im Debugger aktiv ist, zu einem Zeitpunkt. Sie können die aktive app einrichten, in der Visual Studio **Debugspeicherort** Symbolleiste oder **Prozesse** Fenster.  

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anfügen an einen Prozess auf einem Remotecomputer  

Sie können auch auswählen, einem Remotecomputer in die **an den Prozess anhängen** (Dialogfeld), zeigen Sie eine Liste der verfügbaren Prozesse, die auf diesem Computer ausgeführt, und fügen Sie auf eine oder mehrere Prozesse debuggen. Der Remotedebugger (*msvsmon.exe*) muss auf dem Remotecomputer ausgeführt werden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md). 

Vollständige Anweisungen für das Debuggen von ASP.NET-Anwendungen, die auf IIS bereitgestellt wurden, finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**So fügen Sie an einen laufenden Prozess auf einem Remotecomputer an**  

1. Wählen Sie in Visual Studio **Debuggen** > **an den Prozess anhängen** (oder drücken Sie **STRG**+**Alt** + **P**) zum Öffnen der **an den Prozess anhängen** Dialogfeld.
  
2. **Verbindungstyp** muss **Standard** in den meisten Fällen. In der **Verbindungsziel** Wählen der remote-Computer mit einem der folgenden Methoden:

   - Aktivieren Sie den Dropdown-Pfeil neben **Verbindungsziel**, und wählen Sie den Namen des Computers aus der Dropdown Liste.  
   - Geben Sie den Namen in der **Verbindungsziel** Feld.
      
     > [!NOTE]
     > Wenn Sie keine Verbindung mit dem Remotecomputer mit dem Namen herstellen können, versuchen Sie es mit der IP-Adresse und den port der Adresse (z. B. `123.45.678.9:4022`). 4022 ist der Standardport für den Remotedebugger von Visual Studio 2017 X64. Andere Remotedebugger-portzuweisungen finden Sie unter [Remotedebugger – portzuweisungen](remote-debugger-port-assignments.md).  
      
   - Wählen Sie die **finden** neben der **Verbindungsziel** um öffnen die **Remoteverbindungen** Dialogfeld. Die **Remoteverbindungen** Dialogfeld listet alle Geräte, die im lokalen Subnetz oder direkt auf Ihrem Computer verbunden. Sie müssen möglicherweise [Öffnen von UDP-Port 3702](../debugger/remote-debugger-port-assignments.md) auf dem Server um Remotegeräte zu ermitteln. Wählen Sie die Computer oder das gewünschte Medium, und klicken Sie dann auf **wählen**. 
  
   > [!NOTE]
   > Die **Verbindungstyp** Einstellung bleibt zwischen Debugsitzungen erhalten. Die **Verbindungsziel** Einstellung bleibt zwischen Debugsitzungen erhalten nur, wenn eine erfolgreiche Debugverbindung mit diesem Ziel aufgetreten sind.

3. Klicken Sie auf **aktualisieren** zum Auffüllen der **verfügbare Prozesse** Liste.
     
    >[!TIP]
    >Prozesse können starten und beenden, die im Hintergrund, während die **an den Prozess anhängen** Dialogfeld geöffnet ist, damit die Liste der ausgeführten Prozesse möglicherweise nicht immer aktuelle. Sie können auswählen, **aktualisieren** jederzeit auf die aktuelle Liste anzuzeigen. 
     
4. In der **verfügbare Prozesse** auflisten, suchen und wählen Sie Prozesse, die Sie anfügen möchten.  

   - Um schnell einen Prozess auswählen, geben Sie den Namen oder die ersten Buchstaben der **Filterprozesse** Feld. 
  
   - Wenn Sie den Namen des Prozesses nicht kennen, Durchsuchen Sie die Liste oder finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen. 
  
   - Um Prozesse, die unter der alle Benutzerkonten zu suchen, wählen Sie die **Prozesse aller Benutzer anzeigen** Kontrollkästchen.
      
     >[!NOTE]
     >Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
      
5. In der **Anfügen an** Feld, stellen Sie sicher, dass der Code, die Sie debuggen möchten aufgeführt ist. Der Standardwert **automatische** funktioniert für die meisten app-Typen festlegen. 
  
   Codetypen manuell auswählen:
   1. Klicken Sie auf **Auswählen**. 
   1. In der **Codetyp auswählen** wählen Sie im Dialogfeld **diese Codetypen debuggen**.
   1. Wählen Sie die Codetypen, die Sie debuggen möchten.
   1. Klicken Sie auf **OK**.
  
6. Wählen Sie **Anfügen**.
  
>[!NOTE]
>Sie können mehrere apps für das Debuggen angefügt sein, aber nur eine app im Debugger aktiv ist, zu einem Zeitpunkt. Sie können die aktive app einrichten, in der Visual Studio **Debugspeicherort** Symbolleiste oder **Prozesse** Fenster.  

In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der **verfügbare Prozesse** Liste nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, die ein Standardbenutzerkonto, hat die **verfügbare Prozesse** Liste nicht angezeigt Prozesse in Sitzung 0 ausgeführt werden. Sitzung 0 wird verwendet, für Dienste und andere Serverprozesse einschließlich *w3wp.exe*. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. 

Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p <ProcessId>` in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit *tlist.exe* ermittelt werden. Laden Sie die Debugtools für Windows unter [WDK and WinDbg downloads (Herunterladen von WDK und WinDbg)](/windows-hardware/drivers/download-the-wdk) herunter, um *tlist.exe* abzurufen.

## <a name="BKMK_reattach"></a> Anfügen an einen Prozess

Sie können schnell erneut anfügen an Prozesse, die Sie zuvor durch Auswahl angefügt wurden **Debuggen** > **erneut an Prozess anfügen** (**UMSCHALT** + **Alt**+**P**). Wenn Sie diesen Befehl auswählen, verarbeitet der Debugger sofort versucht, mit dem letzten Prozesse anfügen, die Sie angefügt haben, indem er zunächst versucht, mit die vorherigen Prozess-ID übereinstimmen, und wenn dies fehlschlägt, durch den Vergleich mit dem vorherigen, Name. Wenn keine Übereinstimmungen gefunden werden, oder wenn mehrere Prozesse den gleichen Namen haben, die **an den Prozess anhängen** Dialogfeld wird geöffnet, sodass Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Die **erneut an Prozess anfügen** Befehl ist neu in Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Häufige Szenarios des Debuggens

Können Sie die zu ermitteln, ob verwenden **an den Prozess anhängen** und welcher Prozess zu, sofern verfügbar, fügen die folgende Tabelle zeigt einige allgemeine Debuggen Szenarien mit Links auf Weitere Anweisungen. (Die Liste ist nicht vollständig.) 

Für einige app-Typen, wie apps der universellen Windows-App (UWP), Sie nicht direkt mit dem Namen anfügen, aber die **Debuggen Installed App Package** Menü option in Visual Studio (siehe Tabelle).

Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

Für Client-seitige Skript Debuggen muss das Skriptdebugging im Browser aktiviert sein. Wählen Sie für das Debuggen des clientseitigen Skripts in Chrome **Webkit** als den Codetyp aus, und je nach Ihren app-Typ, müssen Sie möglicherweise schließen Sie alle Chrome-Instanzen, und starten den Browser im Debugmodus (Typ `chrome.exe --remote-debugging-port=9222` über die Befehlszeile).

Geben Sie einen laufenden Prozess anfügen, in Visual Studio schnell auf **STRG**+**Alt**+**P**, und geben Sie dann auf den ersten Buchstaben der Name des Prozesses.

|Szenario|Debuggen-Methode|Prozessname|Anmerkungen zu dieser Version und links|
|-|-|-|-|
|Remotedebuggen von ASP.NET 4 oder 4.5 auf einem IIS-server|Remotetools verwenden und **an den Prozess anhängen**|*w3wp.exe*|Finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebuggen von ASP.NET Core auf einem IIS-server|Remotetools verwenden und **an den Prozess anhängen**|*dotnet.exe*|App-Bereitstellung, finden Sie unter [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html). Debuggen, finden Sie unter [Remote debugging ASP.NET Core auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debuggen des clientseitigen Skripts auf einem lokalen IIS-Server, für unterstützte app-Typen |Verwendung **an den Prozess anhängen**|*chrome.exe*, *MicrosoftEdgeCP.exe* oder *iexplore.exe*|Debuggen von Skripts muss aktiviert sein. Chrome, müssen Sie auch Chrome im Debugmodus befindet, und wählen ausführen **Webkit-Code** in die **Anfügen an** Feld.|
|Debuggen einer C#, Visual Basic oder C++-app auf dem lokalen Computer|Verwenden Sie entweder [standard Debuggen](../debugger/debugger-feature-tour.md) oder **an den Prozess anhängen**|*\<appname>.exe*|In den meisten Szenarien verwenden standard Debuggen und nicht **an den Prozess anhängen**.|
|Remotedebuggen einer Windows-desktop-app|Remotetools|Nicht zutreffend| Finden Sie unter [Remotedebuggen einer C# oder Visual Basic-Anwendungen](../debugger/remote-debugging-csharp.md) oder [Remote Debuggen einer C++-app](../debugger/remote-debugging-cpp.md)|
|Debuggen einer ASP.NET-Apps auf dem lokalen Computer aus, nachdem Sie die app ohne den Debugger starten|Verwendung **an den Prozess anhängen**|*iiexpress.exe*|Dies kann hilfreich sein, Ihre App laden schneller, z. B. (z. B.) bei der profilerstellung. |
|Debuggen Sie andere unterstützte app-Typen für einen Serverprozess|Wenn der Server remote verfügbar ist, verwenden Sie die Remoteserver-Verwaltungstools, und **an den Prozess anhängen**|*Chrome.exe*, *iexplore.exe*, oder andere Prozesse|Verwenden Sie bei Bedarf Resource Monitor können Sie den Prozess zu identifizieren. Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](../debugger/remote-debugging.md).|
|Remotedebuggen eine universellen Windows-App (UWP), OneCore, HoloLens und IoT-app|Installiertes App-Paket debuggen|Nicht zutreffend|Finden Sie unter [Debuggen eines installierten app-Pakets](debug-installed-app-package.md) anstelle von **an den Prozess anhängen**|
|Debuggen einer universellen Windows-App (UWP), OneCore, HoloLens und IoT-app, die Sie in Visual Studio starten nicht|Installiertes App-Paket debuggen|Nicht zutreffend|Finden Sie unter [Debuggen eines installierten app-Pakets](debug-installed-app-package.md) anstelle von **an den Prozess anhängen**|  
  
## <a name="use-debugger-features"></a>Verwenden Sie die Debugger-features

Verwenden Sie die vollständigen Funktionen von Visual Studio-Debugger (z. B. Haltepunkte angesteuert) beim Anfügen an einen Prozess die app muss genau der lokalen Quelle und Symbole. D. h. der Debugger muss die richtige laden befinden [Symboldateien (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Standardmäßig ist dies einen Debugbuild erforderlich.

Für remote debugging-Szenarien müssen Sie den Quellcode (oder eine Kopie des Quellcodes) öffnen in Visual Studio bereits verfügen. Die Binärdateien der kompilierten Anwendung auf dem Remotecomputer müssen aus dem gleichen Build wie auf dem lokalen Computer stammen.

In einigen Szenarien für lokalen Debuggen können Sie in Visual Studio ohne Zugriff auf die Quelle Debuggen, wenn die richtige Symbol-Dateien mit der app vorhanden sind. Standardmäßig ist dies einen Debugbuild erforderlich. Weitere Informationen finden Sie unter [angeben von Symbol-und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Beheben von Fehlern beim Anfügen  
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.  
  
 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.  
  
 Wenn der Debugger nur an einige, aber nicht alle Codetypen angefügt ist, sehen Sie eine Nachricht, die identifizieren, welche Fehler beim Anfügen.  
  
 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die nicht angefügte Code in diesem Prozess wird weiterhin ausgeführt, aber Sie sind nicht in der Lage, Haltepunkte festlegen, zeigen Sie Daten oder andere Debugoperationen auf diesen Code auszuführen.  
  
 Wenn spezifischere Informationen, warum der Debugger an einen Codetyp angefügt konnte werden sollen, versuchen Sie, um nur diesen Codetyp erneut anzufügen.  
  
 **So erhalten Sie Informationen darüber, warum ein bestimmter Codetyp nicht angehängt werden konnte:**  
  
1.  Trennen Sie den Prozess. Auf der **Debuggen** , wählen Sie im Menü **alle trennen**.  
  
1.  Anfügen Sie an den Prozess, und wählen nur den Codetyp aus, der nicht angefügt werden konnte.  
  
    1.  Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.  
  
    2.  Wählen Sie **wählen**.  
  
    3.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Deaktivieren Sie die anderen Codetypen aus.  
  
    4.  Klicken Sie auf **OK**.  
  
    5.  In der **an den Prozess anhängen** wählen Sie im Dialogfeld **Anfügen**.  
  
    Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug multiple processes (Debuggen mehrerer Prozesse)](../debugger/debug-multiple-processes.md)   
 [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)
