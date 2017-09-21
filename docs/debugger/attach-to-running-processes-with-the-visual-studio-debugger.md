---
title: "Anf&#252;gen an laufende Prozesse mit dem Visual Studio Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "Remotedebuggen, Anhängen an Programme"
  - "Prozesse, Anhängen an laufende Prozesse"
  - "Dialogfeld "An den Prozess anhängen""
  - "Debuggen [Visual Studio], Anhängen an Prozesse"
  - "Debugger, Prozesse"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anf&#252;gen an laufende Prozesse mit dem Visual Studio Debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio-Debugger an einen Prozess anfügen ist häufig nützlich, wenn Sie keine app aus Visual Studio gestartet, aber Sie debuggen möchten. Beispielsweise können Sie anfügen, um eine IIS-Prozess oder der Windows-Dienst, eine app .NET hostet. Der Prozess, dem Sie anfügen kann lokal oder remote sein. Ein weiteres Beispiel ist, wenn Sie die app ohne den Debugger ausführen und den Ausnahmefehler, Sie dann Anfügen an den Prozess Ausführen der app zum Debuggen beginnen können.

Für einige app-Typen (z. B. Windows Store-apps), Sie nicht direkt auf einen Prozess anfügen, jedoch die **installiertes App-Paket Debuggen** stattdessen im Menü die option (siehe Tabelle).

Um Ihnen zu erkennen, ob Sie an einen Prozess für Ihr Szenario anfügen müssen, werden ein Paar von den am häufigsten verwendeten Debugszenarios hier angezeigt. Weitere Informationen verfügbar sind, bieten wir Links.

|Szenario|Debuggen-Methode|Prozessname|Hinweis und Links|
|-|-|-|-|
|Debuggen Sie eine beliebige unterstützte app-Typ auf dem lokalen Computer über Visual Studio zu starten|Standard F5-debugging|Nicht zutreffend|Finden Sie unter [Erste Schritte mit dem Debugger](../debugger/getting-started-with-the-debugger.md)|
|Remotedebugging ASP.NET 4 oder 4.5 auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|w3wp.exe|Finden Sie unter [Remote Debuggen von ASP.NET auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remotedebugging ASP.NET Core auf einem IIS-server|Remotetools verwenden und an den Prozess anhängen|DNX.exe|App-Bereitstellung finden Sie unter [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html). Zum Debuggen finden Sie unter [Remote Debuggen von ASP.NET auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debuggen Sie andere unterstützte app-Typen in einem Prozess|Verwenden von Remotetools (wenn der Server remote verfügbar ist) und an den Prozess anhängen|Iexplore.exe oder andere Prozesse|Verwenden Sie ggf. Task-Manager, um den Prozess zu identifizieren. Finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) und in späteren Abschnitten dieses Themas|
|Remote-Debuggen einer Windows-desktop-app|Remotetools und F5|Nicht zutreffend| Finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md)|
|Remote-Debuggen eine Windows Universal (UWP), OneCore, HoloLens oder IoT-app|App-Paket installiert werden|Nicht zutreffend|Verwendung **Debuggen / andere Ziele Debuggen / Debug-App-Paket installiert** anstelle von **an den Prozess anhängen**|
|Debuggen einer Windows Universal (UWP), OneCore, HoloLens oder IoT-app, die Sie in Visual Studio gestartet haben|App-Paket installiert werden|Nicht zutreffend|Verwendung **Debuggen / andere Ziele Debuggen / Debug-App-Paket installiert** anstelle von **an den Prozess anhängen**|
  
> [!WARNING]
>  Zum Anhängen an eine in JavaScript geschriebene universelle Windows-App müssen Sie zuerst das Debuggen für die App aktivieren. Weitere Informationen hierzu finden Sie unter [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) im Windows Developer Center.  
  
> [!NOTE]
>  Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.

## <a name="what-debugger-features-can-i-use"></a>Welche Debuggerfeatures können werden verwendet?

Um die vollständigen Funktionen von Visual Studio-Debugger (z. B. Haltepunkte angesteuert) zu verwenden, die ausführbare Datei muss genau übereinstimmen, die lokale Quelle und Symbole (also der Debugger muss möglicherweise den richtigen laden [Symboldateien (.pbd)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Standardmäßig ist dies einen Debugbuild erforderlich.

Remote debugging-Szenarien müssen Sie entweder den Quellcode eine Kopie des Quellcodes bereits in Visual Studio zu öffnen. Die Binärdateien der kompilierten Anwendung auf dem Remotecomputer müssen aus der gleichen Version wie auf dem lokalen Computer stammen.

In einigen Szenarien für lokalen Debuggen, können Sie Debuggen in Visual Studio ohne Zugriff auf die Quelle die richtige Symbol-Dateien mit der app vorhanden sind (Dies erfordert standardmäßig einen Debugbuild). Weitere Informationen finden Sie unter [Angeben von Symboldateien und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Für Windows desktop-apps können Sie auch die ausgeführte app mit dem JIT-Debugger (Visual Studio geöffnet, und Sie in app-Code unterbrochen wird, nachdem ein Fehler auftritt) Debuggen.

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Fügen Sie an einen Prozess auf einem Remotecomputer an  
 Sie müssen den Namen eines Prozesses kennen, um Dinge daran anhängen zu können. ASP.NET-apps, die auf IIS bereitgestellt wurden, finden Sie unter [Remote Debuggen von ASP.NET auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html) für ASP.NET Core-apps. Bei anderen Anwendungen finden Sie den Namen des Prozesses möglicherweise im Task-Manager.
  
 Wenn Sie das Dialogfeld **An den Prozess anhängen** verwenden, können Sie einen anderen Computer auswählen, der für das Remotedebuggen eingerichtet wurde. Weitere Informationen finden Sie unter [Remotedebuggen](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md). Nach dem Auswählen eines Remotecomputers können Sie über eine Liste, in der alle verfügbaren laufenden Prozesse des Remotecomputers enthalten sind, den Debugger an einen oder mehrere Prozesse anhängen.
  
 **So wählen Sie einen Remotecomputer aus:**  

1. Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.

2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** die entsprechende Verbindungsart aus der Liste **Transport** aus. **Standard** ist für die meisten Programme die richtige Einstellung.

    Die Einstellung **Transport** bleibt zwischen Debugsitzungen erhalten. 
  
3.  Verwenden Sie das Listenfeld **Qualifizierer** , um den Remotecomputernamen mithilfe einer der folgenden Methoden auszuwählen:  
  
    1.  Geben Sie im Listenfeld **Qualifizierer** den Namen ein.
    
        >**Hinweis** Wenn in späteren Schritten auch über den Remotecomputernamen Verbindungsversuch, verwenden Sie die IP-Adresse. (Die Portnummer kann nach dem Auswählen des Prozess automatisch angezeigt. Sie können Sie auch manuell eingeben. In der folgenden Abbildung ist 4020 der Standardport für den Remotedebugger.)  
  
    2.  Klicken Sie auf den Dropdownpfeil neben dem Listenfeld **Qualifizierer** , und wählen Sie den Computernamen aus der Dropdownliste aus.  
  
    3.  Klicken Sie neben der Liste **Qualifizierer** auf die Schaltfläche**Suchen** , um das Dialogfeld **Remotedebuggerverbindung auswählen** zu öffnen. Im Dialogfeld **Remotedebuggerverbindung auswählen** werden alle Geräte aufgeführt, die sich auf dem lokalen Subnetz befinden, sowie sämtliche Geräte, die über ein Ethernetkabel direkt mit dem Computer verbunden sind. Klicken Sie auf den gewünschten Computer bzw. das gewünschte Gerät, und klicken Sie dann auf **Auswählen**. 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     Die Einstellung **Qualifizierer** bleibt nur zwischen Debugsitzungen erhalten, wenn eine erfolgreiche Debugverbindung mit diesem Qualifizierer auftritt.
     
4.  Klicken Sie auf **Aktualisieren**ausgeben.

      Die Liste **Verfügbare Prozesse** wird beim Öffnen des Dialogfelds **Prozesse** automatisch angezeigt. Prozesse können bei geöffnetem Dialogfeld im Hintergrund gestartet und angehalten werden. Der Inhalt ist jedoch nicht immer aktuell. Sie können die Liste jederzeit aktualisieren, um die aktuelle Liste der Prozesse anzuzeigen. Klicken Sie dazu auf **Aktualisieren**. 
     
4.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.  
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
     
5.  Klicken Sie auf **Anfügen**.  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Fügen Sie an einen laufenden Prozess auf dem lokalen Computer an  
 Sie müssen den Namen eines Prozesses kennen, um Dinge daran anhängen zu können.  Den Namen des Prozesses finden Sie möglicherweise im Task-Manager.  
  
1.  Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.
  
2.  Wählen Sie im Dialogfeld **An den Prozess anhängen** aus der Liste **Verfügbare Prozesse** das Programm, mit dem Sie eine Verbindung herstellen möchten.  
  
     Wenn der Prozess unter einem anderen Benutzerkonto ausgeführt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen** .
  
3.  Stellen Sie sicher, dass im Feld **Anfügen an** der Typ des Codes aufgelistet ist, den Sie debuggen möchten. Bei Verwendung der Standardeinstellung **Automatisch** wird versucht, den zu debuggenden Codetyp zu ermitteln. Führen Sie die folgenden Schritte aus, um den Codetyp manuell festzulegen:  
  
    1.  Klicken Sie neben dem Feld **Anfügen an:** auf **Auswählen...**.  
  
    2.  Klicken Sie im Dialogfeld **Codetyp auswählen** auf **Diese Codetypen debuggen** , und wählen Sie die zu debuggenden Codetypen aus.  
  
    3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie auf **Anfügen**.

## <a name="additional-info"></a>Zusätzliche Informationen

Sie können beim Debuggen mit mehreren Programmen verbunden sein, es ist jedoch jeweils nur ein Programm im Debugger aktiv. Sie können das aktive Programm auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen. Weitere Informationen finden Sie unter [Gewusst wie: Festlegen des aktuellen Programms](http://msdn.microsoft.com/de-de/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Wird versucht, eine Verbindung mit einem Prozess herzustellen, der zu einem nicht vertrauenswürdigen Benutzerkonto gehört, wird ein Bestätigungsdialogfeld mit einer Sicherheitswarnung angezeigt. Weitere Informationen finden Sie unter [Sicherheitshinweis: Anfügen an einen Prozess eines nicht vertrauenswürdigen Benutzers kann gefährlich sein. Wenn die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht an diesen Prozess anfügen](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
In einigen Fällen werden beim Debuggen in einer Remotedesktopsitzung (Terminaldienste) in der Liste **Verfügbare Prozesse** nicht alle verfügbaren Prozesse angezeigt. Wenn Sie Visual Studio als Benutzer ausführen, der nur über ein eingeschränktes Benutzerkonto verfügt, enthält die Liste **Verfügbare Prozesse** keine Prozesse, die in Sitzung 0 laufen. Sie wird für Dienste und andere Serverprozesse verwendet, wie z.B. „w3wp.exe“. Sie können dieses Problem beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unter einem Administratorkonto oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an der Serverkonsole und nicht in einer Terminaldienstesitzung ausführen. Wenn keine dieser beiden Problemlösungen möglich ist, können Sie als dritte Möglichkeit den Prozess anfügen, indem Sie `vsjitdebugger.exe -p` *ProzessID* in der Windows-Befehlszeile ausführen. Die Prozess-ID kann mit tlist.exe ermittelt werden. Um die Datei "tlist.exe" abzurufen, laden Sie die Debugtools für Windows von der Seite  [WDK- und WinDbg-Downloads](http://go.microsoft.com/fwlink/?LinkId=168279)herunter, und installieren Sie diese.
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Problembehandlung bei Fehler beim Anfügen  
 Wenn der Debugger an einen laufenden Prozess angehängt wird, kann dieser Prozess mehrere Codetypen enthalten. Die Codetypen, an die der Debugger angefügt werden kann, werden im Dialogfeld **Codetyp auswählen** angezeigt und ausgewählt.  
  
 Manchmal kann der Debugger erfolgreich an den einen Codetyp, nicht aber an den anderen Codetyp angehängt werden. Das kann bei dem Versuch vorkommen, den Debugger an einen Prozess anzufügen, der auf einem Remotecomputer ausgeführt wird. Auf dem Remotecomputer sind möglicherweise nur Remotedebugkomponenten für bestimmte Codetypen installiert. Das Gleiche kann passieren, wenn Sie versuchen, den Debugger an mehr als einen Prozess zum direkten Datenbankdebuggen anzufügen. SQL-Debuggen unterstützt lediglich das Anfügen an einen einzelnen Prozess.  
  
 Wenn der Debugger nur an bestimmte, nicht aber an alle Codetypen angefügt werden kann, wird eine Meldung mit den Typen angezeigt, die nicht angefügt werden konnten.  
  
 Wenn der Debugger erfolgreich an mindestens einen Codetyp angehängt werden kann, können Sie mit dem Debuggen des Prozesses fortfahren. Sie können nur die erfolgreich angehängten Codetypen debuggen. Die vorherige Beispielmeldung weist darauf hin, dass der Skriptcodetyp nicht angefügt werden konnte. Deshalb wäre es nicht möglich, den Skriptcode innerhalb des Prozesses zu debuggen. Der Skriptcode im Prozess würde zwar weiterhin ausgeführt werden, doch Sie wären nicht in der Lage, Haltepunkte festzulegen, Daten anzuzeigen oder andere Debugoperationen im Skript durchzuführen.  
  
 Um weitere Informationen darüber zu erhalten, warum der Debugger nicht an einen Codetyp angefügt werden konnte, versuchen Sie erneut, den Debugger nur an diesen Codetyp anzufügen.  
  
 **Zum Abrufen von Informationen über die Ursache ein Codetyp angefügt**  
  
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