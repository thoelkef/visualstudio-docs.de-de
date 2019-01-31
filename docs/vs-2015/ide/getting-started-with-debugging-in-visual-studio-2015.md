---
title: Erste Schritte beim Debuggen in Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7fecc637a62e96381362d79f66eb5a3cd4d8fa1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764847"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Erste Schritte beim Debuggen in Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 bietet einen leistungsfähigen integrierten Satz von Projektbuild- und Debugtools. Sie erfahren in diesem Thema, wie Sie die grundlegenden Funktionen zum Debuggen von Benutzeroberflächenfunktionen verwenden.

 Hinweis: Links zu erweiterten Features und plattform- oder featurespezifischen Themen befinden sich unten auf dieser Seite.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mein Code funktioniert nicht. Ich benötige Hilfe in Visual Studio 2015.
 Sie haben also herausgefunden, wie der Editor funktioniert, und Code erstellt. Nun möchten Sie mit dem Debuggen von Code beginnen. In Visual Studio 2015 besteht das Debuggen wie bei den meisten IDEs aus zwei Phasen: Erstellen des Codes zum Abfangen und Beheben von Projekt- und Compilerfehlern und Ausführen dieses Codes in der Umgebung zum Abfangen und Beheben von Laufzeit- und dynamischen Fehlern.

### <a name="configuring-a-build"></a>Konfigurieren von Builds
 Es gibt zwei grundlegende Arten der Buildkonfiguration: **Debug** und **Release**. Die erste Konfiguration erzeugt eine langsamere und größere ausführbare Datei, die für ein umfangreicheres interaktives Debuggen zur Laufzeit verwendet werden kann, aber nie ausgeliefert werden sollte. Mit der zweiten wird eine schnellere, optimierte ausführbare Datei erstellt, die (zumindest aus Sicht des Compilers) ausgeliefert werden kann.

 Die Standardbuildkonfiguration ist **Debug**.

 ![Visual Studio, Schaltfläche "Debugversion"](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Sie können auch eine bestimmte Zielplattform für den Build angeben, z. B. **x86** (32-Bit-Intel-CPUs), **x64** (64-Bit-Intel-CPUs) oder **ARM** (ARM-CPUs, nur für bestimmte App-Typen unterstützt). Die Standardeinstellung ist **x86** für verwaltete und native Projekte. Um dies zu ändern, klicken Sie auf die Dropdownliste für die Buildplattform und wählen eine andere Plattform oder den **Konfigurations-Manager** aus.

 ![Visual Studio, Fenster „Konfigurationsdatei-Manager“](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Sie können im **Konfigurations-Manager** die gewünschte Buildkonfiguration angeben. Starten Sie ihn, und klicken Sie auf eine der Dropdownlisten **Konfiguration** oder **CPU**. Wählen Sie dann **Neu...** aus, um einen neuen Build oder eine neue Plattform zu erstellen.

 ![Visual Studio, Fenster „Konfigurations-Manager“](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Verwenden Sie zunächst **Debug** und **x86** als Buildkonfiguration bzw. Plattform. Wenn Sie mit dem Programmieren und Debuggen fertig sind, ändern Sie die Konfiguration in **Release**, und geben Sie die gewünschte Zielplattform an. (In älteren Versionen von Visual Studio wurde die Standardplattform **AnyCPU** für .NET-Codeprojekte bereitgestellt.)

 Hinweis: Wenn Sie das Projekt erstellen, werden die Werte für Konfiguration und Plattform auch verwendet, um den Verzeichnispfad des Projekts zum Speichern der ausführbaren Datei zu bestimmen. Normalerweise ist dies **\<Pfad-zum-Projekt>\\<Projektname>\\<Konfiguration\>\\<Plattform\>**. Beispielsweise würde sich ein Projekt mit der Konfiguration `Debug` und der Plattform `x86` unter `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86` befinden. Dies kann hilfreich sein, wenn Sie eigene Tools oder Skripts zum Verwalten dieser ausführbaren Builddateien verwenden.

### <a name="building-your-code"></a>Erstellen von Code
 Mit Ihrem konfigurierten Build können Sie nun das Projekt erstellen. Die einfachste Möglichkeit besteht darin, F7 zu drücken. Sie können den Build aber auch starten, indem Sie im Hauptmenü **Erstellen > Projektmappe erstellen** auswählen.

 ![Visual Studio, Auswahl im Menü „Projekt erstellen“](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Sie können den Buildprozess im Statusfenster **Ausgabe** am unteren Rand der Visual Studio-Benutzeroberfläche beobachten. Dort werden Fehler, Warnungen und Buildvorgänge angezeigt. Wenn Fehler (oder Warnungen über die konfigurierte Stufe hinaus) auftreten, schlägt der Build fehl. Sie können auf die Fehler und Warnungen klicken, um zu der Zeile zu wechseln, in der der Fehler aufgetreten ist. Erstellen Sie Ihr Projekt neu, indem Sie entweder **F7** erneut drücken (um nur die Dateien mit Fehlern neu zu kompilieren) oder indem Sie **STRG+ALT+F7** drücken (für eine vollständige Neuerstellung).

 Im Ergebnisfenster unterhalb des Editors finden Sie zwei Buildfenster als Registerkarten: Das Fenster **Ausgabe** enthält die unformatierte Compilerausgabe (einschließlich Fehlermeldungen), und das Fenster **Fehlerliste** enthält eine sortierbare und filterfähige Liste aller Fehler und Warnungen.

 Bei erfolgreicher Ausführung werden die Ergebnisse wie folgt im Fenster **Ausgabe** dargestellt.

 ![Visual Studio, erfolgreiche Buildausgabe](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Überprüfen der Fehlerliste
 Sofern Sie keine Änderungen am Code vorgenommen haben, den Sie zuvor erfolgreich kompiliert hatten, tritt vermutlich ein Fehler auf. Wenn Sie noch nie programmiert haben, werden wahrscheinlich viele Fehler auftreten. Fehler sind manchmal offensichtlich, z. B. einfache Syntaxfehler oder falsche Variablennamen, manchmal aber auch schwer zu verstehen, wenn Ihnen nur schwer lesbarer Code zur Verfügung steht. Für eine übersichtlichere Ansicht der Probleme navigieren Sie zum Ende des Fensters **Ausgabe** für den Build, und klicken Sie auf die Registerkarte **Fehlerliste**. Dadurch gelangen Sie zu einer besser angeordneten Ansicht der Fehler und Warnungen für das Projekt mit einigen zusätzlichen Optionen.

 ![Visual Studio 2015, Ausgabe und Fehlerliste](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Klicken Sie im Fenster **Fehlerliste** auf die Zeile mit dem Fehler, um direkt in die Zeile zu springen, in der der Fehler aufgetreten ist. (Oder blenden Sie die Zeilennummern ein, indem Sie oben rechts auf die **Schnellstartleiste** klicken, „Zeilennummern“ eingeben und die EINGABETASTE drücken. Dies ist die schnellste Möglichkeit zum Aufrufen des Fensters **Optionen**, in dem Sie Zeilennummern aktivieren können. Machen Sie sich mit der Verwendung der **Schnellstartleiste** vertraut, denn sie erspart Ihnen viele Klicks auf der Benutzeroberfläche!)

 ![Visual Studio, Editor mit Zeilennummern](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio, Option „Zeilennummern“](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Verwenden Sie STRG+G, um die Nummer der Zeile abzurufen, in der der Fehler aufgetreten ist.

 Der Fehler wird durch eine rote Wellenlinie gekennzeichnet. Bewegen Sie den Mauszeiger darüber, um weitere Informationen anzuzeigen. Wenn Sie die Korrektur vornehmen, wird die Markierung aufgehoben. Es ist natürlich trotzdem möglich, dass Sie mit Ihrer Änderung einen neuen Fehler einfügen. (Dies wird als "Regression" bezeichnet.)

 ![Visual Studio, Draufzeigen auf Fehler](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Bearbeiten Sie die Fehlerliste, und beheben Sie alle Fehler im Code.

 ![Visual Studio, Debugger, Fehlerfenster](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Überprüfen der Fehler im Detail
 Einige Fehler erscheinen Ihnen möglicherweise nicht sinnvoll, wenn sie wie vom Compiler formuliert angezeigt werden. In diesen Fällen benötigen Sie weitere Informationen. Sie können aus dem Fenster **Fehlerliste** heraus eine automatische Suche in Bing nach weiterführenden Informationen über den Fehler (oder die Warnung) durchführen. Klicken Sie dazu mit der rechten Maustaste auf die entsprechende Zeile, und wählen Sie im Kontextmenü **Hilfe zu Fehlern anzeigen** aus.

 ![Visual Studio, Bing-Suche in der Fehlerliste](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Dadurch wird in Visual Studio 2015 eine Registerkarte mit den Ergebnissen einer Bing-Suche nach dem Fehlercode und dem Text angezeigt. Die Ergebnisse stammen aus verschiedenen Quellen im Internet und sind möglicherweise nicht alle hilfreich.

 Sie können auch auf den als Link formatierten Fehlercode in der Spalte **Code** in der **Fehlerliste** klicken. Hierdurch wird eine Suche in Bing nur nach dem Fehlercode durchgeführt.

### <a name="performing-static-code-analysis"></a>Ausführen statischer Codeanalysen
 Die "statische Codeanalyse" stellt eine praktische Möglichkeit dar, den eigenen Code automatisch auf allgemeine Probleme überprüfen zu lassen, die zu Laufzeitfehlern führen oder Probleme bei der Codeverwaltung verursachen können. Gewöhnen Sie sich die Ausführung an, sobald Sie offensichtliche Fehler behoben haben, die das Erstellen verhindern würden. Nehmen Sie sich etwas Zeit, auch die Warnungen zu behandeln. Sie ersparen sich damit einige spätere Probleme und lernen etwas über Stiltechniken beim Codieren.

 Drücken Sie ALT+F11 (oder wählen Sie im oberen Menü **Analysieren > Codeanalyse für Projektmappe ausführen** aus), um die statische Codeanalyse zu starten. Dieser Vorgang kann bei umfangreichem Code einige Zeit dauern.

 ![Visual Studio 2015-Codeanalyse-Menüelement](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Alle neuen oder aktualisierten Warnungen werden auf der Registerkarte **Fehlerliste** am unteren Rand der IDE angezeigt. Klicken Sie auf die Warnungen, um zu diesen zu wechseln.

 ![Visual Studio 2015, Fehlerliste mit Warnungen](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "Vs_ide_gs_debug_code_analysis_warning_error_list")

 Die Warnungen werden mit einer hellen gelb-grünen Wellenlinie anstelle der roten gekennzeichnet. Bewegen Sie den Mauszeiger darüber, um weitere Details anzuzeigen, und klicken Sie mit der rechten Maustaste darauf, um ein Kontextmenü anzuzeigen, das Optionen zur Korrektur oder zum Refactoring enthält.

 ![Visual Studio, Draufzeigen auf Warnungen in der Codeanalyse](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Verwenden von Glühbirnen zum Beheben oder Umgestalten von Code
 Glühbirnen sind ein neues Feature von Visual Studio 2015, mit dem Sie Code inline umgestalten können. Damit können allgemeine Warnungen schnell und effektiv behoben werden. Um darauf zuzugreifen, klicken Sie mit der rechten Maustaste auf die Wellenlinie einer Warnung (oder drücken Sie „STRG+.“, während Sie auf die Wellenlinie zeigen), und wählen Sie dann **Schnelle Aktionen** aus.

 ![Visual Studio 2015, Glühbirne mit schnelloptionen](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Es wird eine Liste der möglichen Korrekturen oder Umgestaltungen angezeigt, die Sie auf diese Codezeile anwenden können.

 ![Vorschau für Visual Studio 2015, Glühbirne](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Glühbirnen können überall dort angewendet werden, wo die Codeanalyse Möglichkeiten zur Problembehebung, Umgestaltung oder Verbesserung Ihres Codes erkannt hat. Klicken Sie mit der rechten Maustaste auf eine beliebige Codezeile, um das Kontextmenü zu öffnen, und wählen Sie **Schnelle Aktionen** aus (oder drücken Sie „STRG+.“). Wenn es Möglichkeiten zur Umgestaltung oder Verbesserung gibt, werden diese angezeigt. Andernfalls wird die Meldung `No quick options available here` in der unteren linken Ecke der IDE angezeigt.

 ![Visual Studio 2015, Glühbirne "keine Option" Text](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Mit etwas Erfahrung können Sie rasch mithilfe der Pfeiltasten und STRG+. überprüfen, ob schnelle Aktionen zur Umgestaltung und Bereinigung Ihres Codes verfügbar sind.

 Weitere Informationen zu Glühbirnen finden Sie unter [Durchführen schneller Aktionen mit Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Debuggen von ausgeführtem Code
 Nachdem Sie Code erstellt und einige Bereinigungen durchgeführt haben, führen Sie ihn aus, indem Sie F5 drücken oder **Debuggen > Debuggen starten** auswählen. Dadurch wird Ihre App in einer Debugumgebung gestartet, damit Sie ihr Verhalten im Detail beobachten können. Die Visual Studio 2015-IDE ändert sich während der Ausführung Ihrer App: Das Fenster **Ausgabe** wird (in der Standardfensterkonfiguration) durch zwei neue ersetzt, und zwar durch die Registerkartenfenster **Auto/Lokal/Module/Überwachung** und **Aufrufliste/Haltepunkte/Ausnahmeeinstellungen/Ausgabe**. Diese Fenster enthalten mehrere Registerkarten, mit denen Sie Variablen, Threads, Aufruflisten und andere Verhaltensweisen während der Ausführung Ihrer App überprüfen und bewerten können.

 ![Visual Studio 2015 "Auto", und rufen Windows Stack](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Führen Sie verschiedene Aktionen mit Ihrer App durch, und beobachten Sie die Änderungen. Wenn etwa ungewöhnlich erscheint, halten Sie die App-Ausführung an, indem Sie STRG+ALT+UNTBR drücken (oder klicken Sie auf die Schaltfläche **Pause**).

 ![Visual Studio, Schaltfläche „Alle unterbrechen“](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Drücken Sie F5, um die App weiter auszuführen (oder klicken Sie auf die Schaltfläche **Fortfahren**).

 ![Visual Studio, Debugschaltfläche „Fortfahren“](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Sie können Ihre App beenden, indem Sie UMSCHALT+F5 drücken oder auf die Schaltfläche **Stopp** klicken. Sie können die App auch einfach durch Schließen des Hauptfensters (oder über die Befehlszeile) schließen.

 Wenn Ihr Code ohne besondere Vorkommnisse genau wie erwartet ausgeführt wurde, sind Sie damit fertig! Ändern Sie die Buildkonfiguration in **Release**, und erstellen Sie den Build für die Bereitstellung neu. (IT-Experten sollten allerdings mit dem Abschnitt zu Unittests am Ende fortfahren.) Wenn der Code jedoch nicht mehr reagiert oder abgestürzt, oder wenn Sie unerwartete Ergebnissen erhalten, müssen Sie die Ursache dieser Probleme suchen und die Fehler beheben.

### <a name="setting-simple-breakpoints"></a>Festlegen einfacher Haltepunkte
 Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Sie müssen ein Projekt NICHT neu erstellen, nachdem Sie Haltepunkte festgelegt oder entfernt haben.

 Legen Sie einen Haltepunkt fest, indem Sie auf den äußeren Rand der Zeile klicken, in der Sie die Unterbrechung einfügen möchten, oder wählen Sie die Codezeile aus, und drücken Sie F9. Wenn Sie Code ausführen, wird er direkt vor der Ausführung der Anweisungen für diese Codezeile angehalten.

 ![Visual Studio, Haltepunkt](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Wenn der Code unterbrochen wird, wurde die markierte Codezeile noch nicht ausgeführt. An diesem Punkt können Sie die Anweisungen für die Codezeile ausführen, die durch den Haltepunkt markiert wurde, und die geänderten Werte überprüfen. Dies wird als "schrittweises Durchlaufen des Codes" bezeichnet. Ist der gekennzeichnete Code ein Methodenaufruf, durchlaufen Sie diesen schrittweise durch Drücken von F11. Sie können die Codezeile durch Drücken von F10 auch „überspringen“. Weitere Informationen für Schrittaktionen für Haltepunkte finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).

 Für Folgendes werden Haltepunkte häufig verwendet:

1. Zum Eingrenzen der Ursache eines Absturzes oder einer Blockade können Sie im gesamten Code Haltepunkte verteilen. Außerdem können Sie in der Nähe des Codes für den Methodenaufruf, von dem Sie annehmen, dass er den Fehler verursacht, ebenfalls Haltepunkte platzieren. Wenn Sie den Code durchlaufen, entfernen Sie die Haltepunkte und platzieren sie dann näher beieinander, um die fehlerhafte Codezeile einzugrenzen.

2. Wenn Sie neuen Code einführen, platzieren Sie einen Haltepunkt am Anfang dieses Codes und durchlaufen diesen dann, um sicherzustellen, dass er sich wie erwartet verhält.

3. Wenn Sie kompliziertes Verhalten implementiert haben, legen Sie Haltepunkte für den algorithmischen Code fest, damit Sie die Werte von Variablen und die Daten überprüfen können, wenn das Programm unterbrochen wird.

4. Wenn Sie Code in C# oder C++ schreiben, verwenden Sie Haltepunkte zum Anhalten des Codes, um die Adresswerte (Suche nach NULL) und Verweiszähler beim Debuggen von speicherbezogenen Fehlern zu überprüfen.

   Weitere Informationen zur Verwendung von Haltepunkten finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).

### <a name="setting-conditional-breakpoints"></a>Festlegen bedingter Haltepunkte
 Verwenden Sie bei Haltepunkten in einer Schleife oder Rekursion oder bei sehr vielen Haltepunkten, die Sie häufig schrittweise durchlaufen, einen bedingten Haltepunkt, damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind. Andernfalls müssen Sie sehr häufig F11 drücken.

 Für das Festlegen eines bedingten Haltepunkts, bei dem die Ausführung automatisch fortgesetzt wird, wenn eine Variable auf einen bestimmten Wert festgelegt ist oder einen bestimmten Schwellenwert übersteigt, klicken Sie auf den Rand, um einen Haltepunkt festzulegen, und wählen Sie dann im angezeigten Menü das "Zahnrad" aus.

 ![Visual Studio 2015, haltepunkteinstellungen](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Es wird ein Dialogfeld angezeigt, das wie folgt aussieht und in dem Sie bestimmte Bedingungen für die Unterbrechung festlegen können.

 ![Visual Studio 2015, bedingter Haltepunkt](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Weitere Informationen zum Deklarieren der Ausdrücke für das Auswerten bedingter Haltepunkte finden Sie im Channel9-Video [Breakpoint Configuration Experience in Visual Studio 2015 (Oberfläche zum Konfigurieren von Haltepunkten in Visual Studio 2015)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Überprüfen von Code zur Laufzeit
 Wenn der ausgeführte Code an einem Haltepunkt anhält, können Sie die Variablen und Aufruflisten untersuchen, um die gerade ausgeführte Aktion zu ermitteln. Liegen die Werte in den erwarteten Bereichen? Werden die Aufrufe in der richtigen Reihenfolge ausgeführt?

 ![Visual Studio 2015 ausgeführt&#45;werteprüfung zur Zeit](../ide/media/vs-ide-gs-debug-inspect-value.PNG "Vs_ide_gs_debug_inspect_value")

 Zeigen Sie auf eine Variable, um die Werte und Verweise anzuzeigen, die sie zurzeit enthält. Wenn Sie einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler. Verschieben Sie Haltepunkte nach oben, oder fügen Sie vorhandenen Haltepunkten Bedingungen hinzu, um die Suche weiter einzugrenzen.

 Darüber hinaus zeigt Visual Studio 2015 das Fenster mit den Diagnosetools an, in dem Sie den CPU- und Speicherverbrauch Ihrer App im Zeitverlauf beobachten können. Verwenden Sie diese, um nach unerwartet hoher CPU-Auslastung oder Arbeitsspeicherzuordnungen zu suchen. Zusammen mit dem Fenster **Überwachung** und Haltepunkten können Sie so sehr schnell ermitteln, wodurch eine unerwartete Auslastung oder nicht freigegebene Ressourcen verursacht werden.

 ![Visual Studio 2015-Diagnosetools-Fenster](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Ausführen von Komponententests
 Komponententests sind Programme, die Codepfade in Ihrer App oder Ihrem Dienst ausführen. Visual Studio 2015 enthält die Komponententest-Frameworks von Microsoft für sowohl verwalteten als auch systemeigenen Code. Verwenden Sie ein Unittest-Framework, um Komponententests zu erstellen, auszuführen und Berichte mit den Ergebnissen dieser Tests zu erstellen. Führen Sie Komponententests erneut durch, wenn Sie Änderungen vorgenommen haben, um zu testen, dass der Code weiterhin ordnungsgemäß ausgeführt wird. Wenn Sie Visual Studio 2015 Enterprise verwenden, können die Tests automatisch nach jedem Build ausgeführt werden.

 Weitere Informationen finden Sie unter [Generieren intelligenter Komponententests für Ihren Code mit IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Weitere Informationen zu Komponententests in Visual Studio 2015 und wie sie Ihnen helfen, besseren Code zu erstellen, finden Sie unter [Unit Test Basics (Grundlagen zu Komponententests)](../test/unit-test-basics.md).

## <a name="see-also"></a>Siehe auch
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md) [Debugger, Einstellungen und Vorbereitung](../debugger/debugger-settings-and-preparation.md) [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md) [Debugger – Grundlagen](../debugger/debugger-basics.md)
