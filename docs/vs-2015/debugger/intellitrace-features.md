---
title: IntelliTrace-Funktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 73
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c5c775dc309c02ca24d27e8b8ac19d2c9d9d588
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440174"
---
# <a name="intellitrace-features"></a>IntelliTrace-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können IntelliTrace verwenden, um Ereignisse und Methodenaufrufe Ihrer Anwendung aufzuzeichnen, mit deren Hilfe Sie den Status (Aufruflisten- und lokale Variablenwerte) zu unterschiedlichen Punkten in der Ausführung ermitteln können. Starten Sie das Debugging wie gewohnt – IntelliTrace ist standardmäßig aktiviert, und im neuen Fenster **Diagnosetools** unter der Registerkarte **Ereignisse** werden Ihnen die von IntelliTrace erfassten Informationen angezeigt. Wählen Sie ein Ereignis aus, und klicken Sie auf **Verlaufsbezogenes Debugging aktivieren**, um die Aufrufliste und lokal erfasste Informationen für dieses Ereignis anzuzeigen.  
  
 Eine detaillierte Beschreibung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace ist verfügbar in Visual Studio Enterprise Edition, jedoch nicht in der Visual Studio Professional oder Community Edition.  
  
 Um zu bestätigen, dass IntelliTrace aktiviert ist, öffnen Sie die **Extras / Optionen / IntelliTrace** Seite "Optionen". Das Kontrollkästchen **IntelliTrace aktivieren** sollte standardmäßig aktiviert sein.  
  
> [!NOTE]
> Der Bereich der Einstellungen auf der **IntelliTrace**-Optionsseite umfasst Visual Studio vollständig, nicht nur Projekte oder Projektmappen. Eine Änderung dieser Einstellungen gilt für alle Instanzen von Visual Studio, alle Debugsitzungen und alle Projekte oder Projektmappen.  
  
## <a name="ChooseEvents"></a> Wählen Sie die Ereignisse von IntelliTrace aufgezeichneten  
 Sie können die Aufzeichnung bestimmter IntelliTrace-Ereignisse aktivieren oder deaktivieren.  
  
 Wenn Sie gerade einen Debugging-Vorgang ausführen, beenden Sie diesen. Wechseln Sie zu **Extras / Optionen / IntelliTrace / IntelliTrace-Ereignisse**. Wählen Sie die Ereignisse, die IntelliTrace aufgezeichnen soll.  
  
## <a name="GoingFurther"></a> Sammeln von IntelliTrace-Ereignisse und Aufrufinformationen  
 Diese Option ist nicht standardmäßig aktiviert, IntelliTrace kann Methodenaufrufe jedoch zusammen mit Ereignissen aufzeichnen. Sammeln von methodenbezogenen aktivieren Aufrufe finden Sie unter **Extras / Optionen / IntelliTrace / Allgemein**, und wählen Sie **IntelliTrace-Ereignisse und Aufrufinformationen**.  
  
 Auf diese Weise können Sie den Verlauf der Aufrufliste anzeigen und Aufrufe in Ihrem Code schrittweise durchlaufen. IntelliTrace zeichnet Daten wie z. B. Methodennamen, Methodeneinstiegs- und -Endpunkte sowie bestimmte Parameter- und Rückgabewerte auf.  
  
> [!TIP]
> Diese Option ist standardmäßig nicht aktiviert, da dadurch ein erheblicher Mehraufwand erforderlich ist. IntelliTrace muss nicht nur jeden Methodenaufruf abfangen, den Ihre Anwendung vornimmt, sondern es muss auch viel größere Datenmenge verarbeiten, wenn es um die Anzeige der Daten auf dem Bildschirm geht.  
>   
> Sie können den Leistungsaufwand reduzieren, indem Sie die Ereignisliste beschränken, die von IntelliTrace aufgezeichnet werden, und indem Sie die Anzahl der Module auf ein Mindestmaß reduzieren. Weitere Informationen finden Sie unter [Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Verwenden des Navigationsbundstegs  
 Sie können den Navigationsbundsteg verwenden, der unten links neben dem Code-Fenster angezeigt wird. Wenn den Navigationsbundsteg nicht angezeigt wird, wechseln Sie zu **Extras / Optionen / IntelliTrace / erweitert**, und wählen Sie **den Navigationsbundsteg im Debugmodus anzeigen**.  
  
 Mithilfe des Navigationsbundstegs können Sie in den Methodenaufrufen und Ereignissen im verlaufsbezogenen Debugmodus vor und zurück navigieren. Weitere Informationen zum verlaufsbezogenen Debuggen finden Sie unter [Verlaufsbezogenes Debugging](../debugger/historical-debugging.md). Dazu gibt es eine Reihe von Befehlen:  
  
|||  
|-|-|  
|**Debuggerkontext hier festlegen**|Legt den Debugkontext auf den Zeitrahmen des Aufrufs fest, in dem er angezeigt wird.<br /><br /> Dieses Symbol wird nur für die aktuelle Aufrufliste angezeigt.|  
|**Zur Aufrufwebsite zurückkehren**|Bewegen Sie den Zeiger und den Debugkontext zurück zu dem Punkt, als die aktuelle Funktion aufgerufen wurde.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging. Wenn Sie zur ursprünglichen Ausführungsunterbrechung navigieren, wird das verlaufsbezogene Debugging deaktiviert und das Live-Debuggen aktiviert.|  
|**Zum vorherigen Aufruf oder IntelliTrace-Ereignis wechseln**|Bewegt den Zeiger und den Debugkontext zurück zum vorherigen Aufruf oder Ereignis.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging.|  
|**Einzelschritt**|Rufen Sie die aktuell ausgewählte Funktion auf.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|  
|**Zum nächsten Aufruf oder IntelliTrace-Ereignis wechseln**|Setzt den Zeiger- und Debugkontext zeitlich auf den nächsten Aufruf oder das nächste Ereignis vor, für den/das IntelliTrace-Daten vorhanden sind.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|  
|**Zum Livemodus wechseln**|Zurück zum Live-Debugmodus|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>In IntelliTrace nach einer Zeile oder Methode suchen  
 Sie können nur bei aktivierten Methodenaufrufinformationen nach Methoden suchen. Sie können den IntelliTrace-Verlauf nach einer bestimmten Zeile oder Methode durchsuchen. Während die Ausführung des Debuggers angehalten ist, können Sie mit der rechten Maustaste in den Text der Funktion klicken, um das Kontextmenü anzuzeigen, und auf die Optionen **In IntelliTrace nach dieser Zeile suchen** oder **In IntelliTrace nach dieser Methode suchen** klicken.  
  
### <a name="ControlCallData"></a> Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen  
 Standardmäßig erfasst IntelliTrace Informationen für alle Module, die von der Projektmappe verwendet werden. Sie können IntelliTrace so einstellen, dass nur Aufrufinformationen für die Module erfasst werden, die für Sie von Bedeutung sind. In **Extras / Optionen / IntelliTrace / Module**, Sie können angeben, die einzuschließenden oder die Module, IntelliTrace ausgeschlossen werden sollen. IntelliTrace erfasst nur die Ereignisse, die aus den Modulen stammen, die Sie angegeben haben, und die Methodenaufrufe, die in den Modulen aufgetreten sind, die für Sie von Bedeutung sind.  
  
 Um mehrere Module hinzuzufügen, verwenden Sie das Platzhalterzeichen * am Anfang oder am Ende der Zeichenfolge. Als Modulnamen müssen Dateinamen und keine Assemblynamen verwendet werden. Dateipfade werden nicht akzeptiert.  
  
 Versuchen Sie, die Anzahl der Module auf ein Mindestmaß zu beschränken. Sie erhalten eine bessere Leistung, da weniger Daten erfasst werden. Sie erhalten auch weniger Störungen auf der Benutzeroberfläche, da weniger Daten verarbeitet werden müssen.  
  
## <a name="SaveSession"></a> IntelliTrace-Daten in Datei speichern  
 Sie können die Daten, die von IntelliTrace erfassten speichern möchte **Debuggen / IntelliTrace / IntelliTrace-Sitzung speichern** während Sie Debuggen und die Anwendung befindet sich im Zustand "unterbrochen". Das Menüelement ist deaktiviert, und Sie können die von IntelliTrace erfassten Daten nicht speichern, sofern die Anwendung noch ausgeführt wird oder das Debuggen bereits beendet wurde.  
  
 Sie können IntelliTrace so konfigurieren, automatisch in einer Datei speichern, indem Sie zu **Extras / Optionen / IntelliTrace / erweitert** und **Store IntelliTrace-Aufzeichnungen in diesem Verzeichnis**. Sie können auch eine feste Größe für die generierte Datei konfigurieren, sodass IntelliTrace ältere Daten überschreibt, wenn kein Speicherplatz mehr verfügbar ist. Visual Studio erstellt zwei Dateien für jede IntelliTrace-Sitzung, wenn sie automatisch gespeichert und der Visual Studio-Hostprozess (vshost.exe) aktiviert ist.  
  
> [!TIP]
> Um Speicherplatz zu sparen, deaktivieren Sie die Speicherung von Dateien, wenn Sie sie nicht mehr benötigen. Alle vorhandenen Dateien werden nicht gelöscht. Sie können die Datei bei Bedarf immer aus dem Kontextmenü speichern.  
  
 Wenn Sie IntelliTrace-Daten in einer Datei speichern, erhalten Sie eine ITRACE-Datei für jeden Prozess, den IntelliTrace erfasst hat. Sie können dann die ITRACE-Datei in Visual Studio öffnen, indem Sie zu **Datei / öffnen / Datei** und das Dialogfeld "Datei öffnen" die ITRACE-Datei auswählen. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogs  
 [IntelliTrace in Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Exemplarische Vorgehensweise des Live Debuggens mit IntelliTrace in Visual Studio 2015 (Text-Editor)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Exemplarische Vorgehensweise des Live Debuggens mit IntelliTrace in Visual Studio 2015 (Social Club)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace in Visual Studio Enterprise 2015 unterstützt jetzt!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Sammeln von Daten aus einem Windowsdienst mithilfe des eigenständigen IntelliTrace Collector](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Bearbeiten die IntelliTrace-erfassungsplans](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Benutzerdefiniertes TraceSource und Debuggen mit IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [IntelliTrace Standalone Collector und Anwendungspools ausgeführt wird, klicken Sie unter Active Directory-Konten](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>Foren  
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Videos  
 [IntelliTrace-Umgebung](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015 (Verlaufsbezogenes Debuggen mit In# in Microsoft Visual Studio Ultimate 2015)](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
