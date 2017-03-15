---
title: "IntelliTrace-Features | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Visual Studio-ALM], IntelliTrace"
  - "Debuggen [Visual Studio-ALM], Verlauf der Ausführungsaufzeichnung"
  - "IntelliTrace, Debuggen mit Ereignissen"
  - "IntelliTrace, Debuggen mit Ereignissen und Aufrufinformationen"
  - "IntelliTrace, Deaktivieren"
  - "IntelliTrace, Aktivieren"
  - "IntelliTrace, Navigieren im Ereignis- und Aufrufverlauf"
  - "IntelliTrace, Verlauf der Ausführungsaufzeichnung"
  - "IntelliTrace, Speichern der Sitzung"
  - "IntelliTrace, Starten des Debuggens"
  - "IntelliTrace, Ausschalten"
  - "IntelliTrace, Einschalten"
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 67
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 67
---
# IntelliTrace-Features
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können IntelliTrace verwenden, um Ereignisse und Methodenaufrufe Ihrer Anwendung aufzuzeichnen, mit deren Hilfe Sie den Status \(Aufruflisten\- und lokale Variablenwerte\) zu unterschiedlichen Punkten in der Ausführung ermitteln können.  Starten Sie das Debugging wie gewohnt – IntelliTrace ist standardmäßig aktiviert, und im neuen Fenster **Diagnosetools** unter der Registerkarte **Ereignisse** werden Ihnen die von IntelliTrace erfassten Informationen angezeigt.  Wählen Sie ein Ereignis aus, und klicken Sie auf **verlaufsbezogenes Debugging aktivieren**, um die Aufrufliste und lokal erfasste Informationen für dieses Ereignis anzuzeigen.  
  
 Eine detaillierte Beschreibung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace ist verfügbar in Visual Studio Enterprise Edition, jedoch nicht in der Visual Studio Professional oder Community Edition.  
  
 Öffnen Sie die Seite **Tools \/ Optionen \/ IntelliTrace**, um sich zu vergewissern, dass IntelliTrace aktiviert ist.  Das Kontrollkästchen **IntelliTrace aktivieren** sollte standardmäßig aktiviert sein.  
  
> [!NOTE]
>  Der Bereich der Einstellungen auf der **IntelliTrace**\-Optionsseite umfasst Visual Studio vollständig, nicht nur Projekte oder Projektmappen.  Eine Änderung dieser Einstellungen gilt für alle Instanzen von Visual Studio, alle Debugsitzungen und alle Projekte oder Projektmappen.  
  
##  <a name="ChooseEvents"></a> Auswählen der von IntelliTrace aufgezeichneten Ereignisse  
 Sie können die Aufzeichnung bestimmter IntelliTrace\-Ereignisse aktivieren oder deaktivieren.  
  
 Wenn Sie gerade einen Debugging\-Vorgang ausführen, beenden Sie diesen.  Wechseln Sie zu **Tools \/ Optionen \/ IntelliTrace \/ IntelliTrace\-Ereignisse**.  Wählen Sie die Ereignisse, die IntelliTrace aufgezeichnen soll.  
  
##  <a name="GoingFurther"></a> Erfassen von IntelliTrace\-Ereignissen und Aufrufen von Informationen  
 Diese Option ist nicht standardmäßig aktiviert, IntelliTrace kann Methodenaufrufe jedoch zusammen mit Ereignissen aufzeichnen.  Wählen Sie unter **Extras \/ Optionen \/ IntelliTrace \/ Allgemein** die Option **IntelliTrace\-Ereignis\- und \-Aufrufinformationen** aus, um die Erfassung von Methodenaufrufen zu aktivieren.  
  
 Auf diese Weise können Sie den Verlauf der Aufrufliste anzeigen und Aufrufe in Ihrem Code schrittweise durchlaufen.  IntelliTrace zeichnet Daten wie z. B. Methodennamen, Methodeneinstiegs\- und \-Endpunkte sowie bestimmte Parameter\- und Rückgabewerte auf.  
  
> [!TIP]
>  Diese Option ist standardmäßig nicht aktiviert, da dadurch ein erheblicher Mehraufwand erforderlich ist.  IntelliTrace muss nicht nur jeden Methodenaufruf abfangen, den Ihre Anwendung vornimmt, sondern es muss auch viel größere Datenmenge verarbeiten, wenn es um die Anzeige der Daten auf dem Bildschirm geht.  
>   
>  Sie können den Leistungsaufwand reduzieren, indem Sie die Ereignisliste beschränken, die von IntelliTrace aufgezeichnet werden, und indem Sie die Anzahl der Module auf ein Mindestmaß reduzieren.  Weitere Informationen finden Sie unter [Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).  
  
### Verwenden des Navigationsbundstegs  
 Sie können den Navigationsbundsteg verwenden, der unten links neben dem Code\-Fenster angezeigt wird.  Wenn den Navigationsbundsteg nicht angezeigt wird, wechseln Sie zu **Extras \/ Optionen \/ IntelliTrace \/ Erweitert**, und wählen Sie **Den Navigationsbundsteg im Debugmodus anzeigen**.  
  
 Mithilfe des Navigationsbundstegs können Sie in den Methodenaufrufen und Ereignissen im verlaufsbezogenen Debugmodus vor und zurück navigieren.  Weitere Informationen zum verlaufsbezogenen Debuggen finden Sie unter [Verlaufsbezogenes Debugging](../debugger/historical-debugging.md).  Dazu gibt es eine Reihe von Befehlen:  
  
|||  
|-|-|  
|**Debuggerkontext hier festlegen**|Legt den Debugkontext auf den Zeitrahmen des Aufrufs fest, in dem er angezeigt wird.<br /><br /> Dieses Symbol wird nur für die aktuelle Aufrufliste angezeigt.|  
|**Zur Aufrufwebsite zurückkehren**|Bewegen Sie den Zeiger und den Debugkontext zurück zu dem Punkt, als die aktuelle Funktion aufgerufen wurde.<br /><br /> Wenn Sie im Live\-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging.  Wenn Sie zur ursprünglichen Ausführungsunterbrechung navigieren, wird das verlaufsbezogene Debugging deaktiviert und das Live\-Debuggen aktiviert.|  
|**Zum vorherigen Aufruf oder IntelliTrace\-Ereignis wechseln**|Bewegt den Zeiger und den Debugkontext zurück zum vorherigen Aufruf oder Ereignis.<br /><br /> Wenn Sie im Live\-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging.|  
|**Einzelschritt**|Rufen Sie die aktuell ausgewählte Funktion auf.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|  
|**Zum nächsten Aufruf oder IntelliTrace\-Ereignis wechseln**|Setzt den Zeiger\- und Debugkontext zeitlich auf den nächsten Aufruf oder das nächste Ereignis vor, für den\/das IntelliTrace\-Daten vorhanden sind.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|  
|**Zum Livemodus wechseln**|Zurück zum Live\-Debugmodus|  
  
### In IntelliTrace nach einer Zeile oder Methode suchen  
 Sie können nur bei aktivierten Methodenaufrufinformationen nach Methoden suchen.  Sie können den IntelliTrace\-Verlauf nach einer bestimmten Zeile oder Methode durchsuchen.  Während die Ausführung des Debuggers angehalten ist, können Sie mit der rechten Maustaste in den Text der Funktion klicken, um das Kontextmenü anzuzeigen, und auf die Optionen **In IntelliTrace nach dieser Zeile suchen** oder **In IntelliTrace nach dieser Methode suchen** klicken.  
  
###  <a name="ControlCallData"></a> Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen  
 Standardmäßig erfasst IntelliTrace Informationen für alle Module, die von der Projektmappe verwendet werden.  Sie können IntelliTrace so einstellen, dass nur Aufrufinformationen für die Module erfasst werden, die für Sie von Bedeutung sind.  Unter **Extras \/ Optionen \/ IntelliTrace \/ Module** können Sie die in IntelliTrace einzuschließenden oder auszuschließenden Module angeben.  IntelliTrace erfasst nur die Ereignisse, die aus den Modulen stammen, die Sie angegeben haben, und die Methodenaufrufe, die in den Modulen aufgetreten sind, die für Sie von Bedeutung sind.  
  
 Um mehrere Module hinzuzufügen, verwenden Sie das Platzhalterzeichen \* am Anfang oder am Ende der Zeichenfolge.  Als Modulnamen müssen Dateinamen und keine Assemblynamen verwendet werden.  Dateipfade werden nicht akzeptiert.  
  
 Versuchen Sie, die Anzahl der Module auf ein Mindestmaß zu beschränken.  Sie erhalten eine bessere Leistung, da weniger Daten erfasst werden.  Sie erhalten auch weniger Störungen auf der Benutzeroberfläche, da weniger Daten verarbeitet werden müssen.  
  
##  <a name="SaveSession"></a> Speichern von IntelliTrace\-Daten in einer Datei  
 Sie können die von IntelliTrace erfassten Daten speichern, indem Sie während des Debuggens zu **Debuggen \/ IntelliTrace \/ IntelliTrace\-Sitzung speichern** wechseln, während die Anwendung unterbrochen ist.  Das Menüelement ist deaktiviert, und Sie können die von IntelliTrace erfassten Daten nicht speichern, sofern die Anwendung noch ausgeführt wird oder das Debuggen bereits beendet wurde.  
  
 Sie können IntelliTrace so konfigurieren, dass Daten automatisch in einer Datei gespeichert werden, indem Sie auf **Extras \/ Optionen \/ IntelliTrace \/ Erweitert** klicken und **IntelliTrace\-Aufzeichnungen in diesem Verzeichnis speichern** auswählen.  Sie können auch eine feste Größe für die generierte Datei konfigurieren, sodass IntelliTrace ältere Daten überschreibt, wenn kein Speicherplatz mehr verfügbar ist.  Visual Studio erstellt zwei Dateien für jede IntelliTrace\-Sitzung, wenn sie automatisch gespeichert und der Visual Studio\-Hostprozess \(vshost.exe\) aktiviert ist.  
  
> [!TIP]
>  Um Speicherplatz zu sparen, deaktivieren Sie die Speicherung von Dateien, wenn Sie sie nicht mehr benötigen.  Alle vorhandenen Dateien werden nicht gelöscht.  Sie können die Datei bei Bedarf immer aus dem Kontextmenü speichern.  
  
 Wenn Sie IntelliTrace\-Daten in einer Datei speichern, erhalten Sie eine ITRACE\-Datei für jeden Prozess, den IntelliTrace erfasst hat.  Sie können dann die ITRACE\-Datei in Visual Studio öffnen, indem Sie zu **Datei \/ Öffnen \/ Datei** wechseln und im Dialogfeld „Datei öffnen“ die ITRACE\-Datei auswählen.  Weitere Informationen finden Sie unter [Debuggen einer App mithilfe gespeicherter IntelliTrace\-Daten](../debugger/using-saved-intellitrace-data.md).  
  
## Blogs  
 [IntelliTrace in Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Exemplarische Vorgehensweise des Live Debuggens mit IntelliTrace in Visual Studio 2015 \(Text\-Editor\)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Exemplarische Vorgehensweise beim Live\-Debuggen mit IntelliTrace in Visual Studio 2015 \(Social Club\)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace in Visual Studio Enterprise 2015 unterstützt jetzt auch Anhänge](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Erfassen von Daten aus einem Windowsdienst mithilfe von IntelliTrace Standalone Collector](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Bearbeiten des IntelliTrace\-Erfassungsplans](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Benutzerdefiniertes TraceSource und Debuggen mit IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Unter Active Directory\-Konten ausgeführte\(r\) IntelliTrace Standalone Collector und Anwendungspools](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## Foren  
 [Visual Studio\-Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## Videos  
 [IntelliTrace\-Erfahrung](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Verlaufsbezogenes Debuggen mit IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)