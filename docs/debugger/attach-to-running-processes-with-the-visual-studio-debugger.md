---
title: Anfügen an laufende Prozesse mit dem Debugger in Visual Studio | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
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
ms.openlocfilehash: 260047497ddb9515505c13f0b861c8eee05d71b0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327332"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wird, klicken Sie auf **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**) zum Öffnen der **an den Prozess anhängen** Dialogfeld.

Sie können diese Funktion verwenden, zum Debuggen von apps, die auf einer lokalen oder Remotecomputer ausgeführt werden, gleichzeitig Debuggen mehrerer Prozesse oder Debuggen einer Anwendung, die nicht in Visual Studio erstellt wurde. Es ist häufig nützlich, wenn Sie eine app debuggen möchten, aber (bei einem beliebigen Grund) wurden Sie nicht die app aus Visual Studio gestartet, mit dem angefügten Debugger. Z. B. Wenn Sie die app ohne den Debugger ausgeführt werden, und drücken eine Ausnahme, können Sie dann an den Prozess Ausführen der app, um das Debuggen zu beginnen anfügen.

> [!TIP]
> Sie wissen nicht genau, ob Sie verwenden müssen **an den Prozess anhängen** für Ihr Szenario Debuggen? Finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios). Wenn Sie möchten zum Debuggen von ASP.NET-Anwendungen, die in IIS bereitgestellt wurden, finden Sie unter [Remote Debugging ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a> Fügen Sie an einen laufenden Prozess auf dem lokalen Computer an  
 Um an einen Prozess anzufügen, müssen Sie den Namen des Prozesses kennen (finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen).
  
1.  Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**).

    Wenn Sie schnell zu einem Prozess stattdessen anfügen möchten, finden Sie unter [erneut an Prozess anfügen](#BKMK_reattach).
  
2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.  

     Um schnell den Prozess auswählen, geben Sie den ersten Buchstaben des Namen des Prozesses ein, oder geben Sie einen Wert in das Feld "Filter", um für einen Prozessnamen zu suchen. Wenn Sie den Namen des Prozesses nicht kennen, finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
  
3.  Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Bei Verwendung der Standardeinstellung **Automatisch** wird versucht, den zu debuggenden Codetyp zu ermitteln. Führen Sie die folgenden Schritte aus, um den Codetyp manuell festzulegen:  
  
    1.  Klicken Sie neben dem Feld **Anfügen an:** auf **Auswählen...**.  
  
    2.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie die zu debuggenden Codetypen aus.

        Der Standardwert **automatische** funktioniert für die meisten app-Typen festlegen. Wählen Sie für das Debuggen des clientseitigen Skripts in Chrome **Webkit** als Codetyp. Chrome, Sie müssen integritätsdienststatus den Browser im Debugmodus ausgeführt, je nach Ihren Anwendungstyp (Typ `chrome.exe --remote-debugging-port=9222` über die Befehlszeile).

        > [!NOTE]
        > Für Client-seitige Skript Debuggen muss das Skriptdebugging im Browser aktiviert sein. 
  
    3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie auf **Anfügen**aus.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Fügen Sie an einen Prozess auf einem Remotecomputer an  
Um an einen Prozess anzufügen, müssen Sie den Namen des Prozesses kennen (finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen). Vollständige Anleitungen für ASP.NET-Apps, die in IIS bereitgestellt wurden, finden Sie unter [Remote Debugging ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Wenn Sie den Namen des Prozesses für Ihr Szenario nicht kennen, finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios)
  
Bei Verwendung der **an den Prozess anhängen** Sie können wählen Sie im Dialogfeld einen anderen Computer, die für das Remotedebuggen eingerichtet wurde (d. h. der Remotedebugger muss auf dem Remotecomputer ausgeführt werden). Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md). Nach dem Auswählen eines Remotecomputers können Sie über eine Liste, in der alle verfügbaren laufenden Prozesse des Remotecomputers enthalten sind, den Debugger an einen oder mehrere Prozesse anhängen.
  
**So wählen Sie einen Remotecomputer aus:**  

1. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**).

    Wenn Sie schnell zu einem Prozess stattdessen anfügen möchten, finden Sie unter [erneut an Prozess anfügen](#BKMK_reattach).

2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** die entsprechende Verbindungsart aus der Liste **Transport** aus. **Standard** ist für die meisten Programme die richtige Einstellung.

    Die Einstellung **Transport** bleibt zwischen Debugsitzungen erhalten. 
  
3.  Verwenden Sie das Listenfeld **Qualifizierer** , um den Remotecomputernamen mithilfe einer der folgenden Methoden auszuwählen:  
  
    1.  Geben Sie im Listenfeld **Qualifizierer** den Namen ein.
    
        > [!Note]
        > Wenn Sie in späteren Schritten Sie eine Verbindung herstellen können nicht mit dem Namen des Remotecomputers, verwenden Sie die IP-Adresse. (Die Portnummer kann automatisch nach dem Auswählen des Prozess angezeigt. Sie können Sie auch manuell eingeben. In der Abbildung unten ist 4020 der Standardport für den Remotedebugger.)  

        Wenn Sie verwenden möchten die **finden** Schaltfläche müssen Sie möglicherweise [Öffnen von UDP-Port 3702](../debugger/remote-debugger-port-assignments.md) auf dem Server.
  
    2.  Klicken Sie auf den Dropdownpfeil neben dem Listenfeld **Qualifizierer** , und wählen Sie den Computernamen aus der Dropdownliste aus.  
  
    3.  Klicken Sie neben der Liste **Qualifizierer** auf die Schaltfläche**Suchen** , um das Dialogfeld **Remotedebuggerverbindung auswählen** zu öffnen. Im Dialogfeld **Remotedebuggerverbindung auswählen** werden alle Geräte aufgeführt, die sich auf dem lokalen Subnetz befinden, sowie sämtliche Geräte, die über ein Ethernetkabel direkt mit dem Computer verbunden sind. Klicken Sie auf den gewünschten Computer bzw. das gewünschte Gerät, und klicken Sie dann auf **Auswählen**. 
  
     Die Einstellung **Qualifizierer** bleibt nur zwischen Debugsitzungen erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Qualifizierer auftritt.
     
4.  Klicken Sie auf **aktualisieren**.

      Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Der Inhalt ist jedoch nicht immer aktuell. Sie können die Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf **Aktualisieren**. 
     
4.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

     Um schnell den Prozess auswählen, geben Sie den ersten Buchstaben des Namen des Prozesses ein, oder geben Sie einen Wert in das Feld "Filter", um für einen Prozessnamen zu suchen. Wenn Sie den Namen des Prozesses nicht kennen, finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios).
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
     
5.  Klicken Sie auf **Anfügen**aus.

## <a name="BKMK_reattach"></a> Erneut an Prozess anfügen

Sie können schnell erneut anfügen an Prozesse, die Sie zuvor durch Auswahl angefügt wurden **Debuggen > an Prozess anfügen...** (**Umschalt + Alt + P**). Wenn Sie diesen Befehl auswählen, der Debugger wird sofort versucht, mit dem letzten Prozesse fügen Sie angefügt, mit der **an den Prozess anhängen** Dialogfeld.

Der Debugger wird erneut anfügen, indem er zunächst versucht, entsprechend die vorherigen Prozess-ID und dann, wenn dies fehlschlägt, durch den Vergleich mit dem vorherigen Prozessnamen,. Wenn keine Übereinstimmungen gefunden werden oder es gibt mehrere Prozesse mit dem gleichen Namen, und klicken Sie dann die **an den Prozess anhängen** Dialogfeld wird angezeigt, sodass Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Die **erneut an Prozess anfügen** Befehl ist neu in Visual Studio 2017.

## <a name="additional-info"></a>Zusätzliche Informationen

Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen.  
  
Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, der nur über ein eingeschränktes Benutzerkonto verfügt, enthält die Liste **Verfügbare Prozesse** keine Prozesse, die in Sitzung 0 laufen. Sie wird für Dienste und andere Serverprozesse verwendet, wie z.B. „w3wp.exe“. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p` *ProzessID* in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um tlist.exe abzurufen, herunterladen und Installieren von Tools für Windows auf [WDK- und WinDbg-Downloads](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_Scenarios"></a> Häufige Szenarios des Debuggens

Können Sie ermitteln, ob Sie verwenden müssen **an den Prozess anhängen** und welcher Prozess anfügen, einige typische debugging-Szenarien werden hier angezeigt (die Liste ist nicht vollständig). Weitere Informationen verfügbar sind, stellen wir Links. Verwenden Sie zum schnellen zugreifen auf das Dialogfeld **STRG + ALT + P** und geben Sie dann auf den ersten Buchstaben des Namen des Prozesses ein.

Für einige app-Typen (z. B. UWP-apps), Sie nicht direkt mit dem Namen anfügen, aber die **Debuggen Installed App Package** Menüoption stattdessen (siehe Tabelle).

> [!NOTE]
> Weitere Informationen zu den Grundlagen des Debuggens in Visual Studio, finden Sie unter [erste Schritte mit dem Debugger](../debugger/getting-started-with-the-debugger.md).

|Szenario|Debuggen-Methode|Prozessname|Anmerkungen zu dieser Version und Links|
|-|-|-|-|
|Remotedebuggen von ASP.NET 4 oder 4.5 auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|w3wp.exe|Finden Sie unter [Remote Debugging ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebuggen von ASP.NET Core auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|dotnet.exe|App-Bereitstellung, finden Sie unter [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html). Debuggen, finden Sie unter [Remote Debugging ASP.NET Core auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debuggen des clientseitigen Skripts auf einem lokalen IIS-Server (gilt nur für unterstützte app-Typen)|Verwendung an den Prozess anhängen.|Chrome.exe MicrosoftEdgeCP.exe oder iexplore.exe|Debuggen von Skripts muss aktiviert sein. Chrome, müssen Sie auch Chrome im Debugmodus befindet, und wählen ausführen **Webkit-Code** in die **Anfügen an** Feld.|
|Debuggen einer C#-, Visual Basic oder C++-app auf dem lokalen Computer|Verwenden Sie entweder [standard Debuggen](../debugger/getting-started-with-the-debugger.md) oder an den Prozess anhängen|*Appname*.exe|Verwenden Sie in den meisten Fällen die standard-Debuggen, und nicht an den Prozess anhängen.|
|Remotedebuggen einer Windows-desktop-app|Remotetools|Nicht zutreffend| Finden Sie unter [Remote Debuggen einer C#- oder Visual Basic-app](../debugger/remote-debugging-csharp.md) oder [Remote Debuggen einer C++-app](../debugger/remote-debugging-cpp.md)|
|Debuggen von ASP.NET-Anwendungen auf dem lokalen Computer nach dem Start der app ohne den debugger|Verwendung an den Prozess anhängen.|iiexpress.exe|Dies kann hilfreich sein, Ihre App laden schneller, z. B. (z. B.) bei der profilerstellung. |
|Debuggen Sie andere unterstützte app-Typen für einen Serverprozess|Verwenden von Remotetools (Wenn Server remote verfügbar ist) und an den Prozess anhängen|Chrome.exe, iexplore.exe oder andere Prozesse|Verwenden Sie bei Bedarf Resource Monitor können Sie den Prozess zu identifizieren. Finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) und in späteren Abschnitten in diesem Thema|
|Remotedebuggen eine app (Universelle), OneCore, HoloLens und IoT|App-Paket Debuggen installiert|Nicht zutreffend|Finden Sie unter [ein installiertes App-Paket Debuggen](debug-installed-app-package.md) anstelle von **an den Prozess anhängen**|
|Debuggen einer universellen Windows-App (UWP), OneCore, HoloLens und IoT-app, die Sie in Visual Studio starten nicht|App-Paket Debuggen installiert|Nicht zutreffend|Finden Sie unter [ein installiertes App-Paket Debuggen](debug-installed-app-package.md) anstelle von **an den Prozess anhängen**|  
  
> [!NOTE]
>  Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

## <a name="what-debugger-features-can-i-use"></a>Welche Debuggerfunktionen kann ich verwenden?

Verwenden Sie die vollständigen Funktionen von Visual Studio-Debugger (z. B. Haltepunkte angesteuert) beim Anfügen an einen Prozess, die ausführbare Datei muss exakt der lokalen Quelle und Symbole (d. h. der Debugger muss die richtige laden befinden [Symboldateien (.pbd) ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Standardmäßig ist dies einen Debugbuild erforderlich.

Für remote debugging-Szenarien müssen Sie den Quellcode (oder eine Kopie des Quellcodes) öffnen in Visual Studio bereits verfügen. Die Binärdateien der kompilierten Anwendung auf dem Remotecomputer müssen aus dem gleichen Build wie auf dem lokalen Computer stammen.

In einigen Szenarien für lokalen Debuggen, können Sie Debuggen in Visual Studio ohne Zugriff auf die Quelle die richtige Symbol-Dateien mit der app vorhanden sind (Dies erfordert standardmäßig einen Debugbuild). Weitere Informationen finden Sie unter [angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Problembehandlung für Fehler beim Anfügen  
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.  
  
 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.  
  
 Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.  
  
 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die vorherige Beispielmeldung weist darauf hin, dass der Skriptcodetyp nicht angefügt werden konnte. Deshalb wäre es nicht möglich, den Skriptcode innerhalb des Prozesses zu debuggen. Der Skriptcode im Prozess würde zwar weiterhin ausgeführt werden, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen im Skript durchzuführen.  
  
 Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.  
  
 **Spezielle Informationen, warum ein Codetyp beim Anfügen des Fehler abrufen**  
  
1.  Trennen Sie den Prozess. Klicken Sie im Menü **Debuggen** auf **Alle trennen**.  
  
2.  Fügen Sie den Prozess erneut an, und wählen Sie hierbei nur einen Codetyp aus.  
  
    1.  Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** den entsprechenden Prozess aus.  
  
    2.  Klicken Sie auf **Auswählen**.  
  
    3.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie anschließend den Codetyp aus, der nicht angefügt werden konnte. Löschen Sie allen übrigen Code.  
  
    4.  Klicken Sie auf **OK**. Das Dialogfeld **Codetyp auswählen** wird geschlossen.  
  
    5.  Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Anhängen**.  
  
     Dieses Mal schlägt das Anfügen komplett fehl, und Sie erhalten eine spezifische Fehlermeldung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen Sie mehrerer Prozesse](../debugger/debug-multiple-processes.md)   
 [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)