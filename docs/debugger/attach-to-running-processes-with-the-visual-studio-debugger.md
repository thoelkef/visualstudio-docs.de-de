---
title: "Anfügen an laufende Prozesse mit dem Debugger in Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7ed9c7f362399d9cd256b02af9f1fe1bcecf8ce
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anfügen an laufende Prozesse mit dem Visual Studio Debugger
Sie können den Visual Studio-Debugger an einen laufenden Prozess auf einem lokalen oder Rmotecomputer anfügen. Nachdem der Prozess ausgeführt wird, klicken Sie auf **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**) zum Öffnen der **an den Prozess anhängen** (Dialogfeld).

Sie können diese Funktion verwenden, zum Debuggen von apps, die auf einem Computer lokal oder remote ausgeführt werden, mehrere Prozesse gleichzeitig zu debuggen oder Debuggen einer Anwendung, die nicht in Visual Studio erstellt wurde. Es ist häufig nützlich, wenn Sie eine app debuggen möchten, aber (aus irgendeinem Grund) wurden Sie nicht die app aus Visual Studio gestartet, mit dem angefügten Debugger. Z. B. Wenn Sie die app ohne den Debugger ausgeführt werden und eine Ausnahme erreicht haben, können Sie dann an den Prozess Ausführen der app, um Debuggen zu starten anfügen.

> [!TIP]
> Nicht sicher, ob Sie verwenden müssen **an den Prozess anhängen** für Ihr Szenario Debuggen? Finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios). Wenn zum Debuggen von ASP.NET-Anwendungen, die für IIS bereitgestellt wurden, finden Sie unter [Remote Debuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a>Fügen Sie an einen laufenden Prozess auf dem lokalen Computer an  
 Um an einen Prozess anfügen, müssen Sie den Namen des Prozesses kennen (finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen).
  
1.  Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**).

    Wenn Sie schnell zu einem Prozess stattdessen anfügen möchten, finden Sie unter [an Prozess anfügen](#BKMK_reattach).
  
2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.  

     Um den Prozess schnell auswählen möchten, die, den Sie möchten, geben Sie den ersten Buchstaben der Prozessname. Wenn Sie den Namen des Prozesses nicht kennen, lesen Sie [allgemeine Debugszenarien](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
  
3.  Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Bei Verwendung der Standardeinstellung **Automatisch** wird versucht, den zu debuggenden Codetyp zu ermitteln. Führen Sie die folgenden Schritte aus, um den Codetyp manuell festzulegen:  
  
    1.  Klicken Sie neben dem Feld **Anfügen an:** auf **Auswählen...**.  
  
    2.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie die zu debuggenden Codetypen aus.  
  
    3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie auf **Anfügen**aus.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Fügen Sie an einen Prozess auf einem Remotecomputer an  
 Um an einen Prozess anfügen, müssen Sie den Namen des Prozesses kennen (finden Sie unter [allgemeine Debugszenarien](#BKMK_Scenarios) für einige allgemeine Prozessnamen). Vollständige Anleitungen für ASP.NET-apps, die auf IIS bereitgestellt wurden, finden Sie unter [Remote Debuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Bei anderen Anwendungen finden Sie den Namen des Prozesses möglicherweise im Task-Manager.
  
 Wenn Sie das Dialogfeld **An den Prozess anhängen** verwenden, können Sie einen anderen Computer auswählen, der für das Remotedebuggen eingerichtet wurde. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md). Nach dem Auswählen eines Remotecomputers können Sie über eine Liste, in der alle verfügbaren laufenden Prozesse des Remotecomputers enthalten sind, den Debugger an einen oder mehrere Prozesse anhängen.
  
 **So wählen Sie einen Remotecomputer aus:**  

1. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** (oder drücken Sie **STRG + ALT + P**).

    Wenn Sie schnell zu einem Prozess stattdessen anfügen möchten, finden Sie unter [an Prozess anfügen](#BKMK_reattach).

2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** die entsprechende Verbindungsart aus der Liste **Transport** aus. **Standard** ist für die meisten Programme die richtige Einstellung.

    Die Einstellung **Transport** bleibt zwischen Debugsitzungen erhalten. 
  
3.  Verwenden Sie das Listenfeld **Qualifizierer** , um den Remotecomputernamen mithilfe einer der folgenden Methoden auszuwählen:  
  
    1.  Geben Sie im Listenfeld **Qualifizierer** den Namen ein.
    
        >**Hinweis** bei, in späteren Schritten verbinden kann nicht über den Remotecomputernamen, verwenden Sie die IP-Adresse. (Die Portnummer kann nach der Auswahl des Prozess automatisch angezeigt. Sie können Sie auch manuell eingeben. In der Abbildung unten ist 4020 der Standardport für den Remotedebugger.)  

        Wenn Sie verwenden möchten die **suchen** Schaltfläche, müssen Sie möglicherweise [Öffnen von UDP-Port 3702](../debugger/remote-debugger-port-assignments.md) auf dem Server.
  
    2.  Klicken Sie auf den Dropdownpfeil neben dem Listenfeld **Qualifizierer** , und wählen Sie den Computernamen aus der Dropdownliste aus.  
  
    3.  Klicken Sie neben der Liste **Qualifizierer** auf die Schaltfläche**Suchen** , um das Dialogfeld **Remotedebuggerverbindung auswählen** zu öffnen. Im Dialogfeld **Remotedebuggerverbindung auswählen** werden alle Geräte aufgeführt, die sich auf dem lokalen Subnetz befinden, sowie sämtliche Geräte, die über ein Ethernetkabel direkt mit dem Computer verbunden sind. Klicken Sie auf den gewünschten Computer bzw. das gewünschte Gerät, und klicken Sie dann auf **Auswählen**. 
  
     Die Einstellung **Qualifizierer** bleibt nur zwischen Debugsitzungen erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Qualifizierer auftritt.
     
4.  Klicken Sie auf **aktualisieren**.

      Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Der Inhalt ist jedoch nicht immer aktuell. Sie können die Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf **Aktualisieren**. 
     
4.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.

     Um den Prozess schnell auswählen möchten, die, den Sie möchten, geben Sie den ersten Buchstaben der Prozessname. Wenn Sie den Namen des Prozesses nicht kennen, lesen Sie [allgemeine Debugszenarien](#BKMK_Scenarios).
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
     
5.  Klicken Sie auf **Anfügen**aus.

## <a name="BKMK_reattach"></a>Schließen Sie den Prozess wieder

Sie können schnell Anfügen an Prozesse, die Sie zuvor durch Auswahl angefügt wurden **Debuggen > an Prozess anfügen...** (**Umschalt + Alt + P**). Wenn Sie diesen Befehl auswählen, der Debugger versucht sofort, bis zum letzten Prozesse fügen Sie angefügt, mit der **an den Prozess anhängen** (Dialogfeld).

Der Debugger wird zunächst wird versucht, entsprechen die vorherige Prozess-ID erneut anzufügen, und klicken Sie dann schlägt dies fehl, durch den Vergleich mit den vorherigen Prozessnamen,. Wenn keine Übereinstimmungen gefunden werden, oder es sind mehrere Prozesse mit dem gleichen Namen gefunden und dann die **an den Prozess anhängen** Dialogfeld wird angezeigt, sodass Sie den richtigen Prozess auswählen können.

> [!NOTE]
> Die **an Prozess anfügen** Befehl ist neu in Visual Studio 2017.

## <a name="additional-info"></a>Zusätzliche Informationen

Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen des aktuellen Programms](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess, der im Besitz eines nicht vertrauenswürdigen Benutzers kann riskant sein. Wenn die folgende Informationen verdächtig, oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, der nur über ein eingeschränktes Benutzerkonto verfügt, enthält die Liste **Verfügbare Prozesse** keine Prozesse, die in Sitzung 0 laufen. Sie wird für Dienste und andere Serverprozesse verwendet, wie z.B. „w3wp.exe“. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p` *ProzessID* in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um die Datei "tlist.exe" abzurufen, laden Sie die Debugtools für Windows von der Seite  [WDK- und WinDbg-Downloads](http://go.microsoft.com/fwlink/?LinkId=168279)herunter, und installieren Sie diese.

## <a name="BKMK_Scenarios"></a>Allgemeine Debugszenarien

Ermitteln Sie, ob Sie verwenden müssen **an den Prozess anhängen** und welcher Prozess anfügen, einige allgemeine Debugszenarien werden hier angezeigt (die Liste ist nicht vollständig). Weitere Anweisungen verfügbar sind, bieten wir Links.

Für einige app-Typen (z. B. uwp-apps), nicht direkt auf einen Prozess anfügen, aber verwenden Sie die **installiertes App-Paket Debuggen** Menü stattdessen option (siehe Tabelle).

> [!NOTE]
> Informationen zu den Grundlagen des Debuggens in Visual Studio finden Sie unter [erste Schritte mit dem Debugger](../debugger/getting-started-with-the-debugger.md).

|Szenario|Debuggen-Methode|Prozessname|Hinweise und Links|
|-|-|-|-|
|Debuggen einer verwalteten oder systemeigenen app auf dem lokalen Computer|Verwendung an den Prozess anhängen oder [standard Debuggen](../debugger/getting-started-with-the-debugger.md)|*Appname*.exe|Um das Dialogfeld schnell zugreifen zu können, verwenden **STRG + ALT + P** , und geben Sie den ersten Buchstaben der Prozessname.|
|Debuggen von ASP.NET-Anwendungen auf dem lokalen Computer nach dem Starten der app ohne den debugger|Verwendung an den Prozess anhängen.|iiexpress.exe|Dies ist möglicherweise hilfreich, um Ihre app laden schneller, z. B. (z. B.) bei der profilerstellung. |
|Remotedebuggen ASP.NET 4 oder 4.5 auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|w3wp.exe|Finden Sie unter [Remote Debuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebuggen ASP.NET Core, die auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|dotnet.exe|App-Bereitstellung finden Sie unter [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html). Zum Debuggen finden Sie unter [Remote Debuggen von ASP.NET Core auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debuggen von anderen unterstützten app-Typen für einen Serverprozess|Verwenden von Remotetools (wenn der Server remote verfügbar ist) und an den Prozess anhängen|Iexplore.exe oder andere Prozesse|Verwenden Sie bei Bedarf Task-Manager, um den Prozess zu identifizieren. Finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) und in späteren Abschnitten dieses Themas|
|Remote-Debuggen einer Windows-desktop-app|Remotetools und von F5|Nicht zutreffend| Finden Sie unter [des Remotedebuggens](../debugger/remote-debugging.md)|
|Remote Debuggen eine app auf UWP (Universal), OneCore, HoloLens und IoT|Installierte app-Paket Debuggen|Nicht zutreffend|Finden Sie unter [ein installiertes App-Paket Debuggen](debug-installed-app-package.md) anstatt **an den Prozess anhängen**|
|Debuggen Sie Universelle Windows-App (), OneCore, HoloLens und IoT-Apps, die Sie in Visual Studio starten nicht|Installierte app-Paket Debuggen|Nicht zutreffend|Finden Sie unter [ein installiertes App-Paket Debuggen](debug-installed-app-package.md) anstatt **an den Prozess anhängen**|
  
> [!WARNING]
>  Um zu einer uwp-App anfügen, die in JavaScript geschrieben ist, müssen Sie zuerst aktivieren, für die app zu debuggen. Finden Sie unter [Anfügen des Debuggers](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) im Windows Developer Center.  
  
> [!NOTE]
>  Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

## <a name="what-debugger-features-can-i-use"></a>Welche Debuggerfunktionen kann ich verwenden?

Verwenden Sie die vollständigen Funktionen von Visual Studio-Debugger (z. B. beim Erreichen von Haltepunkten) beim Anfügen an einen Prozess die ausführbare Datei muss genau entsprechen Ihrem lokalen Quellen und Symbole (d. h. der Debugger muss die richtige laden befinden [Symboldateien (.pbd) ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Standardmäßig ist dies einen Debugbuild erforderlich.

Für Szenarien mit remote Debuggen benötigen Sie den Quellcode (oder eine Kopie des Quellcodes) bereits in Visual Studio öffnen. Die kompilierte app-Binärdateien auf dem Remotecomputer müssen aus dem gleichen Build wie auf dem lokalen Computer stammen.

Lokalen Debuggen Szenarien, in denen Sie beim Debuggen in Visual Studio keinen Zugriff auf die Quelle, wenn die richtige Symbol-Dateien mit der app vorhanden sind (Dies erfordert standardmäßig einen Debugbuild). Weitere Informationen finden Sie unter [geben Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a>Problembehandlung bei Fehler beim Anfügen  
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.  
  
 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.  
  
 Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.  
  
 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die vorherige Beispielmeldung weist darauf hin, dass der Skriptcodetyp nicht angefügt werden konnte. Deshalb wäre es nicht möglich, den Skriptcode innerhalb des Prozesses zu debuggen. Der Skriptcode im Prozess würde zwar weiterhin ausgeführt werden, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen im Skript durchzuführen.  
  
 Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.  
  
 **So erhalten Sie spezifische Informationen zu den Ursachen ein Codetyp angefügt**  
  
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
 [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)