---
title: Finden der Debugaufgabe
description: Identifizieren Sie das Debugger-Feature, mit dem Sie Ihre APP Debuggen können.
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578767"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Suchen Ihres debugtasks in Visual Studio

Wenn Sie Hilfe benötigen, um die debugaufgabe der richtigen Funktion des Visual Studio-Debuggers zuzuordnen, die relevant ist, verwenden Sie die in diesem Artikel bereitgestellten Links. Die Liste der Aufgaben enthält allgemeine Aufgaben, z. b. das Anhalten von Code zum Debuggen, überprüfen von Variablen und Senden von Nachrichten an das **Ausgabe** Fenster. Wenn Sie einen Überblick über die Debugger-Funktionen benötigen, finden Sie weitere Informationen unter [dem Debugger](debugger-feature-tour.md) .

## <a name="pause-running-code"></a>Ausführen von Code anhalten

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Anhalten des laufenden Codes, um eine Codezeile zu überprüfen, die möglicherweise einen Fehler enthält

Festlegen eines Haltepunkts. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Anhalten und Überprüfen der APP, wenn Sie einen bestimmten Zustand erreicht

Verwenden Sie einen bedingten Haltepunkt, um zu steuern, wo und wann ein Breakpoint mithilfe bedingter Logik aktiviert wird. Weitere Informationen finden Sie unter [breakpointbedingungen](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Code nur anhalten, wenn sich die Eigenschaft oder der Wert eines bestimmten Objekts ändert

Legen C++Sie für einen [Daten Breakpoint](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)fest. 
::: moniker range=">= vs-2019"
Für apps, die .net Core 3 verwenden, können Sie auch einen [Daten Haltepunkt](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)festlegen.
::: moniker-end

Andernfalls können Sie C# für F# und nur [eine Objekt-ID mit einem bedingten Haltepunkt verfolgen](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Anhalten von Code innerhalb einer Schleife bei einer bestimmten Iterationen

Legen Sie einen Breakpoint mithilfe der **Treffer Anzahl** als Bedingung fest. Weitere Informationen finden Sie unter [Treffer Anzahl](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Anhalten von Code am Anfang einer Funktion, wenn Sie den Funktionsnamen, aber nicht seinen Speicherort kennen

Hierfür können Sie einen Funktions Haltepunkt verwenden. Weitere Informationen finden Sie unter [Festlegen von Funktions Breakpoints](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Anhalten von Code am Anfang mehrerer Funktionen mit gleichem Namen

Wenn Sie über mehrere Funktionen mit dem gleichen Namen (überladene Funktionen oder Funktionen in unterschiedlichen Projekten) verfügen, können Sie einen Funktions-halte [Punkt](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)verwenden.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Verwalten und Nachverfolgen von Haltepunkten

Verwenden Sie das Fenster **Breakpoints** . Weitere Informationen finden Sie unter [Verwalten von Breakpoints](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Anhalten von Code und Debuggen, wenn eine bestimmte behandelte oder nicht behandelte Ausnahme ausgelöst wird

Obwohl das Exception-Hilfsprogramm anzeigt, wo ein Fehler aufgetreten ist, können Sie [den Debugger anweisen](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown), den Fehler zu unterbrechen, wenn eine Ausnahme ausgelöst wird, wenn Sie den spezifischen Fehler anhalten und debuggen möchten.

### <a name="set-a-breakpoint-from-the-call-stack"></a>Festlegen eines halte Punkts in der aufrufsstapel

Wenn Sie den Code anhalten und debuggen möchten, während Sie den Ausführungs-oder Anzeigefunktionen in den Fenster der Fenster **Aufrufe** untersuchen, finden Sie weitere Informationen unter [Festlegen eines Breakpoints im Fenster "Fenster](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)".

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Anhalten von Code an einer bestimmten Assemblyanweisung

Dies können Sie erreichen, indem Sie [im Fenster Disassembly einen Haltepunkt festlegen](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Code ausführen

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Erlernen der Befehle zum Durchlaufen des Codes während des Debuggens

Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Überprüfen von Daten

### <a name="check-the-value-of-variables-while-running-your-app"></a>Überprüfen Sie beim Ausführen der APP den Wert der Variablen.

Zeigen Sie mithilfe von [Daten Tipps](view-data-values-in-data-tips-in-the-code-editor.md) auf Variablen, oder über [prüfen Sie die Variablen im Fenster Auto und](autos-and-locals-windows.md)lokal.

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Beobachten des veränderlichen Werts einer bestimmten Variablen

Legen Sie eine Überwachung für die Variable fest. Weitere Informationen finden Sie unter [Festlegen einer Überwachung für Variablen](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Anzeigen von Zeichen folgen, die für das Debugger-Fenster zu lang sind

Öffnet die integrierte [Zeichen](view-strings-visualizer.md) folgen Schnellansicht während des Debuggens.

## <a name="configure-debugging"></a>Konfigurieren des Debuggens

### <a name="customize-information-shown-in-the-debugger"></a>Im Debugger angezeigte Informationen anpassen

Möglicherweise möchten Sie andere Informationen als den Objekttyp als Wert in verschiedenen Debuggerfenstern anzeigen. Verwenden C#Sie für- F#, Visual Basic C++-,-und/CLI-Code das [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) -Attribut. Für erweiterte Optionen können Sie auch die Benutzeroberfläche anpassen, indem Sie eine [benutzerdefinierte](create-custom-visualizers-of-data.md)Schnellansicht erstellen.

Verwenden Sie C++für Native das [natvis-Framework](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Debugger-Einstellungen konfigurieren

Informationen zum Konfigurieren von Debuggeroptionen und debuggerprojekteinstellungen finden Sie unter [Debugger-Einstellungen und-Vorbereitung](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Zusätzliche Aufgaben

### <a name="fix-an-exception"></a>Beheben einer Ausnahme

Siehe [beheben einer Ausnahme](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Bearbeiten von Code während einer Debugsitzung

Verwenden Sie [Bearbeiten und Fortfahren](edit-and-continue.md). Verwenden Sie für XAML das [heiße Laden von XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Senden von Nachrichten an das Ausgabefenster, ohne Code zu ändern

Legen Sie einen Ablauf Verfolgungs Punkt fest. Weitere Informationen finden Sie unter [verwenden](using-tracepoints.md)von Ablauf Verfolgungs Punkten.

## <a name="view-the-order-in-which-functions-are-called"></a>Anzeigen der Reihenfolge, in der Funktionen aufgerufen werden

Siehe [How to View the callstack](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Debuggen auf Remote Computern

Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Eine APP Debuggen, die bereits ausgeführt wird

Siehe [Anfügen an einen laufenden Prozess](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Debuggen von Multithreadanwendungen

Siehe [Debuggen von Multithreadanwendungen](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Siehe [erster Einblick in die Profil](../profiling/profiling-feature-tour.md) Erstellungs Tools