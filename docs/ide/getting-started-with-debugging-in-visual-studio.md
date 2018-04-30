---
title: Erste Schritte beim Debuggen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/14/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 085ea00f95124eb6ae2ed7ccc96eed692be0d649
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-debugging-in-visual-studio"></a>Erste Schritte beim Debuggen in Visual Studio
Visual Studio bietet einen leistungsfähigen integrierten Satz von Projektbuild- und Debugtools. Sie erfahren in diesem Thema, wie Sie die grundlegenden Funktionen zum Debuggen von Benutzeroberflächenfunktionen verwenden.  

Wenn Sie Visual Studio noch nicht installiert haben, gehen Sie auf die Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), um es kostenlos herunterzuladen.

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>Mein Code funktioniert nicht. Ich benötige Hilfe in Visual Studio.  
 Sie haben also herausgefunden, wie der Editor funktioniert, und Code erstellt. Nun möchten Sie mit dem Debuggen von Code beginnen. In Visual Studio besteht das Debuggen wie bei den meisten IDEs aus zwei Phasen: Erstellen des Codes zum Abfangen und Beheben von Projekt- und Compilerfehlern und Ausführen dieses Codes in der Umgebung zum Abfangen und Beheben von Laufzeit- und dynamischen Fehlern.  

### <a name="build-your-code"></a>Erstellen des Codes  
 Es gibt zwei grundlegende Arten der Buildkonfiguration: **Debug** und **Release**. Die erste Konfiguration erzeugt eine langsamere und größere ausführbare Datei, die für ein umfangreicheres interaktives Debuggen zur Laufzeit verwendet werden kann, aber nie ausgeliefert werden sollte. Mit der zweiten wird eine schnellere, optimierte ausführbare Datei erstellt, die (zumindest aus Sicht des Compilers) ausgeliefert werden kann. Die Standardbuildkonfiguration ist **Debug**.

Projekte lassen sich am einfachsten mit **F7** erstellen. Sie können aber auch im Hauptmenü auf **Erstellen > Projektmappe erstellen** klicken.  

 ![Visual Studio, Auswahl im Menü „Projekt erstellen“](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 Sie können den Buildprozess im Statusfenster **Ausgabe** am unteren Rand der Visual Studio-Benutzeroberfläche beobachten. Dort werden Fehler, Warnungen und Buildvorgänge angezeigt. Wenn Fehler (oder Warnungen über die konfigurierte Stufe hinaus) auftreten, schlägt der Build fehl. Sie können auf die Fehler und Warnungen klicken, um zu der Zeile zu wechseln, in der der Fehler aufgetreten ist. Erstellen Sie Ihr Projekt neu, indem Sie entweder **F7** erneut drücken (um nur die Dateien mit Fehlern neu zu kompilieren) oder indem Sie **STRG+ALT+F7** drücken (für eine vollständige Neuerstellung).  

 Im Ergebnisfenster unterhalb des Editors finden Sie zwei Buildfenster als Registerkarten: Das Fenster **Ausgabe** enthält die unformatierte Compilerausgabe (einschließlich Fehlermeldungen), und das Fenster **Fehlerliste** enthält eine sortierbare und filterfähige Liste aller Fehler und Warnungen.  

 Bei erfolgreicher Ausführung werden die Ergebnisse wie folgt im Fenster **Ausgabe** dargestellt.  

 ![Visual Studio, erfolgreiche Buildausgabe](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="review-the-error-list"></a>Anzeigen der Fehlerliste  
 Sofern Sie keine Änderungen am Code vorgenommen haben, den Sie zuvor erfolgreich kompiliert hatten, tritt vermutlich ein Fehler auf. Wenn Sie noch nie programmiert haben, werden wahrscheinlich viele Fehler auftreten. Fehler sind manchmal offensichtlich, so z.B. einfache Syntaxfehler oder falsche Variablennamen. Wenn der Code schlecht lesbar ist, können Fehler jedoch sehr schwer zu finden sein. Für eine übersichtlichere Ansicht der Probleme navigieren Sie zum Ende des Fensters **Ausgabe** für den Build, und klicken Sie auf die Registerkarte **Fehlerliste**. Dadurch gelangen Sie zu einer besser angeordneten Ansicht der Fehler und Warnungen für das Projekt mit einigen zusätzlichen Optionen.  

 ![Visual Studio, Ausgabe und Fehlerliste](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 Klicken Sie im Fenster **Fehlerliste** auf die Zeile mit dem Fehler, um direkt in die Zeile zu springen, in der der Fehler aufgetreten ist. (Blenden Sie alternativ die Zeilennummern ein, indem Sie oben rechts auf die **Schnellstartleiste** klicken, „Zeilennummern“ eingeben und die **EINGABETASTE** drücken. Dies ist die schnellste Möglichkeit zum Aufrufen des Fensters **Optionen**, in dem Sie Zeilennummern aktivieren können. Machen Sie sich mit der Verwendung der **Schnellstartleiste** vertraut, denn sie erspart Ihnen viele Klicks auf der Benutzeroberfläche!)  

 ![Visual Studio, Editor mit Zeilennummern](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Visual Studio, Option „Zeilennummern“](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 Mit **STRG+G** können Sie schnell die Nummer der Zeile abrufen, in der der Fehler aufgetreten ist.  

 Der Fehler wird durch eine rote Wellenlinie gekennzeichnet. Bewegen Sie den Mauszeiger darüber, um weitere Informationen anzuzeigen. Wenn Sie die Korrektur vornehmen, wird die Markierung aufgehoben. Es ist natürlich trotzdem möglich, dass Sie mit Ihrer Änderung einen neuen Fehler einfügen. (Dies wird als „Regression“ bezeichnet.)  

 ![Visual Studio, Draufzeigen auf Fehler](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 Bearbeiten Sie die Fehlerliste, und beheben Sie alle Fehler im Code.  

 ![Visual Studio, Debugger, Fehlerfenster](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="review-errors-in-detail"></a>Detaillierte Anzeige der Fehler  
 Einige Fehler erscheinen Ihnen möglicherweise nicht sinnvoll, wenn sie wie vom Compiler formuliert angezeigt werden. In diesen Fällen benötigen Sie weitere Informationen. Sie können aus dem Fenster **Fehlerliste** heraus eine automatische Suche in Bing nach weiterführenden Informationen über den Fehler (oder die Warnung) durchführen. Klicken Sie dazu mit der rechten Maustaste auf die entsprechende Zeile, und wählen Sie im Kontextmenü **Hilfe zu Fehlern anzeigen** aus.  

 ![Visual Studio, Bing-Suche in der Fehlerliste](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 Dadurch wird in Visual Studio eine Registerkarte mit den Ergebnissen einer Bing-Suche nach dem Fehlercode und dem Text angezeigt. Die Ergebnisse stammen aus verschiedenen Quellen im Internet und sind möglicherweise nicht alle hilfreich.  

 Sie können auch auf den als Link formatierten Fehlercode in der Spalte **Code** in der **Fehlerliste** klicken. Hierdurch wird eine Suche in Bing nur nach dem Fehlercode durchgeführt.  

### <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Verwenden von Glühbirnen zum Beheben oder Umgestalten von Code  
 Glühbirnen sind ein neues Feature von Visual Studio, mit dem Sie Code inline umgestalten können. Damit können allgemeine Warnungen schnell und effektiv behoben werden. Um darauf zuzugreifen, klicken Sie mit der rechten Maustaste auf die gezackte Linie (oder drücken Sie **STRG+.**, während Sie auf die Wellenlinie zeigen), und wählen Sie dann **Schnelle Aktionen** aus.  

 ![Visual Studio, schnelle Aktionen für die Glühbirne](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 Es wird eine Liste der möglichen Korrekturen oder Umgestaltungen angezeigt, die Sie auf diese Codezeile anwenden können.  

 ![Visual Studio, Glühbirnenvorschau](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 Glühbirnen können überall dort angewendet werden, wo die Codeanalyse Möglichkeiten zur Problembehebung, Umgestaltung oder Verbesserung Ihres Codes erkannt hat. Klicken Sie mit der rechten Maustaste auf eine beliebige Codezeile, um das Kontextmenü zu öffnen, und klicken Sie auf **Schnelle Aktionen** (oder drücken Sie **STRG+.**). Wenn es Möglichkeiten zur Umgestaltung oder Verbesserung gibt, werden diese angezeigt. Andernfalls wird die Meldung `No quick options available here` in der unteren linken Ecke der IDE angezeigt.  

 ![Visual Studio, Glühbirnentext „Keine Option“](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 Mit etwas Erfahrung können Sie rasch mithilfe der Pfeiltasten und **STRG+.** überprüfen, ob schnelle Aktionen zur Umgestaltung und Bereinigung Ihres Codes verfügbar sind.  

 Weitere Informationen zu Glühbirnen finden Sie unter [Ausführen von schnellen Aktionen mit Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md).  

### <a name="debug-your-running-code"></a>Debuggen von ausgeführtem Code  
 Nachdem Sie Code erstellt und einige Bereinigungen durchgeführt haben, führen Sie ihn aus, indem Sie **F5** drücken oder **Debuggen > Debuggen starten** auswählen. Dadurch wird Ihre App in einer Debugumgebung gestartet, damit Sie ihr Verhalten im Detail beobachten können. Die Visual Studio-IDE ändert sich während der Ausführung Ihrer App: Das Fenster **Ausgabe** wird (in der standardmäßigen Fensterkonfiguration) durch zwei neue ersetzt, und zwar die Registerkartenfenster **Auto/Lokal/Module/Überwachung** und **Aufrufliste/Haltepunkte/Ausnahmeeinstellungen/Ausgabe**. Diese Fenster enthalten mehrere Registerkarten, mit denen Sie Variablen, Threads, Aufruflisten und andere Verhaltensweisen während der Ausführung Ihrer App überprüfen und bewerten können.  

 ![Visual Studio, Fenster „Auto“ und „Aufrufliste“](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 Sie können Ihre App beenden, indem Sie **UMSCHALT+F5** drücken oder auf die Schaltfläche **Stopp** klicken. Sie können die App auch einfach durch Schließen des Hauptfensters (oder über die Befehlszeile) schließen.  

 Wenn Ihr Code ohne besondere Vorkommnisse genau wie erwartet ausgeführt wurde, sind Sie damit fertig! Wenn der Code jedoch nicht mehr reagiert oder abgestürzt, oder wenn Sie unerwartete Ergebnissen erhalten, müssen Sie die Ursache dieser Probleme suchen und die Fehler beheben.  

### <a name="set-simple-breakpoints"></a>Festlegen einfacher Haltepunkte  
 Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Sie müssen ein Projekt NICHT neu erstellen, nachdem Sie Haltepunkte festgelegt oder entfernt haben.  

 Legen Sie einen Haltepunkt fest, indem Sie auf den äußeren Rand der Zeile klicken, in der Sie die Unterbrechung einfügen möchten, oder wählen Sie die Codezeile aus, und drücken Sie **F9**. Wenn Sie Code ausführen, wird er direkt vor der Ausführung der Anweisungen für diese Codezeile angehalten (oder *unterbrochen*).  

 ![Visual Studio, Haltepunkt](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")   

 Für Folgendes werden Haltepunkte häufig verwendet:  

1.  Zum Eingrenzen der Ursache eines Absturzes oder einer Blockade können Sie im gesamten Code Haltepunkte verteilen. Außerdem können Sie in der Nähe des Codes für den Methodenaufruf, von dem Sie annehmen, dass er den Fehler verursacht, ebenfalls Haltepunkte platzieren. Wenn Sie den Code im Debugger ausführen, entfernen Sie die Haltepunkte, und platzieren Sie diese dann näher beieinander, bis Sie die fehlerhafte Codezeile finden.  Im nächsten Abschnitt erfahren Sie, wie Sie Code im Debugger ausführen.

2.  Wenn Sie neuen Code einführen, platzieren Sie am Anfang einen Haltepunkt und führen diesen Code aus, um sicherzustellen, dass er sich wie erwartet verhält.

3.  Wenn Sie kompliziertes Verhalten implementiert haben, legen Sie Haltepunkte für den algorithmischen Code fest, damit Sie die Werte von Variablen und die Daten überprüfen können, wenn das Programm unterbrochen wird.  

4.  Wenn Sie Code in C# oder C++ schreiben, verwenden Sie Haltepunkte zum Anhalten des Codes, um die Adresswerte (Suche nach NULL) und Verweiszähler beim Debuggen von speicherbezogenen Fehlern zu überprüfen.  

 Weitere Informationen finden Sie unter [Verwenden von Breakpoints](../debugger/using-breakpoints.md).  

### <a name="inspect-your-code-at-run-time"></a>Überprüfen von Code zur Laufzeit  
 Wenn der ausgeführte Code auf einen Haltepunkt trifft und anhält, wurde die gelb markierte Codezeile (die aktuelle Anweisung) noch nicht ausgeführt. In dieser Situation ist es empfehlenswert, die aktuelle Anweisung auszuführen und anschließend die geänderten Werte zu überprüfen. Sie können mehrere *step*-Befehle zum Ausführen von Code im Debugger verwenden. Ist der gekennzeichnete Code ein Methodenaufruf, durchlaufen Sie diesen schrittweise durch Drücken von **F11**. Sie können die Codezeile durch Drücken von **F10** auch *überspringen*. Zusätzliche Befehle und Details dazu, wie Code schrittweise durchlaufen wird, finden Sie unter [Navigate code with the debugger (Navigieren im Code mit dem Debugger)](../debugger/navigating-through-code-with-the-debugger.md).

 ![Visual Studio, Überprüfung von Laufzeitwerten](../ide/media/vs_ide_gs_debug_hit_breakpoint.PNG "vs_ide_gs_debug_inspect_value")

 Wie in der vorherigen Abbildung dargestellt, kann der Debugger mit **F10** oder **F11** zur nächsten Anweisung springen (da dies kein Methodenaufruf ist, bewirken beide Befehle dasselbe).

 Während der Debugger angehalten ist, können Sie die Variablen und Aufruflisten untersuchen, um herauszufinden, was gerade vorgeht. Liegen die Werte in den erwarteten Bereichen? Werden die Aufrufe in der richtigen Reihenfolge ausgeführt?  

 ![Visual Studio, Überprüfung von Laufzeitwerten](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 Zeigen Sie auf eine Variable, um die Werte und Verweise anzuzeigen, die sie zurzeit enthält. Wenn Sie einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler.  Weitere Informationen finden Sie unter [Learn to debug using Visual Studio (Debuggen mit Visual Studio)](../debugger/getting-started-with-the-debugger.md).

 Darüber hinaus zeigt Visual Studio das Fenster **Diagnosetools** an, in dem Sie den CPU- und Speicherverbrauch Ihrer App im Zeitverlauf beobachten können. In einer späteren Entwicklungsphase können Sie mit diesen Tools nach unvorhergesehen hoher CPU-Auslastung oder Speicherzuweisung suchen. Zusammen mit dem Fenster **Überwachung** und Haltepunkten können Sie so sehr schnell ermitteln, wodurch eine unerwartete Auslastung oder nicht freigegebene Ressourcen verursacht werden.  Weitere Informationen finden Sie unter [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md).

### <a name="run-unit-tests"></a>Komponententests ausführen  
 Komponententests sind die erste Maßnahme zur Vorbeugung von Fehlern im Code. Bei korrekter Ausführung wird dabei eine einzelne „Codeeinheit“ getestet, in der Regel ist dies eine einzelne Funktion. Das Debuggen einer einzelnen Codeeinheit ist sehr viel einfacher als das Debuggen eines vollständigen Programms. Visual Studio enthält die Komponententest-Frameworks von Microsoft für sowohl verwalteten als auch nativen Code. Verwenden Sie ein Unittest-Framework, um Komponententests zu erstellen, auszuführen und Berichte mit den Ergebnissen dieser Tests zu erstellen. Führen Sie Komponententests erneut durch, wenn Sie Änderungen vorgenommen haben, um zu testen, dass der Code weiterhin ordnungsgemäß ausgeführt wird. Wenn Sie Visual Studio Enterprise Edition verwenden, können die Tests automatisch nach jedem Build ausgeführt werden.  

 Weitere Informationen finden Sie unter [Generieren intelligenter Komponententests für Ihren Code mit IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  

 Weitere Informationen zu Komponententests in Visual Studio und wie diese Ihnen helfen, besseren Code zu erstellen, finden Sie unter [Unit Test Basics (Grundlagen zu Komponententests)](../test/unit-test-basics.md).  

### <a name="perform-static-code-analysis"></a>Ausführen statischer Codeanalysen  
 Die „statische Codeanalyse“ stellt eine praktische Möglichkeit dar, den eigenen Code automatisch auf allgemeine Probleme überprüfen zu lassen, die zu Laufzeitfehlern führen oder Probleme bei der Codeverwaltung verursachen können. Gewöhnen Sie sich die Ausführung an, sobald Sie offensichtliche Fehler behoben haben, die das Erstellen verhindern würden. Nehmen Sie sich etwas Zeit, auch die Warnungen zu behandeln. Sie ersparen sich damit einige spätere Probleme und lernen etwas über Stiltechniken beim Codieren.  

 Drücken Sie **ALT+F11** (oder wählen Sie im oberen Menü **Analysieren > Codeanalyse für Projektmappe ausführen** aus), um die statische Codeanalyse zu starten. Dieser Vorgang kann bei umfangreichem Code einige Zeit dauern.  

 ![Visual Studio, Menüelement „Codeanalyse“](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 Alle neuen oder aktualisierten Warnungen werden auf der Registerkarte **Fehlerliste** am unteren Rand der IDE angezeigt. Klicken Sie auf die Warnungen, um zu diesen zu wechseln.  

 ![Visual Studio, Fehlerliste mit Warnungen](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "Vs_ide_gs_debug_code_analysis_warning_error_list")  

 Die Warnungen werden mit einer hellen gelb-grünen Wellenlinie anstelle der roten gekennzeichnet. Bewegen Sie den Mauszeiger darüber, um weitere Details anzuzeigen, und klicken Sie mit der rechten Maustaste darauf, um ein Kontextmenü anzuzeigen, das Optionen zur Korrektur oder zum Refactoring enthält.  

 ![Visual Studio, Draufzeigen auf Warnungen in der Codeanalyse](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

## <a name="see-also"></a>Siehe auch  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)  
 [Weitere Informationen zur Verwendung des Debuggers](../debugger/getting-started-with-the-debugger.md)
