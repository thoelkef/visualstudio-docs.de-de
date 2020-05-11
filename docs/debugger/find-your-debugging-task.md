---
title: Finden der Debugaufgabe
description: Identifizieren des Debuggerfeatures, das Sie beim Debuggen Ihrer App unterstützt
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301146"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Finden der Debugaufgabe in Visual Studio

Wenn Sie Hilfe benötigen, um die Debugaufgabe der richtigen Funktion des Visual Studio-Debuggers zuzuordnen, die relevant ist, verwenden Sie die in diesem Artikel bereitgestellten Links. Die Liste der Aufgaben enthält allgemeine Aufgaben, z. B. das Anhalten von Code zum Debuggen, Untersuchen von Variablen und Senden von Meldungen an das **Ausgabe**fenster. Einen allgemeineren Überblick über die Funktionen des Debuggers finden Sie unter [Ein erster Blick auf den Debugger](debugger-feature-tour.md).

## <a name="pause-running-code"></a>Anhalten von aktuell ausgeführtem Code

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Anhalten des ausgeführten Codes, um eine Codezeile zu untersuchen, die möglicherweise einen Fehler enthält

Festlegen eines Haltepunkts. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Anhalten und Untersuchen der App, wenn sie einen bestimmten Zustand erreicht

Probieren Sie einen bedingten Breakpoint aus, um mithilfe von bedingter Logik zu steuern, wo und wann ein Breakpoint aktiviert wird. Weitere Informationen finden Sie unter [Breakpointbedingungen](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Code nur anhalten, wenn sich die Eigenschaft oder der Wert eines bestimmten Objekts ändert

Legen Sie für C++ einen [Datenbreakpoint](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus) fest. 
::: moniker range=">= vs-2019"
Für Apps, die .NET Core 3 verwenden, können Sie ebenfalls einen [Datenbreakpoint](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed) festlegen.
::: moniker-end

Andernfalls können Sie nur für C# und F# eine [Objekt-ID mit einem bedingten Breakpoint nachverfolgen](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Anhalten von Code innerhalb einer Schleife bei einer bestimmten Iteration

Legen Sie einen Breakpoint mithilfe von **Trefferanzahl** als Bedingung fest. Weitere Informationen finden Sie unter [Trefferanzahl](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Anhalten von Code am Anfang einer Funktion, wenn Sie den Funktionsnamen, aber nicht den Speicherort kennen

Hierfür können Sie einen Funktionsbreakpoint verwenden. Weitere Informationen finden Sie unter [Festlegen von Funktionbreakpoints](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Anhalten von Code am Anfang mehrerer Funktionen mit dem gleichen Namen

Wenn Sie über mehrere Funktionen mit dem gleichen Namen (überladene Funktionen oder Funktionen in unterschiedlichen Projekten) verfügen, können Sie einen [Funktionsbreakpoint](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file) verwenden.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Verwalten und Nachverfolgen von Breakpoints

Verwenden Sie das Fenster **Breakpoints**. Weitere Informationen finden Sie unter [Verwalten von Breakpoints](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Anhalten von Code und Debuggen, wenn eine bestimmte behandelte oder nicht behandelte Ausnahme ausgelöst wird

Obwohl das Ausnahmehilfsprogramm zeigt, wo ein Fehler aufgetreten ist, können Sie den [Debugger anweisen, eine Unterbrechung vorzunehmen, wenn eine Ausnahme ausgelöst wird](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown), wenn Sie die Ausführung anhalten und den spezifischen Fehler debuggen möchten.

### <a name="set-a-breakpoint-from-the-call-stack"></a>Festlegen eines Breakpoints aus der Aufrufliste

Wenn Sie Code anhalten und debuggen möchten, während Sie den Ausführungsfluss untersuchen oder Funktionen in den **Aufruflistenfenstern** anzeigen, finden Sie weitere Informationen unter [Festlegen eines Breakpoints im Aufruflistenfenster](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Anhalten von Code an einer bestimmten Assemblyanweisung

Dies können Sie erreichen, indem Sie im [Fenster „Disassemblierung“ einen Breakpoint festlegen](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ausführen von Code

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Erlernen der Befehle zum schrittweisen Durchlaufen des Codes während des Debuggens

Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Untersuchen von Daten

### <a name="check-the-value-of-variables-while-running-your-app"></a>Überprüfen des Werts von Variablen beim Ausführen der App

Zeigen Sie mit der Maus auf Variablen, und verwenden Sie [Datentipps](view-data-values-in-data-tips-in-the-code-editor.md), oder [untersuchen Sie Variablen im Fenster für automatische und lokale Variablen](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Beobachten des sich ändernden Werts einer bestimmten Variablen

Legen ein Überwachungselement für die Variable fest. Weitere Informationen finden Sie unter [Festlegen eines Überwachungselements für Variablen](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Anzeigen von Zeichenfolgen, die zu lang für das Debuggerfenster sind

Öffnen Sie beim Debuggen die integrierte [Zeichenfolgenschnellansicht](view-strings-visualizer.md).

## <a name="configure-debugging"></a>Konfigurieren des Debuggens

### <a name="customize-information-shown-in-the-debugger"></a>Anpassen der im Debugger angezeigten Informationen

Möglicherweise möchten Sie andere Informationen als den Objekttyp als Wert in anderen Debuggerfenstern anzeigen. Verwenden Sie für C#-, Visual Basic-, F#- und C++/CLI-Code das [DebuggerDisplay](using-the-debuggerdisplay-attribute.md)-Attribut. Für erweiterte Optionen können Sie die Benutzeroberfläche auch anpassen, indem Sie eine [benutzerdefinierte Schnellansicht](create-custom-visualizers-of-data.md) erstellen.

Verwenden Sie für natives C++ das [NatVis-Framework](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurieren von Debuggereinstellungen

Weitere Informationen zum Konfigurieren von Debuggeroptionen und Debuggerprojekteinstellungen finden Sie unter [Debuggereinstellungen und -vorbereitung](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Zusätzliche Aufgaben

### <a name="fix-an-exception"></a>Beseitigen einer Ausnahme

Weitere Informationen finden Sie unter [Beseitigen einer Ausnahme](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Bearbeiten von Code während einer Debugsitzung

Verwenden Sie [Bearbeiten und fortfahren](edit-and-continue.md). Verwenden Sie für XAML [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Senden von Nachrichten an das Ausgabefenster, ohne Code zu ändern

Legen Sie einen Ablaufverfolgungspunkt fest. Weitere Informationen finden Sie unter [Verwenden von Ablaufverfolgungspunkten](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Anzeigen der Reihenfolge, in der Funktionen aufgerufen werden

Weitere Informationen finden Sie unter [Anzeigen der Aufrufliste](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Debuggen auf Remotecomputern

Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Debuggen einer App, die bereits ausgeführt wird

Weitere Informationen finden Sie unter [Anfügen an laufenden Prozess](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Debuggen von Multithreadanwendungen

Weitere Informationen finden Sie unter [Debuggen von Multithreadanwendungen](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Weitere Informationen finden Sie unter [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)