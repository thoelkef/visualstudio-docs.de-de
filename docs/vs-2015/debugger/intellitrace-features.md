---
title: IntelliTrace Features | Microsoft Docs
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
ms.openlocfilehash: dc16094c98a912d073bd6b873ecb3d1b3b411d1e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298950"
---
# <a name="intellitrace-features"></a>IntelliTrace-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können IntelliTrace verwenden, um Ereignisse und Methodenaufrufe Ihrer Anwendung aufzuzeichnen, mit deren Hilfe Sie den Status (Aufruflisten- und lokale Variablenwerte) zu unterschiedlichen Punkten in der Ausführung ermitteln können. Just start debugging as usual - IntelliTrace is turned on by default, and you can see the information IntelliTrace is recording in the new **Diagnostic Tools** window under the **Events** tab. Select an event and click **Activate Historical Debugging** to see the call stack and locals recorded for this event.  
  
 Eine detaillierte Beschreibung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace ist verfügbar in Visual Studio Enterprise Edition, jedoch nicht in der Visual Studio Professional oder Community Edition.  
  
 To confirm that IntelliTrace is turned on, open the **Tools / Options / IntelliTrace** options page. Das Kontrollkästchen **IntelliTrace aktivieren** sollte standardmäßig aktiviert sein.  
  
> [!NOTE]
> Der Bereich der Einstellungen auf der **IntelliTrace**-Optionsseite umfasst Visual Studio vollständig, nicht nur Projekte oder Projektmappen. Eine Änderung dieser Einstellungen gilt für alle Instanzen von Visual Studio, alle Debugsitzungen und alle Projekte oder Projektmappen.  
  
## <a name="ChooseEvents"></a> Choose the events that IntelliTrace records  
 Sie können die Aufzeichnung bestimmter IntelliTrace-Ereignisse aktivieren oder deaktivieren.  
  
 Wenn Sie gerade einen Debugging-Vorgang ausführen, beenden Sie diesen. Go to **Tools / Options / IntelliTrace / IntelliTrace Events**. Wählen Sie die Ereignisse, die IntelliTrace aufgezeichnen soll.  
  
## <a name="GoingFurther"></a> Collect IntelliTrace events and call information  
 Diese Option ist nicht standardmäßig aktiviert, IntelliTrace kann Methodenaufrufe jedoch zusammen mit Ereignissen aufzeichnen. To enable collection of method calls go to **Tools / Options / IntelliTrace / General**, and select **IntelliTrace events and call information**.  
  
 Auf diese Weise können Sie den Verlauf der Aufrufliste anzeigen und Aufrufe in Ihrem Code schrittweise durchlaufen. IntelliTrace zeichnet Daten wie z. B. Methodennamen, Methodeneinstiegs- und -Endpunkte sowie bestimmte Parameter- und Rückgabewerte auf.  
  
> [!TIP]
> Diese Option ist standardmäßig nicht aktiviert, da dadurch ein erheblicher Mehraufwand erforderlich ist. IntelliTrace muss nicht nur jeden Methodenaufruf abfangen, den Ihre Anwendung vornimmt, sondern es muss auch viel größere Datenmenge verarbeiten, wenn es um die Anzeige der Daten auf dem Bildschirm geht.  
>   
> Sie können den Leistungsaufwand reduzieren, indem Sie die Ereignisliste beschränken, die von IntelliTrace aufgezeichnet werden, und indem Sie die Anzahl der Module auf ein Mindestmaß reduzieren. Weitere Informationen finden Sie unter [Steuern der Anzahl der von IntelliTrace aufgezeichneten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Verwenden des Navigationsbundstegs  
 Sie können den Navigationsbundsteg verwenden, der unten links neben dem Code-Fenster angezeigt wird. If you don't see the navigation gutter, go to **Tools / Options / IntelliTrace / Advanced**, and select **Display the navigation gutter while in debug mode**.  
  
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
 Standardmäßig erfasst IntelliTrace Informationen für alle Module, die von der Projektmappe verwendet werden. Sie können IntelliTrace so einstellen, dass nur Aufrufinformationen für die Module erfasst werden, die für Sie von Bedeutung sind. In **Tools / Options / IntelliTrace / Modules**, You can specify the modules to include or the modules to exclude from IntelliTrace. IntelliTrace erfasst nur die Ereignisse, die aus den Modulen stammen, die Sie angegeben haben, und die Methodenaufrufe, die in den Modulen aufgetreten sind, die für Sie von Bedeutung sind.  
  
 Um mehrere Module hinzuzufügen, verwenden Sie das Platzhalterzeichen * am Anfang oder am Ende der Zeichenfolge. Als Modulnamen müssen Dateinamen und keine Assemblynamen verwendet werden. Dateipfade werden nicht akzeptiert.  
  
 Versuchen Sie, die Anzahl der Module auf ein Mindestmaß zu beschränken. Sie erhalten eine bessere Leistung, da weniger Daten erfasst werden. Sie erhalten auch weniger Störungen auf der Benutzeroberfläche, da weniger Daten verarbeitet werden müssen.  
  
## <a name="SaveSession"></a> Saving IntelliTrace data to file  
 You can save the data that IntelliTrace has collected going to **Debug / IntelliTrace / Save IntelliTrace Session** while you are debugging and the application is in a break state. Das Menüelement ist deaktiviert, und Sie können die von IntelliTrace erfassten Daten nicht speichern, sofern die Anwendung noch ausgeführt wird oder das Debuggen bereits beendet wurde.  
  
 You can configure IntelliTrace to automatically save to a file by going to **Tools / Options / IntelliTrace / Advanced** and selecting **Store IntelliTrace recordings in this directory**. Sie können auch eine feste Größe für die generierte Datei konfigurieren, sodass IntelliTrace ältere Daten überschreibt, wenn kein Speicherplatz mehr verfügbar ist. Visual Studio erstellt zwei Dateien für jede IntelliTrace-Sitzung, wenn sie automatisch gespeichert und der Visual Studio-Hostprozess (vshost.exe) aktiviert ist.  
  
> [!TIP]
> Um Speicherplatz zu sparen, deaktivieren Sie die Speicherung von Dateien, wenn Sie sie nicht mehr benötigen. Alle vorhandenen Dateien werden nicht gelöscht. Sie können die Datei bei Bedarf immer aus dem Kontextmenü speichern.  
  
 Wenn Sie IntelliTrace-Daten in einer Datei speichern, erhalten Sie eine ITRACE-Datei für jeden Prozess, den IntelliTrace erfasst hat. You can then open the .itrace file in Visual Studio by going to **File / Open / File** and selecting the .itrace file from the Open File dialog. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogs  
 [IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)  
  
 [Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Text Editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)  
  
 [Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Social Club)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)  
  
 [IntelliTrace in Visual Studio Enterprise 2015 now supports attach!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)  
  
 [Collect data from a windows service using the IntelliTrace Standalone Collector](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)  
  
 [Editing the IntelliTrace collection plan](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan/)  
  
 [Custom TraceSource and debugging using IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)  
  
 [IntelliTrace Standalone Collector and Application Pools running under Active Directory accounts](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)  
  
## <a name="forums"></a>Foren  
 [Visual Studio Debugger](https://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Videos  
 [IntelliTrace Experience](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015 (Verlaufsbezogenes Debuggen mit In# in Microsoft Visual Studio Ultimate 2015)](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
