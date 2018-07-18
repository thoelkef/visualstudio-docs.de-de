---
title: IntelliTrace-Features | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18e3058416e6ce14dd8a481eb5dd8f8200217895
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478212"
---
# <a name="intellitrace-features"></a>IntelliTrace-Funktionen

Sie können IntelliTrace verwenden, um Ereignisse und Methodenaufrufe Ihrer Anwendung aufzuzeichnen, mit deren Hilfe Sie den Status (Aufruflisten- und lokale Variablenwerte) zu unterschiedlichen Punkten in der Ausführung ermitteln können. Starten Sie das debugging wie gewohnt – IntelliTrace ist standardmäßig aktiviert, und sehen Sie die von IntelliTrace erfassten Informationen in der neuen **Diagnosetools** Fenster unter dem **Ereignisse** Registerkarte. Wählen Sie ein Ereignis aus, und klicken Sie auf **verlaufsbezogenes Debugging aktivieren** um die Aufrufliste und lokal erfasste Informationen für dieses Ereignis anzuzeigen.

Eine detaillierte Beschreibung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace ist verfügbar in Visual Studio Enterprise Edition, jedoch nicht in der Visual Studio Professional oder Community Edition.

Überprüfen Sie, dass IntelliTrace aktiviert ist, öffnen Sie die **Extras > Optionen > IntelliTrace** Seite "Optionen". **Aktivieren von IntelliTrace** sollte standardmäßig aktiviert werden.

> [!NOTE]
> Der Bereich der Einstellungen für die **IntelliTrace** -Optionsseite umfasst Visual Studio als Ganzes, nicht einzelne Projekte oder Lösungen. Eine Änderung dieser Einstellungen gilt für alle Instanzen von Visual Studio, alle Debugsitzungen und alle Projekte oder Projektmappen.

## <a name="ChooseEvents"></a> Wählen Sie die Ereignisse von IntelliTrace aufgezeichneten

Sie können die Aufzeichnung bestimmter IntelliTrace-Ereignisse aktivieren oder deaktivieren.

Wenn Sie gerade einen Debugging-Vorgang ausführen, beenden Sie diesen. Wechseln Sie zu **Extras > Optionen > IntelliTrace > IntelliTrace-Ereignisse**. Wählen Sie die Ereignisse, die IntelliTrace aufgezeichnen soll.

## <a name="Snapshots"></a> Sammeln von Ereignissen und Momentaufnahmen

Dies ist nicht standardmäßig aktiviert, aber IntelliTrace Momentaufnahmen Ihrer Anwendung bei jeder haltepunktereignissen und den Debugger Schritt Ereignis erfassen kann, und Sie können Thesen Momentaufnahmen in einer verlaufsbezogenes debugging-Sitzung anzeigen. Eine Momentaufnahme bietet Ihnen einen Überblick über Ihre vollständigem Anwendungszustand. Um das Aufzeichnen von Momentaufnahmen zu aktivieren, wechseln Sie zu **Tools > Optionen > IntelliTrace > Allgemein**, und wählen Sie **IntelliTrace-Ereignisse und Momentaufnahmen**. Weitere Informationen finden Sie unter [Anzeigen von Momentaufnahmen mithilfe von IntelliTrace-Schritt-zurück](../debugger/how-to-use-intellitrace-step-back.md)

Momentaufnahmen sind in Visual Studio Enterprise 2017 Version 15.5 und höher verfügbar und erfordert Anniversary-Update für Windows 10 oder höher.  Für .NET Core und ASP.NET Core-apps ist Visual Studio Enterprise 2017 Version 15.7 Preview 1 erforderlich.

## <a name="GoingFurther"></a> Sammeln von IntelliTrace-Ereignisse und Aufrufinformationen

Dies ist standardmäßig aktiviert, aber IntelliTrace kann Methodenaufrufe zusammen mit Ereignissen aufzeichnen. Sammeln von methodenbezogenen aktivieren, wechseln Sie Aufrufe zu **Tools > Optionen > IntelliTrace > Allgemein**, und wählen Sie **IntelliTrace-Ereignisse und Aufrufinformationen**.

Aufrufinformationen ist nicht verfügbar für .NET Core und ASP.NET Core-apps. 

Auf diese Weise können Sie den Verlauf der Aufrufliste anzeigen und Aufrufe in Ihrem Code schrittweise durchlaufen. IntelliTrace zeichnet Daten wie z. B. Methodennamen, Methodeneinstiegs- und -Endpunkte sowie bestimmte Parameter- und Rückgabewerte auf.

> [!TIP]
> Diese Option ist standardmäßig nicht aktiviert, da dadurch ein erheblicher Mehraufwand erforderlich ist. IntelliTrace muss nicht nur jeden Methodenaufruf abfangen, den Ihre Anwendung vornimmt, sondern es muss auch viel größere Datenmenge verarbeiten, wenn es um die Anzeige der Daten auf dem Bildschirm geht.
>
> Sie können den Leistungsaufwand reduzieren, indem Sie die Ereignisliste beschränken, die von IntelliTrace aufgezeichnet werden, und indem Sie die Anzahl der Module auf ein Mindestmaß reduzieren. Weitere Informationen finden Sie unter [Steuerelement wie viel IntelliTrace erfassten Aufrufinformationen](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Den Navigationsbundsteg verwenden

Sie können den Navigationsbundsteg verwenden, der unten links neben dem Code-Fenster angezeigt wird. Wenn den Navigationsbundsteg nicht angezeigt wird, wechseln Sie zu **Tools > Optionen > IntelliTrace > erweitert**, und wählen Sie **den Navigationsbundsteg im Debugmodus anzeigen**.

Mithilfe des Navigationsbundstegs können Sie in den Methodenaufrufen und Ereignissen im verlaufsbezogenen Debugmodus vor und zurück navigieren. Weitere Informationen zum verlaufsbezogenen Debuggen finden Sie unter [verlaufsbezogenes Debugging](../debugger/historical-debugging.md). Dazu gibt es eine Reihe von Befehlen:

|||
|-|-|
|**Debuggerkontext hier festlegen**|Legt den Debugkontext auf den Zeitrahmen des Aufrufs fest, in dem er angezeigt wird.<br /><br /> Dieses Symbol wird nur für die aktuelle Aufrufliste angezeigt.|
|**Zur Aufrufwebsite zurückkehren**|Bewegen Sie den Zeiger und den Debugkontext zurück zu dem Punkt, als die aktuelle Funktion aufgerufen wurde.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging. Wenn Sie zur ursprünglichen Ausführungsunterbrechung navigieren, wird das verlaufsbezogene Debugging deaktiviert und das Live-Debuggen aktiviert.|
|**Wechseln Sie zum vorherigen Aufruf oder IntelliTrace-Ereignis**|Bewegt den Zeiger und den Debugkontext zurück zum vorherigen Aufruf oder Ereignis.<br /><br /> Wenn Sie im Live-Debugmodus sind, aktiviert dieser Befehl das verlaufsbezogene Debugging.|
|**Schritt**|Rufen Sie die aktuell ausgewählte Funktion auf.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|
|**Wechseln Sie zum nächsten Aufruf oder IntelliTrace-Ereignis**|Setzt den Zeiger- und Debugkontext zeitlich auf den nächsten Aufruf oder das nächste Ereignis vor, für den/das IntelliTrace-Daten vorhanden sind.<br /><br /> Dieser Befehl ist nur im verlaufsbezogenen Debugmodus verfügbar.|
|**Zum Livemodus wechseln**|Zurück zum Live-Debugmodus|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>In IntelliTrace nach einer Zeile oder Methode suchen

Sie können nur bei aktivierten Methodenaufrufinformationen nach Methoden suchen. Sie können den IntelliTrace-Verlauf nach einer bestimmten Zeile oder Methode durchsuchen. Während der Debugger die Ausführung angehalten wird, mit der rechten Maustaste im Textkörper der Funktion, die das Kontextmenü anzuzeigen, und klicken Sie auf **In IntelliTrace nach dieser Zeile suchen** oder **In IntelliTrace nach dieser Methode suchen**.

### <a name="ControlCallData"></a> Steuern Sie, wie viele IntelliTrace aufgezeichneten Aufrufinformationen

Standardmäßig erfasst IntelliTrace Informationen für alle Module, die von der Projektmappe verwendet werden. Sie können IntelliTrace so einstellen, dass nur Aufrufinformationen für die Module erfasst werden, die für Sie von Bedeutung sind. In **Extras > Optionen > IntelliTrace > Module**, können Sie die Module einschließen oder zum Ausschließen der IntelliTrace-Module angeben. IntelliTrace erfasst nur die Ereignisse, die aus den Modulen stammen, die Sie angegeben haben, und die Methodenaufrufe, die in den Modulen aufgetreten sind, die für Sie von Bedeutung sind.

Um mehrere Module hinzuzufügen, verwenden Sie das Platzhalterzeichen * am Anfang oder am Ende der Zeichenfolge. Als Modulnamen müssen Dateinamen und keine Assemblynamen verwendet werden. Dateipfade werden nicht akzeptiert.

Versuchen Sie, die Anzahl der Module auf ein Mindestmaß zu beschränken. Sie erhalten eine bessere Leistung, da weniger Daten erfasst werden. Sie erhalten auch weniger Störungen auf der Benutzeroberfläche, da weniger Daten verarbeitet werden müssen.

## <a name="SaveSession"></a> IntelliTrace-Daten in Datei speichern

Sie können die Daten, die von IntelliTrace erfassten speichern möchten **Debuggen > IntelliTrace > Speichern der IntelliTrace-Sitzung** während Sie Debuggen und die Anwendung unterbrochen wird. Das Menüelement ist deaktiviert, und Sie können die von IntelliTrace erfassten Daten nicht speichern, sofern die Anwendung noch ausgeführt wird oder das Debuggen bereits beendet wurde.

Sie können IntelliTrace so konfigurieren, automatisch in eine Datei zu speichern, navigieren Sie zu **Extras > Optionen > IntelliTrace > erweitert** auswählen und **Store IntelliTrace-Aufzeichnungen in diesem Verzeichnis**. Sie können auch eine feste Größe für die generierte Datei konfigurieren, sodass IntelliTrace ältere Daten überschreibt, wenn kein Speicherplatz mehr verfügbar ist. Visual Studio erstellt zwei Dateien für jede IntelliTrace-Sitzung, wenn sie automatisch gespeichert und der Visual Studio-Hostprozess (vshost.exe) aktiviert ist.

> [!TIP]
> Deaktivieren Sie sich um sehr viel Speicherplatz sparen, Speichern von Dateien automatisch, wenn Sie sie nicht mehr benötigen. Alle vorhandenen Dateien werden nicht gelöscht. Sie können die Datei bei Bedarf immer aus dem Kontextmenü speichern.

Wenn Sie IntelliTrace-Daten in einer Datei speichern, erhalten Sie eine ITRACE-Datei für jeden Prozess, den IntelliTrace erfasst hat. Sie können dann die ITRACE-Datei in Visual Studio öffnen, navigieren Sie zu **Datei > Öffnen > Datei** und die ITRACE-Datei aus dem Dialogfeld "Datei öffnen" auswählen. Weitere Informationen finden Sie unter [Verwenden gespeicherter IntelliTrace-Daten](../debugger/using-saved-intellitrace-data.md).

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

[IntelliTrace-Erfahrung](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Verlaufsbezogenes Debugging mit IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
